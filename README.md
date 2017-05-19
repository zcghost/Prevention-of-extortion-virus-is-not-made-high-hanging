### 预防勒索病毒,事不发己,高高挂起

![](http://i.imgur.com/XMF0EZD.gif)

前言:

从5月12号至今,影响范围大,波及广,响度大变种的勒索病毒(WannaCry)持续升温发酵,可谓史无前例,空前浩荡,来势凶猛,政府,学校,医院,公安等固持守旧,不愿意接受新事物,停滞不前,懒于升级系统的怀旧者来说,无一幸免,至于什么是勒索病毒,可百度百科,虽事不发己,但需高高挂起,一旦电脑被感染,绝非非典那么容易遏止,若无备份,电脑的文件,图片,视频,文件等被强行加密,无法访问,提示受害用户支付赎金,方可解密,况且付费了也不一定能得到解决,因为犯罪分子往往是言而无信的,种子没了,可以在下,系统坏了,可以重装,银行密码忘了,可以重置申请,但是若你重要的文件,或许急着用的文档,数据等一旦被该病毒感染,便永不可恢复,至少现在,还没有破解之道,只有防患于未然,拥有好的备份习惯才是上上之策,及时备份资料于云存储,有道云,网盘,github等,不瞎戳不明链接,邮件，诱惑性网站等,本篇不是介绍勒索病毒,是在于如何避免预防勒索病毒,简单粗暴,将勒索病毒拒之门外

> 什么是中了勒索病毒？

如果你电脑里若弹出如下这个红色警示框,表示你的电脑已经中毒,一定是拒绝付款,只不过是一些资料文件没了的,很多童鞋可能觉得我重装系统不就ok了么,只是c系统盘没了的,然而其他盘的该有的资料文件还是可以的,注意若一旦感染,什么,文件,视频,文档都是永恒的(打不开文件),既然官方称永恒之蓝,那么至少现在是无解的,格式化硬盘,重装系统可以让系统正常,但是无法解决勒索病毒的入侵,下面来看一下具体解决办法
![](http://i.imgur.com/el0DgJc.jpg)

> 方法一:关闭445端口,通过更改注册表的方式

首先,查看一下当前的系统有哪些开放的端口,具体怎么查看,通过调用dos命令行终端上进行查看,window+R-->cmd-->输入命令-->netstat -na，可以查看到所有开放的端口(由于我的已经关闭了445端口的,你若没有关闭的话,是可以看到这个445端口是处于listen监听状态的)
![](http://i.imgur.com/gCpItDD.gif)

一旦确认自己的系统445端口是处于listening状态的,那么就要手动的关闭这个高危端口了,首先进入系统注册表,步骤如下gif图所示：输入regedit进入`注册表编辑器`
![](http://i.imgur.com/Q7jAUBg.gif) 

接着，依次点击注册表选项`HKEY_LOCAL_MACHINE` \ `SYSTEM`\ `CurrentControlSet`\ `services` \ `NetBT` \ `Parameters`，进入`NetBT`这个服务的相关注册表项,然后在`Parameters`这个子项的右侧,点击数鼠标右键,`新建`,`DWORD(32位值)` / `WQORD(64位值)`,命名为SMBDeviceEnabled,并且设置十进制参数设置为0,这个根据你电脑的系统位数而定,至于怎么查看计算机系统的位数,可以用快捷键`window+pause break`(笔记本的右边倒数第三个键),也可以鼠标手的方式点击计算机右键属性

如果电脑是的系统是windows XP的话,那么重启电脑就可以关闭445端口了,但是如果是window7的话,还要把操作系统的server服务关闭,依次调出运行窗口,输入`serverices.msc`,进入服务管理控制台,然后找到server服务,双击(或鼠标右键属性)进入管理控制页面,把这个服务的启动类型更改为`禁用`，服务状态更改为`禁止`,最后点击应用即可,注意在当前终端上,依旧是看得到445端口的,你可以在重新打开一个新的终端,查看445端口是否关闭了的,最后重启电脑即可,如下gif显示
![](http://i.imgur.com/AdpyfUT.gif)

> 方法二:通过设置防火墙禁止端口

如何快速的找到防火墙:window+R-->control,打开控制面板--即可快速的找到防火墙
![快速的开启防火墙](http://i.imgur.com/Kt1rbCQ.gif)
![](http://i.imgur.com/gclJPg6.gif)

至于关闭135,137,138方法同理，当禁止端口后,可查看,如下gif所示
![](http://i.imgur.com/yHiT40O.gif)

> 关闭共享文件和打印机服务,防止别人访问你的电脑携带病毒入侵

关闭Mircosoft网络客户端,以及Microsoft网络的文件和打印机共享
window+R-->更改适配器设置-->无线网连接-->右键属性-->(勾掉)Microsoft网络客户端与Microsoft网络文件和打印机共享
![](http://i.imgur.com/WXyHwDm.gif)

> 其他方法,网上也有,什么用电脑管家,360管家来禁止445端口的，时不时电脑弹出勒索病毒的预防的温馨提示的,还有安装补丁的方式,不过我个人还是倾向建议自己动手设置的

`总结:`

其实，本节并没有涉及什么高大上的内容,网上一些介绍勒索病毒的文章也一大推,本篇通过进入注册表的方式和设置防火墙的方式,都是可以的减少病毒入侵的风险,至于安装补丁和使用电脑管家等一些杀毒软件的方式我没有试过，我觉得还是自己手动设置比较好,安全,有效,终归结底来说,想想这个勒索病毒还是挺可怕的，据已知信息，这次造成勒索病毒的永恒之蓝只不过是众多病毒种类的其中之一,还在继续升级,变种,敛财于无形,其实,无论是Mac电脑,window10等高版本系统,Linux系统,那些黑客想要黑别人的电脑,对他们来说就是玩似的,也不要五十步笑百步,是没有绝对的安全的,这次是445端口,下次又是别的东东的,但凡有漏洞可钻,你就防不胜防,觉得还是时常备份资料的习惯,并且加强上网安全意识比较重要.虽事情没发生在自己身上,或许没中毒的你也许心存侥幸心里,但是,防患于未然终归是好的,周边人的血泪史要引以为鉴,深刻的教训值得自己思考,一旦事情发生在自己身上,便无药可治,后悔莫及

![](http://i.imgur.com/vxZBX0R.jpg)

`更多精彩内容,想收听对应音频,可关注微信itclan公众号`









