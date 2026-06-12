---
title: "Ubuntu doesn't appear on GRUB listing"
date: 2010-08-09
forum: General Help
---

### Post by CanadianPenguin on 2010-08-09
Okay, I have an old Windows XP Media Centre 2005 computer. My sister is the primary user of the computer and she's always downloading viruses and stuff on it so I decided to clean it up a bit and install Ubuntu via Wubi so we could use something that was harder to screw up, easier to use, and faster. I downloaded the iso of Lucid and ran Wubi.

The installation worked fine (with the exception of that annoying "no disk" pyrun.exe error, which I had to keep clicking cancel to get out of). I restarted the computer, selected Ubuntu, and Lucid began to install and showed that very well-presented slideshow of Ubuntu's features. It finished, told me to reboot my computer and all seemed well until it reached the boot menu.

When it comes up to XP's boot selector, it gives me the standard list - pick between XP Media Centre and Ubuntu. I selected Ubuntu. Then, it brings me to the GRUB menu. Except, there's no Ubuntu options, just "Dell Recovery Partition" and "Windows XP." I'm positive that Dell Recovery Partition is the factory restore thing since I've used it before, but selecting Windows XP brings be back to XP's OS chooser. It's just an infinite loop until you choose XP from its own OS list.

I'm not sure if this has anything to do with it, but a "skip" button appeared on the installation near the end when it didn't appear to be doing anything, so I clicked it. Would that have affected the install?

I've already googled this problem and I've only come across one thread with this problem, and it was from 2 months ago and didn't seem to have a clear resolution. This problem is pretty depressing considering I've used Wubi on two other computers and never ran into any trouble.

Also, I would dual boot but I see no problem with using Wubi since it saves a lot of trouble and there's 95% less chance of breaking something (I've been using it for a month or so on my Dell laptop since my preinstalled Windows Vista KSOD'd and I haven't ran into any complications). Plus, I don't have any blank disks or USBs laying around and I'm not waiting 2 months to get a Ubuntu CD.

---

### Post by bcbc on 2010-08-09
I've seen a few instances of this cropping up recently. First time I heard about someone pressing the SKIP button.

You could try booting manually. Next time you get to the grub menu, press 'c' to get to command line.
Then look for your root.disk:
```
search.file /ubuntu/disks/root.disk
```
if that works it will give you a partition (hdX,Y). Determine the device name of the partition:
(hd0,1) = /dev/sda1
(hd0,5) = /dev/sda5
(hd1,2) = /dev/sdb2

Try booting (I'm assuming (hd0,1) and /dev/sda1 here, change as appropriate):
```
insmod ntfs
set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```

I don't know this will work - if any part gives you an error or unexpected result, post back here (don't continue).
To get out of the grub command line, you can enter "reboot" to restart the computer or press ESC to get back to the menu.

If it boots, run "sudo update-grub" and see if it picks up the linux kernel.

---

### Post by CanadianPenguin on 2010-08-09
> **bcbc said:**
> I've seen a few instances of this cropping up recently. First time I heard about someone pressing the SKIP button.

You could try booting manually. Next time you get to the grub menu, press 'c' to get to command line.
Then look for your root.disk:
```
search.file /ubuntu/disks/root.disk
```if that works it will give you a partition (hdX,Y). Determine the device name of the partition:
(hd0,1) = /dev/sda1
(hd0,5) = /dev/sda5
(hd1,2) = /dev/sdb2

Try booting (I'm assuming (hd0,1) and /dev/sda1 here, change as appropriate):
```
insmod ntfs
set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```I don't know this will work - if any part gives you an error or unexpected result, post back here (don't continue).
To get out of the grub command line, you can enter "reboot" to restart the computer or press ESC to get back to the menu.

If it boots, run "sudo update-grub" and see if it picks up the linux kernel.

I got it working with a similar command,  but unfortunately I have to enter it every time I start the computer. Any suggestions?

---

### Post by bcbc on 2010-08-09
> **CanadianPenguin said:**
> I got it working with a similar command,  but unfortunately I have to enter it every time I start the computer. Any suggestions?

so you've run sudo update-grub and it doesn't fix it?

Post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")  - maybe this will help see what's happening.

---

