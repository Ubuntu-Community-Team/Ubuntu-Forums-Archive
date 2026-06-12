---
title: "Lucid boot hangs when using Thinkpad with monitor"
date: 2010-08-15
forum: General Help
---

### Post by aextance on 2010-08-15
I use an IBM Thinkpad T30 with an ATI Radeon Mobility 7500 graphics card as my work machine, mostly at a desk, using a docking station to link it into a monitor. I upgraded to Lucid last weekend. When using the integral screen on the laptop the graphics have been fine, but when using a monitor I initially got some very poor contrast, brightness and gamma output, described in this bug.

[https://bugs.launchpad.net/ubuntu/lu...ux/+bug/548709](https://bugs.launchpad.net/ubuntu/lu...ux/+bug/548709)

According to the advice in that bug report, I upgraded the kernel, with Kernelcheck automatically updating me to 2.6.35-candela. Now, rather than poor graphics with the monitor it just hangs on the splash screen, displaying the words Ubuntu with the dots underneath. 

Reading around, when similar problems have been seen in previous versions of Ubuntu it has been a graphics issue, which fits. One piece of advice I've seen quite commonly is to remove the "quiet splash" from grub, which I've tried but doesn't work. I am tempted to try and work through the different grub commands these guys used to tackle a similar problem with the live CD:

[http://ubuntuforums.org/showthread.php?t=1472054](http://ubuntuforums.org/showthread.php?t=1472054)

But am a bit reticent as I don't know what they all do. 

As an aside, the 2.6.35-candela kernel brings up a bunch of errors on boot, described at the link below, but reading that thread they don't look like they would cause my problem:

[http://kerneltrap.org/mailarchive/linux-kernel/2010/7/8/4591800/thread](http://kerneltrap.org/mailarchive/linux-kernel/2010/7/8/4591800/thread)

Thankfully the integral laptop screen still works, but as I'm staring down the barrel of quite an intensive week of work I'd really like to be able to use my monitor, so that I don't end up with a ruined neck by the end of it. 

So what do I do? Should I try some different grub commands? Should I go back to an earlier kernel (I haven't been enjoying my recent efforts at kernel upgrades) even if it means putting up with a barely readable screen?

---

### Post by aextance on 2010-08-15
OK, I've got the monitor working now, but disappointingly I can't use Compiz, whereas I was very excited that I could now use it with this computer when I first installed Lucid.

The issue appears to be with Kernel Mode Setting (KMS):

[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

Changing the grub to radeon.modeset=0 allows me to use my laptop and my monitor together again. Interestingly, trying to turn KMS back on using the virtual console as described in the page above immediately turns the screen blank. I blindly tried typing the command that I thought would turn KMS off again, but that didn't work. I'll report a bug on this in due course, but in the meantime, I need to start chipping away at my mountain of work.

---

