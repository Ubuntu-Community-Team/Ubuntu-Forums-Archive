---
title: "I want to make Ubuntu My main OS"
date: 2010-09-19
forum: General Help
---

### Post by coldfire6695 on 2010-09-19
Hey Guys, I have been wanting to make Ubuntu My main OS for about a week now, and I know my Custom Built system is fully compatible except for one thing, My USB Wifi Card, Its a Netgear WNA1100 (A clone of the Atheros AR9271). I have heard of a ath9k driver, but I have no idea how to install it or anything of that sort, I have linux on one of my laptops, so I can test the driver on it. Thanks, 

-Jeff

---

### Post by TBABill on 2010-09-19
Did you run Ubuntu LiveCD on that machine and see if your wireless is automatically detected? It may be as simple as booting, allowing the machine to detect components that have proprietary drivers available, updating and installing...and off and running. I'm not familiar with that specific card, but give it a go via the LiveCD and see what you can get going before installing.

---

### Post by hdemarzo on 2010-09-19
That is a GOOD idea just make sure that you turn the built-in wifi off before you try it.  Just so you dont get a false result.

---

### Post by coldfire6695 on 2010-09-19
No luck :( Its a WNA 1100 (or atheros AR9271) like I said earlier, Apparently the Ath9k Driver will work, but I have NO IDEA how to install it =/

---

### Post by themusicalduck on 2010-09-19
So you have Ubuntu installed but can't get your wireless to work?

Are you using Ubuntu 10.04? Have you tried going to System > Administration > Hardware Drivers to see if you can install it from there?

You said you don't know how to install the driver, what exactly are you trying to install and how? Did you download it from somewhere?

---

### Post by coldfire6695 on 2010-09-19
I have tried the Hardware drivers thing, No luck there. I am using 10.04.

I found the ath9k driver here, I read the whole page and couldn't find anything about downloading it.

[http://linuxwireless.org/en/users/Drivers/ath9k](http://linuxwireless.org/en/users/Drivers/ath9k)

---

### Post by pastalavista on 2010-09-19
To install wireless drivers, you need to be connected to the internet by wired ethernet connection. The Hardware Drivers tool will then automatically install whatever it finds you need.

---

### Post by coldfire6695 on 2010-09-19
Well, I tried that with no luck, I have read that the INF's for this device under XP will work with ndiswrapper, So I am installing XP via Virtualbox. Hope to get it working soon :p

---

### Post by themusicalduck on 2010-09-19
This post might fix it - [http://ubuntuforums.org/showpost.php?p=9578986&postcount=18](http://ubuntuforums.org/showpost.php?p=9578986&postcount=18)

You do need to be connected to the internet through a cable to do it though.

I'd read the whole thread after that post too though, as apparently it might cause a problem with the kernel. But there is a post that details a fix and talks about it on the next page - [http://ubuntuforums.org/showthread.php?t=1527654&page=2](http://ubuntuforums.org/showthread.php?t=1527654&page=2)

---

### Post by dougalkerr on 2010-09-19
I am trying the same thing but, with a Realtek device and a desktop machine. I am at the stage where a Ubuntu utility called RutilT can detect the device but, there is a frequency/channel not found message and a Code: 22 along with it.
However, I have set-up my laptop wireless using the System/Adminstration/Windows Wireless Drivers.
Have you tried this - just have your Windows drivers to hand, downloaded from the site to a directory under your username or something.

---

### Post by coldfire6695 on 2010-09-19
Hey, I was able to install the INF's under ndiswrapper, It recognizes it and says the device is present when I use the "Ndiswrapper -l" command, but it doesn't show up under my Wifi, I have even tried to go under System>Administration>Hardware Drivers. Any Ideas?

---

### Post by dougalkerr on 2010-09-19
System/Administration/Windows Wireless Drivers

---

### Post by coldfire6695 on 2010-09-19
Still no luck, it shows up that the device is connected but doesn't show anything within the wireless manager, anymore ideas?

---

### Post by dougalkerr on 2010-09-20
[http://ubuntuforums.org/showthread.php?t=1285828](http://ubuntuforums.org/showthread.php?t=1285828)

I was pointed to this link above. It obviously worked for someone although, I still have to get things working but, it improved things a lot. I just need an error code verified and then hopefully I'll get an answer.
What you and I have to realize is that there is a monopoly upon hardware around the world. This monopoly is governed by the demand of the sheep that continue to blindly buy Windows based computers just to 'keep up with the Joneses'.
Linux and especially Ubuntu have made huge leaps forward lately to make this environment easy to customize and use.
Granted we are both having a problem with USB wireless devices but, compared with Windows - most devices connected to Linux - just work.

Persevere and maybe you will be rewarded.
Try the other Linux forums. We are mostly people helping one another to have an operating system on OUR computers working and looking the way we want and not how Microsoft wants.

---

### Post by coldfire6695 on 2010-09-22
Guys, Well, It obviously is not going to work. I may put it on my Windows Server considering it is Wireless N and is just as fast as Ethernet, Can anyone recommend a Wireless N rated USB Card that works with Linux? Preferably not to hard on the wallet xD

---

