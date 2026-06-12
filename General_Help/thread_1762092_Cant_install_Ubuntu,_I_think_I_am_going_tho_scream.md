---
title: "Cant install Ubuntu, I think I am going tho scream!"
date: 2011-05-18
forum: General Help
---

### Post by brad1138 on 2011-05-18
I have been building computers for over 15 years. I used windows up till 2006, when I started dual booting with Ubuntu. It is usually a very easy task. 

In the last year or so I have been having a lot of trouble with the install discs. Now I can't install Ubuntu at all on a pc I am trying to build.

I have burned ISOs of 10.04 lts/10.04.2 lts, 10.10, 11.04. I have burned with multiple computers with multiple CD Burners with XP & Ubuntu & I have verified the checksums and I still have the same problem with the discs. I get one of about 3 or 4 different errors, which I see other people getting when I search for them. 

I get the very common: "BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu4) built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs"

I get: "Chroot can not execute" errors & Input output errors. 

occasionally the live cd will actually make it to the GUI, then I get errors trying to install ubuntu.

THIS IS RIDICULOUS! 

I have 4 computers in the house that are dual boot, but right now, if one crashes I could not reinstall ubuntu and would have to go back to XP.

What the heck is going on?????

Thanks,
Brad

---

### Post by lmarmisa on 2011-05-18
I do not like CDs. I prefer USB flash drives. 

If you get so many problems with CDs, I recommend to create a Ubuntu Live USB using UNetbootin or Startup Disk Creator. Select the iso file of Ubuntu which you wish to install for preparing the Live USB. Do not use the physical CD as source, because it seems not reliable.

---

### Post by brad1138 on 2011-05-18
> **lmarmisa said:**
> I do not like CDs. I prefer USB flash drives. 

If you get so many problems with CDs, I recommend to create a Ubuntu Live USB using UNetbootin or Startup Disk Creator. Select the iso file of Ubuntu which you wish to install for preparing the Live USB. Do not use the physical CD as source, because it seems not reliable.

My computers (motherboards anyway) are from about 2000 to 2005. Athlon XP 2400+ to Athlon 64 3200. I don't believe any of them will boot from a USB drive.

---

### Post by lmarmisa on 2011-05-18
If you are using only one optical disc drive, maybe this is the origin of your problems. Some of the components of these devices (for example, the internal lens) may deteriorate over time or require some type of cleaning. 

Try to use another CD drive in order to check if this is the cause of your trouble.

---

### Post by dFlyer on 2011-05-18
> **brad1138 said:**
> I have been building computers for over 15 years. I used windows up till 2006, when I started dual booting with Ubuntu. It is usually a very easy task. 

In the last year or so I have been having a lot of trouble with the install discs. Now I can't install Ubuntu at all on a pc I am trying to build.

I have burned ISOs of 10.04 lts/10.04.2 lts, 10.10, 11.04. I have burned with multiple computers with multiple CD Burners with XP & Ubuntu & I have verified the checksums and I still have the same problem with the discs. I get one of about 3 or 4 different errors, which I see other people getting when I search for them. 

I get the very common: "BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu4) built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs"

I get: "Chroot can not execute" errors & Input output errors. 

occasionally the live cd will actually make it to the GUI, then I get errors trying to install ubuntu.

THIS IS RIDICULOUS! 

I have 4 computers in the house that are dual boot, but right now, if one crashes I could not reinstall ubuntu and would have to go back to XP.

What the heck is going on?????

Thanks,
Brad

I've had a similar problem that I solved by switching to dvd's. I realize it's a waste of disc space, but I'm no longer wasting cd's.

---

### Post by ghostborg on 2011-05-18
I have installed almost always with CD's and not had problems with the discs that I have created even with the cheapo's.

I have stuck the wrong architecture disc in at times.

I have had problems in the past on an older machine where I disabled the on-board video in the bios and selected to initialize the AGP card first but Ubuntu would not install. Had to remove AGP card, enable on-board video and then install Ubuntu. Afterward put the AGP card in and disabled the on-board to get it to work.

If your building a new machine your interface has to be set correctly in the bios.

On my machine in the bios I have my Hard-drives connected to Sata ports (0-3) set to AHCI but I have an option to set just Sata ports 4/5 as "type IDE" which my Sata DVD drive is plugged into otherwise it wouldn't work.

Good luck

---

### Post by brad1138 on 2011-05-18
> **lmarmisa said:**
> If you are using only one optical disc drive, maybe this is the origin of your problems. Some of the components of these devices (for example, the internal lens) may deteriorate over time or require some type of cleaning. 

Try to use another CD drive in order to check if this is the cause of your trouble.


I have tried 5 different CD recorders in 3 different machines.

> I have had problems in the past on an older machine where I disabled the on-board video in the bios and selected to initialize the AGP card first but Ubuntu would not install. Had to remove AGP card, enable on-board video and then install Ubuntu. Afterward put the AGP card in and disabled the on-board to get it to work.

If your building a new machine your interface has to be set correctly in the bios.


all bios setting are correct. Also I have xp installed on this machine and it works fine. Most of my Motherboards have no onboard video.


I just tried the USB option. I found that I can boot from the USB with the computer I am building. But once again, it failed. With a whole new problem:

"Unknown keyword in configuration file: gfxboot vesamenu.c32: not a com32r image boot:"

I was trying 10.04.2

This is a joke. How can so many separate computers, all working fine, create so many bad install devices?

OK just searched for that last problem and found this [https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779/comments/7](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779/comments/7) fix, it booted and so far so good.

Thanks lmarmisa for mentioning the usb option.

---

### Post by brad1138 on 2011-05-18
addendum: The problem with the USB drive is a bug caused by creating a 10.04 boot with 10.10 or 11.04. (11.04 for me) and is also covered by this [https://bugs.launchpad.net/ubuntu/maverick/+source/usb-creator/+bug/645818](https://bugs.launchpad.net/ubuntu/maverick/+source/usb-creator/+bug/645818)

---

### Post by claracc on 2011-05-19
About the problem of reinstalling ubuntu systems, you always can use dd command (if CDs nor usb work).

You can download to your computer the iso image of the ubuntu distro to your user folder and the use dd if=/home/user/distro.iso of=/dev/sdb1 bs=4M (or whatever part where you want to duplicate the image), and then install or simply trying the distro from there.

You can see the man dd pages to learn howto use the command in the safe way.

---

