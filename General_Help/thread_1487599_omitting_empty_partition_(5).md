---
title: "omitting empty partition (5)"
date: 2010-05-19
forum: General Help
---

### Post by tubia87 on 2010-05-19
Hi all,
I created a different thread from the [one](http://ubuntuforums.org/showpost.php?p=9324458&postcount=10) in wich I originally posted this issue in order to avoid confusing threads.
I explain my problem:
I have 2 disks: sda 500 gigabyte and sdb 1,5 terabyte. sdb has 2 partitions: 1 ext4 empty, only for data and the other in wich I installed Xp. In sda I (should) have 5 partitions: 1 with ubuntu 10.04 beta2, 1 with the /home, 1 is an NTFS partition with data, 1 with linux mint (that I have to erase) and 1 with linux swap.
sda is now lost. This happened after I installed xp then, booting from liveCD and opening GParted, sda was all unallocated. I executed fdisk on /dev/sda and thi is the result:
```

ubuntu@ubuntu:~$ sudo fdisk /dev/sda
omitting empty partition (5)

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): p

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe541e541

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5159    41432617+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2            5159       60801   446949921+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3   *       10459       57425   377262427+   7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda5            5159       10458    42569773   83  Linux
/dev/sda6           57426       60752    26724096   83  Linux
/dev/sda7           60753       60801      393561   82  Linux swap / Solaris
```
I see in [other threads](http://ubuntuforums.org/archive/index.php/t-1078820.html), that it is a possible issue when reinstalling Xp.
Running testdisk, this is what I got in the last screen:
```

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start        End    Size in sectors
D Linux                    0   1  1  5158 254 63   82879272
P Linux                 5158  78 41 10457 254 63   85139546
P HPFS - NTFS          10458   0  1 57424 254 63  754524855
L Linux                57425   1  1 60751 254 63   53448192
L Linux Swap           60752   1  1 60800 254 63     787122


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT4 Large file Sparse superblock, 43 GB / 40 GiB
```First disk is ubuntu 10.04 beta2
Second disk is the /home partition
Third disk is the NTFS data partition (that in the beginning was set as *=Primary bootable)
Fourth disk is linux mint
Fifth disk is linux swap

Testdisk doesn't let me to hold both the first and the second partition: one of the two should be deleted (in other cases it says that the structure is bad)

Any hints or suggestions about what I should do whould be really appreciated.

Thank you in advance.

---

### Post by srs5694 on 2010-05-19
I'm not sure how to force matters with testdisk. I'm going to make a radical suggestion, which might or might not work:

Download my [GPT fdisk,](http://www.rodsbooks.com) version 0.6.5 or later. If you can't boot now, both [System Rescue CD](http://www.sysresccd.org/) and [PartedMagic](http://partedmagic.com) include GPT fdisk, although I don't know offhand what version numbers they use. If necessary, I can provide you with a binary to put on a USB flash disk for use with whatever emergency disc you're using. GPT fdisk is a tool for editing GPT partition tables. Although you probably don't want GPT, since you've got a bootable Windows on the disk, GPT fdisk also has the ability to convert to and from GPT, so you may be able to use it to produce a legal MBR setup, using GPT as an entirely in-RAM intermediate stage.

Once you've got it, launch GPT fdisk's gdisk command on the disk and verify that you're looking at all your partitions (use the 'p' command to display the partition table). If any partitions are missing, exit by typing 'q'. (Note that Linux and Windows use the same partition type codes in GPT, so both Windows and Linux partitions will be listed as type 0700, "Linux/Windows data.") If everything is present, type 'r' to get to the recovery & transformation menu and then type 'g' to to convert from the current in-memory GPT representation of your partitions back to MBR. You'll see a display that summarizes your current partitions, something like this:

```

Recovery/transformation command (? for help): **g**
Sorted GPT partitions and their current conversion status:
                                      Can Be
Number    Boot    Size       Status   Logical   Code   GPT Name
   1             4.0 GiB     primary     Y       07    Linux/Windows data
   2             3.5 GiB     primary     Y       07    Linux/Windows data

Type partition to change, 0 to accept, -1 to abort:

```

You'll probably have to adjust the type codes for some partitions, since it'll try to convert your Linux partitions to type 0x07 (NTFS), since Linux and Windows use the same type code in GPT. You may also need to adjust some primary/logical assignments. When everything looks good, type '0' to save the changes.

If at any point it looks like gdisk might omit a partition or do  something else undesirable, abort it. You can do this by typing 'q' at a  regular menu or by typing Ctrl+C at any time (during the 'g' operation  to convert to MBR, for instance).

Alternatively, but recommended only if you can't recover it any other way, you could create a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) via the 'h' option on the recovery & transformation menu. This uses both GPT and MBR partition definitions, so Windows will be happy and Linux can use the GPT definitions. Something like this could be necessary in some configurations, but I don't think it should be needed for what you've got. I mention it only as a contingency in case I've overlooked something.

In either case, the probability of your having to re-install your boot loader is pretty high, so be prepared for this. You may need to use your Ubuntu install CD/DVD or a tool such as [Super GRUB Disk,](http://www.supergrubdisk.org) which will enable you to boot without an on-disk GRUB. You can then re-install it via a "grub-install" command.

---

### Post by tubia87 on 2010-05-19
Hi srs5694, thank you for the reply!
I'm trying right now to copy the data of the second partition in sda that is my /home. I'm trying to copy that with testdisk in a 500 giga partition in sdb (another disk), in order to save all that data before trying to do anything. Lastly, I could erase totally sda and rewrote the partition table with GParted remaking one partition for ubuntu and one for its /home and no more NTFS. Windows will be only in sdb (and I hope it will not destroy anything).
If something goes wrong I'll try what you suggested (I can't interrupt the process of testdisk while copying data).

Thank you very much for the reply :)

---

### Post by dino99 on 2010-05-19
boot with partedmagic and check your partitions: look at comments about each partition into partedmagic

you probably dont need to change your installations, only small errors

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

