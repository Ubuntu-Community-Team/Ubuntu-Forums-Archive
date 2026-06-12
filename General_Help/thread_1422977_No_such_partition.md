---
title: "No such partition"
date: 2010-03-06
forum: General Help
---

### Post by Scythix on 2010-03-06
Hello, newbie here.

Whenever I boot up the computer, the following error occurs:

Grub loading.
error: no such partition
grub rescue>

And when I prompt set

grub rescue> set
prefix=(hd0,1)/boot/grub
root=hd0,1

I'm not dual booting with another OS.

---

### Post by Intrepid Ibex on 2010-03-06
Gulps, can you post the output of "sudo fdisk -l" with live cd?

You can also check up what gparted has to say (also with livecd), as its graphical.

---

### Post by Scythix on 2010-03-06
I would but for some reason it wont boot from the livedisk.
I cant burn any cds on this computer and my flashdrive recently failed.

I dont know what to do!

---

### Post by drpjkurian on 2010-03-06
> **Scythix said:**
> I would but for some reason it wont boot from the livedisk.
I cant burn any cds on this computer and my flashdrive recently failed.

I dont know what to do!
It looks like complete hardware failure...

---

### Post by Scythix on 2010-03-06
It was working fine a while ago. I think its the livedisk that i have. If i remember correctly, I installed ubuntu off of the flashdrive that I unfortunately do not have anymore.

If i put in the original windows XP disk that came with the computer, itll recognize that but i cant do anything with it.

So i think its the disk that im trying to use. I'll see if i can go to a neighbors house and burn a livedisk there.

---

### Post by Scythix on 2010-03-09
I got the livecd to work:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
Note: sector size is 2048 (not 512)

Disk /dev/sdf: 3930 MB, 3930062848 bytes
64 heads, 32 sectors/track, 937 cylinders
Units = cylinders of 2048 * 2048 = 4194304 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1         937     3837938    b  W95 FAT32
ubuntu@ubuntu:~$

---

