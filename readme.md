# Confluence 对接 Feishu

目标：
```bash
通过飞书客户端或Chrome浏览器免登陆（借助飞书身份验证）进入confluence wiki系统，避免二次登录。
```

流程图:

<p align="center">
	<img src="./docs/static/process.png?raw=true" width="90%" height="90%">
</p>


1. 用户通过浏览器或飞书客户端打开Wiki应用.
2. 反向代理服务通过session判断该请求是否登录,如果已登录,代理转到Wiki请求.否则重定向到飞书身份验证页面.
3. 等待用户完成飞书身份验证(飞书确认页面)
4. 验证完成,通过access_token到获取到当前用户的基础信息.
5. 根据获取到用户基础信息,登录Wiki系统.
6. 登录成功后,返回用户请求页面.


----

## Confluence配置

1. 站点管理->安全配置->登录验证码->关闭(不要勾选)
2. 站点管理->安全配置->保护管理员事务->关闭(不要勾选)
3. 配置访问域名  
4. 站点管理->一般配置->站点配置->服务器主页URL

----

##  开发资料

<a href="https://open.feishu.cn/document/ukTMukTMukTM/uETOwYjLxkDM24SM5AjN">飞书开发文档</a>
```bash
https://open.feishu.cn/document/ukTMukTMukTM/uETOwYjLxkDM24SM5AjN
```


<a href="https://developer.atlassian.com/cloud/confluence/rest/api-group-users/#api-api-user-get">Confluence 开发文档</a>
```bash
https://developer.atlassian.com/cloud/confluence/rest/api-group-users/#api-api-user-get
```
