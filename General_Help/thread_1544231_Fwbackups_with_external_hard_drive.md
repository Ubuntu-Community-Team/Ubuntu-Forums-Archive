---
title: "Fwbackups with external hard drive"
date: 2010-08-02
forum: General Help
---

### Post by sambody on 2010-08-02
Hi. 

I want to backup my documents, using **Fwbackups**, on an external hard drive (a LaCie Ethernet Disk mini). But I can't seem to access that drive from FWbackups.

As a first test, I tried a One-time backup (to backup some of my personal folders).

Using Nautilus file manager, I access the external hard drive simply by going to Network, then to "Edmini FTP" or to "EDmini SMB". 

But when I need to pick a destination folder in Fwbackups, I can't seem to find the external hard drive. 
I tried "local folder", then Browse, but Network doesn't appear. (Can I find it somewhere else?)
I tried "local folder", then copy pasted the location from Nautilus ([ftp://edmini.local/](ftp://edmini.local/)) but that didn't work - I get the red button, and when I do try the backup, I get 
"ERROR : The destination folder `[ftp://edmini.local/share/sam/](ftp://edmini.local/share/sam/)' could not be created: [Errno 2] No such file or directory: 'ftp://edmini.local/share/sam/'"

So how do I choose my external hard drive as destination ? 
I have a feeling there is a very simple answer to this...

Thanks

EDIT: in this thread, I explain how I configured Samba sharing, make the external hard drive writeable, and use rsync with it (by owning the share)

---

### Post by sambody on 2010-08-09
It's getting better. It is a SAMBA problem, it seems. Now the external hard disk, as a Samba share, is accessible but not writable.

Using the guide here: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
I have done the following steps:

******* start *******

$ gksu gedit /etc/samba/user
In that file I have added username and password of the share

Made read only:
$ sudo chmod 0400 /etc/samba/user 

Created directory where I wanted to mount my shares
$ sudo mkdir /media/samba_share

Edited file to auto mount
$ sudo cp /etc/fstab /etc/fstab.bak
$ gksu gedit /etc/fstab
Added the line:
//192.168.1.101/backupcathsam  /media/samba_share  cifs  credentials=/etc/samba/user,noexec  0 0

******* end *******

I have mounted the share without rebooting:
$ sudo mount /media/samba_share

Now 
[LIST]
[*]the EDmini files are available through /media/samba_share in Open dialogs of FWbackups (or Firefox or any other app), 
[*]but they are READ ONLY. I can access the share through Nautilus, but again, I CAN NOT WRITE on it.
[/LIST]

On the other hand, when rebooting, the Samba share doesn't show up. [edit: when rebooting, the hard disk was not running - that's why it didn't show up] So I go to Places > Network, I choose EDmini SMB, and 
[LIST]
[*]I can access it with Nautilus, and it is WRITABLE. 
[*]But I can not access it via Open dialogue of FWbackups (or Firefox etc) - /media/samba_shared is empty
[/LIST]

So depending on how I access/mount it, the share is writable or not.
How can I make the share Writable AND accessible through /media/samba_shared ?

(ps: I can access and write on the Samba share using Windows XP, running in Virtualbox)

Thanks

---

### Post by sambody on 2010-08-09
Getting closer. I figured out how to make it writable, after reading this tutorial: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534).

I did
```
$ gksu gedit /etc/fstab
```
In the file I replaced 
```
//192.168.1.101/backupcathsam  /media/samba_share  cifs  credentials=/etc/samba/user  0 0
```
with
```
//192.168.1.101/backupcathsam  /media/samba_share  cifs  credentials=/etc/samba/user,iocharset=utf8,file_mode=0777,dir_mode=0777  0 0
```
so that the mount is writable

Then
```
$ sudo umount /media/samba_share
```
```
$ sudo mount /media/samba_share
```
to mount it again, and now I can access it in Nautilus, and in FWbackups, and I can write on the share.

Great!

Now the problem that I'm encountering:
When I try a one-time backup with FWbackups (with option "copy files and folder"), I get an error message, and folders are copied, but not files.

The error:

```
Aug 09 23:04:03 :: INFO : Starting one-time backup operation
Aug 09 23:04:03 :: ERROR : Error(s) occurred while backing up path ''/home/sam/Backups services''.
Please check the error output below to determine if any files are incomplete or missing.
Aug 09 23:04:03 :: ERROR : Output:
Return value: 23
stdout: 
stderr: rsync: failed to set times on "/media/samba_share/sam/Backups services/Backup-OneTime-2010-08-09_23-04/home": Operation not permitted (1)
rsync: failed to set times on "/media/samba_share/sam/Backups services/Backup-OneTime-2010-08-09_23-04/home/sam": Operation not permitted (1)
rsync: failed to set times on "/media/samba_share/sam/Backups services/Backup-OneTime-2010-08-09_23-04/home/sam/Backups services": Operation not permitted (1)
rsync: failed to set times on "/media/samba_share/sam/Backups services/Backup-OneTime-2010-08-09_23-04/home/sam/Backups services/Delicious": Operation not permitted (1)
rsync: failed to set times on "/media/samba_share/sam/Backups services/Backup-OneTime-2010-08-09_23-04/home/sam/Backups services/Gmail": Operation not permitted (1)
rsync: failed to set times on "/media/samba_share/sam/Backups services/Backup-OneTime-2010-08-09_23-04/home/sam/Backups services/Other": Operation not permitted (1)
rsync: failed to set times on "/media/samba_share/sam/Backups services/Backup-OneTime-2010-08-09_23-04/home/sam/Backups services/Wordpress": Operation not permitted (1)
rsync: mkstemp "/media/samba_share/sam/Backups services/Backup-OneTime-2010-08-09_23-04/home/sam/Backups services/Delicious/.delicious-20090825.htm.VKybmm" failed: Operation not permitted (1)
rsync: mkstemp "/media/samba_share/sam/Backups services/Backup-OneTime-2010-08-09_23-04/home/sam/Backups services/Delicious/.exportDelicious03112005.htm.iBxz16" failed: Operation not permitted (1)
rsync: mkstemp "/media/samba_share/sam/Backups services/Backup-OneTime-2010-08-09_23-04/home/sam/Backups services/Gmail/.backup contacts google 2009 09.csv.21RvOR" failed: Operation not permitted (1)
rsync: mkstemp "/media/samba_share/sam/Backups services/Backup-OneTime-2010-08-09_23-04/home/sam/Backups services/Gmail/.backup google contacts - format google 05 2010.csv.liTXHC" failed: Operation not permitted (1)
rsync: mkstemp "/media/samba_share/sam/Backups services/Backup-OneTime-2010-08-09_23-04/home/sam/Backups services/Other/.firegestures-2009-06-17.sqlite.QNuSGn" failed: Operation not permitted (1)
rsync: mkstemp "/media/samba_share/sam/Backups services/Backup-OneTime-2010-08-09_23-04/home/sam/Backups services/Wordpress/.backup database samplify wordpress 08 2006.txt.XbHSJ8" failed: Operation not permitted (1)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]
Aug 09 23:04:04 :: INFO : Finished one-time backup
Aug 09 23:04:04 :: INFO : Canceling the current operation!
```

Does anyone know what is happening and how I can solve this ?

---

### Post by sambody on 2010-08-24
I have found the solution, after reading a bunch of forum threads and tutorials. I needed to use UID, **so that I own the files on the mounted filesystem**, not just being able to read/write.

So in fstab, I have written
```
//192.168.1.101/backupcathsam  /media/samba_share  cifs  credentials=/etc/samba/user,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=sam  0 0
```

Note the **uid=sam** that was added. "sam" being my Linux username.

Conclusion: it was not a FWbackups problem, and it was not a Samba problem, it was a rsync issue.

Now rsync doesn't complain anymore, and I can use backup tools that use rsync, like Fwbackups or LuckyBackups.


Finally !

---

