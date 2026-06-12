---
title: "cursor disappearing Lucid"
date: 2010-05-08
forum: General Help
---

### Post by cmcanulty on 2010-05-08
Since Lucid install the cursor periodically disappears, both mouse and trackpad. Requires restart. Any ideas?

---

### Post by mediajunkie on 2010-05-09
> **cmcanulty said:**
> Since Lucid install the cursor periodically disappears, both mouse and trackpad. Requires restart. Any ideas?

Hi, 

I don't know if you experience the same as I do, but on one of my older systems, (installed with Lucic) I have a mouse pointer in the login-screen, but then it doesn't show up in X once logged in. Holding down my control key is the only option to find the mouse pointer. but it still works. 

What I found solving the issue is [Ctrl + Alt  + F1] to open a terminal screen, and just enter so login fails, then [Ctrl + Alt + F7] to go back in X, and my mouse pointer is back, everything works normal after that. 

Worth giving a try... not ideal... but still better than reboot.

---

### Post by cmcanulty on 2010-05-09
Mine just disappears while working and I can see some movement on screen but no cursor so have to restart. I will try that though, thanks. I never had this before Lucid. Also spacebar stops working sometimes.

---

### Post by ljanvier on 2010-05-23
I had the same issue with my thinkpad (intel 855GM). I had to upgrade my kernel to 2.6.34, the command for this is on this page :
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

I opened a bug on LP :
[https://bugs.launchpad.net/bugs/584486](https://bugs.launchpad.net/bugs/584486)

---

### Post by specialk1st on 2010-07-13
I just posted this on another thread, but having had this problem myself I figured I would spread the word. :)

You can use this as a workaround to get back the missing cursor after opening your laptop lid ...

Try switching desktops via:
Ctrl+Alt+LeftArrow OR Ctrl+Alt+RightArrow

It is a reported bug.

Resource:  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/552058](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/552058)

---

### Post by cmcanulty on 2010-07-13
All the fixes I have tried messed up my hibernate so now it won't hibernate at all, goes black and a few seconds later comes back on. Does anyone know or can post a config file for hibernate and suspend so I can fix mine?

---

### Post by yves on 2010-11-28
OK, I had that problem for a while and none of the workarounds was working. But now it seems I fixed it !!
It was happening everytime my screensaver was activated after the computer was idle for the specified time.
So I just remove the check from "Activate screen saver when computer is idle" in my Sytem - Preferences - Screensaver options !!!

So far, so good.

---

### Post by johnnyhop on 2011-11-14
I was having the pointer disappear problem in Kubuntu 11.10 64 bit.  There was mouse activity but no pointer.  Also system was very prone to freezing necessitating a forced power down.  All has been well since I installed the recommended proprietary driver for my GeForce 6100 display adapter.

---

