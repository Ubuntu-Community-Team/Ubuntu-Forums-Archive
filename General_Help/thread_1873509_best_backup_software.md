---
title: "best backup software"
date: 2011-11-01
forum: General Help
---

### Post by donald73d on 2011-11-01
Under Windows I have used Norton Ghost and Windows 7 full backup to make full and incremental copies of my C drive.  What are my options under Linux?  Also my backup harddrive is a Startech external RAID 1 box accessed via ESATA.  The RAID part is completely within within the box I believe.  I do have SteelVine Manager installed under windows for it, but I believe that only provides management, not access.

---

### Post by 2F4U on 2011-11-01
Of course, that depends on your needs. Some GUI backup tools are
- Back in Time
- Déjá Dup
- duplicity

If you intend to clone entire partitions you could use 
- CloneZilla
- SystemRescueCD
__

---

### Post by mjuhasz on 2011-11-01
In Ubuntu 11.10 **Deja-Dup** is included by default. It's not easy to browse the archive since it uses an opaque format for files stored in your backup location. It is well maintained, nicely integrated into the system and proved to be reliable for me.
Before Deja-Dup I used **Back In Time**. The backup is done by taking snapshots of a specified set of directories using rsync. It's very easy to browse the backups. I have always been happy with it. It is a bit more technical than Deja Dup. It's in the repositories so you can install it from the Ubuntu Software Center.

In case you need to backup the whole system you can check out **Partimage** that you can easily run from SystemRescueCd which is a Linux system rescue disk.

For more information you can check the [Ubuntu backup wiki page]("https://help.ubuntu.com/community/BackupYourSystem").

---

### Post by Mark Phelps on 2011-11-01
Unless they fixed it, Partimage does not handle Ext4 partitions (from what I last recall).

Clonezilla is actually the closest to what GHOST did -- with one exception: You can not mount the images and browse them.  But, it does make complete images of partitions and/or entire drives.  So, it's a good tool for complete backups and restores.

---

