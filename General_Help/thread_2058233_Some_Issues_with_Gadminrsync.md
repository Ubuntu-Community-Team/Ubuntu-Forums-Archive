---
title: "Some Issues with Gadminrsync"
date: 2012-09-15
forum: General Help
---

### Post by Quarkrad on 2012-09-15
Newbie running 12.04 and running gadminrsync for backup.  I have some troubles with my pc not shutting down/taking a long time. I have a script in etc/init.d that runs rsync.  This script/gadminrsync has been running brilliantly for a number of years. I have been running gadmin just my home folder onto a 2nd backup HD that I delete each time I do a (testing) manual run.  At the begining of my Gadminrsync Backup Progress tab I get:
[B]
Backup operation starting, please wait...

sending rsync: readlink_stat("/home/dad/.gvfs") failed: Permission denied (13)
incremental file list
dad/
dad/.ICEauthority
dad/.Xauthority
dad/.apport-ignore.xml
dad/.bash_history
dad/.bash_logout
dad/.bashrc
dad/.conky_start.sh
dad/.dmrc
etc
etc[/B]

Is this f**ailed: Permission denied (13)** statement an issue as it appears the backup is taking place?

At the bottom of my Gadminrsync Backup Progress tab I get:

[B]Nrsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9]
umber of files: 14626
Number of files transferred: 12452
Total file size: 33.86G bytes
Total transferred file size: 33.86G bytes
Literal data: 33.86G bytes
Matched data: 0 bytes
File list size: 385.75K
File list generation time: 0.001 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 33.86G
Total bytes received: 245.20K[/B]

So not all files are being transferred and there is an error code.  Any advice on what to do now much appreciated.

---

### Post by LewisTM on 2012-09-15
No worries. 
The thing is that the ~/.gvfs directory is a mount point to remote filesystems. 
See the output of the [FONT="Courier New"]mount[/FONT] command, it should contain the following entry:
> gvfs-fuse-daemon on /home/dad/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dad)
.gvfs should never be backed up and in fact has restricted permissions that don't play well with rsync. You can just ignore it or explicitly exclude it from backups.

Easiest would be to add the -x switch to your rsync command. I'm not sure if it's possible to customize the command with gadminrsync but it's definitely possible with related rsync-based backup programs like LuckyBackup or GRsync.

The -x switch restricts rsync to one filesystem and ignores mount points. That can also be useful if you have NFS mount points inside you home directory.

Cheers!

---

### Post by Quarkrad on 2012-09-15
That explains it - thank you. I'm running Meld to see if I can find out what files were not copied across.

---

