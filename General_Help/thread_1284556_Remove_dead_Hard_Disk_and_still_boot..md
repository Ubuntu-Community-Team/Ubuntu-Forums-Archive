---
title: "Remove dead Hard Disk and still boot."
date: 2009-10-06
forum: General Help
---

### Post by Merovius on 2009-10-06
Can someone tell me how to remove a dying HD without GRUB going crazy and stopping me from booting with error 21? 

I am on Karmic beta. There is a new disk Utility that is telling me my third HD (20 gig) is failing and I would like to remove it. (It's only in there as a spare anyway.)

Karmic is on one HD. XP pro is on a second HD. If I disconnect the third useless drive I cannot boot. I get to error 21 and stop.

So how exactly do you remove a HD without screwing up GRUB?? :confused:

---

### Post by lindsay7 on 2009-10-06
Post the results of 

sudo fdisk -l   (that is the lower case letter L)


If this disk is just a spare, your grub menu should not care if it is removed. So lets see what your system looks like.

---

### Post by Merovius on 2009-10-06
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00092911

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9337    74999421   83  Linux
/dev/sda2            9338       38913   237569220    5  Extended
/dev/sda5            9338        9835     4000153+  82  Linux swap / Solaris
/dev/sda6            9836       19172    74999421   83  Linux
/dev/sda7           19173       38913   158569551    7  HPFS/NTFS

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb1119bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100       14946    79096027+   f  W95 Ext'd (LBA)
/dev/sdb5            5100        7649    20482843+   7  HPFS/NTFS
/dev/sdb6            7650       14946    58613121    7  HPFS/NTFS

Disk /dev/sdc: 20.5 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec34ec34

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2491    20008926    b  W95 FAT32

Thanks..

---

### Post by lindsay7 on 2009-10-06
I see no reason for your grub menu to need your extra disk drive. I think that your bios must be set to look at this drive to start before the actual disk drive with your system on it. So go to your bios setup and make sure that the extra 20 gig drive is not listed in your startup sequence of disk drives.

---

### Post by Merovius on 2009-10-06
I went into the bios and had it auto detect the drives and it showed that the drive was no longer installed. I thought GRUB might be checking with the bios before boot. This had no effect.

Replace the drive and all is well.

I had removed it without any concern as I too thought it would just disappear from my list of drives. I never gave GRUB a thought. I have done this under Windows for years and It has never effected the boot.

I'm about to try super GRUB disk. Do you see any harm in that?

Thanks again.

---

### Post by lindsay7 on 2009-10-06
You can try SuperGrub just be careful with it and read the docs on it.

You may want to try this first,



1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type “sudo grub”. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

---

### Post by lindsay7 on 2009-10-06
You may also want to try,

sudo update-grub

---

### Post by Merovius on 2009-10-06
I have determined that with the 20 Gig drive installed it is second in the boot order. The Linux 320 Gig drive is third. XP 120 Gig is first. I think Grub is on the XP disk (1st in order) Maybe it's on the Linux disk and I need to change the order..... ??

I will have to disconnect the drive and then look at the order. I will then try booting with the XP disk first and then the Linux disk first.

If that doesn't do it I will try the Live CD as you recommend.

Thanks for the help/tips.

---

### Post by lindsay7 on 2009-10-06
YOur bios should only show the Linux and Windows hard drive and not even look for the third (extra drive). If bios looks for it and does not see it you will get the grub 21 error.  You may need to set your bios so that it looks for the correct drive first and that could be the windows or the linux drive depending on how your grub menu is setup.

---

### Post by Merovius on 2009-10-06
I will focus in that area. Sounds like we are on to something..:)

---

### Post by Merovius on 2009-10-11
Super grub disk has solved the problem. I removed the failing drive and booted to SGD and poked around in there. Tried two things and the second "automatic" choice I made worked. Couldn't honestly tell you what it fixed or how but all is well. :guitar:

---

