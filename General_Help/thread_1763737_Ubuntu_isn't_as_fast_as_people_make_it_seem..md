---
title: "Ubuntu isn't as fast as people make it seem."
date: 2011-05-20
forum: General Help
---

### Post by GKCzar on 2011-05-20
Hey, guys I am new to linux. I installed Ubuntu cause I wanted to start learning python as my first programing language to start my journey to learning how to hack and just learn about computers in general. I was told that I should use linux cause it will help me in the process. Plus every source I see makes it seem like ubuntu is a really lightweight OS that is blazing fast, even on netbooks and old computers. So far from me using ubuntu, it is only fast in the wait time after it booted up. But other than that, it is about the same in speed to my XP OS sometimes even slower/laggier than XP. I think I am just missing something. Oh and I am dual/booting this. Hope you guys can help me out, looking forward toward your replies :p.

---

### Post by nrundy on 2011-05-20
compared to XP, 10.04 is a LOT faster on my box. faster at everything.

---

### Post by snowpine on 2011-05-20
Of course XP is faster than Ubuntu! XP was released in 2001 when the average customer had a Pentium 3 with 128mb ram. Compare the hardware requirements:

> The minimum hardware requirements for Windows XP Home Edition are:
Pentium 233-megahertz (MHz) processor or faster (300 MHz is recommended)
At least 64 megabytes (MB) of RAM (128 MB is recommended)
At least 1.5 gigabytes (GB) of available space on the hard disk
CD-ROM or DVD-ROM drive
Keyboard and a Microsoft Mouse or some other compatible pointing device
Video adapter and monitor with Super VGA (800 x 600)or higher resolution
Sound card
Speakers or headphones

> Ubuntu Desktop Edition
1 GHz x86 processor
1 Gb of system memory (RAM)
8 Gb of hard-drive space
Graphics card and monitor capable of 1024 by 768
Either a Cd/Dvd-Drive or a Usb port (or both)
Internet access is helpful


A better comparison would be Ubuntu vs. Windows 7. :)

> If you want to run Windows 7 on your PC, here's what it takes:

1 gigahertz (GHz) or faster 32-bit (x86) or 64-bit (x64) processor

1 gigabyte (GB) RAM (32-bit) or 2 GB RAM (64-bit)

16 GB available hard disk space (32-bit) or 20 GB (64-bit)

DirectX 9 graphics device with WDDM 1.0 or higher driver

---

### Post by GKCzar on 2011-05-20
> **snowpine said:**
> Of course XP is faster than Ubuntu! XP was released in 2001 when the average customer had a Pentium 3 with 128mb ram. Compare the hardware requirements:





A better comparison would be Ubuntu vs. Windows 7. :)

Hmm, but it seems that even other people who had XP Ubuntu is running faster for them. :confused:

---

### Post by bdoe on 2011-05-20
It depends on a whole lot of variables, not the least of which is your choice of desktop environment. KDE and Gnome (and now Unity) are full of eye-candy, but are also slow in comparison with other DE's such as xfce and LXDE. If speed is of greater importance, then consider Xubuntu or lubuntu. Both of these are considerably faster and lighter than their Gnome and KDE siblings.

---

### Post by GKCzar on 2011-05-20
> **bdoe said:**
> It depends on a whole lot of variables, not the least of which is your choice of desktop environment. KDE and Gnome (and now Unity) are full of eye-candy, but are also slow in comparison with other DE's such as xfce and LXDE. If speed is of greater importance, then consider Xubuntu or lubuntu. Both of these are considerably faster and lighter than their Gnome and KDE siblings.

Alright thanks, I actually was just reading
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
which explained a lot. 
How can I upgrade this post to solved?

---

### Post by tgalati4 on 2011-05-20
The default Ubuntu desktop kernel is set to 250 Hz interrupt timer.  I recompiled my kernel after setting it to 100 Hz.  That actually makes it appear to run slower, but saves more power.  You can set it to 1000 Hz and it will appear to be snappier (mouse and keyboard response).

Windows XP is optimized for snappy response, not for getting work done.  Look how long you have to wait after bootup before you can really open any applications.  It's a joke.  You have a desktop and a spinning ball of wait--for like 5 minutes.  That spinning ball is snappy though.

Because linux is true multithreaded, multitasking, and multi-user, you will sometimes have to wait for things to happen.  And that wait appears to be slower than Windows.  But try doing some real work like mixing music or compressing videos and you will see the advantages.

---

