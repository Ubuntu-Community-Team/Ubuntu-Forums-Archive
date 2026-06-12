---
title: "Suddenly I have free space on my machine."
date: 2010-11-26
forum: General Help
---

### Post by Jetso on 2010-11-26
I installed GParted just so that I could have it in case I ever needed to resize my partitions. I opened it just because, with no intent of changing anything. That's when I noticed that I have 1.7 GiB of free space. I KNOW this was not here when I installed Ubuntu, so why is it there? Also, if it is safe can I add it to my / partiton. It is in between my NTFS partiton and my Extended Linux partition so I would have to change the start point of /. Would that present a problem?

---

### Post by sikander3786 on 2010-11-26
Please post the output of

```
sudo fdisk -lu
```

It would tell us about your partitions more specifically.

---

### Post by Jetso on 2010-11-26
Here you go!
```
jetso@Jetso-Inspiron-1525:~$ sudo fdisk -lu
[sudo] password for jetso: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2           81920    20561919    10240000    7  HPFS/NTFS
/dev/sda3   *    20561920   276616863   128027472    7  HPFS/NTFS
/dev/sda4       276619262   312580095    17980417    f  W95 Ext'd (LBA)
/dev/sda5       276619264   284431763     3906250   82  Linux swap / Solaris
/dev/sda6       284432384   312580095    14073856   83  Linux

``` Hope this helps.

---

### Post by SecretCode on 2010-11-26
sda4 is your extended partition - it's not taking up any space (well, 63 sectors) - the space is used by sda5 and sda6.

sda5 is the swap partition (not entirely necessary, but would just take up space inside your linux partition if you used a swap file)

I don't see any unallocated space.

---

### Post by Jetso on 2010-11-26
I don't know what you mean? I attached a screenshot this time around

---

### Post by SecretCode on 2010-11-26
Oh! But that's only 1.17**M**iB. It will be to do with aligning partitions on cylinder boundaries. Don't try to recover that ...

---

### Post by Jetso on 2010-11-26
Duh! I don't know why I thought it was GiB](*,)

---

### Post by ivarn on 2010-11-26
I think I know why. You wish it was GB so your brain fooled you.

---

### Post by Jetso on 2010-11-26
Haha, ya probably.

---

