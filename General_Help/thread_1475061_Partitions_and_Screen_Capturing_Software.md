---
title: "Partitions and Screen Capturing Software"
date: 2010-05-06
forum: General Help
---

### Post by Hman242 on 2010-05-06
Okay, I have two problems I need some help with.

I seem to be in a bit of a pickle. I have four primary partitions currently. I need to keep all of them. I need to make a fifth that is also a primary partition. Is there a way to somehow make a partition into a partition that's in an extended partition without losing any data? Maybe you know of another solution to my problem, but this is the only one I can conjure up.

The second problem is much less severe. I can't find any screen capturing software for Ubuntu that will record my desktop and simultaneously record sound from a microphone. Would any of you know of one that does this?

Thanks for helping me with my problem in advance.

---

### Post by Twitch6000 on 2010-05-06
> **Hman242 said:**
> Okay, I have two problems I need some help with.

I seem to be in a bit of a pickle. I have four primary partitions currently. I need to keep all of them. I need to make a fifth that is also a primary partition. Is there a way to somehow make a partition into a partition that's in an extended partition without losing any data? Maybe you know of another solution to my problem, but this is the only one I can conjure up.

The second problem is much less severe. I can't find any screen capturing software for Ubuntu that will record my desktop and simultaneously record sound from a microphone. Would any of you know of one that does this?

Thanks for helping me with my problem in advance.
Problem 1: This cannot be done. Only four primary partitions can be made. 

Problem 2: There are a few programs for this. Your results may vary.

gtk-recordmydesktop is the most common. The second most common is istanbul.

---

### Post by Hman242 on 2010-05-06
[LIST=1]
[*]I know that, but I was asking if I could turn an already existing partition into an extended partition without losing any data.
[*]I've tried Istanbul, but I don't recall it having that feature. I'll try the other one once I get a chance.
[/LIST]

---

### Post by Twitch6000 on 2010-05-06
> **Hman242 said:**
> [LIST=1]
[*]I know that, but I was asking if I could turn an already existing partition into an extended partition without losing any data.
[*]I've tried Istanbul, but I don't recall it having that feature. I'll try the other one once I get a chance.
[/LIST]

1. I do not think so,but I could be wrong. if anything just back it up with a usb flash drive and try.

2. Okay there also is [http://sourceforge.net/projects/webcamstudio/develop](http://sourceforge.net/projects/webcamstudio/develop) which does what you want and more.

---

### Post by srs5694 on 2010-05-06
> **Hman242 said:**
> I seem to be in a bit of a pickle. I have four primary partitions currently. I need to keep all of them. I need to make a fifth that is also a primary partition. Is there a way to somehow make a partition into a partition that's in an extended partition without losing any data? Maybe you know of another solution to my problem, but this is the only one I can conjure up.

It can be done, but it's at least potentially a bit risky and how best to do it depends on your current partition layout and precise needs. Please post the output of the following command, typed in a Terminal or similar command shell window: "sudo fdisk -lu". Please post the output between a [noparse]```
[/noparse] string and a [noparse]
```[/noparse] string; this will preserve the spaces in the output, improving legibility. Also please tell us what you hope to accomplish and why. For instance, "I want to create a shared-data partition for Linux and Windows" or "I want to create a separate /home partition for Linux to enable future re-installations while preserving my user data."

---

### Post by Hman242 on 2010-05-06
I would like to install another operating system on a new partition.

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x29e95222

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          409600   470222549   234906475    7  HPFS/NTFS
/dev/sda3       470222550   976559219   253168335   83  Linux
/dev/sda4       976560128   976771119      105496    c  W95 FAT32 (LBA)

```

---

### Post by srs5694 on 2010-05-06
I'm guessing you've got Windows and Linux dual-booting, presumably with /dev/sda4 being a shared-data partition. You do have room to convert /dev/sda4 into a logical partition, but the partition is tiny enough that it's not worth risking a raw conversion -- it's only 103MB in size, which is very easy to back up. Thus, I recommend you back it up, delete it, resize and move /dev/sda2 and/or /dev/sda3, create a new extended partition, create a new partition to hold whatever had been in /dev/sda4, and create new logical partition(s) for your additional OS.

Note that some OSes must be installed to primary partitions. If you're trying to install such asn OS, you'll have to convert /dev/sda3 into a logical partition. This can be done, but it's a risky proposition. I won't go into all the gory details just yet, since I'm hoping it won't be necessary; post back with more information if you think it is.

---

### Post by chappajar on 2010-05-07
> **Hman242 said:**
> Okay, I have two problems I need some help with.

I seem to be in a bit of a pickle. I have four primary partitions currently. I need to keep all of them. I need to make a fifth that is also a primary partition. Is there a way to somehow make a partition into a partition that's in an extended partition without losing any data? Maybe you know of another solution to my problem, but this is the only one I can conjure up.

The second problem is much less severe. I can't find any screen capturing software for Ubuntu that will record my desktop and simultaneously record sound from a microphone. Would any of you know of one that does this?

Thanks for helping me with my problem in advance.

Just curious; why do you need so many partitions to be primary?

---

### Post by Hman242 on 2010-05-07
> **srs5694 said:**
> I'm guessing you've got Windows and Linux  dual-booting, presumably with /dev/sda4 being a shared-data partition.  You do have room to convert /dev/sda4 into a logical partition, but the  partition is tiny enough that it's not worth risking a raw conversion --  it's only 103MB in size, which is very easy to back up. Thus, I  recommend you back it up, delete it, resize and move /dev/sda2 and/or  /dev/sda3, create a new extended partition, create a new partition to  hold whatever had been in /dev/sda4, and create new logical partition(s)  for your additional OS.

Note that some OSes must be installed to primary partitions. If you're  trying to install such asn OS, you'll have to convert /dev/sda3 into a  logical partition. This can be done, but it's a risky proposition. I  won't go into all the gory details just yet, since I'm hoping it won't  be necessary; post back with more information if you think it  is.
I am dual-booting Ubuntu and Windows but I'm not able to delete the  other two partitions. For some odd reason, Windows won't boot without  them so I have to keep them.

You said *some* OSs need to be on a primary partition. Is Ubuntu one of these?

---

### Post by srs5694 on 2010-05-07
Linux can boot from either a primary or a logical partition. If Windows won't boot without /dev/sda4 (your FAT partition), then it's an odd configuration. Perhaps you've got some remnant of an ancient Windows or even DOS installation on that partition that's gotten tangled up in your Windows boot process. If so, it would be unwise to convert it from a primary partition to a logical partition, whether directly or via a backup/restore process. Going on that presumption, you're left with the Ubuntu partition for conversion. Here's the process:


[list=1]
[*]Resize /dev/sda2 to trim a bit off its end, leaving a gap between it and /dev/sda3. If you don't want to shrink /dev/sda2, then just shrink it by a bit; but if you want to devote much of its space to your new partition(s), shrink it by more. If possible, do this resize operation using Windows tools, since shrinking the Windows boot partition from Linux can occasionally leave Windows unbootable.
[*]Test that Windows still boots. If it doesn't, use Windows recovery tools to fix the problem.
[*]Boot Linux.
[*]Type "sudo sfdisk -d /dev/sda > sda-parts.txt".
[*]Copy sda-parts.txt to a USB flash drive, CD-R, or other removable medium. If things go south, you'll be able to restore it to get a working system back.
[*]Edit sda-parts.txt. Duplicate the entry for /dev/sda3, putting the duplicate at the end of the file and renaming it /dev/sda5. Then edit the /dev/sda3 entry, reducing its start field by one and increasing its length field by one. Also, change its "Id" code from "83" to " f". These changes create a new extended partition that's just barely big enough to hold the Ubuntu partition, which (as /dev/sda5) will be interpreted as a logical partition.
[*]Type "sudo sfdisk --force /dev/sda < sda-parts.txt".
[*]Check the contents of your /etc/fstab and GRUB configuration files (/boot/grub/menu.lst or /boot/grub/grub.cfg). If you see any entries that reference /dev/sda3, change them to /dev/sda5. It's OK if there are no such entries; Ubuntu often uses UUIDs rather than device names.
[*]Cross your fingers and reboot.
[*]If the system comes up, you're golden. You can now reboot into an emergency disc and use GParted to move and resize your partitions. (You can't do this from within your disk-based boot because GParted doesn't let you edit in-use partitions.) Note that you may need to resize the extended partition that now surrounds /dev/sda5 (the logical partition) before you'll be able to add new partitions.
[*]If the system *doesn't* boot correctly, it may be possible to recover by using an emergency disc to re-install GRUB or edit partitions with GParted; however, you may need to dig out the *original* (unmodified) sda-parts.txt file and re-write it via "sudo sfdisk --force /dev/sda < sda-parts.txt". If you do this, you'll need to change your GRUB and /etc/fstab references to /dev/sda5 back to /dev/sda3.
[/list]


Note that what I've just described is *risky.* Be *very careful,* particularly when editing sda-parts.txt. Back up your data -- at least your important personal files, and preferably everything -- before proceeding.

---

