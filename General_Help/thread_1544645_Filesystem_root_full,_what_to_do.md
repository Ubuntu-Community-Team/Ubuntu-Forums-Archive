---
title: "Filesystem root full, what to do?"
date: 2010-08-02
forum: General Help
---

### Post by mamboze on 2010-08-02
Hi, 
I installed sbackup yesterday and followed the instructions here:

[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

selected the custom backup settings without changing any defaults.

Today, I got a filesystem root warning of limited disk space. 

Using a command from another thread
[http://ubuntuforums.org/showthread.php?t=1515270](http://ubuntuforums.org/showthread.php?t=1515270) , I got:
```

~ $ sudo du -ak --exclude=/home/* / 2> /dev/null | sort -n | tail -30
[sudo] password for roy: 
113508	/usr/lib/jvm/java-6-sun-1.6.0.20/jre
113544	/usr/lib/jvm/java-6-sun-1.6.0.20
126956	/usr/share/icons
131844	/usr/share/doc
134560	/opt/Adobe/Reader9/Reader/intellinux
135460	/usr/lib/jvm/java-6-openjdk
136800	/opt/Adobe/Reader9/Reader
148236	/opt/Adobe/Reader9
148240	/opt/Adobe
148244	/opt
176132	/usr/lib/openoffice/basis3.2/program
212168	/usr/bin
217020	/usr/lib/openoffice/basis3.2
217800	/usr/lib/openoffice
249032	/usr/lib/jvm
256564	/usr/src
262904	/var/lib
291668	/lib/modules
340344	/lib
582740	/var/cache/apt/archives
610892	/var/cache/apt
630740	/var/cache
1298412	/usr/share
1635964	/usr/lib
3426308	/usr
8026296	/var/backup/2010-08-03_04.30.04.832754.prospero.ful/files.tgz
8032944	/var/backup/2010-08-03_04.30.04.832754.prospero.ful
8032948	/var/backup
8939872	/var
12960392	/

```


I've checked gparted and it says 0.0 unused on /

What can I do to correct this?

TIA

---

### Post by CharlesA on 2010-08-02
Delete or move the backups in /var/backup/

How big is the / partition?

---

### Post by mamboze on 2010-08-02
Hi CharlesA

I've removed the /var/backup files and this has freed up 7.66Gb of 9.31 total on / 

I've now removed sbackup as this (or my configuration of it) seems to be the problem. I'm a bit wary of reinstalling it as I pretty sure I didn't change any of the default settings. So I'll look further for a backup arrangement, maybe tar. 

Thank you, your help is much appreciated.

BTW I can't find the thanks button, is it still available?

---

### Post by CharlesA on 2010-08-02
I don't know of any thanks button, but there is a place to mark the thread as solved: Thread Tools > Mark as Solved.

You can probably tell sbackup to save the backup elsewhere, but I don't know for sure, since I don't use it.

---

### Post by libssd on 2010-08-02
For what purpose were you intending the backup? If to create a recoverable system image (i.e., for restoring your system to a pre-disaster state after something has gone wrong), I recommend Remastersys: [http://geekconnection.org/remastersys/](http://geekconnection.org/remastersys/)

Documentation is a little sketchy, but once you manage to install it, remastersys requires almost no thinking for either a backup or restore -- a critical attribute. You can exclude specific directories, if you wish. Remastersys has several times saved my bacon from Linux experiments gone wrong.

For "ordinary" data files (e.g., documents, images, music, etc.) I just copy them to another device.

---

### Post by CharlesA on 2010-08-02
> **libssd said:**
> For "ordinary" data files (e.g., documents, images, music, etc.) I just copy them to another device.

I just rsync any user data to another device. I can always reinstall the OS is something goes haywire.

---

### Post by mamboze on 2010-08-03
@libssd
I had intended to simply backup files without wanting to create a system image. I think I'll follow this way for starters anyhow. It has the virtue of being pretty straightforward. But Rmastersys looks interesting and I may give it a go later.  

@CharlesA

What files do you copy with rsync? sbackup default copies /var/, /home/, /usr/local/ and /etc/. This would include configuration files like /etc/fstab but are there others elsewhere which should be in a backup? 

Thanks to you both for your helpful suggestions

---

