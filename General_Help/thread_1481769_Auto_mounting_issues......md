---
title: "Auto mounting issues....."
date: 2010-05-12
forum: General Help
---

### Post by toji on 2010-05-12
So i wanted to auto mount an ntfs partition and i edited fstab...

every thing works fine, except when i move something to the partition, the file is moved but it gives me an error saying 
"Could not change permissions for /media/disk/file.txt"

my /etc/fstab looks like this:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=db5c9ea1-106e-4d23-ad71-975b1eb3aba4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8e243d72-4b03-4152-a7c0-d47a6bb65ba5 none            swap    sw              0       0
[COLOR="DarkRed"]/dev/sda4	/media/disk	ntfs-3g	rw,auto,user,fmask=0111,dmask=0000	0	1[/COLOR]

fdisk -l gives:\
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x865a6b4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        3825    30617600    7  HPFS/NTFS
/dev/sda3            3825        8287    35838977    5  Extended
[COLOR="DarkRed"]/dev/sda4            8287       14594    50658304    7  HPFS/NTFS[/COLOR]
Partition 4 does not end on cylinder boundary.
/dev/sda5            3825        7472    29295616   83  Linux
/dev/sda6            7472        8287     6542336   82  Linux swap / Solaris


and df -h gives...
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              28G  4.0G   23G  16% /
none                  998M  296K  998M   1% /dev
none                 1002M  140K 1002M   1% /dev/shm
none                 1002M  192K 1002M   1% /var/run
none                 1002M     0 1002M   0% /var/lock
none                 1002M     0 1002M   0% /lib/init/rw
[COLOR="DarkRed"]/dev/sda4              49G   33G   17G  67% /media/disk[/COLOR]

---

