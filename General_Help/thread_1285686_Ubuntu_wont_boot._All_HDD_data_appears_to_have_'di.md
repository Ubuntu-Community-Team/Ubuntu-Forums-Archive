---
title: "Ubuntu wont boot. All HDD data appears to have 'disapeared'"
date: 2009-10-08
forum: General Help
---

### Post by chrisbay90 on 2009-10-08
[FONT=Verdana]Hi,

When i turn my laptop on, the BIOS loads and then moves to a blank black screen with a blinking cursor and stay like that. I can boot from live CD and other media if I insert it.

The last time i used my laptop was a few hours prior to this. I did nothing but a little web browsing and then hibernated it. I put it in my car and drove home (it didn't suffer any unusual bumps knocks or other shocks)

The hard drive passes a hard disk test from the BIOS settings menu. The installer on a ubuntu 9.04 CD loads up and correctly identifies my hard drive but claims it has no OS installed and does not detect any of the partitions on the drive. I cannot mount the harddrive from the ubuntu live CD or backtrack pre 4 CD.

--More Info on attempting to mount--
clicking on 'Mass Storage Device' in my computer in the ubuntu live cd gives the error "Cannot mount device".
At the command line i'v tried

```
root@bt:~# mount /dev/sdb /mnt/sdb
mount: you must specify the filesystem type
root@bt:~# mount -t ntfs /dev/sdb /mnt/sdb
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```I was dual booting with Win XP and it was the first partition on the drive.


--System info--
I was running Windows XP on the first partition
Ubuntu 9.04 on an ext3(or 4, i cant remember unfortunately) with a 2GB swap partition. Both inside an logical partition
A windows XP 'recovery partition' that came pre-installed on my system
another small ntfs partition at the end of the drive. I dont know what it was for but it came pre-installed and i didn't want to delete it.

[/FONT]         [FONT=Verdana]I was using grub as my boot loader.

Any help you can give you be greatly appreciated. If nothing else i would at least like to recover some of the files from my hard drive (from my linux home folder, i had nothing of use in windows) and then re-install Ubuntu if necessary.
[/FONT]

---

### Post by chrisbay90 on 2009-10-08
Bump.
I know common curtesy is to wait 24 hours. But i have a lot of important files on that hard drive. Including many uni assignments and financial data.

---

### Post by howefield on 2009-10-08
> **chrisbay90 said:**
> ...i have a lot of important files on that hard drive. Including many uni assignments and financial data...

You do have a backup of course ?

What does fdisk -l give you ?

---

### Post by drs305 on 2009-10-08
In your mount commands, you must specify a particular partition (sdb***1***) rather than the drive (sdb).  As the error message suggests, you might also try sda instead of sdb in case the computer is recognizing things in a different order.

The Super Grub Disk is great for resolving boot issues. It would not help if the partition table is corrupted for some reason but that's not likely the problem. It's a resource I'd give a try. Even if it's not the issue, it's a good disk to have handy.
[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by chrisbay90 on 2009-10-08
> **howefield said:**
> You do have a backup of course ?

What does fdisk -l give you ?

Unfortunatly my last backup was about 3 months ago.

```
root@bt:~# fdisk -l

Disk /dev/sda: 4007 MB, 4007657472 bytes
86 heads, 21 sectors/track, 4334 cylinders
Units = cylinders of 1806 * 512 = 924672 bytes
Disk identifier: 0x621d25a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1702     1536895+   b  W95 FAT32
/dev/sda2            1703        4334     2376696   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22513ab6

Disk /dev/sdb doesn't contain a valid partition table
```

[quote=drs305]
In your mount commands, you must specify a particular partition (sdb***1***) rather than the drive (sdb)
[/quote]

The thing is 'ls /dev' only lists an sdb, nothing about sdb1, sdb2 etc. Thats why I only typed sdb. This probably has something to do with there not being a valid partition table.

[quote=drs305]
It would not help if the partition table is corrupted for some reason but that's not likely the problem.
[/quote]

Given the output of dev -l would it be worth my while to go get some cd-r's and trying out super grub disk?

Thank you both drs305 and howefield for your suggestions. Does it seem likley that there is a way to retrive any of my data? Or should i just cut my losses, reinstall ubuntu and take this as a lesson to be more thorough with my backups?

---

### Post by drs305 on 2009-10-08
To restore sdb, you should give testdisk a try. It is very good at restoring partition tables. 

A search of the forums should find some good guides although I don't have any bookmarked at the moment.

Testdisk is in the repositories if you don't have it installed.

Added: Actually, I do have one bookmark:
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/~herman546/p21.html")

---

### Post by chrisbay90 on 2009-10-17
> **drs305 said:**
> To restore sdb, you should give testdisk a try. It is very good at restoring partition tables. 

A search of the forums should find some good guides although I don't have any bookmarked at the moment.

Testdisk is in the repositories if you don't have it installed.

Added: Actually, I do have one bookmark:
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")

Thank you very much. I was able to recover all of my data with testdisk.

Try as i might for the whole weekend i just couldnt seem to make ubuntu boot again. So i ended up backing up all my data and reinstalling ubuntu.

---

