---
title: "how can I backup or clone install to usb hd"
date: 2011-05-25
forum: General Help
---

### Post by craig.brisbane on 2011-05-25
I have ubuntu 10.10 installed on 1TB HD. I would like to back up the full hd, on a 2TB usb HD I have. I would like an easy way to clone/backup the full installation, so if my hd fails I would be able to book the usb hd to get files or do a full reinstall. 

I have tried dd, but not certain if it worked correctly.Also tried clonezilla and that did not work 

Any suggestions would be appreciated of an easy straight forward way.

Craig

---

### Post by btindie on 2011-05-25
Try getting [Parted Magic]("http://partedmagic.com") and put it on a CD/USB. Boot from that then use CloneZilla from within there to backup your hard disk, works a treat.

---

### Post by seawolf167 on 2011-05-25
What didn't work with [Clonezilla]("http://www.clonezilla.org")? I haven't had any problems with it other than having to run in safe graphics mode on a couple of workstations, and highly recommend using Clonezilla if you can get it working.

You could always use *rsync* and mirror your entire directory tree over to your external hard drive, a simply *cron* job would keep this updated. An example command could be

```
rsync -ruv --delete-before /source/1TB/drive /destination/2TB/drive
```

---

### Post by craig.brisbane on 2011-05-25
Thanks for the ideas, when I tried Clonezilla, and reviewed the 2T drive where I copied, it did not appear to have copied all the files

---

### Post by linuxinstalledfromhdd on 2011-05-25
I would recommend that you give Remastersys for Ubuntu a go. 

It's entirely gui. And you can copy your settings to skel from the command line, and create your own custom version of Ubuntu if you want.   Great application. :)

---

### Post by seawolf167 on 2011-05-25
> **craig.brisbane said:**
> Thanks for the ideas, when I tried Clonezilla, and reviewed the 2T drive where I copied, it did not appear to have copied all the files

Try it again! Create a folder in your external hard drive, give it a descriptive name with no spaces, i.e. "my_1tb_backup"

Restart your computer after this, and boot off the Clonezilla LiveCD. Follow the onscreen prompts telling you when to plug in the device. Select to image the entire drive and all partitions to an external media, and use the folder you selected to store your backups. [Here is a how-to ]("http://www.howtoforge.com/back-up-restore-hard-drives-and-partitions-with-clonezilla-live")with pictures.

---

### Post by LordNeo on 2011-05-25
you always can use low level utilities like dd

dd if=/dev/(INSERT HERE THE ORIGINAL DISK, PROBABLY SDA) of=/dev/(INSERT HERE USB DISK, PROBABLY SDB)

Check with the disk utility first to know the disk names.
It will copy the entire disk, including MBR, so you will be able to remove the original disk and boot from the other disk.

If your first disk is sda and your second disk is sdb it will look like:

dd if=/dev/sda of=/dev/sdb

It will take TON of time, because it will also copy "empty blocks" (that as you may know, it could also contain data, recoverable by other means)

---

