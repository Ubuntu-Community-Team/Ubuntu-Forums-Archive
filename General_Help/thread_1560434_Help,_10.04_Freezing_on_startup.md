---
title: "Help, 10.04 Freezing on startup"
date: 2010-08-24
forum: General Help
---

### Post by bryan3091 on 2010-08-24
I am getting frustrated and at my wits end.:mad:  I went away from home for 3 days and came back to a frozen computer.  To start, my linux computer was locked and wouldn't allow me to switch to my other computer using my KVM.  All I saw was the default wallpaper with no icons, cursor or anything.  Rebooting the computer allowed me to resume normal operation on the other but not on my linux comp.

Now when I boot I can only get to a recovery console if luck is on my side and trying a normal boot freezes the computer with a blank screen and blinking cursor.

I tried editing the GRUB commands with "nomodeset", "i915.modeset=0" and "i915.modeset=1" with no luck.  I also tried removing "quiet" and "splash" from the boot and it freezes at random parts of the boot.  Sometimes with an error loading a device with IRQ 21 and sometimes on a memory address.  

I am running XP on the same computer, so I thought I would try to boot into that, even THAT freezes!

I have even tried running my LiveCD and it tells me there is an error reading the boot CD...the same CD I installed with 3 weeks ago without any problem!  

As I type this, the computer is booting, sort of, to a black screen with a ridiculously large "X" cursor and a small white dot in the upper left.

I am going crazy, this is the computer I use for everything.  Someone please help me out.

System Specs:
Athlon 3200
4gb RAM
GeForce 7200
generic DVD
generic sound

---

### Post by bryan3091 on 2010-08-26
****UPDATE (and maybe a bump)****
I got back home and decided to give it a try again.  I managed to get into Ubuntu again.  Don't know why?  I went ahead and changed over to the correct nVidia driver (nvidia-current) and rebooted as it told me to.  It locked up again on boot and gave me a generic wallpaper with a mouse cursor but was frozen.

I booted into a recovery console and let it run an update like it wanted to.  Again, it froze, this time about 60% through the updates.  Now it won't even bother to reboot, it drops me to a command prompt for initramfs.  

Any ideas?

---

