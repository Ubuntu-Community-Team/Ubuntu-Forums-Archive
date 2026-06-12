---
title: "After installing ubuntu by wubi, boot speed become slow down."
date: 2011-05-25
forum: General Help
---

### Post by wangmir on 2011-05-25
I took wubi to install ubuntu 11.04.
 
**And after installing wubi, my desktop's boot speed become very slow.**
 
**After switched, ASUS(the screen that DEL key can make acess bios screen) screen takes very long time to get next screen(OS selecting).  And, after choosing ubuntu, also took long time as black screen(with white bar appearing at upper left).**
 
**Qurious thing is, I did same things at my lab top too, but didn't get slow down.**
 
This is my devices' details, 
 
my desktop environment is
1. i7 cpu
2. 8G memory
3. ASUS mainboard(P8H61)
4. Windows7 pro 64bit
 
And I installed wubi with ubuntu 11.04 i386, AMD64 either, but both were slow.
 
my laptop(hp dm3) environment is
1. Core2Duo(SP9300)
2. 4G memory
3. Windows7 home 32bit
 
And I installed wubi with ubuntu 11.04 i386, and it was cool.
 
How can I fix it?

---

### Post by novinick on 2011-05-25
when using wubi
underlying filesystem that ubuntu cow image is stated on is NTFS , 
so then curent ntfs-3g may have slower preformance with w7 flavor of ntfs
on your machine :( have no experience with that

try also to login as gnome , not unity
and as gnome without desktop effects,as a troubleshooting step
[http://www.virtualhelp.me/linux/324-disable-unity-on-ubuntu-1104](http://www.virtualhelp.me/linux/324-disable-unity-on-ubuntu-1104)

**Ubuntu Classic Desktop (no effect**)

however ,after carefuly reading
i suspect this is a GRUB related problem ,betweeen grub  -  i7cpu  -  and&or motherborad

> 
**After switched, ASUS(the screen that DEL key can make acess bios  screen) screen takes very long time to get next screen(OS selecting).   And, after choosing ubuntu, also took long time as black screen(with  white bar appearing at upper left).**


---

