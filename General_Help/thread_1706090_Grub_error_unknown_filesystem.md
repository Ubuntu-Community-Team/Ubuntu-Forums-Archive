---
title: "Grub error unknown filesystem"
date: 2011-03-13
forum: General Help
---

### Post by chuyenhiu on 2011-03-13
My computer froze so I shut it down. When it rebooted i get
> Grub loading
error unknown filesystem
grub rescue
I can't get my hd with ubuntu 9.10 to mount.
i type in sudo fdisk -l and this is what i get
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB,  200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units  = cylinders of 16065 * 512 = 8225280 bytes
Sector size  (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal):  512 bytes / 512 bytes
Disk identifier: 0xeadaeada

   Device  Boot      Start         End      Blocks   Id  System
/dev/sda1   *         1276        6290    40282956    7  HPFS/NTFS
/dev/sda2             6291       24321   144834007+   f  W95 Ext'd (LBA)
/dev/sda3                1         262     2104483+  82  Linux swap / Solaris
/dev/sda4              263        1275     8136922+  83  Linux
/dev/sda5             6291       11970    45624568+   b  W95 FAT32
/dev/sda6            11971       24321    99209376    b  W95 FAT32when i try and mount this is what it gives me
> ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt
mount: you must specify  the filesystem type> ubuntu@ubuntu:~$ sudo grub-install --recheck -f --root-directory=/mnt  /dev/sda4
/usr/sbin/grub-setup: error: unable to identify a  filesystem in hd0,4; safety check can't be performed i hope someone can help me out on this. Thanks

---

### Post by ajgreeny on 2011-03-13
Using a live CD run ```
sudo e2fsck /dev/sda4
```I am assuming from your comments that sda4 is your problem ubuntu partition, but if so, how are you running ```
sudo fdisk -l
``` is that from a live CD?

PS:  Your mount command should have been ```
sudo mount /dev/sda4 -t ext4 /mnt
```or ext3 if it was that file-system type.

---

### Post by chuyenhiu on 2011-03-13
> **ajgreeny said:**
>  how are you running ```
sudo fdisk -l
``` is that from a live CD?

PS:  Your mount command should have been ```
sudo mount /dev/sda4 -t ext4 /mnt
```or ext3 if it was that file-system type.

Yes . I Using a live CD run 
sudo fdisk -l

> Using a live CD run 
Using a live CD run 

> error : file not found
grub rescue>

---

### Post by runeh76 on 2011-03-13
Hi

Read part: **Reinstalling GRUB 2**
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by chuyenhiu on 2011-03-13
> **runeh76 said:**
> Hi

Read part: **Reinstalling GRUB 2**
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt  /dev/sda4
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition  instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be  installed in this setup by using blocklists.  However, blocklists are  UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
```

---

### Post by runeh76 on 2011-03-13
Try this:

reboot to recovery mode

```
sudo update-grub2
```

---

### Post by wilee-nilee on 2011-03-13
> **chuyenhiu said:**
> ```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt  /dev/sda[B]4
/usr/sbin/grub-setup[/B]: warn: Attempting to install GRUB to a partition  instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be  installed in this setup by using blocklists.  However, blocklists are  UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
```

Your command is wrong this is what it should be.
```
sudo grub-install --root-directory=/mnt /dev/sda
```

Look again at the link only two commands after the fdisk -l

---

### Post by runeh76 on 2011-03-13
edit: partitions ok

---

### Post by Animal X on 2011-03-13
every time i see this posted:
> ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt   /dev/sda4
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition  instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be  installed in this setup by using blocklists.  However, blocklists are  UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force. i notice an extra space between "--root-directory=/mnt" and "/dev/sda4", did you copy/paste exact?

---

