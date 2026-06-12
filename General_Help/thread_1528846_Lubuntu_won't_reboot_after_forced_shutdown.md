---
title: "Lubuntu won't reboot after forced shutdown"
date: 2010-07-11
forum: General Help
---

### Post by Brendo613 on 2010-07-11
Hi all :)  I'm running a Dell XPS T700r with 700 mhz on Lubuntu 10.04, and was *very*happy with its performance.  I had many tabs on Firefox open, Pidgin running, but when I changed an appearance setting (or something of the like) the system froze.  I hit the restart button, and ever since I get this message upon boot-up:

```
No init found.  Try passing init=bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)[blinking cursor]
```


I've searched the web for that error message, and found some helpful sites, namely [this]("https://answers.launchpad.net/ubuntu/+source/grub/+question/63005") which describes the same problem.  Following the posts on there, I booted into a live CD and browsed the hard drive (not the live cd's) /root/boot/grub directory.  There is no menu.lst in there ... is this because of grub 2 doing things differently, and perhaps the thread post I followed was assuming the presence of the previous grub? 

I'm confused as to what the problem even IS here.  The computer attempts to boot - the lubuntu splash screen comes up for a few seconds before dropping to this "init" error message.  Any pointers would be greatly appreciated

---

### Post by cavalier911 on 2010-07-11
Grub2 hides the boot menu unless it detects other operating systems on your computer.To see the menu tap on your shift key continually from the time your bios starts.When the grub menu appears highlight the (recoverymode) selection, hit enter and cross your fingers.If you get lucky you'll boot to the recovery menu.Highlight grub update grub bootloader,tab to ok,enter.Grub2 will reconfigure itself,listing your kernel, memtest, etc..When finished the recovery menu reappears, choose resume normal boot. This will stop in text mode,login,start graphics mode with ```
sudo lxdm
```
Reboot,you won't see the menu,pray it boots.
If not we'll try to narrow it down further.

---

### Post by Brendo613 on 2010-07-16
I haven't been able to get into the grub menu, oddly enough.  My screen flickers a bunch of times like it's getting no signal after the BIOS beep.  I doubt that graphics issues could be causing this, but I did stick a 64 mb GeForce in there instead of the 32 mb card that was with it originally.

I've been able to use the system; when I get to the BusyBox error message & command prompt, I type

```
mount /dev/sda1 /
reboot
```

and then it boots normally.  I'm perplexed why I have to do this *sometimes*, and not always.  It's not all that big of a deal, but I am curious why it's happening

---

### Post by alecolli on 2010-09-26
hi, i have the same problem, but nothing seems to work... When i type 'mount /dev/sda1 /' it says: failed:invalid argument.

I would be very happy to reinstall everything but when i reboot with disk inserted it seems the system don't 'see' the disk (the same disk i used to istall the first time)...
Can somebody please help me? (the bios boot sequence is ok)

---

