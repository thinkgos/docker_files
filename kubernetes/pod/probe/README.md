# 健康检查
为了确保容器在部署后确实处在正常运行状态，Kubernetes 提供了两种探针（Probe）来探测容器的状态：
- LivenessProbe：探测应用是否处于健康状态，如果不健康则删除并重新创建容器。
- ReadinessProbe：探测应用是否启动完成并且处于正常服务状态，如果不正常则不会接收来自 Kubernetes Service 的流量，即将该Pod从Service的endpoint中移除。

Kubernetes 支持三种方式来执行探针：
- exec：在容器中执行一个命令，如果 命令退出码 返回 0 则表示探测成功，否则表示失败
- tcpSocket：对指定的容器 IP 及端口执行一个 TCP 检查，如果端口是开放的则表示探测成功，否则表示失败
- httpGet：对指定的容器 IP、端口及路径执行一个 HTTP Get 请求，如果返回的 状态码 在 [200,400) 之间则表示探测成功，否则表示失败
[健康检查](https://kubernetes.feisky.xyz/concepts/objects/pod#jian-kang-jian-cha)