---
title: "Cant mount hdd to save data"
date: 2010-09-09
forum: General Help
---

### Post by slafer_00 on 2010-09-09
Hi everyone!
  My system ubuntu 10.04 crashed. Now I boot from liveCD and I can’t mount HDD.
  fdisk –l  give partitions, but mount does not work. Crashed system should be on sda1 and it is ext4.
   
  [FONT=&quot]ubuntu@ubuntu:~$ sudo fdisk -l[/FONT]
  
  [FONT=&quot]Disk /dev/sda: 1000.2 GB, 1000204886016 bytes[/FONT]
  [FONT=&quot]255 heads, 63 sectors/track, 121601 cylinders[/FONT]
  [FONT=&quot]Units = cylinders of 16065 * 512 = 8225280 bytes[/FONT]
  [FONT=&quot]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
  [FONT=&quot]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
  [FONT=&quot]Disk identifier: 0x0005dae8[/FONT]
  
  [FONT=&quot]   Device Boot      Start         End      Blocks   Id  System[/FONT]
  [FONT=&quot]/dev/sda1   *           1      120969   971683461   83  Linux[/FONT]
  [FONT=&quot]/dev/sda2          120970      121601     5076540    5  Extended[/FONT]
  [FONT=&quot]/dev/sda5          120970      121601     5076508+  82  Linux swap / Solaris[/FONT]
  
  [FONT=&quot]Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes[/FONT]
  [FONT=&quot]255 heads, 63 sectors/track, 121601 cylinders[/FONT]
  [FONT=&quot]Units = cylinders of 16065 * 512 = 8225280 bytes[/FONT]
  [FONT=&quot]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
  [FONT=&quot]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
  [FONT=&quot]Disk identifier: 0x651cb50c[/FONT]
  
  [FONT=&quot]   Device Boot      Start         End      Blocks   Id  System[/FONT]
  [FONT=&quot]/dev/sdb1   *           1      121602   976759808    7  HPFS/NTFS[/FONT]
  
  [FONT=&quot]Disk /dev/sdc: 2044 MB, 2044723200 bytes[/FONT]
  [FONT=&quot]2 heads, 63 sectors/track, 31695 cylinders[/FONT]
  [FONT=&quot]Units = cylinders of 126 * 512 = 64512 bytes[/FONT]
  [FONT=&quot]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
  [FONT=&quot]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
  [FONT=&quot]Disk identifier: 0x00019628[/FONT]
  
  [FONT=&quot]   Device Boot      Start         End      Blocks   Id  System[/FONT]
  [FONT=&quot]/dev/sdc1   *           1       31696     1996784    6  FAT16[/FONT]
  
  [FONT=&quot]Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes[/FONT]
  [FONT=&quot]255 heads, 63 sectors/track, 121601 cylinders[/FONT]
  [FONT=&quot]Units = cylinders of 16065 * 512 = 8225280 bytes[/FONT]
  [FONT=&quot]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
  [FONT=&quot]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
  [FONT=&quot]Disk identifier: 0xad5df7a1[/FONT]
  
  [FONT=&quot]   Device Boot      Start         End      Blocks   Id  System[/FONT]
  [FONT=&quot]/dev/sdd1               1      121601   976760001    7  HPFS/NTFS[/FONT]
  [FONT=&quot]ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda1 /mnt[/FONT]
  [FONT=&quot]mount: special device /dev/sda1 does not exist[/FONT]
  [FONT=&quot]ubuntu@ubuntu:~$ [/FONT]
  I would like to save data to other disk. Please help me how to do it. Thanks.

---

### Post by JohnHeikkila on 2010-09-09
If you open Nautilus/folder management, on the left sidebar, there should be a shortcut to your HDD?

---

### Post by slafer_00 on 2010-09-09
In Nautilus there is no shortcut to HDD. It is not mounted, fsck doesnt work, rescue mode from alternate  cd didnt work. Is it maby problem with grub?

---

### Post by garvinrick4 on 2010-09-09
Before you start mounting give one of these in a terminal just for hell of it.
```
sudo e2fsck /dev/sda1
```
 
Open gparted in live cd and right click on sda1 and go to label and give it a label. Lets say you name it lucid and then click green arrow to apply. close gparted.
Open a terminal: Copy and paste these.
```
sudo mkdir /media/lucid
```
```
sudo mount /dev/sda1 /media/lucid
```
Now you should be mounted. If you want try to fix since you believe it is dead anyway.
Make sure your internet connection is on in live CD. And copy and paste these.
```
sudo cp /etc/resolv.conf /media/lucid/etc/resolv.conf
```
```
sudo chroot /media/lucid
```
```
apt-get -f install
```
```
apt-get update
```
```
apt-get upgrade
```
```
apt-get -f install
```
Hit Ctrl and D same time
```
exit
```

---

### Post by slafer_00 on 2010-09-09
e2fsck give this:

ubuntu@ubuntu:/$ sudo e2fsck /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: No such file or directory while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

Other commands are of no use, because I cant mount partition.
There is no  sda1 in /dev/.. Is there any way to make it?

---

