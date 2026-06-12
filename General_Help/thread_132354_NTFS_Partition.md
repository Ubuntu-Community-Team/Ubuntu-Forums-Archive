---
title: "NTFS Partition"
date: 2006-02-18
forum: General Help
---

### Post by gerowen on 2006-02-18
I want to be able to browse my NTFS partition without having to use the terminal to run:
sudo nautilus /media/hda1
Is there a way to give myself the permissions needed to access that drive?  The ch* commands don't work because it gives me the message "read only file system".  I don't care about writing to it, I just want to be able to double click the icon and browse it with no hassle.

---

### Post by twigboy on 2006-02-18
[https://wiki.ubuntu.com/AutomaticallyMountPartitions?action=show&redirect=AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountPartitions?action=show&redirect=AutomaticallyMountMSWindowsPartitions)

I followed this guide to automatically mount one of my ntfs partitions on startup

---

### Post by akudewan on 2006-02-18
You can mount the partition using fstab. Edit the /etc/fstab and add a line similar to this one:
```

/dev/hda1     /media/hda1          ntfs    auto,user,rw,umask=0000 0 2

```

Before mounting the filesystem, make sure that the /media/hda1 has writing permission.

---

### Post by polt on 2006-02-19
will this still work if the drive is on /dev/sda1 ?

---

### Post by aeiah on 2006-02-19
[QUOTE=polt]will this still work if the drive is on /dev/sda1 ?[/QUOTE]

if you change hda1 to sda1 in the applicable place(s), yes

---

### Post by aysiu on 2006-02-19
[QUOTE=polt]will this still work if the drive is on /dev/sda1 ?[/QUOTE] I don't know if this will work (it might): ```
/dev/hda1     /media/hda1          ntfs    auto,user,rw,umask=0000 0 2
``` but I do know that this *will* work: ```
sudo umount /dev/sda1
sudo mkdir /windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` Replace whatever /dev/sda1 line is in there with this (or create this line if none exists): ```
/dev/sda1 /windows ntfs nls=utf8,umask=0222 0 0
``` Save and exit Gedit and then ```
sudo mount -a
```

---

### Post by polt on 2006-02-25
Okay, so I added this line to fstab:

> /dev/sdb1	/media/usbdisk	ntfs	nls=utf8,umask=777 0 0

It did not quite work.  Now the folders on this usbdisk are listed as "unknown file type" and I cannot browse through them.  However, when the disk auto mounts, it works fine.

---

### Post by aysiu on 2006-02-25
[QUOTE=polt]Okay, so I added this line to fstab: ```
/dev/sdb1 /media/usbdisk ntfs nls=utf8,umask=777 0 0
``` It did not quite work.  Now the folders on this usbdisk are listed as "unknown file type" and I cannot browse through them.  However, when the disk auto mounts, it works fine.[/QUOTE] Why did you add that line? You should have added this line: ```
/dev/sdb1 /media/usbdisk ntfs nls=utf8,umask=0222 0 0
``` I don't know where you got 777 from...

---

### Post by polt on 2006-03-04
[QUOTE=aysiu]Why did you add that line? You should have added this line: ```
/dev/sdb1 /media/usbdisk ntfs nls=utf8,umask=0222 0 0
``` I don't know where you got 777 from...[/QUOTE]

touché.  however, it still claims to be a read-only file system.

---

### Post by aysiu on 2006-03-04
NTFS is *supposed* to be read-only.

If you want read/write, you need FAT32.

---

### Post by akiro.yamamoto on 2006-03-04
Well either fat32 or ext3, with the ext file system drivers installed to WinXp.
That's what I did ;)

---

