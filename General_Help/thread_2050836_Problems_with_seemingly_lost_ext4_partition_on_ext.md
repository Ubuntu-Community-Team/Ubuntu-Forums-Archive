---
title: "Problems with seemingly lost ext4 partition on external USB drive"
date: 2012-08-31
forum: General Help
---

### Post by cuthbert123 on 2012-08-31
Hi all - I recently made the switch from Windows 7 to Ubuntu with a  Cinnamon shell, I copied files off my NTFS partitioned 250GB USB drive  onto my desktop partition, used gparted to partition the USB drive as  EXT4, copied files from desktop back onto it. All seemed fine and well  until I rebooted and suddenly gparted is showing the drive as not being  partitioned.... I also deleted the files before this from my desktop  partition thinking things were fine.

I have not done anything to the USB drive now, bar check it on two different machines which say the same thing.

I have ran testdisk on the drive which is /dev/sdb and I have the following output:

TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63

The harddisk (250 GB / 232 GiB) seems too small! (< 7020021 TB / 6384672 TiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
   HFS                   7412 219 21 242808  58 49 3781626626 [^C]
>  btrfs                22576 246 62 3065509969 231 30 13710979677795088 [(%d stripes (%d substripes) of %lx)
   btrfs                22783 207 32 3065510176 191 63 13710979677795088 [(%d stripes (%d substripes) of %lx)
   btrfs                27788  23 22 3065515181   7 53 13710979677795088 [(%d stripes (%d substripes) of %lx)
   btrfs                29418 239 28 3065516811 223 59 13710979677795088 [(%d stripes (%d substripes) of %lx)
   btrfs                29957 127 25 3065517350 111 56 13710979677795088 [(%d stripes (%d substripes) of %lx)
   btrfs                30328 180 43 3065517721 165 11 13710979677795088 [(%d stripes (%d substripes) of %lx)
   btrfs                30343 248 32 3065517736 232 63 13710979677795088 [(%d stripes (%d substripes) of %lx)
]


[ Continue ]
btrfs Backup superblock, 7020021 TB / 6384672 TiB

I'm going to try parted magic on a dvd using a netbook to look at it overnight but I'm not hopeful.

Any help appreciated.

---

### Post by oldfred on 2012-08-31
Welcome to the forums.

Why is testdisk showing HFS and btrfs or are those pure errors because it cannot read it?

Was this a gpt drive which then would be a different structure and read differently?

What does this show anything?

sudo parted /dev/sdb unit s print

I have used photorec but that is a long slow process as it just scans drive for anything that looks like a file type. No names, just extensions or type.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by cuthbert123 on 2012-08-31
Hi - it turned out ok, i chose a different option and it's creating an image .dd file to my desktop computer. Once I have the files i'll be damn sure to keep them on the desktop until i'm sure the external usb is ok.

---

