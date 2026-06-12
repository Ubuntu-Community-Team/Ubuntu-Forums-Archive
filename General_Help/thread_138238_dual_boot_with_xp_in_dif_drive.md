---
title: "dual boot with xp in dif drive"
date: 2006-03-01
forum: General Help
---

### Post by gizmokaka on 2006-03-01
hey everybody
I have two HD's on my machine
one with linux installed & one with windows
I wanna dual boot them let's say threw grub.
in my device.map i only see the linux drive & cant see the other one
but in /dev I do have the windows HD represented by /dev/sdb
how do I find out what hd% is my windows drive & make dual boot with windows???

thanks in advenced

---

### Post by Ramses de Norre on 2006-03-01
sudo fdisk -l should show all your partitions

---

### Post by gizmokaka on 2006-03-01
yes I kind of found it out already 
this is my structure of you need it
hope you could help mw dual boot

[B]Disk /dev/sda: 80.0 GB, 80025280000 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4900    39359218+  83  Linux
/dev/sda2            9195        9729     4297387+   5  Extended
/dev/sda3   *        4901        9194    34491555   83  Linux
/dev/sda5            9381        9729     2803311   82  Linux swap / Solaris
/dev/sda6            9195        9380     1493982   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120033041920 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8924    71681998+   7  HPFS/NTFS
/dev/sdb2            8925       14592    45528210    f  W95 Ext'd (LBA)
/dev/sdb5            8925       13258    34812823+   7  HPFS/NTFS
/dev/sdb6           13259       14592    10715323+   b  W95 FAT32
[/B]
right now I change bios boot sequence in order to change operating systems boot
wanna dual boot easy threw a boot loader

can you help me?????????

---

