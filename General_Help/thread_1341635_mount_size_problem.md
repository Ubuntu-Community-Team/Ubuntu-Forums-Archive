---
title: "mount size problem"
date: 2009-11-29
forum: General Help
---

### Post by mahiyar on 2009-11-29
My scheme on one of the machine is really simple. I did a clean install of 9.10 on 40gb drive, ext4 file system, the partition 20gb for root and all, and the other 20 gb for data. Now suddenly I see that out of 20gb in root I have only 2gb left. On probing further I found that out of 20gb root is mounted on only 5gb or so. What's up? and how to reclaim the balance 15gb.

---

### Post by fluffman86 on 2009-11-29
please post the output of

sudo fdisk -l

---

### Post by mahiyar on 2009-11-30
Ok here is the output of fdisk -l, also the attached pic files shows output of system monitor where clearly root partition is less.

antony@antony-desktop:~$ sudo fdisk -l
[sudo] password for antony: 

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb0fdb0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2033    16330041   83  Linux
/dev/sda2            2034        2175     1140615   82  Linux swap / Solaris
/dev/sda3            2176        4863    21591360    b  W95 FAT32

---

### Post by mahiyar on 2009-12-01
A polite .................. Bump .......................

---

### Post by mahiyar on 2009-12-03
Even the 'sudo df -h' shows the same thing. i.e / mounted on /dev/sda1 size 4.6 gb.

I do not understand my sda1 is 16gb as can be seen from fdisk output.

---

### Post by mahiyar on 2009-12-05
Well finally I had to reinstall/reformat the entire drive. It seems that on last install, I had used gparted to reinstall some partitions. Might be some problem in gparted, using ext4? So this time I reformatted using the live disc facility.

---

### Post by audiomick on 2009-12-05
Hallo.
I am not good at reading that fdisc output, but it seems to me that the swap partition was inordinately large.

---

### Post by mahiyar on 2009-12-06
I do not think a 1gb swap is very big. The rule is the swap space should be the same size of RAM. Look at the blocks column the amount divided by 1,000,000 roughly gives you the size in GB.

---

