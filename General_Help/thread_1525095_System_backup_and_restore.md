---
title: "System backup and restore"
date: 2010-07-06
forum: General Help
---

### Post by wkt on 2010-07-06
I'm a new user of Ubuntu and want to work with it in the future.

Before I start I need some information how a **complete system backup** to an external USB drive is done under Ubuntu. Is there special software or has one to use a command for that purpose ?

Even more important to me is the question how I then can **restore** the backup in case of a hard disk crash for instance. Is there some kind of **emergency CD** to be burned as in Windows 7 or is there some tool on the ubuntu installation DVD ?

---

### Post by dethorpe on 2010-07-06
you could try systemrescuecd which is what i use. Its a  Linux **system rescue disk** available as a **bootable CD-ROM or **USB stick for administrating or repairing your system  and data after a crash.

Can then use it to back up your partition using the partimage or FSArchiver tools on the CD, then use it to restore if required.

Get it and instructions at [http://www.sysresccd.org/](http://www.sysresccd.org/) 

Craig

---

### Post by warfacegod on 2010-07-06
Clonezilla and Remastersys are both excellent tools for backing up. This is another great way to do it: [http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

---

