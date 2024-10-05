Spheron 网络工作节点
Spheron 的 Fizz 节点为任何希望为 Spheron 的去中心化计算网络贡献资源的人提供了一个低门槛的入口，并为他们的贡献获得持续的奖励。

无论您希望运行基本的 CPU 配置还是强大的 GPU 设置，本指南将引导您完成整个过程。

您将获得 $FN 积分，最终将与 $SPHN 代币合并

运行 Fizz 节点的分步指南
硬件要求


注册 Fizz 节点
打开您的浏览器：导航至 https://fizz.spheron.network
注册或登录：通过 Gmail 或 Github 注册或登录
点击“注册新的 Fizz 节点” 按钮并连接您的钱包


选择您的节点配置：选择您的节点的操作系统、资源、地区、支付代币和提供商（我选择了最高级别的提供商）


点击“注册您的 Fizz 节点”：要完成注册，您需要在 Spheron 链上有一些 ETH 作为燃料费。如果您没有，可以从我们的水龙头获取：https://faucet.spheron.network


运行 Fizz 节点
下载脚本：在已注册节点的设置页面，您应该找到一个链接来下载 fizzup.sh 脚本


传输脚本到 VPS：将 fizzup.sh 脚本下载到您的电脑。使用 Mobaxterm 或 Termius 客户端将其发送到您的 VPS

安装 Docker

bash
复制代码
sudo apt update -y && sudo apt upgrade -y
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo chmod +x /usr/local/bin/docker-compose

# 检查 Docker 版本
docker --version
赋予脚本权限
bash
复制代码
# 假设您将脚本传输到服务器的主（根）文件夹
chmod +x /root/fizzup.sh
运行 Fizz 节点脚本
bash
复制代码
./fizzup.sh


提示：如果您的节点提供更高等级的资源，如强大的 GPU 或更多的 CPU 核心，您将获得更多收益。

注意：Fizz 节点必须在一个 ERA（24 小时）内至少保持 50% 的正常运行时间才能获得奖励。

备注：我使用仅 CPU 运行了此节点，但您可以使用 GPU 运行以获得更多奖励。

检查节点健康状况
bash
复制代码
docker compose -f ~/.spheron/fizz/docker-compose.yml logs -f
或

bash
复制代码
docker-compose -f ~/.spheron/fizz/docker-compose.yml logs -f


确认节点正在运行后，返回 Spheron Fizz 应用程序的设置页面：

手动检查状态：在设置页面，您将看到一个“检查状态”按钮和一个“自动检查状态”开关。点击“检查状态”按钮手动启动对您的 Fizz 节点的状态检查

自动检查状态：或者，您可以打开“自动检查状态”开关，让系统定期检查您的节点状态，而无需手动干预



等待验证：系统现在将执行检查，以验证您的节点是否处于活动状态且配置正确
验证过程可能需要几分钟。在此期间，系统会验证您的节点的连接性、资源可用性和配置。一旦您的节点被确认处于活动状态，您将自动被引导到您的 Fizz 仪表板



在仪表板中领取您的 NFT


加入 Discord 并领取您的角色
Discord：https://discord.gg/spheron-network-745315423783878757
角色领取：https://guild.xyz/spheronfdn


Intract 角色
完成此 任务 并领取一个角色

使用 htop 检查您的 VPS 资源（RAM、CPU）
bash
复制代码
# 安装 htop
sudo apt install htop

# 运行 htop
htop
