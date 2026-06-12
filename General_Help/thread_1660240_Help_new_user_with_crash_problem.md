---
title: "Help new user with crash problem"
date: 2011-01-05
forum: General Help
---

### Post by stuwoody007 on 2011-01-05
hello all new user and have had a crash boot up and get the following:

missing modules (cat/proc/madules;is/dev)

Alert! /dev/disk/by-uuid/13bf007d-3bab-48et-b91a-babe68ab3223 does not exist

INTITRAMFS

Any ideas? or is there a restore CD available for download like windows?

---

### Post by matt_symes on 2011-01-05
Hi

Boot into the liveCD, open a terminal and type

```
sudo fdisk -l
```

(That is small L above). Enter your password. It will not be echoed on the screen. This is normal.

Post the results back here.

Kind regards

---

### Post by stuwoody007 on 2011-01-05
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91149114

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9764864   83  Linux
/dev/sda2            1216      121602   966994945    5  Extended
/dev/sda5            1216      121602   966994944   83  Linux

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by stuwoody007 on 2011-01-05
ideas?

---

### Post by matt_symes on 2011-01-05
Hi

> **stuwoody007 said:**
> ideas?

Sorry. I meant

```
sudo blkid
```

I have not had my morning coffee yet ;)

Please post results back.

Kind regards

---

### Post by stuwoody007 on 2011-01-05
its ok - 8pm here and i still dont know whats going on


/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="13bf007d-3bab-48e6-b91a-6abe68ab3223" TYPE="ext4" 
/dev/sda5: UUID="abbe7d9b-5304-4b45-9c59-450cef6ed5f5" TYPE="ext4" 
/dev/sdb1: LABEL="Luggage" UUID="9A0C734A0C732105" TYPE="ntfs" 
ubuntu@ubuntu:~$

---

### Post by matt_symes on 2011-01-05
Hi

From the terminal post back the results of

```
ls /dev/disk/by-uuid
```

Kind regards

---

### Post by stuwoody007 on 2011-01-05
ubuntu@ubuntu:~$ ls /dev/disk/by-uuid
13bf007d-3bab-48e6-b91a-6abe68ab3223  abbe7d9b-5304-4b45-9c59-450cef6ed5f5
9A0C734A0C732105
ubuntu@ubuntu:~$

---

### Post by stuwoody007 on 2011-01-05
anyone else able to help??

---

### Post by matt_symes on 2011-01-05
Hi

There are a couple of files to look at as well.

From the liveCD, at a terminal type...

```
sudo mkdir /media/tmp
```

```
sudo mount -t ext4 /dev/sda1 /media/tmp
```

Post the output of /etc/fstab

```
cat /media/tmp/etc/fstab
```

and the file grub.cfg

```
cat /media/tmp/boot/grub/grub.cfg
```

This last file might be rather long so post it between code tags.

Kind regards

---

### Post by stuwoody007 on 2011-01-05
ubuntu@ubuntu:~$ sudo mkdir /madia.tmp
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sdal /media/tmp
mount: mount point /media/tmp does not exist
ubuntu@ubuntu:~$ 

half way

---

### Post by stuwoody007 on 2011-01-05
ubuntu@ubuntu:~$ cat /media/tmp/etc/fstab
cat: /media/tmp/etc/fstab: No such file or directory
ubuntu@ubuntu:~$ cat /media/tmp/boot/grub/grub.cfg
cat: /media/tmp/boot/grub/grub.cfg: No such file or directory
ubuntu@ubuntu:~$

---

### Post by stuwoody007 on 2011-01-05
Anybody help please - bed time is coming

---

### Post by matt_symes on 2011-01-05
Hi

```
sudo mkdir /madia.tmp
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sdal /media/tmp
mount: mount point /media/tmp does not exist
```

should be

```
sudo mkdir /media/tmp
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sdal /media/tmp
```

you spelt this incorrectly..

```
sudo mkdir /madia.tmp
```

Kind regards

---

