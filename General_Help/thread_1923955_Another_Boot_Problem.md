---
title: "Another Boot Problem"
date: 2012-02-11
forum: General Help
---

### Post by ilikebananafudge on 2012-02-11
Hi,

I'm new to Ubuntu. I just installed 11.10 on my laptop after making a bootable USB with UNetbootin. I liked it. I decided to boot into Ubuntu with my USB stick on my desktop and it would not work. I get the normal UNetbootin screen asking me to install, try without installing, check memory, etc. However, after I select Try without installing, I get a bunch of text on the screen, ending with this (see attached image). If it helps, I am able to type commands at the bottom of the screen.

This is a computer that I built. It has the following specs:

CPU: Intel i5 2500k
GPU: EVGA nVidia Geforce 560 Ti
Motherboard: ASUS P8Z68-V LE
Hard Drive #1: Samsung 830 64GB Solid State Drive (this is where Windows 7 is installed)
Hard Drive #2: Western Digital Caviar Blue 500GB HDD

The USB drive that I'm using is a Centon DataStickPro 4GB.

Please let me know what I should do. Thanks!

Kind Regards,
Adam

---

### Post by LinuxFan999 on 2012-02-11
Have you tried booting the desktop with the live CD?

---

### Post by ilikebananafudge on 2012-02-11
I tried the CD. I got the following similar screen (see image). I have read that the UEFI system that my motherboard uses has had some problems in the past? Any other suggestions are welcome. Thanks!

Adam

---

### Post by ilikebananafudge on 2012-02-13
Still haven't solved the problem, any other ideas?

---

### Post by raja.genupula on 2012-02-13
> If it helps, I am able to type commands at the bottom of the screen.

this may help you 

[http://blog.eracks.com/2008/10/ubuntu-livecd-wont-boot-no-problem/](http://blog.eracks.com/2008/10/ubuntu-livecd-wont-boot-no-problem/)

---

### Post by ilikebananafudge on 2012-02-14
So I tried manually mounting after I get the failed boot from the USB and the CD. However, I wasn't sure how to find the device name in Windows, so I guessed to some extent. How do I find the device name in Windows?

Then I thought I would try to install Ubuntu using Wubi. I know its not going to be as fast, but I have a fast computer so I don't care very much. I had to choose the option of ACPI workaround when using Wubi, and that worked, until I had to restart the computer at the end of the install. Then I get the GRUB menu and can boot Ubuntu in regular or recovery mode. If I boot in regular I get the purple screen of death (frozen on purple), and if I boot in recovery mode it freezes on loading initial ramdisk...

I appreciate the help so far. Any other advice?

---

### Post by ilikebananafudge on 2012-02-14
Update: If I hit F6 when attempting to boot from CD and change it so that the acpi is off, then I can boot into Ubuntu successfully. I've read that turning acpi off is not always great for your system, is that true? Also, I want to install Ubuntu on this computer, but I worry that it will not work. Should I install it?

---

