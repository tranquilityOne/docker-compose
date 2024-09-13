### Docker-Compose 一键部署分布式配置中心Apollo 注意事项

1. LOCAL_HOST_ADDRESS 为本机local host ip, 非外网IP
2. eureka 配置修改：  
`update  apolloconfigdb.serverconfig set Value = 'http://1LOCAL_HOST_ADDRESS:8080/eureka/' where `key` ='eureka.service.url';` 
3. 指定 EUREKA_INSTANCE_IP_ADDRESS 为 LOCAL_HOST_ADDRESS。这里如果不指定具体的IP，默认为容器内部ip,会导致注册eureka失败


#### 本地测试部署注意事项

 LOCAL_HOST_ADDRESS 为Docker或WSL 分配的动态IP, 192.168.X.X  
  windows 可通过ipconfig查找，如：Ethernet adapter vEthernet (WSL):等分配的IPV4地址。

#### 参考资料
https://github.com/apolloconfig/apollo/wiki/%E9%83%A8%E7%BD%B2&%E5%BC%80%E5%8F%91%E9%81%87%E5%88%B0%E7%9A%84%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98  
https://github.com/yuefengkai/Brook.Apollo  这里有client demo代码