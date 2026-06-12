---
title: "Recover from backup. Can't find HD (wrong UUID)"
date: 2010-08-31
forum: General Help
---

### Post by carandraug on 2010-08-31
Hi

I rsync the filesystem where I have my server to another HD. Now, when I try to boot I'm dropped at initramfs with an error. It looks like it's still looking for the root in the previous HD even tough I already changed /etc/fstab. It says it can't find the device with a certain UUID, and that UUID is from the previous HD.

Here's the full details:

[LIST]
[*]I'm running Ubuntu server 10.04
[*]It has 2 hard drives. Every night it backups one to another with the command ```
rsync --archive --one-file-system --hard-links --numeric-ids --delete
```
[*]I moved the HD where I have the backup to another machine and rsynced them with the same command
[*]I then changed /etc/fstab in the new machine. I also installed Grub on it
[*]When I boot in the new machine I get a error about not finding root. It says that a device is not present. It says the UUID of the device is looking for, and it's the UUID of the first HD.
[/LIST]

I thought I only had to change /et/fstab but seems I am wrong. Any help is appreciated

---

### Post by lmarmisa on 2010-08-31
I do not recommend to use rsync for a full backup of your machine. The result will be always a failure.

Why?. Because your system is not stopped during the backup and the data stored will be inconsistent.

The full backup has to be done with the system in "shut-down" mode.

So a backup Live CD is the best and only solution for a full backup. 

According to my experience, I recommend to use [Clonezilla]("http://www.clonezilla.org/") for a full backup. It works great both cloning disks/partitions or saving/restoring images of disks/partitions. Clonezilla Live runs from a Live CD or a pendrive. Download the stable Debian-based version.

Use rsync every night for a backup of your user files (photos, music, etc) if you wish but not for the backup of the full machine.

Kind regards,

Luis

---

### Post by carandraug on 2010-08-31
I don't have any users on the machine. There's no photos or movies or personal documents to backup. I'm backing up my lab server which means a svn server, a wiki, a MySQL database and soon a samba share. The files are spread all over the filesystem and I can't shut it down everyday for the backup.

Even if I could, that doesn't solve my problem which is to make Linux boot from that HD.

But thanks nonetheless.

---

### Post by redmk2 on 2010-09-01
> **carandraug said:**
> I don't have any users on the machine. There's no photos or movies or personal documents to backup. I'm backing up my lab server which means a svn server, a wiki, a MySQL database and soon a samba share. The files are spread all over the filesystem and I can't shut it down everyday for the backup.

Even if I could, that doesn't solve my problem which is to make Linux boot from that HD.

But thanks nonetheless.

Change the new partition to the old UUID.  See [**_here_**]("http://nixcraft.com/shell-scripting/948-change-uuid-ext3-partition.html").

---

### Post by lmarmisa on 2010-09-01
> **carandraug said:**
> I don't have any users on the machine. There's no photos or movies or personal documents to backup. I'm backing up my lab server which means a svn server, a wiki, a MySQL database and soon a samba share. The files are spread all over the filesystem and I can't shut it down everyday for the backup.

Even if I could, that doesn't solve my problem which is to make Linux boot from that HD.

But thanks nonetheless.

I understand your comment but you should think a different strategy for the daily backups.

IMHO, you have to be sure that if your main hard disk (or your complete server) is broken, you will be able to recover your server in a short time. But I seriously doubt that it could be done with your full backup. If your backuped data are inconsistent, you will need a lot of time to recover your system and, in the worse case, this task will be completely impossible.

Consider a better strategy. Try to install a mirror of your server (no problem if this is a different model of computer; even an old computer could be acceptable). Install the same Ubuntu server version and the same programs there (mysql, apache, svn server, etc). The applications installed in your server very rarely change. So,  you do not need to waste your time with the administration of this second computer.

Now, you have to create some scripts for the daily backup of your applications data. I do not know the detalis of your programs, but probably more than 95% of these data will be stored by the database MySql. So, you will need a script for its daily backup. 

You can see here a couple of examples about daily backups of MySql:

[http://www.websitepublisher.net/article/mysql-backup/](http://www.websitepublisher.net/article/mysql-backup/)

[http://www.debianhelp.co.uk/mysqlscript.htm](http://www.debianhelp.co.uk/mysqlscript.htm)

These are only the two first results of a Google search.

Consider to extend this strategy to other dynamic configuration data or directories that are able to change daily (/var/www?, samba shared dirs).

The last step is to verify that, if you recover a daily backup in your mirror server, this server is able to offer the same service than the main server.

I think that the new strategy is not very difficult to implement.

In relation with your first question, it is possible that you need to update your grub file configuration because the old UUID is still in this file. But I think that this is only your first problem with your rsync backup. Consider to modify your strategy.

---

### Post by carandraug on 2010-09-01
> **lmarmisa said:**
> In relation with your first question, it is possible that you need to update your grub file configuration because the old UUID is still in this file. But I think that this is only your first problem with your rsync backup. Consider to modify your strategy.

You were right. I also needed to change the grub conf files. Not too hard. Just followed the [chroot method in the ubuntu documentation for Grub2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"). Now I'm having a problem when shutting down. It hangs at

```
* Stopping Likewise DCE/RPC Endpoint Mapper: dcerpcd 
```

Thanks for the links. I better start looking into an alternatives backup method.

---

