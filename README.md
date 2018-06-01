安装注意事项和步骤
================
脚本暂时只支持ubuntu系统，offline版还没有更新

这个主要是kolla-openstack的kolla_prepare前期准备脚本和kolla_deploy部署脚本
kolla_prepare分为online版和offline版，offline版主要用的是本地源，online和offline都是用的本地镜像仓库
kolla_prepare主要是前期给安装openstack的集群安装拷贝python包、安装pip、安装依赖包、安装linux镜像扩展、安装容器、注册镜像仓库和重启。
kolla_deploy主要是启动mysql和deploy镜像，用于安装kolla的页面部署使用

第一步: 前期准备
-----------------

* inventory: hosts,先修改kolla_prepare和kolla_deploy的host
* 修改变量: 修改harbor_ip、mysql镜像和deploy镜像ip变量
* 执行命令: ansible-playbook -i hosts kolla_deploy.yml --tags prepare_online/prepare_offline


第二步: 部署deploy镜像
----------------
* 执行命令: ansible-playbook -i raid_hosts kolla_deploy.yml --tags deploy


