---
title: "Backup failed - space eaten up"
date: 2009-10-01
forum: General Help
---

### Post by Xavier71 on 2009-10-01
I have tried to perform a backup using the simple backup config (that is in the system -> admin menu).  It failed because I didn't have enough disk space to perform the operation.  That much I do know.  

But what I do not know is whether the file created until now is saved somewhere (and thus eats up about 3 Gb of disk space) or has been deleted once the backup failed.  I did not cancel anything, I only realised the issue once other parts of Ubuntu stopped responding owing to having no space left on my drive!

So I have made more space available for Ubuntu and all seems to work fine, but I have the nagging feeling that some backup file is left behind and I would like to clean the drive!
The question is how??

Whilst at it, how do you do a backup to send the files directly to a USB portable hard drive (already mounted when the operation begin).

Thanks in advance.

---

### Post by drs305 on 2009-10-01
You can search for the failed backup with this command, which will look for any file larger than 1GB:
```
sudo find / -name '*' -size +1G

```

Simplebackup is a common reason partitions fill up - usually because the backup is written to the system partition (/) instead of a backup partition. This is caused because the backup partition was not mounted at the time the backup was started.

To send the backup to another device, you would just designate a back up folder, mount your external USB paritition to that folder, *and make sure that folder is mounted before the backup begins*.

The command above and other methods of finding where lost disk space has disappeared to can be found in the following link:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by Giblet5 on 2009-10-01
```
sudo find / -size +1000M | less
```

That will display every file that's more than a gig or so.

A backup file should be pretty obvious.

Here's how I backup my system. Your mileage will vary.

```
#!/bin/sh

SYSF="/etc/hosts /etc/network /etc/ssh /etc/samba /var/www"

echo "Make sure the USB drive is connected and hit Enter"
read abc

tar cvjf /media/MyBook/backup.tar.bz2 /home $SYSF

exit $?
```

Obviously, I use those cheap-o WD MyBook drives, so you'll have to modify to your own drive path, at least.

---

### Post by Xavier71 on 2009-10-01
Thanks for the tip, found the file!  And also for the pointer to mount the drive before the program starts, which is where things failed last time I think.

---

### Post by Xavier71 on 2009-10-01
Mmm spoke too soon here!!

I have a folder called 'backup' but it is owned by root ... so, how do I remove the files in there (command line?) or how do I change the ownership??

Full path: /var/backup/.../files.tgz

Still new in this business, lots to learn!

---

### Post by drs305 on 2009-10-01
> **Xavier71 said:**
> Mmm spoke too soon here!!

I have a folder called 'backup' but it is owned by root ... so, how do I remove the files in there (command line?) or how do I change the ownership??

Full path: /var/backup/.../files.tgz

Still new in this business, lots to learn!

The safest way is probably to open nautilus with admin rights so you can delete it as 'root'.
```
gksu nautilus /var/backup
```
Navigate to the folder and use SHIFT-DEL to remove the file. If you just use the DEL key it will just recycle the file back to the Trash bin.

You can also use the rm command with "sudo" but a typo could cause you to delete your entire system.

---

