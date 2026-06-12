---
title: "Ubuntu 11.10 does not have enough disk space"
date: 2012-01-27
forum: General Help
---

### Post by agahlawa on 2012-01-27
Hi,

I have an Asus 64e laptop and after much headbanging and lots of tears I finally managed to get 11.10 running on it. However, now it keeps on giving me the error "There is only 100 MB left on the disk". I can't even download the updates. As far as I remember at the time of install I had an option of assigning Ubuntu more space but maybe I skipped it. 

My question is, how can I assign Ubuntu more space as majority of my lab work is done on Ubuntu. I have a 750 GB hard disk so there is enough space.

I went to the Windows disk manager and found out that there are 3 partitions:

1) Type-Basic, File system-'Blank', Status-Healthy(Primary Partition), Capacity-17.09 GB, Free space-17.09 GB

2)Type-Basic, File system-'Blank', Status-Healthy(Primary Partition), Capacity-7.91 GB, Free space-7.91 GB

3) Type-Basic, File system-NTFS, Status-Healthy(System, Boot, Page File, Active, Crash Dump, Primary Partition), Capacity-673.63 GB, Free space-594.88 GB

I know that the third one, the NTFS, is the one on which my Windows is, but where is my Ubuntu installed on? I did not install 11.10 using Wubi.

Any help would be appreciated, I would like to assign about 400 GB to 11.10 and the rest to Windows. Thanks a lot.

Adi

---

### Post by luckyEddy on 2012-01-27
Rehi,

from within you UBUNTU-system open a shell and try ```
cat /etc/mtab 
```

This will give you a list of your currently mounted filesystems. have a look at something like > /dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
In this case "/dev/sda1" is the first harddrive (sda), first partition (1) and the mountpoint is "/", the root of your installation.

---

### Post by gsgleason on 2012-01-27
please show the output of the following:

df -h
sudo fdisk -l

---

### Post by QIII on 2012-01-27
That's a small "L", not a one.

---

### Post by agahlawa on 2012-01-27
Ok, the output of df -h is 

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              17G   16G  176M  99% /
udev                  3.9G  4.0K  3.9G   1% /dev
tmpfs                 1.6G  876K  1.6G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  3.9G  1.3M  3.9G   1% /run/shm
/home/adi/.Private     17G   16G  176M  99% /home/adi


The output of the command sudo fdisk -l is

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xaa9693fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    52430848  1465143168   706356160+   7  HPFS/NTFS/exFAT
/dev/sda2            2046    52430847    26214401    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5            2048    35835903    17916928   83  Linux
/dev/sda6        35837952    52430847     8296448   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mapper/cryptswap1: 8495 MB, 8495562752 bytes
255 heads, 63 sectors/track, 1032 cylinders, total 16592896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x34c71df4

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table


Thanks for your quick replies.

---

### Post by agahlawa on 2012-01-31
So what do I do now?

---

### Post by dragonfly41 on 2012-01-31
I had similar problems and received advice here ..

[http://ubuntuforums.org/showthread.php?t=1794170](http://ubuntuforums.org/showthread.php?t=1794170)

Boot up ubuntu Live CD

I ran the command **gksu nautilus** to open file manager

explore /dev/sda5/which is 99% full

start to jettison  redundant files .. e.g. in /var/log and elsewhere

If you get to a point where you've released enough space in /dev/sda5/ to boot up your internal kernel, then after booting up install bleachbit to tidy up /dev/sda5/ further.

Keep an eye on used space and if it is getting full you may have to resize partitions or put data in another partition.

---

### Post by hilz on 2012-01-31
> **agahlawa said:**
> So what do I do now?

Hi agahlawa. Your Ubuntu partition is full. It looks like you have  Windows on another partition. If you feel confident enough, you could  try booting with the Live CD of Ubuntu and increase the size of your  Ubuntu partition - sda5. You don't need to re-install Ubuntu to do this.

Before starting you should back up anything of importance. Just in case.

---

