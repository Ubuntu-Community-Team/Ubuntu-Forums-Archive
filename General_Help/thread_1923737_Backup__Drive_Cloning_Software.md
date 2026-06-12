---
title: "Backup / Drive Cloning Software"
date: 2012-02-11
forum: General Help
---

### Post by i3design on 2012-02-11
Hi,

I have the following setup:

1 x OS Drive
2 x 2TB Content Drives  (NTFS)
2 x 2TB Backup Drives  (NTFS)

My NAS has hardware RAID and I understand that I can put software RAID on it, but I dont really want RAID. What I want is some software which will clone the content drives onto the backup drives every 2 hours.

Since the drive is quite big, I also want it to do it intelligently. For example, know if anything has changed on drive A and only clone the new files onto drive B, rather than doing EVERY file each time.

I want it setup so that if my OS drive fails, or either the content drive or backup drive, I can just pop out the working drive and still be able to access all my files by plugging it into my windows PC without running any commands or scripts.

What software is available on ubuntu to do this?

James

---

### Post by jerrrys on 2012-02-11
[Clonezilla]("http://clonezilla.org/")

But to clone a HDD, it must be off line.  So cloning every two hours would be impractical.

Take a look at the rsync family.

[http://en.wikipedia.org/wiki/Rsync](http://en.wikipedia.org/wiki/Rsync)

[http://en.wikipedia.org/wiki/Grsync](http://en.wikipedia.org/wiki/Grsync)

[http://luckybackup.sourceforge.net/](http://luckybackup.sourceforge.net/)

You already have rsync installed; its part of the default install.  The GUI's can be found in the software center.

---

### Post by bluexrider on 2012-02-11
I use GRsync myself. But there are a lot of different apps to back up with. Here is a list of some
[http://linux.about.com/od/softbackup/Linux_Software_Backup_Solutions.htm](http://linux.about.com/od/softbackup/Linux_Software_Backup_Solutions.htm)

---

