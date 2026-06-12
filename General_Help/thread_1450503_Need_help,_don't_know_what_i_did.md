---
title: "Need help, don't know what i did??"
date: 2010-04-09
forum: General Help
---

### Post by VEI2I7AS on 2010-04-09
Well the resolution is off and that was my initial problem, but i feel ive just made things worse. Im using ubuntu 9.10 Karmic Koala and im very new to linux. From the login screen i had clicked on the options menu, the little man icon. I selected the "magnify screen" option and it completely threw off the image. now i cant see anything once it gets to the startup screen, even b4 the capability to login is given. Can someone please help me with this? Maybe a command or something i can run to help revert me to default settings? lol sorry newbie here.

thanks, ryan

---

### Post by orkyahaalhai on 2010-04-09
are u getting the same problem while getting in via recovery mode??

---

### Post by VEI2I7AS on 2010-04-09
I noticed upon reboot that it gave me the option to do run it in recovery mode, but stupid me clicked the regular version. It hasnt given me that option since then, is there a way to boot up in recovery mode while the processor or grub are loading?

---

### Post by bhencetotozo on 2010-04-09
> **VEI2I7AS said:**
> Well the resolution is off and that was my initial problem, but i feel ive just made things worse. Im using ubuntu 9.10 Karmic Koala and im very new to linux. From the login screen i had clicked on the options menu, the little man icon. I selected the "magnify screen" option and it completely threw off the image. now i cant see anything once it gets to the startup screen, even b4 the capability to login is given. Can someone please help me with this? Maybe a command or something i can run to help revert me to default settings? lol sorry newbie here.

thanks, ryan

I don't know exactly what your problem is... but try this:

ALT+CONTROL+F1 ... when the screen gets black, type your user login, and password...

once you sucessfully login, type 

1) sudo /etc/init.d/gdm stop
2) sudo /etc/init.d/gdm start

...See what happens... OR, hold Control, and roll your mouse wheel see if that unmagnifies it.

But i still dont exactly understand the problem, can you please be more specific?

---

### Post by VEI2I7AS on 2010-04-09
OK so i rebooted. and it brought to a black screen to either run in recovery mode or regular, i chose recovery. It ran commands down the screen, and then came to a blue screen that gave me choice to use he terminal or resume in regular OS, along with a few other choices. I selected resume, and clicked enter. then it gives me 

root@user1-desktop:~#

what next?

---

### Post by VEI2I7AS on 2010-04-09
Nevermind, it allowd me to enter commands and then stopped. I just rebooted again. im at the reboot screen allowing recovery mode or not. fullscreen says:

GNU GRUB VERSION 1.97~beta4

then gives the OS's:

Ubuntu, Linux 2.6.31-20-generic
Ubuntu, Linux 2.6.31-20-generic (recovery mode)
Memory Test (memtest86+)
Memory Test (memtest86+,serial console 115200)

I think im going to need someone to walk through this with me. If anyone could be so kind. All im trying to do is boot up in default settings, with my screen resolution back to viewable. I originally messed around with settings at the login screen to try to adjust the resolution but ended up magnifying the screen and have been stuck with it being messed up at the login screen since.

---

### Post by bhencetotozo on 2010-04-09
> **VEI2I7AS said:**
> Nevermind, it allowd me to enter commands and then stopped. I just rebooted again. im at the reboot screen allowing recovery mode or not. fullscreen says:

GNU GRUB VERSION 1.97~beta4

then gives the OS's:

Ubuntu, Linux 2.6.31-20-generic
Ubuntu, Linux 2.6.31-20-generic (recovery mode)
Memory Test (memtest86+)
Memory Test (memtest86+,serial console 115200)

I think im going to need someone to walk through this with me. If anyone could be so kind. All im trying to do is boot up in default settings, with my screen resolution back to viewable. I originally messed around with settings at the login screen to try to adjust the resolution but ended up magnifying the screen and have been stuck with it being messed up at the login screen since.


What caused that bug? did u update ur system? did you install any software? ... what did u do while it was working fine? ...

---

