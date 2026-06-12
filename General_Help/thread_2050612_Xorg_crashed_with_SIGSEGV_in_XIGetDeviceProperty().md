---
title: "Xorg crashed with SIGSEGV in XIGetDeviceProperty()"
date: 2012-08-31
forum: General Help
---

### Post by scarsman on 2012-08-31
My laptop is crashing soon after resuming from being asleep/hibernating. Unfortunately, I haven't yet found a way to reliably reproduce the problem.

Here's what happens:

I'll close the lid to put it to sleep (I usually only have Chrome running, but this has happened with different combinations of applications running) and leave it for an hour or two. When I come back and open the lid, I get the Ubuntu login screen and am taken to the desktop. Everything seems fine, but then I get an error message like the following. 

I'm using:

[INDENT]Ubuntu 12.04 LTS on a 
Samsung NP350U2B
3.9 GiB
IntelCore i5-2410M CPU # 2.30GHz x 4
Intel Sandybridge Mobile x86/MMX/SSE2
32-bit[/INDENT]

I Googled "Xorg crashed with SIGSEGV" and came across a bug report at launchpad.net. People seem to think that this might be a good solution:

[https://bugs.launchpad.net/debian/+source/xorg-server/+bug/956071/comments/32](https://bugs.launchpad.net/debian/+source/xorg-server/+bug/956071/comments/32)

But I was hoping to maybe get a second opinion. (I'm kind of a newb and don't want to get in over my head!)

Any (not too technical... sorry!) advice would be greatly appreciated! Thanks!


Here's the beginning of the error report (I can copy more of it next time if that would be helpful):

```
ExecutablePath
/usr/bin/Xorg

Package
xserver-xorg-core 2:1.11.4-0ubuntu10.6

ProblemType
Crash

Title
Xorg crashed with SIGSEGV in XIGetDeviceProperty()

ApportVersion
2.0.1-0ubuntu12

Architecture
i386

CoreDump
(binary data)
```

---

### Post by scarsman on 2012-09-02
Any ideas? Am I posting my problem in the right forum?

---

