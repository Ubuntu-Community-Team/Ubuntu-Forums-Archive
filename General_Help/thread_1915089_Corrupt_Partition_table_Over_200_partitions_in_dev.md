---
title: "Corrupt Partition table? Over 200 partitions in /dev/sda"
date: 2012-01-25
forum: General Help
---

### Post by apoorvumang on 2012-01-25
I was trying to install fedora on a separate partition on my hard disk(already having natty + win7) and something went wrong (I think I formatted a swap partition) and the computer hung.
Upon forced reboot, I got the grub rescue prompt.
I was unable to boot ubuntu oneiric or fedora 15 from a usb drive or cd - it said something like
```

Kernel panic - not syncing. Out of memory

```
Upon booting from an old 10.04 LTS Alternate cd, I checked the partitions, and it said I had over 200 partitions, ie from /dev/sda1 to /dev/sda250 or something!
I was finally able to boot ubuntu using a Super Grub2 disk and install grub using --force in grub install(otherwise it wouldn't install). However, windows does not boot, and if I try to run gparted on ubuntu, it scans for a long time and finally reports that my hard disk is 100% unallocated.

Is this because the partition table is corrupt? Is there any way to fix this?
Any help is appreciated.

---

### Post by apoorvumang on 2012-01-25
If it helps, here is the output of sudo fdisk -lu
```


Warning: omitting partitions after #60.
They will be deleted if you save this partition table.

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00030f9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   740250222   370124087+  83  Linux
/dev/sda2       740251646  1027342335   143545345    5  Extended
/dev/sda3      1027342336  1027547135      102400    7  HPFS/NTFS
/dev/sda4      1027547136  1234190335   103321600    7  HPFS/NTFS
/dev/sda5      1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda6       986329088  1015611391    14641152   83  Linux
/dev/sda7      1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda8       986329088  1015611391    14641152   83  Linux
/dev/sda9      1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda10      986329088  1015611391    14641152   83  Linux
/dev/sda11     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda12      986329088  1015611391    14641152   83  Linux
/dev/sda13     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda14      986329088  1015611391    14641152   83  Linux
/dev/sda15     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda16      986329088  1015611391    14641152   83  Linux
/dev/sda17     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda18      986329088  1015611391    14641152   83  Linux
/dev/sda19     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda20      986329088  1015611391    14641152   83  Linux
/dev/sda21     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda22      986329088  1015611391    14641152   83  Linux
/dev/sda23     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda24      986329088  1015611391    14641152   83  Linux
/dev/sda25     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda26      986329088  1015611391    14641152   83  Linux
/dev/sda27     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda28      986329088  1015611391    14641152   83  Linux
/dev/sda29     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda30      986329088  1015611391    14641152   83  Linux
/dev/sda31     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda32      986329088  1015611391    14641152   83  Linux
/dev/sda33     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda34      986329088  1015611391    14641152   83  Linux
/dev/sda35     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda36      986329088  1015611391    14641152   83  Linux
/dev/sda37     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda38      986329088  1015611391    14641152   83  Linux
/dev/sda39     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda40      986329088  1015611391    14641152   83  Linux
/dev/sda41     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda42      986329088  1015611391    14641152   83  Linux
/dev/sda43     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda44      986329088  1015611391    14641152   83  Linux
/dev/sda45     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda46      986329088  1015611391    14641152   83  Linux
/dev/sda47     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda48      986329088  1015611391    14641152   83  Linux
/dev/sda49     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda50      986329088  1015611391    14641152   83  Linux
/dev/sda51     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda52      986329088  1015611391    14641152   83  Linux
/dev/sda53     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda54      986329088  1015611391    14641152   83  Linux
/dev/sda55     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda56      986329088  1015611391    14641152   83  Linux
/dev/sda57     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda58      986329088  1015611391    14641152   83  Linux
/dev/sda59     1015625728  1027342335     5858304   82  Linux swap / Solaris
/dev/sda60      986329088  1015611391    14641152   83  Linux

Partition table entries are not in disk order

```

---

### Post by oldfred on 2012-01-25
Logical partitions are a linked list. You have something in one link that refers back to another partition in a loop.

I would try to backup partition table with this, not sure if it will follow link error or not.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

Extended partition linking to another extended partition
Your partition table is slightly messed up. But it should be easy to fix. Boot into Ubuntu with Supergrub if you cannot boot and are not in system.
this occasionally fixes issues and is worth trying:
you do the following :
fdisk /dev/sda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit
else if it is not ok
then post the output of option p and v


If you cannot reboot normally:
Reboot (using Supergrub) so that the changes take effect.

Above reorder may change device numbers and cause other issues if mounting with device like /dev/sda1 in fstab or using device in grub. If using UUIDs it should not matter.

---

### Post by apoorvumang on 2012-01-26
Really sorry for the late reply!
I did fdisk /dev/sda till p and v. Here are the outputs:
p:
```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00030f9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       46079   370124087+  83  Linux
/dev/sda2           46079       63950   143545345    5  Extended
/dev/sda3           63950       63962      102400    7  HPFS/NTFS
/dev/sda4           63962       76825   103321600    7  HPFS/NTFS
/dev/sda5           61397       63219    14641152   83  Linux
/dev/sda6           61397       63219    14641152   83  Linux
/dev/sda7           61397       63219    14641152   83  Linux
/dev/sda8           61397       63219    14641152   83  Linux
/dev/sda9           61397       63219    14641152   83  Linux
/dev/sda10          61397       63219    14641152   83  Linux
/dev/sda11          61397       63219    14641152   83  Linux
/dev/sda12          61397       63219    14641152   83  Linux
/dev/sda13          61397       63219    14641152   83  Linux
/dev/sda14          61397       63219    14641152   83  Linux
/dev/sda15          61397       63219    14641152   83  Linux
/dev/sda16          61397       63219    14641152   83  Linux
/dev/sda17          61397       63219    14641152   83  Linux
/dev/sda18          61397       63219    14641152   83  Linux
/dev/sda19          61397       63219    14641152   83  Linux
/dev/sda20          61397       63219    14641152   83  Linux
/dev/sda21          61397       63219    14641152   83  Linux
/dev/sda22          61397       63219    14641152   83  Linux
/dev/sda23          61397       63219    14641152   83  Linux
/dev/sda24          61397       63219    14641152   83  Linux
/dev/sda25          61397       63219    14641152   83  Linux
/dev/sda26          61397       63219    14641152   83  Linux
/dev/sda27          61397       63219    14641152   83  Linux
/dev/sda28          61397       63219    14641152   83  Linux
/dev/sda29          61397       63219    14641152   83  Linux
/dev/sda30          61397       63219    14641152   83  Linux
/dev/sda31          61397       63219    14641152   83  Linux
/dev/sda32          61397       63219    14641152   83  Linux
/dev/sda33          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda34          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda35          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda36          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda37          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda38          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda39          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda40          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda41          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda42          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda43          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda44          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda45          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda46          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda47          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda48          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda49          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda50          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda51          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda52          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda53          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda54          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda55          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda56          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda57          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda58          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda59          63220       63950     5858304   82  Linux swap / Solaris
/dev/sda60          63220       63950     5858304   82  Linux swap / Solaris

```
v:
```


Warning: partition 5 overlaps partition 6.
Warning: partition 5 overlaps partition 7.
Warning: partition 6 overlaps partition 7.
Warning: partition 5 overlaps partition 8.
Warning: partition 6 overlaps partition 8.
Warning: partition 7 overlaps partition 8.
Warning: partition 5 overlaps partition 9.
Warning: partition 6 overlaps partition 9.
Warning: partition 7 overlaps partition 9.
Warning: partition 8 overlaps partition 9.
Warning: partition 5 overlaps partition 10.
Warning: partition 6 overlaps partition 10.
Warning: partition 7 overlaps partition 10.
Warning: partition 8 overlaps partition 10.
Warning: partition 9 overlaps partition 10.
Warning: partition 5 overlaps partition 11.
Warning: partition 6 overlaps partition 11.
Warning: partition 7 overlaps partition 11.
Warning: partition 8 overlaps partition 11.
Warning: partition 9 overlaps partition 11.
Warning: partition 10 overlaps partition 11.
Warning: partition 5 overlaps partition 12.
Warning: partition 6 overlaps partition 12.
Warning: partition 7 overlaps partition 12.
Warning: partition 8 overlaps partition 12.
Warning: partition 9 overlaps partition 12.
Warning: partition 10 overlaps partition 12.
Warning: partition 11 overlaps partition 12.
Warning: partition 5 overlaps partition 13.
Warning: partition 6 overlaps partition 13.
Warning: partition 7 overlaps partition 13.
Warning: partition 8 overlaps partition 13.
Warning: partition 9 overlaps partition 13.
Warning: partition 10 overlaps partition 13.
Warning: partition 11 overlaps partition 13.
Warning: partition 12 overlaps partition 13.
Warning: partition 5 overlaps partition 14.
Warning: partition 6 overlaps partition 14.
Warning: partition 7 overlaps partition 14.
Warning: partition 8 overlaps partition 14.
Warning: partition 9 overlaps partition 14.
Warning: partition 10 overlaps partition 14.
Warning: partition 11 overlaps partition 14.
Warning: partition 12 overlaps partition 14.
Warning: partition 13 overlaps partition 14.
Warning: partition 5 overlaps partition 15.
Warning: partition 6 overlaps partition 15.
Warning: partition 7 overlaps partition 15.
Warning: partition 8 overlaps partition 15.
Warning: partition 9 overlaps partition 15.
Warning: partition 10 overlaps partition 15.
Warning: partition 11 overlaps partition 15.
Warning: partition 12 overlaps partition 15.
Warning: partition 13 overlaps partition 15.
Warning: partition 14 overlaps partition 15.
Warning: partition 5 overlaps partition 16.
Warning: partition 6 overlaps partition 16.
Warning: partition 7 overlaps partition 16.
Warning: partition 8 overlaps partition 16.
Warning: partition 9 overlaps partition 16.
Warning: partition 10 overlaps partition 16.
Warning: partition 11 overlaps partition 16.
Warning: partition 12 overlaps partition 16.
Warning: partition 13 overlaps partition 16.
Warning: partition 14 overlaps partition 16.
Warning: partition 15 overlaps partition 16.
Warning: partition 5 overlaps partition 17.
Warning: partition 6 overlaps partition 17.
Warning: partition 7 overlaps partition 17.
Warning: partition 8 overlaps partition 17.
Warning: partition 9 overlaps partition 17.
Warning: partition 10 overlaps partition 17.
Warning: partition 11 overlaps partition 17.
Warning: partition 12 overlaps partition 17.
Warning: partition 13 overlaps partition 17.
Warning: partition 14 overlaps partition 17.
Warning: partition 15 overlaps partition 17.
Warning: partition 16 overlaps partition 17.
Warning: partition 5 overlaps partition 18.
Warning: partition 6 overlaps partition 18.
Warning: partition 7 overlaps partition 18.
Warning: partition 8 overlaps partition 18.
Warning: partition 9 overlaps partition 18.
Warning: partition 10 overlaps partition 18.
Warning: partition 11 overlaps partition 18.
Warning: partition 12 overlaps partition 18.
Warning: partition 13 overlaps partition 18.
Warning: partition 14 overlaps partition 18.
Warning: partition 15 overlaps partition 18.
Warning: partition 16 overlaps partition 18.
Warning: partition 17 overlaps partition 18.
Warning: partition 5 overlaps partition 19.
Warning: partition 6 overlaps partition 19.
Warning: partition 7 overlaps partition 19.
Warning: partition 8 overlaps partition 19.
Warning: partition 9 overlaps partition 19.
Warning: partition 10 overlaps partition 19.
Warning: partition 11 overlaps partition 19.
Warning: partition 12 overlaps partition 19.
Warning: partition 13 overlaps partition 19.
Warning: partition 14 overlaps partition 19.
Warning: partition 15 overlaps partition 19.
Warning: partition 16 overlaps partition 19.
Warning: partition 17 overlaps partition 19.
Warning: partition 18 overlaps partition 19.
Warning: partition 5 overlaps partition 20.
Warning: partition 6 overlaps partition 20.
Warning: partition 7 overlaps partition 20.
Warning: partition 8 overlaps partition 20.
Warning: partition 9 overlaps partition 20.
Warning: partition 10 overlaps partition 20.
Warning: partition 11 overlaps partition 20.
Warning: partition 12 overlaps partition 20.
Warning: partition 13 overlaps partition 20.
Warning: partition 14 overlaps partition 20.
Warning: partition 15 overlaps partition 20.
Warning: partition 16 overlaps partition 20.
Warning: partition 17 overlaps partition 20.
Warning: partition 18 overlaps partition 20.
Warning: partition 19 overlaps partition 20.
Warning: partition 5 overlaps partition 21.
Warning: partition 6 overlaps partition 21.
Warning: partition 7 overlaps partition 21.
Warning: partition 8 overlaps partition 21.
Warning: partition 9 overlaps partition 21.
Warning: partition 10 overlaps partition 21.
Warning: partition 11 overlaps partition 21.
Warning: partition 12 overlaps partition 21.
Warning: partition 13 overlaps partition 21.
Warning: partition 14 overlaps partition 21.
Warning: partition 15 overlaps partition 21.
Warning: partition 16 overlaps partition 21.
Warning: partition 17 overlaps partition 21.
Warning: partition 18 overlaps partition 21.
Warning: partition 19 overlaps partition 21.
Warning: partition 20 overlaps partition 21.
Warning: partition 5 overlaps partition 22.
Warning: partition 6 overlaps partition 22.
Warning: partition 7 overlaps partition 22.
Warning: partition 8 overlaps partition 22.
Warning: partition 9 overlaps partition 22.
Warning: partition 10 overlaps partition 22.
Warning: partition 11 overlaps partition 22.
Warning: partition 12 overlaps partition 22.
Warning: partition 13 overlaps partition 22.
Warning: partition 14 overlaps partition 22.
Warning: partition 15 overlaps partition 22.
Warning: partition 16 overlaps partition 22.
Warning: partition 17 overlaps partition 22.
Warning: partition 18 overlaps partition 22.
Warning: partition 19 overlaps partition 22.
Warning: partition 20 overlaps partition 22.
Warning: partition 21 overlaps partition 22.
Warning: partition 5 overlaps partition 23.
Warning: partition 6 overlaps partition 23.
Warning: partition 7 overlaps partition 23.
Warning: partition 8 overlaps partition 23.
Warning: partition 9 overlaps partition 23.
Warning: partition 10 overlaps partition 23.
Warning: partition 11 overlaps partition 23.
Warning: partition 12 overlaps partition 23.
Warning: partition 13 overlaps partition 23.
Warning: partition 14 overlaps partition 23.
Warning: partition 15 overlaps partition 23.
Warning: partition 16 overlaps partition 23.
Warning: partition 17 overlaps partition 23.
Warning: partition 18 overlaps partition 23.
Warning: partition 19 overlaps partition 23.
Warning: partition 20 overlaps partition 23.
Warning: partition 21 overlaps partition 23.
Warning: partition 22 overlaps partition 23.
Warning: partition 5 overlaps partition 24.
Warning: partition 6 overlaps partition 24.
Warning: partition 7 overlaps partition 24.
Warning: partition 8 overlaps partition 24.
Warning: partition 9 overlaps partition 24.
Warning: partition 10 overlaps partition 24.
Warning: partition 11 overlaps partition 24.
Warning: partition 12 overlaps partition 24.
Warning: partition 13 overlaps partition 24.
Warning: partition 14 overlaps partition 24.
Warning: partition 15 overlaps partition 24.
Warning: partition 16 overlaps partition 24.
Warning: partition 17 overlaps partition 24.
Warning: partition 18 overlaps partition 24.
Warning: partition 19 overlaps partition 24.
Warning: partition 20 overlaps partition 24.
Warning: partition 21 overlaps partition 24.
Warning: partition 22 overlaps partition 24.
Warning: partition 23 overlaps partition 24.
Warning: partition 5 overlaps partition 25.
Warning: partition 6 overlaps partition 25.
Warning: partition 7 overlaps partition 25.
Warning: partition 8 overlaps partition 25.
Warning: partition 9 overlaps partition 25.
Warning: partition 10 overlaps partition 25.
Warning: partition 11 overlaps partition 25.
Warning: partition 12 overlaps partition 25.
Warning: partition 13 overlaps partition 25.
Warning: partition 14 overlaps partition 25.
Warning: partition 15 overlaps partition 25.
Warning: partition 16 overlaps partition 25.
Warning: partition 17 overlaps partition 25.
Warning: partition 18 overlaps partition 25.
Warning: partition 19 overlaps partition 25.
Warning: partition 20 overlaps partition 25.
Warning: partition 21 overlaps partition 25.
Warning: partition 22 overlaps partition 25.
Warning: partition 23 overlaps partition 25.
Warning: partition 24 overlaps partition 25.
Warning: partition 5 overlaps partition 26.
Warning: partition 6 overlaps partition 26.
Warning: partition 7 overlaps partition 26.
Warning: partition 8 overlaps partition 26.
Warning: partition 9 overlaps partition 26.
Warning: partition 10 overlaps partition 26.
Warning: partition 11 overlaps partition 26.
Warning: partition 12 overlaps partition 26.
Warning: partition 13 overlaps partition 26.
Warning: partition 14 overlaps partition 26.
Warning: partition 15 overlaps partition 26.
Warning: partition 16 overlaps partition 26.
Warning: partition 17 overlaps partition 26.
Warning: partition 18 overlaps partition 26.
Warning: partition 19 overlaps partition 26.
Warning: partition 20 overlaps partition 26.
Warning: partition 21 overlaps partition 26.
Warning: partition 22 overlaps partition 26.
Warning: partition 23 overlaps partition 26.
Warning: partition 24 overlaps partition 26.
Warning: partition 25 overlaps partition 26.
Warning: partition 5 overlaps partition 27.
Warning: partition 6 overlaps partition 27.
Warning: partition 7 overlaps partition 27.
Warning: partition 8 overlaps partition 27.
Warning: partition 9 overlaps partition 27.
Warning: partition 10 overlaps partition 27.
Warning: partition 11 overlaps partition 27.
Warning: partition 12 overlaps partition 27.
Warning: partition 13 overlaps partition 27.
Warning: partition 14 overlaps partition 27.
Warning: partition 15 overlaps partition 27.
Warning: partition 16 overlaps partition 27.
Warning: partition 17 overlaps partition 27.
Warning: partition 18 overlaps partition 27.
Warning: partition 19 overlaps partition 27.
Warning: partition 20 overlaps partition 27.
Warning: partition 21 overlaps partition 27.
Warning: partition 22 overlaps partition 27.
Warning: partition 23 overlaps partition 27.
Warning: partition 24 overlaps partition 27.
Warning: partition 25 overlaps partition 27.
Warning: partition 26 overlaps partition 27.
Warning: partition 5 overlaps partition 28.
Warning: partition 6 overlaps partition 28.
Warning: partition 7 overlaps partition 28.
Warning: partition 8 overlaps partition 28.
Warning: partition 9 overlaps partition 28.
Warning: partition 10 overlaps partition 28.
Warning: partition 11 overlaps partition 28.
Warning: partition 12 overlaps partition 28.
Warning: partition 13 overlaps partition 28.
Warning: partition 14 overlaps partition 28.
Warning: partition 15 overlaps partition 28.
Warning: partition 16 overlaps partition 28.
Warning: partition 17 overlaps partition 28.
Warning: partition 18 overlaps partition 28.
Warning: partition 19 overlaps partition 28.
Warning: partition 20 overlaps partition 28.
Warning: partition 21 overlaps partition 28.
Warning: partition 22 overlaps partition 28.
Warning: partition 23 overlaps partition 28.
Warning: partition 24 overlaps partition 28.
Warning: partition 25 overlaps partition 28.
Warning: partition 26 overlaps partition 28.
Warning: partition 27 overlaps partition 28.
Warning: partition 5 overlaps partition 29.
Warning: partition 6 overlaps partition 29.
Warning: partition 7 overlaps partition 29.
Warning: partition 8 overlaps partition 29.
Warning: partition 9 overlaps partition 29.
Warning: partition 10 overlaps partition 29.
Warning: partition 11 overlaps partition 29.
Warning: partition 12 overlaps partition 29.
Warning: partition 13 overlaps partition 29.
Warning: partition 14 overlaps partition 29.
Warning: partition 15 overlaps partition 29.
Warning: partition 16 overlaps partition 29.
Warning: partition 17 overlaps partition 29.
Warning: partition 18 overlaps partition 29.
Warning: partition 19 overlaps partition 29.
Warning: partition 20 overlaps partition 29.
Warning: partition 21 overlaps partition 29.
Warning: partition 22 overlaps partition 29.
Warning: partition 23 overlaps partition 29.
Warning: partition 24 overlaps partition 29.
Warning: partition 25 overlaps partition 29.
Warning: partition 26 overlaps partition 29.
Warning: partition 27 overlaps partition 29.
Warning: partition 28 overlaps partition 29.
Warning: partition 5 overlaps partition 30.
Warning: partition 6 overlaps partition 30.
Warning: partition 7 overlaps partition 30.
Warning: partition 8 overlaps partition 30.
Warning: partition 9 overlaps partition 30.
Warning: partition 10 overlaps partition 30.
Warning: partition 11 overlaps partition 30.
Warning: partition 12 overlaps partition 30.
Warning: partition 13 overlaps partition 30.
Warning: partition 14 overlaps partition 30.
Warning: partition 15 overlaps partition 30.
Warning: partition 16 overlaps partition 30.
Warning: partition 17 overlaps partition 30.
Warning: partition 18 overlaps partition 30.
Warning: partition 19 overlaps partition 30.
Warning: partition 20 overlaps partition 30.
Warning: partition 21 overlaps partition 30.
Warning: partition 22 overlaps partition 30.
Warning: partition 23 overlaps partition 30.
Warning: partition 24 overlaps partition 30.
Warning: partition 25 overlaps partition 30.
Warning: partition 26 overlaps partition 30.
Warning: partition 27 overlaps partition 30.
Warning: partition 28 overlaps partition 30.
Warning: partition 29 overlaps partition 30.
Warning: partition 5 overlaps partition 31.
Warning: partition 6 overlaps partition 31.
Warning: partition 7 overlaps partition 31.
Warning: partition 8 overlaps partition 31.
Warning: partition 9 overlaps partition 31.
Warning: partition 10 overlaps partition 31.
Warning: partition 11 overlaps partition 31.
Warning: partition 12 overlaps partition 31.
Warning: partition 13 overlaps partition 31.
Warning: partition 14 overlaps partition 31.
Warning: partition 15 overlaps partition 31.
Warning: partition 16 overlaps partition 31.
Warning: partition 17 overlaps partition 31.
Warning: partition 18 overlaps partition 31.
Warning: partition 19 overlaps partition 31.
Warning: partition 20 overlaps partition 31.
Warning: partition 21 overlaps partition 31.
Warning: partition 22 overlaps partition 31.
Warning: partition 23 overlaps partition 31.
Warning: partition 24 overlaps partition 31.
Warning: partition 25 overlaps partition 31.
Warning: partition 26 overlaps partition 31.
Warning: partition 27 overlaps partition 31.
Warning: partition 28 overlaps partition 31.
Warning: partition 29 overlaps partition 31.
Warning: partition 30 overlaps partition 31.
Warning: partition 5 overlaps partition 32.
Warning: partition 6 overlaps partition 32.
Warning: partition 7 overlaps partition 32.
Warning: partition 8 overlaps partition 32.
Warning: partition 9 overlaps partition 32.
Warning: partition 10 overlaps partition 32.
Warning: partition 11 overlaps partition 32.
Warning: partition 12 overlaps partition 32.
Warning: partition 13 overlaps partition 32.
Warning: partition 14 overlaps partition 32.
Warning: partition 15 overlaps partition 32.
Warning: partition 16 overlaps partition 32.
Warning: partition 17 overlaps partition 32.
Warning: partition 18 overlaps partition 32.
Warning: partition 19 overlaps partition 32.
Warning: partition 20 overlaps partition 32.
Warning: partition 21 overlaps partition 32.
Warning: partition 22 overlaps partition 32.
Warning: partition 23 overlaps partition 32.
Warning: partition 24 overlaps partition 32.
Warning: partition 25 overlaps partition 32.
Warning: partition 26 overlaps partition 32.
Warning: partition 27 overlaps partition 32.
Warning: partition 28 overlaps partition 32.
Warning: partition 29 overlaps partition 32.
Warning: partition 30 overlaps partition 32.
Warning: partition 31 overlaps partition 32.
Warning: partition 33 overlaps partition 34.
Warning: partition 33 overlaps partition 35.
Warning: partition 34 overlaps partition 35.
Warning: partition 33 overlaps partition 36.
Warning: partition 34 overlaps partition 36.
Warning: partition 35 overlaps partition 36.
Warning: partition 33 overlaps partition 37.
Warning: partition 34 overlaps partition 37.
Warning: partition 35 overlaps partition 37.
Warning: partition 36 overlaps partition 37.
Warning: partition 33 overlaps partition 38.
Warning: partition 34 overlaps partition 38.
Warning: partition 35 overlaps partition 38.
Warning: partition 36 overlaps partition 38.
Warning: partition 37 overlaps partition 38.
Warning: partition 33 overlaps partition 39.
Warning: partition 34 overlaps partition 39.
Warning: partition 35 overlaps partition 39.
Warning: partition 36 overlaps partition 39.
Warning: partition 37 overlaps partition 39.
Warning: partition 38 overlaps partition 39.
Warning: partition 33 overlaps partition 40.
Warning: partition 34 overlaps partition 40.
Warning: partition 35 overlaps partition 40.
Warning: partition 36 overlaps partition 40.
Warning: partition 37 overlaps partition 40.
Warning: partition 38 overlaps partition 40.
Warning: partition 39 overlaps partition 40.
Warning: partition 33 overlaps partition 41.
Warning: partition 34 overlaps partition 41.
Warning: partition 35 overlaps partition 41.
Warning: partition 36 overlaps partition 41.
Warning: partition 37 overlaps partition 41.
Warning: partition 38 overlaps partition 41.
Warning: partition 39 overlaps partition 41.
Warning: partition 40 overlaps partition 41.
Warning: partition 33 overlaps partition 42.
Warning: partition 34 overlaps partition 42.
Warning: partition 35 overlaps partition 42.
Warning: partition 36 overlaps partition 42.
Warning: partition 37 overlaps partition 42.
Warning: partition 38 overlaps partition 42.
Warning: partition 39 overlaps partition 42.
Warning: partition 40 overlaps partition 42.
Warning: partition 41 overlaps partition 42.
Warning: partition 33 overlaps partition 43.
Warning: partition 34 overlaps partition 43.
Warning: partition 35 overlaps partition 43.
Warning: partition 36 overlaps partition 43.
Warning: partition 37 overlaps partition 43.
Warning: partition 38 overlaps partition 43.
Warning: partition 39 overlaps partition 43.
Warning: partition 40 overlaps partition 43.
Warning: partition 41 overlaps partition 43.
Warning: partition 42 overlaps partition 43.
Warning: partition 33 overlaps partition 44.
Warning: partition 34 overlaps partition 44.
Warning: partition 35 overlaps partition 44.
Warning: partition 36 overlaps partition 44.
Warning: partition 37 overlaps partition 44.
Warning: partition 38 overlaps partition 44.
Warning: partition 39 overlaps partition 44.
Warning: partition 40 overlaps partition 44.
Warning: partition 41 overlaps partition 44.
Warning: partition 42 overlaps partition 44.
Warning: partition 43 overlaps partition 44.
Warning: partition 33 overlaps partition 45.
Warning: partition 34 overlaps partition 45.
Warning: partition 35 overlaps partition 45.
Warning: partition 36 overlaps partition 45.
Warning: partition 37 overlaps partition 45.
Warning: partition 38 overlaps partition 45.
Warning: partition 39 overlaps partition 45.
Warning: partition 40 overlaps partition 45.
Warning: partition 41 overlaps partition 45.
Warning: partition 42 overlaps partition 45.
Warning: partition 43 overlaps partition 45.
Warning: partition 44 overlaps partition 45.
Warning: partition 33 overlaps partition 46.
Warning: partition 34 overlaps partition 46.
Warning: partition 35 overlaps partition 46.
Warning: partition 36 overlaps partition 46.
Warning: partition 37 overlaps partition 46.
Warning: partition 38 overlaps partition 46.
Warning: partition 39 overlaps partition 46.
Warning: partition 40 overlaps partition 46.
Warning: partition 41 overlaps partition 46.
Warning: partition 42 overlaps partition 46.
Warning: partition 43 overlaps partition 46.
Warning: partition 44 overlaps partition 46.
Warning: partition 45 overlaps partition 46.
Warning: partition 33 overlaps partition 47.
Warning: partition 34 overlaps partition 47.
Warning: partition 35 overlaps partition 47.
Warning: partition 36 overlaps partition 47.
Warning: partition 37 overlaps partition 47.
Warning: partition 38 overlaps partition 47.
Warning: partition 39 overlaps partition 47.
Warning: partition 40 overlaps partition 47.
Warning: partition 41 overlaps partition 47.
Warning: partition 42 overlaps partition 47.
Warning: partition 43 overlaps partition 47.
Warning: partition 44 overlaps partition 47.
Warning: partition 45 overlaps partition 47.
Warning: partition 46 overlaps partition 47.
Warning: partition 33 overlaps partition 48.
Warning: partition 34 overlaps partition 48.
Warning: partition 35 overlaps partition 48.
Warning: partition 36 overlaps partition 48.
Warning: partition 37 overlaps partition 48.
Warning: partition 38 overlaps partition 48.
Warning: partition 39 overlaps partition 48.
Warning: partition 40 overlaps partition 48.
Warning: partition 41 overlaps partition 48.
Warning: partition 42 overlaps partition 48.
Warning: partition 43 overlaps partition 48.
Warning: partition 44 overlaps partition 48.
Warning: partition 45 overlaps partition 48.
Warning: partition 46 overlaps partition 48.
Warning: partition 47 overlaps partition 48.
Warning: partition 33 overlaps partition 49.
Warning: partition 34 overlaps partition 49.
Warning: partition 35 overlaps partition 49.
Warning: partition 36 overlaps partition 49.
Warning: partition 37 overlaps partition 49.
Warning: partition 38 overlaps partition 49.
Warning: partition 39 overlaps partition 49.
Warning: partition 40 overlaps partition 49.
Warning: partition 41 overlaps partition 49.
Warning: partition 42 overlaps partition 49.
Warning: partition 43 overlaps partition 49.
Warning: partition 44 overlaps partition 49.
Warning: partition 45 overlaps partition 49.
Warning: partition 46 overlaps partition 49.
Warning: partition 47 overlaps partition 49.
Warning: partition 48 overlaps partition 49.
Warning: partition 33 overlaps partition 50.
Warning: partition 34 overlaps partition 50.
Warning: partition 35 overlaps partition 50.
Warning: partition 36 overlaps partition 50.
Warning: partition 37 overlaps partition 50.
Warning: partition 38 overlaps partition 50.
Warning: partition 39 overlaps partition 50.
Warning: partition 40 overlaps partition 50.
Warning: partition 41 overlaps partition 50.
Warning: partition 42 overlaps partition 50.
Warning: partition 43 overlaps partition 50.
Warning: partition 44 overlaps partition 50.
Warning: partition 45 overlaps partition 50.
Warning: partition 46 overlaps partition 50.
Warning: partition 47 overlaps partition 50.
Warning: partition 48 overlaps partition 50.
Warning: partition 49 overlaps partition 50.
Warning: partition 33 overlaps partition 51.
Warning: partition 34 overlaps partition 51.
Warning: partition 35 overlaps partition 51.
Warning: partition 36 overlaps partition 51.
Warning: partition 37 overlaps partition 51.
Warning: partition 38 overlaps partition 51.
Warning: partition 39 overlaps partition 51.
Warning: partition 40 overlaps partition 51.
Warning: partition 41 overlaps partition 51.
Warning: partition 42 overlaps partition 51.
Warning: partition 43 overlaps partition 51.
Warning: partition 44 overlaps partition 51.
Warning: partition 45 overlaps partition 51.
Warning: partition 46 overlaps partition 51.
Warning: partition 47 overlaps partition 51.
Warning: partition 48 overlaps partition 51.
Warning: partition 49 overlaps partition 51.
Warning: partition 50 overlaps partition 51.
Warning: partition 33 overlaps partition 52.
Warning: partition 34 overlaps partition 52.
Warning: partition 35 overlaps partition 52.
Warning: partition 36 overlaps partition 52.
Warning: partition 37 overlaps partition 52.
Warning: partition 38 overlaps partition 52.
Warning: partition 39 overlaps partition 52.
Warning: partition 40 overlaps partition 52.
Warning: partition 41 overlaps partition 52.
Warning: partition 42 overlaps partition 52.
Warning: partition 43 overlaps partition 52.
Warning: partition 44 overlaps partition 52.
Warning: partition 45 overlaps partition 52.
Warning: partition 46 overlaps partition 52.
Warning: partition 47 overlaps partition 52.
Warning: partition 48 overlaps partition 52.
Warning: partition 49 overlaps partition 52.
Warning: partition 50 overlaps partition 52.
Warning: partition 51 overlaps partition 52.
Warning: partition 33 overlaps partition 53.
Warning: partition 34 overlaps partition 53.
Warning: partition 35 overlaps partition 53.
Warning: partition 36 overlaps partition 53.
Warning: partition 37 overlaps partition 53.
Warning: partition 38 overlaps partition 53.
Warning: partition 39 overlaps partition 53.
Warning: partition 40 overlaps partition 53.
Warning: partition 41 overlaps partition 53.
Warning: partition 42 overlaps partition 53.
Warning: partition 43 overlaps partition 53.
Warning: partition 44 overlaps partition 53.
Warning: partition 45 overlaps partition 53.
Warning: partition 46 overlaps partition 53.
Warning: partition 47 overlaps partition 53.
Warning: partition 48 overlaps partition 53.
Warning: partition 49 overlaps partition 53.
Warning: partition 50 overlaps partition 53.
Warning: partition 51 overlaps partition 53.
Warning: partition 52 overlaps partition 53.
Warning: partition 33 overlaps partition 54.
Warning: partition 34 overlaps partition 54.
Warning: partition 35 overlaps partition 54.
Warning: partition 36 overlaps partition 54.
Warning: partition 37 overlaps partition 54.
Warning: partition 38 overlaps partition 54.
Warning: partition 39 overlaps partition 54.
Warning: partition 40 overlaps partition 54.
Warning: partition 41 overlaps partition 54.
Warning: partition 42 overlaps partition 54.
Warning: partition 43 overlaps partition 54.
Warning: partition 44 overlaps partition 54.
Warning: partition 45 overlaps partition 54.
Warning: partition 46 overlaps partition 54.
Warning: partition 47 overlaps partition 54.
Warning: partition 48 overlaps partition 54.
Warning: partition 49 overlaps partition 54.
Warning: partition 50 overlaps partition 54.
Warning: partition 51 overlaps partition 54.
Warning: partition 52 overlaps partition 54.
Warning: partition 53 overlaps partition 54.
Warning: partition 33 overlaps partition 55.
Warning: partition 34 overlaps partition 55.
Warning: partition 35 overlaps partition 55.
Warning: partition 36 overlaps partition 55.
Warning: partition 37 overlaps partition 55.
Warning: partition 38 overlaps partition 55.
Warning: partition 39 overlaps partition 55.
Warning: partition 40 overlaps partition 55.
Warning: partition 41 overlaps partition 55.
Warning: partition 42 overlaps partition 55.
Warning: partition 43 overlaps partition 55.
Warning: partition 44 overlaps partition 55.
Warning: partition 45 overlaps partition 55.
Warning: partition 46 overlaps partition 55.
Warning: partition 47 overlaps partition 55.
Warning: partition 48 overlaps partition 55.
Warning: partition 49 overlaps partition 55.
Warning: partition 50 overlaps partition 55.
Warning: partition 51 overlaps partition 55.
Warning: partition 52 overlaps partition 55.
Warning: partition 53 overlaps partition 55.
Warning: partition 54 overlaps partition 55.
Warning: partition 33 overlaps partition 56.
Warning: partition 34 overlaps partition 56.
Warning: partition 35 overlaps partition 56.
Warning: partition 36 overlaps partition 56.
Warning: partition 37 overlaps partition 56.
Warning: partition 38 overlaps partition 56.
Warning: partition 39 overlaps partition 56.
Warning: partition 40 overlaps partition 56.
Warning: partition 41 overlaps partition 56.
Warning: partition 42 overlaps partition 56.
Warning: partition 43 overlaps partition 56.
Warning: partition 44 overlaps partition 56.
Warning: partition 45 overlaps partition 56.
Warning: partition 46 overlaps partition 56.
Warning: partition 47 overlaps partition 56.
Warning: partition 48 overlaps partition 56.
Warning: partition 49 overlaps partition 56.
Warning: partition 50 overlaps partition 56.
Warning: partition 51 overlaps partition 56.
Warning: partition 52 overlaps partition 56.
Warning: partition 53 overlaps partition 56.
Warning: partition 54 overlaps partition 56.
Warning: partition 55 overlaps partition 56.
Warning: partition 33 overlaps partition 57.
Warning: partition 34 overlaps partition 57.
Warning: partition 35 overlaps partition 57.
Warning: partition 36 overlaps partition 57.
Warning: partition 37 overlaps partition 57.
Warning: partition 38 overlaps partition 57.
Warning: partition 39 overlaps partition 57.
Warning: partition 40 overlaps partition 57.
Warning: partition 41 overlaps partition 57.
Warning: partition 42 overlaps partition 57.
Warning: partition 43 overlaps partition 57.
Warning: partition 44 overlaps partition 57.
Warning: partition 45 overlaps partition 57.
Warning: partition 46 overlaps partition 57.
Warning: partition 47 overlaps partition 57.
Warning: partition 48 overlaps partition 57.
Warning: partition 49 overlaps partition 57.
Warning: partition 50 overlaps partition 57.
Warning: partition 51 overlaps partition 57.
Warning: partition 52 overlaps partition 57.
Warning: partition 53 overlaps partition 57.
Warning: partition 54 overlaps partition 57.
Warning: partition 55 overlaps partition 57.
Warning: partition 56 overlaps partition 57.
Warning: partition 33 overlaps partition 58.
Warning: partition 34 overlaps partition 58.
Warning: partition 35 overlaps partition 58.
Warning: partition 36 overlaps partition 58.
Warning: partition 37 overlaps partition 58.
Warning: partition 38 overlaps partition 58.
Warning: partition 39 overlaps partition 58.
Warning: partition 40 overlaps partition 58.
Warning: partition 41 overlaps partition 58.
Warning: partition 42 overlaps partition 58.
Warning: partition 43 overlaps partition 58.
Warning: partition 44 overlaps partition 58.
Warning: partition 45 overlaps partition 58.
Warning: partition 46 overlaps partition 58.
Warning: partition 47 overlaps partition 58.
Warning: partition 48 overlaps partition 58.
Warning: partition 49 overlaps partition 58.
Warning: partition 50 overlaps partition 58.
Warning: partition 51 overlaps partition 58.
Warning: partition 52 overlaps partition 58.
Warning: partition 53 overlaps partition 58.
Warning: partition 54 overlaps partition 58.
Warning: partition 55 overlaps partition 58.
Warning: partition 56 overlaps partition 58.
Warning: partition 57 overlaps partition 58.
Warning: partition 33 overlaps partition 59.
Warning: partition 34 overlaps partition 59.
Warning: partition 35 overlaps partition 59.
Warning: partition 36 overlaps partition 59.
Warning: partition 37 overlaps partition 59.
Warning: partition 38 overlaps partition 59.
Warning: partition 39 overlaps partition 59.
Warning: partition 40 overlaps partition 59.
Warning: partition 41 overlaps partition 59.
Warning: partition 42 overlaps partition 59.
Warning: partition 43 overlaps partition 59.
Warning: partition 44 overlaps partition 59.
Warning: partition 45 overlaps partition 59.
Warning: partition 46 overlaps partition 59.
Warning: partition 47 overlaps partition 59.
Warning: partition 48 overlaps partition 59.
Warning: partition 49 overlaps partition 59.
Warning: partition 50 overlaps partition 59.
Warning: partition 51 overlaps partition 59.
Warning: partition 52 overlaps partition 59.
Warning: partition 53 overlaps partition 59.
Warning: partition 54 overlaps partition 59.
Warning: partition 55 overlaps partition 59.
Warning: partition 56 overlaps partition 59.
Warning: partition 57 overlaps partition 59.
Warning: partition 58 overlaps partition 59.
Warning: partition 33 overlaps partition 60.
Warning: partition 34 overlaps partition 60.
Warning: partition 35 overlaps partition 60.
Warning: partition 36 overlaps partition 60.
Warning: partition 37 overlaps partition 60.
Warning: partition 38 overlaps partition 60.
Warning: partition 39 overlaps partition 60.
Warning: partition 40 overlaps partition 60.
Warning: partition 41 overlaps partition 60.
Warning: partition 42 overlaps partition 60.
Warning: partition 43 overlaps partition 60.
Warning: partition 44 overlaps partition 60.
Warning: partition 45 overlaps partition 60.
Warning: partition 46 overlaps partition 60.
Warning: partition 47 overlaps partition 60.
Warning: partition 48 overlaps partition 60.
Warning: partition 49 overlaps partition 60.
Warning: partition 50 overlaps partition 60.
Warning: partition 51 overlaps partition 60.
Warning: partition 52 overlaps partition 60.
Warning: partition 53 overlaps partition 60.
Warning: partition 54 overlaps partition 60.
Warning: partition 55 overlaps partition 60.
Warning: partition 56 overlaps partition 60.
Warning: partition 57 overlaps partition 60.
Warning: partition 58 overlaps partition 60.
Warning: partition 59 overlaps partition 60.
Total allocated sectors 18446744060307029404 greater than the maximum 1250263728

```
I don't think this is quite right, but at least the number of partitions is 60 now?
Should I write this partition table or try something else?

---

### Post by apoorvumang on 2012-01-26
I would also like to tell that my linux partition, /dev/sda1, is the only one I want to save. So should I write this partition table (of 60 partitions) and delete the ones I don't want through gparted?

---

### Post by apoorvumang on 2012-01-26
UPDATE: I wrote that partition table and deleted all the partitions that I didn't require through gparted. Now my system is as good as before! Windows is booting and nautilus isn't slow anymore.
Thanks a lot oldfred!

---

