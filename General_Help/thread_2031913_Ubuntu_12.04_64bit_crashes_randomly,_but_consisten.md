---
title: "Ubuntu 12.04 64bit crashes randomly, but consistently"
date: 2012-07-22
forum: General Help
---

### Post by motorsep on 2012-07-22
At certain point of time I thought Linux is a rock stable OS. With Ubuntu 12.04 64bit I no longer feel that way. I feel that now Ubuntu is total junk. I can't use it as workstation OS any longer because whether I listen to Pandora radio, or work in GIMP, or run OpenGL game, at certain point it will either freeze my PC completely (there is no way to reboot except hard reset), or Unity will crash and I will be back into login screen loosing all unsaved data. Every day, for about a month or more, I have this issue.

I am not sure if anyone addressed it yet, but if that's not going to change, I would rather spend money on Windows 7 64bit and have no headaches than worry about Ubuntu crashing on me all the time (not like Canonical cares anyway).

Has anyone found solution for such problem, if anyone has had that problem?

Thanks.

---

### Post by 3Miro on 2012-07-22
The most likely culprit for such issues is video card issues.

- What is your video card?
- Which driver are you using?
- Have you kept an eye on the laptop temperature? Crashes like that can happen if the hardware is overheating.

---

### Post by motorsep on 2012-07-22
> **3Miro said:**
> The most likely culprit for such issues is video card issues.

- What is your video card?
- Which driver are you using?
- Have you kept an eye on the laptop temperature? Crashes like that can happen if the hardware is overheating.

GF 8800 GT 512Mb VRAM
8Gb of DDR2 RAM
AMD Phenom x3
Nvidia v295.49 driver

It's not laptop, it's desktop and I've used it since Ubuntu 10.04

Ubuntu 11.10 was rock stable. Same setup.

---

### Post by 3Miro on 2012-07-22
Desktops are less likely to overheat, but you should check the temperature just in case. Check the CPU too, I remember having a Phenom II and it ran hot sometimes.

Also, make the following test: logout and go into Unity 2D. I know it is not as pretty, but if you have no issues with Unity 2D, then we know the issue is with compiz.

You can also try to disable the Nvidia driver, just for a test to see if you experience any crashes.

If it is the driver, we can update the driver. If it is compiz, we can play with CCSM, disabling some of the effects may fix the issue. Or we may have to look at other options.

---

### Post by motorsep on 2012-07-22
> **3Miro said:**
> Desktops are less likely to overheat, but you should check the temperature just in case. Check the CPU too, I remember having a Phenom II and it ran hot sometimes.

Also, make the following test: logout and go into Unity 2D. I know it is not as pretty, but if you have no issues with Unity 2D, then we know the issue is with compiz.

You can also try to disable the Nvidia driver, just for a test to see if you experience any crashes.

If it is the driver, we can update the driver. If it is compiz, we can play with CCSM, disabling some of the effects may fix the issue. Or we may have to look at other options.

I can't check CPU temperature (sensor isn't showing up), GPU has been always hot and it never crashed before (it never freezes on WinXP).

Unity 2D crashes too. Tried reverting video driver, same thing. Btw, I noticed that Nvidia has 259.59 version out for Linux. What's with these guys who update drivers on ppa ? (the highest version I can update to here is 259.49)

Actually, I didn't have issue at the very beginning.. Then with one of the kernels update this issue started.

---

### Post by 3Miro on 2012-07-23
You can check the CPU temperature by running "sudo sensors-detect", this will load the module needed for the CPU monitoring.

Since the DE doesn't make too much difference, it may be an issue with the kernel. Try reverting the kernel or alternatively update the kernel to a newer version:

[http://www.ubuntubuzz.com/2012/03/upgrade-to-kernel-33-in-ubuntu.html](http://www.ubuntubuzz.com/2012/03/upgrade-to-kernel-33-in-ubuntu.html)

This may look complicated, but all you need to do is copy/paste six commands.

---

### Post by motorsep on 2012-07-23
> **3Miro said:**
> You can check the CPU temperature by running "sudo sensors-detect", this will load the module needed for the CPU monitoring.

Lol, did that and it detected no thermal sensors for CPU. Totally weird as CPUFan on WinXP detects everything fine.

As far as updating kernel, I really wanted to, but I will have issues with video drivers guaranteed because Canonical decided t make it easy for users to install video drivers through ppa, but that made it p.i.t.a. to install video drivers old fashion way (the way it was done prior to 11.10). So since no drivers were created in pp for new kernel, I don't see how would I deal with that :/

---

### Post by motorsep on 2012-07-24
New development in the case.. Today there was a kernel update and so far, after I updated, no freeze. Played Pandora with Pithos, used GIMP and OpenGL games and experienced no freeze or crash. I am keeping my fingers crossed.

---

### Post by idoitprone on 2012-07-24
> **motorsep said:**
> New development in the case.. Today there was a kernel update and so far, after I updated, no freeze. Played Pandora with Pithos, used GIMP and OpenGL games and experienced no freeze or crash. I am keeping my fingers crossed.

sound like the nvidia binary blob didnt like the stock kernel.

---

### Post by motorsep on 2012-07-24
> **idoitprone said:**
> sound like the nvidia binary blob didnt like the stock kernel.

Well, if by stock kernel you mean the one that came with vanilla Ubuntu 12.04, then it's not it. I had no issues with stock kernel. There were few updates after 12.04 came out and I bet the update before today was the buggy one (yeah, Linux kernel can be unstable :) ). Hopefully the issue is solved (the issue was definitelly in the kernel).

---

