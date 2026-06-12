---
title: "Installing Grub: Could not find device for /boot: Not found or not a block device."
date: 2010-01-04
forum: General Help
---

### Post by pete-the-meat on 2010-01-04
Hello,

I am trying to reinstall grub on my hard drive - I'm currently running off a live CD since I can't boot to Ubuntu. Here's my partition info:

```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0bc6c084

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       13042   104652344    7  HPFS/NTFS
/dev/sda3           13043       91201   627812167+   5  Extended
/dev/sda5           13043       14535    11992491   82  Linux swap / Solaris
/dev/sda6           14536       27564   104655411   83  Linux
/dev/sda7           27565       91201   511164171   83  Linux
```

The NTFS partitions are for my Windows 7 install, /dev/sda6 is the root filesystem of my Ubuntu install, which I installed after Windows 7. There is no stage1 file in the /boot/grub directory on sda6 so I tried this:

```
sudo grub-install /dev/sda6
```

but it gave me this error message:

```
Could not find device for /boot: Not found or not a block device.
```

Once I get grub installed on there I can do the root(hd0,5) and setup (hd0,5) steps no problem, I just can't seem to get over this wee hump. Can anyone help?

Thanks :)

---

### Post by jamesisin on 2010-01-04
Try using UUID's instead of /dev/[drive] designations.  You can get the UUID's for your drives using sudo blkid.

I think you will want to insert UUID=blahblahblah though it could be UUID="blahblahblah" (into your command above).

---

### Post by Leppie on 2010-01-04
what version of grub do you have installed?
you can find the version number like this:
```
$sudo grub-install -v
```

---

### Post by Maya_Iz on 2011-02-26
How did you solve your problem? I am having the same problem.

```
ubuntu@ubuntu:~$ sudo grub-install -v
grub-install (GNU GRUB 0.97)
```

---

### Post by Maya_Iz on 2011-02-26
Nevermind. I solved the problem by running the following:

```
mount | tail -l
```

And got:
dev/sda5 on /media/a71fb74d-1fa3-4305-afbc-60b171c0f419 type ext3 (rw,nosuid,nodev,uhelper=udisks)


Then I ran:
```
sudo grub-install --root-directory=/media/a71fb74d-1fa3-4305-afbc-60b171c0f419 /dev/sda

```

Problem solved.

---

