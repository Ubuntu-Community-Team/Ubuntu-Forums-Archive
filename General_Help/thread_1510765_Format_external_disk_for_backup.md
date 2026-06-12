---
title: "Format external disk for backup"
date: 2010-06-15
forum: General Help
---

### Post by rplantz on 2010-06-15
I just bought a 1 TB Verbatim external usb disk for backup. It includes Nero BackIt 4 on the disk. The disk is formatted FAT32.

My system dual boots Ubuntu and Windows 7.

My thought is that I should copy the Nero folder onto my system disk under Windows 7 to keep the original and reformat the entire external disk to NTFS.

Should I partition the external disk, one for Windows, the other for Ubuntu? Or can I simply use different folders on the external disk?

I don't have anything super critical. I'm not running a business where data loss will cost me money or where I have to stay online.

Right now I backup with rsync to a 160 GB external disk, but it's old and there's no Windows 7 driver for it.

---

### Post by HermanAB on 2010-06-16
Howdy, if you use it with both Windows and Linux, consider formatting it with NTFS.  

Something like this:
$ sudo mkfs.ntfs -L NTFSUSB -Q /dev/sdb1

---

### Post by dcstar on 2010-06-16
> **rplantz said:**
> I just bought a 1 TB Verbatim external usb disk for backup. It includes Nero BackIt 4 on the disk. The disk is formatted FAT32.

My system dual boots Ubuntu and Windows 7.

My thought is that I should copy the Nero folder onto my system disk under Windows 7 to keep the original and reformat the entire external disk to NTFS.

**Should I partition the external disk, one for Windows, the other for Ubuntu?** Or can I simply use different folders on the external disk?

I don't have anything super critical. I'm not running a business where data loss will cost me money or where I have to stay online.

Right now I backup with rsync to a 160 GB external disk, but it's old and there's no Windows 7 driver for it.

It is impossible to backup Linux filesystems correctly to Windows filesystems. They do not fully support all the attributes that Linux uses.

Make two different partitions to ensure that each FS is backup correctly (use gparted).

---

### Post by rplantz on 2010-06-16
> **dcstar said:**
> It is impossible to backup Linux filesystems correctly to Windows filesystems. They do not fully support all the attributes that Linux uses.

Make two different partitions to ensure that each FS is backup correctly (use gparted).

Thank you, dcstar. So I would lose some of my file attributes if I copy a file from ext4 to NTFS, right? I had forgotten about this problem.

---

### Post by jerome1232 on 2010-06-16
Well that depends on your backup method, if you say stick them in a tar archive it won't matter what file system your backups are on since the tar archive will preserve permissions inside of itself.

---

### Post by rplantz on 2010-06-16
> **jerome1232 said:**
> Well that depends on your backup method, if you say stick them in a tar archive it won't matter what file system your backups are on since the tar archive will preserve permissions inside of itself.

Good point. I've been using an rsync script for my Linux backup. I'm pretty sure that would not preserve permisssions for NTFS. I'm a Windows newbie and don't have much of importance on that side, so I'll probably just use the Nero BackIt that came with my external disk.

---

