---
title: "Skim loads but doe nothing."
date: 2006-05-06
forum: General Help
---

### Post by Circleback on 2006-05-06
I'm trying to set up skim for Chinese (traditional and simplified). I installed all the packages and language support options. The icon is in the tray saying it is loaded but i still cannot type in Chinese. I'm using Kubuntu in Dapper.

Thanks

---

### Post by jeremywhiting on 2006-06-09
try this post if you are still looking to get this working:

[http://ubuntuforums.org/showthread.php?t=167341&highlight=skim]("http://ubuntuforums.org/showthread.php?t=167341&highlight=skim")

namely adding 

```
QT_IM_MODULE=scim
GTK_IM_MODULE=scim

``` 

to your /etc/environment file.

I'm trying it now, I'll let you know if it worked for me.  

P.S. I'm on 6.06 kubuntu

Edit: worked like a charm. I previously had added chinese support in System/Language Support (not sure if that helped, but it added lots of packages, so probably.)

Also, I didn't need to reboot, just log out of kde and log back in
then ctrl-space to your hearts content.  It's great.

---

