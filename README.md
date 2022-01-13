# 作业小程序
```
关于小程序登陆一些总结：
有关链接：
https://developers.weixin.qq.com/community/develop/doc/000cacfa20ce88df04cb468bc52801
https://viencoding.com/article/300
https://developers.weixin.qq.com/community/develop/article/doc/00062e6c7a8a081949fb8959656813

首先：wx.getSetting + wx.getUserInfo 和wx.login 都是需要的
wx.login 通过code 传给服务端  服务端通过code调用微信api，获取session_key,再结合wx.getUserInfo获取的用户加密信息，就可以
在服务端通过调用微信提供的api就可以解密出用户的详细信息了，如下，所以需要两者结合的
注意点：session_key会过期的，可以用微信维护的session_key作为用户的过期验证，也可以自己去定义过期机制，自己维护
{
  "openId": "OPENID",
  "nickName": "NICKNAME",
  "gender": GENDER,
  "city": "CITY",
  "province": "PROVINCE",
  "country": "COUNTRY",
  "avatarUrl": "AVATARURL",
  "unionId": "UNIONID",
  "watermark": {
    "appid":"APPID",
    "timestamp":TIMESTAMP
  }
}
如需要获取手机号码  这是另外的功能接口。

占位组件：
用时注入」可以指定一部分自定义组件不在小程序启动时注入，而是在真正渲染的时候才进行注入。
在已经指定 lazyCodeLoading 为 requiredComponents 的情况下，为自定义组件配置 占位组件，组件就会自动被视为用时注入组件：

感觉这个就像是：颗粒度更细的优化
```
