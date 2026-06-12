---
title: "Disk Imaging ???"
date: 2009-11-12
forum: General Help
---

### Post by windowsfree on 2009-11-12
Is there a program I can use that is similar to Acronis Disk Image for Windows that I can make a disk image of my current Linux install on my laptop?  I am using Ubuntu 9.04 and have it customized to the way I want it.  My laptop is an older Gateway with a 60 gig HD and 1GB of Ram.

---

### Post by Minsky on 2009-11-12
you could use Clonezilla which runs from a live CD and uses a command line menu system [http://clonezilla.org](http://clonezilla.org), or if you prefer to use a GUI then there's Remastersys [http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html). If you prefer to stick with Acronis, then they also have a shareware version called Acronis True Image Server For Linux 8.0 [http://www.freedownloadscenter.com/Network_and_Internet/Remote_Computing_Tools/Acronis_True_Image_Server_for_Linux.html](http://www.freedownloadscenter.com/Network_and_Internet/Remote_Computing_Tools/Acronis_True_Image_Server_for_Linux.html). I use Clonezilla which I find is very good for personal use and provides backups quickly.

---

### Post by windowsfree on 2009-11-12
Thank you, I will try both that you described and see what I like best.  Your help is greatly appreciated.

---

### Post by Mark Phelps on 2009-11-12
If you just want an app to do simple image backup and restore, check out Partimage Is Not Ghost (PING) at windowsdream.com.

It is available as a bootable ISO that can be burned to CD, it can also be installed in your /boot folder and then be selected from the GRUB menu.

It's not super fancy, but it's fast and easy to use.

---

### Post by windowsfree on 2009-11-12
> **Mark Phelps said:**
> If you just want an app to do simple image backup and restore, check out Partimage Is Not Ghost (PING) at windowsdream.com.

It is available as a bootable ISO that can be burned to CD, it can also be installed in your /boot folder and then be selected from the GRUB menu.

It's not super fancy, but it's fast and easy to use.

Thank You - simplicity is GRAND.

---

### Post by falconindy on 2009-11-12
Simplicity is using the built in Linux tools to accomplish what you want and not installing more software.

```
dd if=/dev/sda1 of=/path/to/backup/sda1.image bs=16k
```
The above will make an exact image of sda1. Be aware that it's the also the size of sda1, regardless of free space. As an added bonus, you can mount this image as follows:
```
sudo mount -t ext3 /path/to/sda1.image /path/to/mount -o loop
```

---

### Post by windowsfree on 2009-11-12
Thank you very much.  Can I use that to back up to a USB external drive?  Could I do it to a Windows shared Folder?
Thanks again

---

### Post by bernardfrancois on 2009-11-15
You could use that to backup to another destination, just enter the path where you want to put it in the 'of=...' part of the line (as actually already indicated there).

If you want to store your backup somewhere, you need to have enough free space: as much as the size of the disk you're backing up. If you want to make a backup of a 120GB hard disk, you need 120GB available space to store the backup (even if that 120GB is not full).

**[SIZE="2"]_Alternate solution:_[/SIZE]**

I searched a bit and found a way to zip the output of the dd command, so we directly create a gzipped disk image:

```
dd if=/dev/sda1 | gzip -9 > /path/to/backup/sda1.image
```

In this line, you can replace -9 by any value between -1 and -9; the higher the number the better the compression, but the longer it will take.

To restore your backup, you need the following line:
```
gunzip /path/to/backup/sda1.image - | dd if=/dev/sda1
```

This is the page where I found this info:
[http://www.openbsdsupport.org/backup-with-dd-and-gzip.html](http://www.openbsdsupport.org/backup-with-dd-and-gzip.html)

Note that I didn't try this yet.

I would like to use this method, but only if I could also mount the gzipped disk image... **Does anyone have a clue to how this could be done?**

---

