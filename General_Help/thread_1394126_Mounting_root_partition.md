---
title: "Mounting root partition"
date: 2010-01-30
forum: General Help
---

### Post by Macamba on 2010-01-30
Hi,

Today my system broke down. And I'm trying to get it working again. 

**What happened:**
I was working with my Ubuntu and suddenly I got troubles opening a directory. When I clicked on a directory in the file browser it opened empty. Next I rebooted, and got the following message:
```

Grub loading stage 1.5

Grub loading please wait ...
Error 17

```

I booted from the LiveCD, and got on the Internet to search for a solution for my problem. 

As far as I can see I can not mount the partition on which Ubuntu is installed. I tried:
```

ubuntu@ubuntu:/$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x64bdceff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6375    51207156    7  HPFS/NTFS
/dev/sda2            6376       25497   153597465    7  HPFS/NTFS
/dev/sda3           25498       91201   527767380    5  Extended
/dev/sda5           25498       31871    51199123+   7  HPFS/NTFS
/dev/sda6           31872       38245    51199123+   7  HPFS/NTFS
/dev/sda7           38246       44619    51199123+   7  HPFS/NTFS
/dev/sda8           44620       46186    12586896   83  Linux
/dev/sda9           46187       57080    87506023+  83  Linux
/dev/sda10          57081       57367     2305296   82  Linux swap / Solaris
/dev/sda11          57368       70115   102398278+   7  HPFS/NTFS
/dev/sda12          70116       82863   102398278+   7  HPFS/NTFS
/dev/sda13          82864       91201    66974953+   7  HPFS/NTFS
ubuntu@ubuntu:/$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> fdisk -l
fdisk -l

Error 27: Unrecognized command
grub> quit
quit
ubuntu@ubuntu:/$ 

```

Next I tried to do it a bit different:
```

ubuntu@ubuntu:/$ sudo mkdir /mnt/root
ubuntu@ubuntu:/$ ls /mnt
root  ubuntu
ubuntu@ubuntu:/$ sudo mount -t ext3 /dev/sda8 /mnt/root
mount: wrong fs type, bad option, bad superblock on /dev/sda8,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:/$ 

```

Does anyone know what I can do?

Macamba

---

### Post by Sycron on 2010-01-30
Did you tried running fsck with the partition unmounted?

---

### Post by SecretCode on 2010-01-30
Is this exactly the same issue as your post [[ubuntu] Problems with filesystem - Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=1394044)? If so, it would be better to stick to one thread.

---

### Post by rnerwein on 2010-01-30
hi [Macamba]("http://ubuntuforums.org/member.php?u=731906")
try mount without -t ext3 - let mount decide what kind of fs it is. if you are running 9.10 (you ain't tell us) i guess the fs type is ext4 by default - isn't it.
--> mount /dev/sda9 /mnt
try this
ciao

---

