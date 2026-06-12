---
title: "backup to remote, mounted ftp with tar"
date: 2010-03-04
forum: General Help
---

### Post by Turiko on 2010-03-04
I'm trying to make a backup to a remote ftp server. the ftp server is on the same network, and so far i have been able to create a file and add a lot of files. The ftp folder is mounted with curlftpfs. I need this because my server runs off an usb stick, thus creating a local copy is impossible.

These are the commands i used: 

sudo mkdir /remoteftp
sudo curlftpfs 192.168.0.1:60021 -o user=admin:admin /remoteftp
sudo tar cvpzf /remoteftp/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/media --exclude=/mnt --exclude=/sys --exclude=/remoteftp  --directory / /

this works fine, up to the location /cdrom, upon tar gives me this:

tar: Exiting with failure status due to previous errors

/cdrom is an empty folder, as there is no cd currently in there. 

So what exactly is causing tar to lock up? for now, i'm going to go ahead and exclude /cdrom, but i'd really like to know what is causing tar to break. It could happen again later and that could cause me to miss a lot of backups.

EDIT: after another try, i got slightly further, but now tar got stuck and exited when trying to put /vmlinuz in the backup. However, i can not find this folder at all. From what i understand, vmlinuz is the linux kernel, but i do not see how this would cause tar to see a new folder. Another exclude until i can find the cause.

EDIT 2: after the third try, i got a "gzip: stdout: Input/output error" after the archive reached 4 kb. Odd, as the ftp server has plenty of room left.

EDIT 3: fourth try, again a "gzip: stdout: Input/output error", this time at 878 MB. I really don't see why this pops up, as the ftp connection is set to time out after 24 hours, and 500 simultaneous connections allowed. This is the only job using the ftp server.

EDIT 4: fifth try, "tar: Exiting with failure status due to previous errors". This time, /SElinux is the problem.

---

### Post by Turiko on 2010-03-05
bump, anyone have an idea?

---

### Post by lavinog on 2010-03-05
This might help you understand what is going on:
```

ls -l /

```
look at cdrom and vmlinuz...you should see that they are symlinks to other files.

Since it runs off of a usb stick, could you not just boot a live cd and backup the usb stick with dd to an image?  This way recovery would just involve copying that image back on.

---

### Post by Turiko on 2010-03-05
not really, as this system should run for a long time. I'd like to have this update in cron every two days or so, as i host a website and use it as a small security system (in the works).

---

### Post by gmargo on 2010-03-05
Every problem you posted (except the /cdrom one) make it sound like curlftpfs is pretty buggy.  The bug list over here: [http://sourceforge.net/tracker/?group_id=160565&atid=816357](http://sourceforge.net/tracker/?group_id=160565&atid=816357) shows a lot of old unresolved bugs.  Is there any chance you can do it over NFS instead of FTP?

Another idea is to try separating the tar from the gzip.

---

### Post by Turiko on 2010-03-05
It's not really feasible to do it over anything but ftp as the server i use for remote backups uses nothing but ftp.

And how exactly would i separate the tar from the gzip? tar just puts the files into the gzip, correct?

---

### Post by lavinog on 2010-03-05
Why not backup just the data folders on a regular basis...the system files shouldn't change except for updates.  If you make a drive image first...the updates will take care of them selves.

Even if you go through the trouble of backing up the full system...you might find that restoration wont work as expected...you should do a trial run once you decide how you want to approach it.

Also, you can also mount the whole drive on a local system with sftp.  (places>connect to server>ssh...the mount should be located in /home/user/.gvfs/)
It might eliminate some of your issues.

---

### Post by Turiko on 2010-03-05
the problem is that i'm relatively new to linux, and i don't know where the configuration files for my programs are kept. I'd like to just set all the applications back with their config files, or even better: copy all files onto the drive and have a fully functional system again, no reinstalling required.

---

### Post by lavinog on 2010-03-05
> **Turiko said:**
> the problem is that i'm relatively new to linux, and i don't know where the configuration files for my programs are kept. I'd like to just set all the applications back with their config files, or even better: copy all files onto the drive and have a fully functional system again, no reinstalling required.

That is the reason why I recommended making a drive image...You only need to image it once, then backup just the user data files routinely.

Tar is not going to save the boot sector, and many times uuids wont match, making the restored drive unbootable without some work.

I would recommend reading this page:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by Turiko on 2010-03-05
Okay, so i've decided to use sbackup and create an image using Systemrescuecd. What directories should i include so that all my applications and config files are saved?

sbackup includes /var/, /home/, /usr/local/ and /etc/ by default. Will this do the trick?

---

### Post by gmargo on 2010-03-05
> **Turiko said:**
> And how exactly would i separate the tar from the gzip?

What I meant by separating the tar from the gzip was breaking it into two explicit steps like this:
```

tar cvpf /remoteftp/backup.tar
gzip /remoteftp/backup.tar

```You could also try the "B" and "b" options on tar to increase the blocking size.  (Just speculating that bigger block sizes might play better on top of FTP.)

---

### Post by Agent ME on 2010-03-05
> **gmargo said:**
> What I meant by separating the tar from the gzip was breaking it into two explicit steps like this:
```

tar cvpf /remoteftp/backup.tar
gzip /remoteftp/backup.tar

```
That will cause a lot of network activity, because the backup will be sent over the network uncompressed, then sent back over to the system being backed up to be compressed, and sent back!

If you want to split the tar and gzip commands apart, you really should use a pipe.
```
sudo tar cvp --exclude=/proc --exclude=/lost+found --exclude=/media --exclude=/mnt --exclude=/sys --exclude=/remoteftp --directory / / | gzip > /remoteftp/backup.tar.gz

```

---

