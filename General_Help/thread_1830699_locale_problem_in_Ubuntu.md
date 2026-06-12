---
title: "locale problem in Ubuntu"
date: 2011-08-22
forum: General Help
---

### Post by volvolinux on 2011-08-22
Hello friends
 
I want to ask a question regarding on the "locale" problem. I've searched a lot on Google, but I think there is no detailed information and logic explained this topic well....
 
Someone may suggest use Preference->Administration->Language Support to add or change whatever language I want. I can't use this way beacuse:
 
1. I need try to push locale configuration to a lot of linux clients.
2. I want to know the detailed information of how to configure.
 
 
I have tried to find the most helpful page on the Internet and read some "man locale":
 
[[FONT=Calibri][SIZE=3][COLOR=#800080]https://help.ubuntu.com/community/Locale[/COLOR][/SIZE][/FONT]]("https://help.ubuntu.com/community/Locale")
[[FONT=Calibri][SIZE=3][COLOR=#800080]http://packages.ubuntu.com/natty/locales[/COLOR][/SIZE][/FONT]]("http://packages.ubuntu.com/natty/locales")
[http://isis.poly.edu/~qiming/chinese-debian-mini-howto.html](http://isis.poly.edu/~qiming/chinese-debian-mini-howto.html)
[http://isis.poly.edu/~qiming/fine-tuning-ubuntu-locale.html](http://isis.poly.edu/~qiming/fine-tuning-ubuntu-locale.html)
 
The step i get is:
 
1. find out the language Ubuntu supports, let's say Chinese
 
```
root@VPC:~# cat /usr/share/i18n/SUPPORTED | grep zh
zh_CN.GB18030 GB18030
zh_CN.GBK GBK
zh_CN.UTF-8 UTF-8
zh_CN GB2312
zh_HK.UTF-8 UTF-8
zh_HK BIG5-HKSCS
zh_SG.UTF-8 UTF-8
zh_SG.GBK GBK
zh_SG GB2312
zh_TW.EUC-TW EUC-TW
zh_TW.UTF-8 UTF-8
zh_TW BIG5

```
 
2. add the output from the console to "/var/lib/locales/supported.d/locale"
 
```

[EMAIL="root@VPC:/var/lib/locales/supported.d"]root@VPC:/var/lib/locales/supported.d[/EMAIL]# cat local
en_US.UTF-8 UTF-8
zh_CN.GB18030 GB18030
zh_CN.GBK GBK
zh_CN.UTF-8 UTF-8
zh_CN GB2312
zh_HK.UTF-8 UTF-8
zh_HK BIG5-HKSCS
zh_SG.UTF-8 UTF-8
zh_SG.GBK GBK
zh_SG GB2312
zh_TW.EUC-TW EUC-TW
zh_TW.UTF-8 UTF-8
zh_TW BIG5


```
 
step3 run **[FONT=Courier New]dpkg-reconfigure locales[/FONT]**
**[FONT=Courier New][/FONT]** 
```

 
[EMAIL="root@VPC:/var/lib/locales/supported.d"]root@VPC:/var/lib/locales/supported.d[/EMAIL]# dpkg-reconfigure locales
Generating locales...
  en_AG.UTF-8... up-to-date
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
  zh_CN.GB18030... up-to-date #the first time i run, it gives something like "done"
  zh_CN.GB2312... up-to-date
  zh_CN.GBK... up-to-date
  zh_CN.UTF-8... up-to-date
  zh_HK.BIG5-HKSCS... up-to-date
  zh_HK.UTF-8... up-to-date
  zh_SG.GB2312... up-to-date
  zh_SG.GBK... up-to-date
  zh_SG.UTF-8... up-to-date
  zh_TW.BIG5... up-to-date
  zh_TW.EUC-TW... up-to-date
  zh_TW.UTF-8... up-to-date
Generation complete.
 

```
 
step 4 change settings in "/etc/envrionment" and "etc/default/locale" to let it contain something like below.. Actually, I don't find any clue what does "C" means....
 
> 
LC_MESSAGES="C"LC_COLLATE="C"LC_CTYPE="C"LC_TIME="C"LC_NUMERIC="C"LC_MONETARY="C"LC_PAPER="C"LC_NAME="C"LC_ADDRESS="C"LC_TELEPHONE="C"LC_MEASUREMENT="C"LC_IDENTIFICATION="C" 

 
step x, maybe missing something in X-windows settings?
step y, maybe missing something in language package installtion?
 
 
I really appreciate that some "big guys" can give some help on this!
 
The reason why I want to figure this out is I found that some Windows files name in Chinese can't be displayed correctly. It is may caused by the file name is not in UTF-8 encoding. So I want to play with locale to see if it can solve such problem.
 
Sometimes, it is really depressed that when I play with Ubuntu, I can't find a good documenation, or the information is too discrete to combine them....

---

### Post by volvolinux on 2011-08-22
I hope some one can help or give some link for me read.
Thanks.....

---

### Post by volvolinux on 2011-08-22
shout for help!

---

