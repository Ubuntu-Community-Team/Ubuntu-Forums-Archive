---
title: "how to manualy configure sceen,graphic card, input device setting manualy?"
date: 2011-05-31
forum: General Help
---

### Post by vat with tux on 2011-05-31
Hi there.:)
 
I have installed ubuntu 11.04 on windows 7 using wubi installer. 

Everythig was going perfect just before 1 hour. Then i installed Compiz Configuration Manager & changed some settigs using it. After that changed my system hanged & i had to use hardware key to restart my computer. After that when syatem restarted I'm having a dialog box showing following error.

> your screen graphic card & input device setting could not be detected correctly . you will need to configure these your self.



Also i'm not having any graphic card in my pc & processor is intel core 2 duo.
Now i'm not able to loginto ubuntu so please tell me that what is the solution for this problem??
thanking in advance.

---

### Post by linuxinstalledfromhdd on 2011-05-31
You would need to boot Ubuntu into the command line:

[http://askubuntu.com/questions/20628/cant-boot-video-drivers-or-x-server-problem](http://askubuntu.com/questions/20628/cant-boot-video-drivers-or-x-server-problem)

---

### Post by wildmanne39 on 2011-05-31
> **vat with tux said:**
> Hi there.:)
 
I have installed ubuntu 11.04 on windows 7 using wubi installer. 

Everythig was going perfect just before 1 hour. Then i installed Compiz Configuration Manager & changed some settigs using it. After that changed my system hanged & i had to use hardware key to restart my computer. After that when syatem restarted I'm having a dialog box showing following error.




Also i'm not having any graphic card in my pc & processor is intel core 2 duo.
Now i'm not able to loginto ubuntu so please tell me that what is the solution for this problem??
thanking in advance.
Hi, you can use this to get into recovery mode.
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode) then I think the simple thiing to do would be to use this command and let it run for about three minutes.
```
unity --reset
```then you should be able to enable your video card drive again if you have to.

---

### Post by vat with tux on 2011-05-31
:guitar: hey thanks a lot to both of u. It's solved. I need to use 

> apt-get install ubuntu-desktop 

command to recover my desktop. 
But by only using above command I wasn't able to use unity environment means system was working fine only with classic GNOME env.

So to reset unity need to use 

> unity --reset 

Again thanks a lot to both of you. :D
:guitar:

---

### Post by wildmanne39 on 2011-05-31
> **vat with tux said:**
> :guitar: hey thanks a lot to both of u. It's solved. I need to use 

 

command to recover my desktop. 
But by only using above command I wasn't able to use unity environment means system was working fine only with classic GNOME env.

So to reset unity need to use 

 

Again thanks a lot to both of you. :D
:guitar:
Hi, your welcome and it will tell you a lot of errors dont worry about them but let it run for about 3 minutes to let it finish.

---

