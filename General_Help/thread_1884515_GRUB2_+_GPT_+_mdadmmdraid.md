---
title: "GRUB2 + GPT + mdadm/mdraid"
date: 2011-11-21
forum: General Help
---

### Post by slipdipper on 2011-11-21
i'm having a ton of problems getting my system set up. it all basically comes down to getting grub2 to see my raid devices. I can get to a rescue prompt, but after that, nothing

I booted to a live cd, partitioned my harddrive, then set up the mdraid and ran the 10.04.3 server installation. It failed on grub and i just continued without it. 


Now i'm booted back into a ubuntu 10.10 desktop. but i just cannot get grub to recognize my raid devices. 

here's some info:

**Partitions**
```

# parted -l
Model: ATA Hitachi HDS72303 (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name     Flags
 1      17.4kB  2000kB  1983kB                  grub     bios_grub
 2      2097kB  2997GB  2997GB  xfs             primary  raid
 3      2997GB  3001GB  4001MB  linux-swap(v1)  swap     raid


Model: ATA Hitachi HDS72303 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name     Flags
 1      17.4kB  2000kB  1983kB                  grub     bios_grub
 2      2097kB  2997GB  2997GB  xfs             primary  raid
 3      2997GB  3001GB  4001MB  linux-swap(v1)  swap     raid


```

**RAID info**
```

Model: Linux Software RAID Array (md)
Disk /dev/md0: 2997GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  2997GB  2997GB  xfs


Model: Linux Software RAID Array (md)
Disk /dev/md1: 4001MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  4001MB  4001MB  linux-swap(v1)

# mdadm --detail --scan
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=01.00 name=0 UUID=6bb41264:84b97c4c:85f5beb4:355f331c
ARRAY /dev/md1 level=raid1 num-devices=2 metadata=01.00 name=1 UUID=ef7ecae8:4969eec3:4439ba59:e65ce048

root@ubuntu:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 01.00
  Creation Time : Tue Nov 22 00:27:38 2011
     Raid Level : raid1
     Array Size : 2926356344 (2790.79 GiB 2996.59 GB)
  Used Dev Size : 5852712688 (5581.58 GiB 5993.18 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Nov 22 02:11:40 2011
          State : active, resyncing
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

 Rebuild Status : 23% complete

           Name : 0
           UUID : 6bb41264:84b97c4c:85f5beb4:355f331c
         Events : 9

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2
root@ubuntu:~# mdadm --detail /dev/md1
/dev/md1:
        Version : 01.00
  Creation Time : Tue Nov 22 00:28:49 2011
     Raid Level : raid1
     Array Size : 3907572 (3.73 GiB 4.00 GB)
  Used Dev Size : 3907572 (3.73 GiB 4.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Tue Nov 22 02:11:40 2011
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : 1
           UUID : ef7ecae8:4969eec3:4439ba59:e65ce048
         Events : 2

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       8       19        1      active sync   /dev/sdb3


```


**UUIDs:**
```

root@ubuntu:~# blkid
/dev/loop0: TYPE="squashfs"
/dev/sda2: UUID="6bb41264-84b9-7c4c-85f5-beb4355f331c" LABEL="0" TYPE="linux_raid_member"
/dev/sda3: UUID="ef7ecae8-4969-eec3-4439-ba59e65ce048" LABEL="1" TYPE="linux_raid_member"
/dev/sdb2: UUID="6bb41264-84b9-7c4c-85f5-beb4355f331c" LABEL="0" TYPE="linux_raid_member"
/dev/sdb3: UUID="ef7ecae8-4969-eec3-4439-ba59e65ce048" LABEL="1" TYPE="linux_raid_member"
/dev/md0: UUID="2b463369-10d0-4e01-aa6c-948ab4284f1d" TYPE="xfs"
/dev/md1: UUID="b36b8777-0e52-4c76-a365-c36f81519dac" TYPE="swap"
/dev/sdc1: LABEL="PENDRIVE" UUID="1203-1228" TYPE="vfat"

```

**Install Procedure**
Hit tab when the LiveCD prompts you to pick what to boot from. Add

```
nodmraid
```
to the end of the option and boot. 

install mdadm:
```
sudo apt-get install --no-install-recommends mdadm
```

make sure your drives are recognized
```
sudo mdadm --detail --scan
```

Mount everything and enter chroot
```
mount /dev/md0 /mnt; for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done ; chroot /mnt
```


use the following to install:

create /boot/grub/device.map:
```
grub-mkdevicemap
```

I added the (md0) entry manually:
```

root@ubuntu:/# cat /boot/grub/device.map
(md0)   /dev/md0
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc

```

create grub.cfg
```

root@ubuntu:/# grub-mkconfig -o /boot/grub/grub.cfg
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-35-generic
Found initrd image: /boot/initrd.img-2.6.32-35-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /cdrom: No such file or directory
ls: cannot access /cdrom: No such file or directory
ls: cannot access /cdrom: No such file or directory
ls: cannot access /cdrom: No such file or directory
ls: cannot access /cdrom: No such file or directory
ls: cannot access /cdrom: No such file or directory
done

```

I also added the following to the top of /boot/grub/grub.cfg
```

set pager=1
set debug=all
insmod part_gpt
insmod raid
insmod mdraid
insmod normal
insmod configfile

```

install to bios_grub partitions:
```

root@ubuntu:/# grub-install --no-floppy --modules='biosdisk xfs raid mdraid' /dev/sda
Installation finished. No error reported.
root@ubuntu:/# grub-install --no-floppy --modules='biosdisk xfs raid mdraid' /dev/sdb
Installation finished. No error reported.

```

exit chroot
```
exit
```

umount and reboot:
```

for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done ; umount /mnt; reboot

```

Note:
this is a loosely related voyage starting: [http://ubuntuforums.org/showthread.php?p=11477254](http://ubuntuforums.org/showthread.php?p=11477254)

---

### Post by toshko3 on 2011-11-21
Would you tell us what is the purpose of all this? Which would be the root partition? I assume the /dev/md0 will be data partition? And why are the swap partitions in RAID1, too?

---

### Post by slipdipper on 2011-11-21
So i'd just like to have a single raid 1 setup on /dev/sda2,/dev/sdb2.. 

i made the swap partitions raid1 as well to avoid and manual changes if something fails on the primary drive. from what i read, it didnt matter if swap was in a raid config.

---

### Post by toshko3 on 2011-11-23
OK, I don't have any experience with GPT, but from my experience with root partition on RAID1, I have had only headaches and nothing more. So now I am doing it only on data partitions. I create two identical partition tables on both of the HDDs, but only RAID the data partition. 
The first partition on the first HDD is used for root partition with a normal file system, the second for RAID1-data and the last for swap. The second HDD - first partition is used for backup of the root partition (every week), second for RAID1-data and the last for swap. You can mount 2 swaps and you do not have to make any changes if one fails. If you are doing RAID1 underneath them, you will load the CPU with unnecessary jobs for syncing. Of course there is a little risk of not saving the data in the swap partition when one HDD dies. But as it is temporary data, you have to decide depending on the applications you are using.
Normally the root partition is not so often changed and I back it up once a week. Again you will have to decide depending on the applications and usage.
In case of failure of the first hard disk, you will have to reconfigure and install GRUB on the other HDD and change the UUIDs in menu.lst and fstab.
If this scenario doesn't help you, I'm sorry, I'm just trying to help here.
Otherwise check if grub can read your file system...

---

