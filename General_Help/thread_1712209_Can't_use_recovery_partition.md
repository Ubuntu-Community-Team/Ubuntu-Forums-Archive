---
title: "Can't use recovery partition"
date: 2011-03-22
forum: General Help
---

### Post by jhargis1012 on 2011-03-22
Hello, friends. I need to recover a system (Gateway laptop, four years old) I've had Ubuntu installed on for a few years. I've never used the recovery partition, so I'm not sure how it is supposed to work, but I know something is wrong.

First off, grub has always seen my recovery partition (listed beneath the primary Windows Vista partition). Now that I actually want to use it, I try to select it from the menu, but it just boots right back to regular Windows Vista.

Inside Vista, there is a Gateway recovery application, inside which there is an option to restore the system to its factory condition. I select this, and it tells me to reboot to begin the process, which I do, but as I said before nothing happens.

I've tried fixing the boot process on my machine by getting rid of grub, deleting the Ubuntu partition, etc... I used a Windows Vista recovery disc, hoping this would reinstate the original boot settings of the computer, but instead, during some repair process, it didn't recognize my recovery partition and suggested I get rid of it. I (stupidly) told it to go ahead and do whatever it was going to do. Now there is no boot option for my recovery partition.

I used a program called EasyBCD by Neosmart to make a new boot menu. As of right now, the only partition that can be booted from is the primary Vista one. However, I know my recovery partition is still intact because I can see it in Windows Explorer.

I've gotten myself into a bit of a mess, as you can see. I would just like to know if there is some way I can get the recovery partition (which is still there, just not starting) to boot up the way it is supposed to.

I appreciate any help you can offer.

---

### Post by Mark Phelps on 2011-03-22
You could start by giving us a look at your current partition setup.  To do that, boot from an Ubuntu CD, use the Try It option (don't install), open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list out your partitions and their usage.  

That will show us if you Recovery partition, although still there, is actually empty.

If it is empty, you only recourse then will be to contact Gateway and see how much they will charge you for a full-recovery set of CDs (or DVD).

---

### Post by jhargis1012 on 2011-03-22
Thanks for getting back to me.

Here you go:

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x779281f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20836304    10418121    7  HPFS/NTFS
/dev/sda2        20836305   312576704   145870200    7  HPFS/NTFS

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          38     7839719     3919841    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 

```

---

### Post by Mark Phelps on 2011-03-22
Hmmm ... don't see anything that looks like a recovery partition.

So, boot back into Ubuntu, using the CD, and use Partition Editor to look at the details of the partitions on the drive.  If one of these partitions actually is a recovery partition, it should have a label indicating that -- which you will see in the Partition Editor.

---

### Post by jhargis1012 on 2011-03-22
Yep, gparted shows two main partitions. It looks like this:

/dev/sda1 NTFS Recovery 9.94GiB(size) 5.28GiB(used) 4.65GiB(unused) boot(flags)

/dev/sda2 NTFS Vista 139.11GiB etc...

unallocated 2.49MiB (Don't know what that's about)

And then there's an indicator on the Vista partition that says it's corrupted (which is weird because that's the one that works). It's also weird that the boot flag is on the recovery partition.

---

### Post by Mark Phelps on 2011-03-23
> **jhargis1012 said:**
> Yep, gparted shows two main partitions. It looks like this:

/dev/sda1 NTFS Recovery 9.94GiB(size) 5.28GiB(used) 4.65GiB(unused) boot(flags)

/dev/sda2 NTFS Vista 139.11GiB etc...

unallocated 2.49MiB (Don't know what that's about)
OK ... looks like your Recovery partition is still there and (maybe) still intact.

>  And then there's an indicator on the Vista partition that says it's corrupted (which is weird because that's the one that works). It's also weird that the boot flag is on the recovery partition.

The boot flag was probably set on the Recovery partition when you tried to do the restore.  Typically, there's a small minimal installation of WinPE or WinRE in that partition, allowing it to boot into a environment that will then perform the restore.

You should NOT need the Vista partition to be intact in able to do a restore using the Recovery partition -- but if it's not working, that could be the reason.

Under other circumstances, I would suggest booting from an Ubuntu desktop CD and using Partition Editor to delete the Vista partition.  Perhaps with that gone, the Restore operation would then work.

But if you can't boot into the Restore operation, you're not going to be able to use the Recovery partition.

At this point, you should contact Gateway and see what they will do for you. They might provide you a CD that will enable you to do the restore -- but they will probably charge you for it.

---

### Post by jhargis1012 on 2011-03-23
Got it, thanks for the help.

---

