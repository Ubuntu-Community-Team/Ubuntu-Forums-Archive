---
title: "Parted and UFS/ZFS FreeBSD partition types"
date: 2011-06-24
forum: General Help
---

### Post by User4519 on 2011-06-24
Hello :)

I'm about to migrate a 7-disk ZFS-FUSE array to a new bigger 19-disk one. My previous array was just disks (and md arrays) with MS-DOS partition tables and x83 partitions on them.

The new one I'd like to be compatible with FreeBSD, too, so I want to use GPT tables and proper partition types for FreeBSD, which [according to wikipedia]("http://en.wikipedia.org/wiki/GUID_Partition_Table") all have a GUID of 516E7CBA-6ECF-11D6-8FF8-00022D09712B, except for boot partitions.

This includes ufs partitions, which according to [FONT="Courier New"]man parted[/FONT] is supported:
[FONT="Courier New"]mkpart part-type [fs-type] start end
                     Make a part-type partition with filesys&#8208;
                     tem fs-type (if specified), beginning at
                     start and ending at end (by  default  in
                     megabytes).    fs-type  can  be  one  of
                     "fat16", "fat32", "ext2", "HFS", "linux-
                     swap",  "NTFS",  "reiserfs",  or  "**ufs**".
                     part-type should be  one  of  "primary",
                     "logical", or "extended".[/FONT]

But, when using mkpart or mkpartfs and asked which type to create, and answering "ufs", I get "parted: invalid token: ufs", even though ufs is explicitly listed as an option in the manpages. Interestingly, answering "zfs" which **isn't listed** as an option, I get "Support for creating zfs file systems is not implemented yet."

What gives? Are the manpages broken or the program buggy, and most importantly, how can I know which partition types are possible to create, and how do I create a FreeBSD type partition?

These attempts were with the latest parted from the repos of a an Ubuntu Natty Server installation.

Thanks in advance,
Daniel :)

---

### Post by srs5694 on 2011-06-24
The UFS support in parted is probably restricted to MBR partitions. You can use my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) to create FreeBSD UFS and ZFS partitions on a GPT disk. (You'd give them type codes of a503 and a504, respectively.)

Also and FWIW, the latest version of parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition. That's not directly relevant to your current needs, but I just wanted to throw it out there as a heads-up. (I don't think this will affect GParted, since it seems to implement filesystem support independently of libparted.)

---

### Post by User4519 on 2011-06-24
Hi Rod, thanks for replying :)

You might be right about the UFS MBR thing, though it doesn't seem right considering that UFS is Solaris/BSD, and the default partition table type there is GPT?

About the FS gotcha - you're right, it's not an issue for me, since I'll be using zpool for that anyway (and I'm used to doing fdisk + mkfs anyway).

In the meantime, I tried some more combos, and while UFS is still a total no-go with both mkpart and mkpartfs in parted, I can actually create a "zfs" type partition using mkpart with no warnings or errors. Completely undocumented, LOL :D

Anyway, thanks for linking to your program. I also quickly noted the documentation you've written about GPT. I'll be reading that now, thank you, as GPT is pretty much in the dark for me ATM, and I have a couple of hours anyway, waiting for badblocks to finish on a couple of drives ;)

One quick follow-up question: Does that gdisk app of yours make it easy to ensure 4k alignment? Or, if not, do you have advice for ensuring this with parted? I found this,
[FONT="Courier New"]parted /dev/sda
unit s                      
mkpart primary ext4 2048 3906248704
[/FONT]
- which seems right when comparing to what one would do with fdisk, but I do like to make absopositively sure when dealing with this ;)

Thanks again!

Daniel

---

### Post by User4519 on 2011-06-24
Btw, in your docs, "Eight for the Price of One?", about Windows XP and 4k drives: I did test this, and XP (32-bit) has no problems using such a drive. The problem is that the Windows installer itself will create misaligned partitions if you let it. The only way to properly align partitions is to created them first in another capable OS and then install XP onto the previously created partitions.

Just an FYI :)

---

### Post by User4519 on 2011-06-24
Okay, reading through your texts and checking out gdisk, I can see that it's very easy to create proper FreeBSD ZFS partitions AND ensure 4k alignment with its default 2048*512B alignment strategy.

This gdisk is **really** good! Thank you so much for making it! :)

---

### Post by User4519 on 2011-06-24
Just one final question, though :) With the "compatibility" MBR partition being created (i.e. the one that appears as 0xEE/GPT in fdisk for say, /dev/sda), is /dev/sda1 and /dev/disk/by-id/ata-BLAHBLAH-part1 then the MBR partition 0xEE or the GPT partition a520?

---

### Post by srs5694 on 2011-06-24
> **DanielBuus said:**
> You might be right about the UFS MBR thing, though it doesn't seem right considering that UFS is Solaris/BSD, and the default partition table type there is GPT?

In the BSD world, at least, the default partition table type is a BSD disklabel inside an MBR partition. In the past, BSD disklabels without an MBR partition table were at least somewhat common, but they don't seem to be very common today. GPT support in BSD exists, and it's possible to install FreeBSD to a GPT disk, but the last time I checked, the FreeBSD installer couldn't do so directly; you had to do so indirectly in one way or another. (FWIW, the BSDs are transitioning to GPT just like everybody else because BSD disklabels use 32-bit sector pointers, so they're limited to 2 TiB disks just like MBR.)

> Just one final question, though :smile:  With the "compatibility" MBR partition being created (i.e. the one that  appears as 0xEE/GPT in fdisk for say, /dev/sda), is /dev/sda1 and  /dev/disk/by-id/ata-BLAHBLAH-part1 then the MBR partition 0xEE or the  GPT partition a520?

Linux ignores the protective partition in the MBR on GPT disks, except as part of its verification that a disk *is* a GPT disk. The device nodes (/dev/sd??, /dev/disk/by-id/*, and so on) all refer to GPT partitions.

---

### Post by User4519 on 2011-06-24
> **srs5694 said:**
> In the BSD world, at least, the default partition table type is a BSD disklabel inside an MBR partition. In the past, BSD disklabels without an MBR partition table were at least somewhat common, but they don't seem to be very common today. GPT support in BSD exists, and it's possible to install FreeBSD to a GPT disk, but the last time I checked, the FreeBSD installer couldn't do so directly; you had to do so indirectly in one way or another. (FWIW, the BSDs are transitioning to GPT just like everybody else because BSD disklabels use 32-bit sector pointers, so they're limited to 2 TiB disks just like MBR.)

Thanks for the info :) I've been fiddling around with PC-BSD 9 in a VM because it comes with KDE, and at least here you have the option to use GPT when installing, although it's unticked by default. For the server that I'd be putting FreeBSD 8.2 on it doesn't matter, because the server drive is the only thing it'd autosetup, and that's a 60GB SSD :) (woops - or maybe not - it really should 4k align, at least...)

I just did a test using VMware where I created a RAIDZ3 pool on GPT partitions created by your magnificent tool in a Kubuntu live environment, and then attached the virtual disks to the PC-BSD 9 environment, and the pool is immediately recognized by ZFS :) It also seems very happy about the GPT setup :)

> **srs5694 said:**
> Linux ignores the protective partition in the MBR on GPT disks, except as part of its verification that a disk *is* a GPT disk. The device nodes (/dev/sd??, /dev/disk/by-id/*, and so on) all refer to GPT partitions.

I deduced as much after creating a pool on /dev/sd?1 GPT'd disks, and afterwards both the MBR and GPT were left unscathed :)

I also really like about GPT (and gdisk) that you get to label your partitions. With 19 drives and one failing, this makes it a lot easier to pinpoint which one it is, when I get to name them Debby, Dolly, Darlene and so on ;)

Thank you once again for your help, and for your great gdisk tool! You made my day much easier :)

Daniel

---

### Post by srs5694 on 2011-06-25
Glad to have helped! Thanks for the heads-up on PC-BSD's GPT support, too -- I'll have to check it out.

---

