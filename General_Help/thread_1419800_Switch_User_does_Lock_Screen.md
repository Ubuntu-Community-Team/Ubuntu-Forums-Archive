---
title: "Switch User does Lock Screen"
date: 2010-03-02
forum: General Help
---

### Post by saganomics on 2010-03-02
The only things I can find on this topic are:
[https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/195114](https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/195114)
and...
[http://ubuntuforums.org/showthread.php?t=699436](http://ubuntuforums.org/showthread.php?t=699436)

...neither of which call out, directly, what I am referring to. When I click "Switch User...", no matter which user account I am currently logged into, I get the lock screen. This only happens on my 64 bit Karmic machine and appears to work correctly on my x86 Karmic laptop.

On the laptop it takes me to the login window where it says I am currently logged in and can select other users. On the 64 bit machine is takes me to the exact screen generated after clicking "Lock Screen"

What gives?

---

### Post by saganomics on 2010-03-05
I'm still struggling with this issue. I'll add some information. Since I opened the thread, I installed Ubuntu x86 on the machine that had the x86_64 version that also was not switching users. I assumed that would solve the problem. I was not correct.

The situation is the same on this machine, so I guess it is hardware related.

---

### Post by ndkexp on 2010-03-06
You are not alone, I have the same issue. Switch user results blank (black) screen and systems goes totally unresponsive, even the magical SysRq+reisub does not work. The only way out is hardware reset or power off.

Shortly after the screen goes black the computer fan ramps up, possibly indicating CPU or GPU clock frequency increase. The same happens when trying to Stand-by. Log off works just fine.

When googling the issue, I think that I have narrowed the problem down to ATI-proprietary fglrx driver and X.org 1.6 conflict.

Some specs of my computer:
CPU: AMD 64bit dual core
GPU: ATI Radeon HD2600 (Motherboard integrated)
OS: Ubuntu Karmic 9.10 64-bit
GPU driver: fglrx

Most annoying, as the switch user is highly important in family  computer.

---

### Post by ndkexp on 2010-03-31
My issues with switch user hang has been solved by installing the new version (10.3) of the proprietary Radeon drivers. 

I followed these instructions [http://ubuntuforums.org/showthread.php?t=1440323](http://ubuntuforums.org/showthread.php?t=1440323)

Rgds,

-Jyri-

---

