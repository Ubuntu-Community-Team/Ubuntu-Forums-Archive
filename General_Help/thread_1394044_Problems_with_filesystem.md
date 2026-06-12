---
title: "Problems with filesystem"
date: 2010-01-30
forum: General Help
---

### Post by Macamba on 2010-01-30
Hi,

Today I was downloading away, and at one moment I got problems opening a directory. I double clicked the directory I wanted to enter, the directory was opened, but nothing was displayed. I killed the directory browser which came up a few seconds later. But still no contents of the directory. 

Next I rebooted and got stuck in the boot loader:
```

Grub loading stage 1.5

Grub loading please wait ...
Error 17

```

I'm totally at a loss. Looking at an old discussions about this topic I had earlier ([Reinstall XP, problems booting Ubuntu]("http://ubuntuforums.org/showthread.php?p=7098899#post7098899")) got me nowhere. The links mentioned in the post about mounting the file system led to missing pages. 

I think my file system is messed up, together with my boot loader (probably GRUB).

My filesystem:
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

```

/dev/sda8 is my Linux partition.

Next I started grub to fdisk, resulting in:
```

ubuntu@ubuntu:/$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> fdisk -l
fdisk -l

Error 27: Unrecognized command
grub> 

```

So, no device listing. I'm at a loss. :shock:

I'm trying to mount my Linux OS (/dev/sda8), but probably have problems finding it. At the moment I have a computer as a ornament, something to look at. Not something to use, as my boot loader and/or file system is broken. What do I need to do to get things working again?

TIA,
Macamba

---

### Post by john newbuntu on 2010-01-30
Follow step 15 in: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
where (hdX,Y) will be (hd0,8) in your case and sdXY will be sda8

---

### Post by Macamba on 2010-01-30
I'm getting confused. I do not have a /boot/grub. Might that be a problem?

```

ubuntu@ubuntu:/$ ls -la /boot
total 3569
drwxr-xr-x  2 root root     149 2008-07-02 10:17 .
drwxr-xr-x 32 root root     280 2010-01-30 08:56 ..
-rw-r--r--  1 root root  420224 2008-06-18 16:47 abi-2.6.24-19-generic
-rw-r--r--  1 root root   74164 2008-06-18 16:47 config-2.6.24-19-generic
-rw-r--r--  1 root root  103204 2007-09-28 11:03 memtest86+.bin
-rw-r--r--  1 root root 1152332 2008-06-18 16:47 System.map-2.6.24-19-generic
-rw-r--r--  1 root root 1903960 2008-06-18 16:47 vmlinuz-2.6.24-19-generic
ubuntu@ubuntu:/$ 

```

---

### Post by oldos2er on 2010-01-30
Which version of Ubuntu are you running?

If you have a LiveCD, you can boot from it and run fsck on your Linux partitions. The link john newbuntu posted is for grub2, and from your /boot list it looks like you're running an older version of Ubuntu.

---

