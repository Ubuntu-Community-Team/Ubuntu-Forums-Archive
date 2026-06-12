---
title: "Cannot boot after update, and forgot to uninstall non-working GRUB2"
date: 2009-08-20
forum: General Help
---

### Post by murderslastcrow on 2009-08-20
K, sooo... Here we go.

2 days ago I installed GRUB2. I tried to chainload into it, but met an Error 11 : Device not found, something like that.

So, I push c, and enter

root (hd0,0)
kernel /vmlinuz
boot

It boots correctly, no problem. Then I get this update before uninstalling GRUB2 or trying to fix it, and it required a restart, although I'm not sure if it was a new kernel or anything. (an hour ago, presumably)

So, restart and I get to a point in the startup telling me that it can't find the root device. Aaaww, shih. It lists possible drives with their size, sda1 obviously being my HD (along with sda2 and sda5, one of which is swap space).

SO, I restart and try using UUIDs provided by the backup Debian list left by GRUB2's chainloading menu. root= BIGFATNUMBERWITHHYPHENS. Doesn't work. root= /dev/sda1, or any variation does not work. root= /dev/hda1, or /dev/hd... nothing works.

So, I try to just enter the line using the kernel versions I have. Example:

root (hd0,0)
kernel /boot/vmlinuz(kernelname)-(kernelversion)-generic
initrd /boot/initrd(kernelname)-(kernelversion)-generic.img

So, when I do that, it gets to a certain point about Clocksource tsc unstable, after trying to load something (Sonic Silicons, something something), then gives me a different error than the first one.

ALERT! does not exist (that's right, doesn't list what doesn't exist). And it's preceded by rootdelay long enough? root= right? Did you choose the right one, stupid!?

Then it drops to busybox, which is SOOOO helpful.

So, I just need to find out what root is supposed to be, hopefully. The main issue here is that the CD drive doesn't work on this computer, and my USB drives with Ubuntu are cities away at the moment, so no option to boot into a Live environment.

Anyone see what I'm doing wrong, other than updating without fixing stuff? XD

---

### Post by murderslastcrow on 2009-08-20
Another note- same results when I use ro single or ro quiet splash, etc. I've tried a lot of options. @_@ Something tells me I'm not gonna' be able to work for tonight.

For the first time in my life, Linux has DECREASED my productivity. How embarrassing.

---

### Post by murderslastcrow on 2009-08-21
No root ID experts here, I guess. Well, I found some mp3-headphones I can use as a live-USB, so I'll try to fix it from the Live environment. Still, it'd be nice to know what to do if I didn't have one available, since not everyone in the world will.

@_@ So annoying. I'm glad Linux keeps getting better with each new kernel. Hopefully Ubuntu will, too. I'll come back here with a solution if I can find one.

---

### Post by neophyte_7 on 2009-08-21
Have you tried editing the menu.lst?

just put a live cd, run fdisk -l, and see where the linux root partition is.....

eg. let root partition is at sda5
then type sudo vi /boot/grub/menu.lst
and check the numbers inside the bracket hd(0,?) near linux root partiton.....enter 4 in place of question mark, save and reboot from HDD


i.e, if the partition is on 5 put hd(0,4)
if its on 4 put hd(0,3) 


I had screwed up order of numbers and had error 17 on boot.....this had helped

---

