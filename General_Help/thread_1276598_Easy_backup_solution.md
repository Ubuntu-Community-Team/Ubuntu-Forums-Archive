---
title: "Easy backup solution?"
date: 2009-09-27
forum: General Help
---

### Post by odinb on 2009-09-27
Hi!

Had 2 hard-drives go bad on me recently, they got "infected" with the "click of death".

Since all reviews of hard-drives I've read looking for new ones basically tells me today's hard-drives, while growing tremendously in size, are even worse quality than they used to be, I now feel like I need some easy powerful backup solution before the next hard-drive dies on me, where even the missus can restore individual files.

All my media (videos, music) except my photos I have sitting on a RAID5 set-up (that is getting full, time to upgrade).

My personal documents, photos etc. I have in my /home in a separate partition on the main drive.

Have been looking around looking for an incremental backup tool that does not fill up the backup-drive too fast, and basically everything I read point towards using rsync or rsnapshot. These are however not easy to use for people not used to the terminal.

My wife would like to be able to use this for doing recovery of certain files etc. and she does not know how to use the terminal. Have therefore looked at different powerful(?) GUI-front-ends for rsync

The 2 (3?) most promising solutions with a graphical front-end I have found are FlyBack ([http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)) and TimeVault ([http://www.techthrob.com/2009/03/02/backing-up-in-ubuntu-made-easy-with-timevault-an-in-depth-review/](http://www.techthrob.com/2009/03/02/backing-up-in-ubuntu-made-easy-with-timevault-an-in-depth-review/)), with grsync as a contender ([http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)).

TimeVault probably disqualifies due to the naming convention used, which forces you to use the snapshot browser. I would like to be able to use any file-manager to restore files, if necessary after a total breakdown of a hard-drive.

This leaves me with FlyBack, which has not been updated in a while, or?

Have I missed any GUI-app for doing easy incremental backup and restore?

Any views on these apps?

---

### Post by StuartN on 2009-09-27
> **odinb said:**
> Have I missed any GUI-app for doing easy incremental backup and restore?
Any views on these apps?

I have an icon on my desktop to run some rsync backup commands (**rsync -avh --delete source destination**), which is essentially a one-click duplication of my system on an external hard disk, but it only copies the changes since the last backup. I backup at least weekly, and immediately after doing any valuable work.

Once in a while (before going away on holiday, usually) I make a dated copy of the backup. I have a series of these complete backups going back for years, but I also manually delete the media (video, photos, pictures etc) from the oldest backups to save duplicated space.

Anyone who can find files on the system can find lost files on the backup, and if the system disk failed then an **rsync destination source** would restore it.

---

### Post by SuperSonic4 on 2009-09-27
Why not use a simple cp every now and again. You could also make a bash script and get it to run on startup.

```
#!/bin/bash
#
cp -Rvu '~/Music' '~/Documents' '~/Videos' /mnt/backup
```

-u, --update : copy only when the SOURCE file is newer than the destination file or when the destination file is missing

of course you may add/remove/change any of the source and/or destination folder depending on local setup

---

### Post by chaanakya_chiraag on 2009-09-27
Just follow my tutorial [here]("http://ubuntuforums.org/showthread.php?t=1215609").  Instead of the whole Samba share stuff, just use the mountpoint of the disk instead of /mnt/backup.  Another option would be to UNMOUNT the disk first and then REMOUNT it to /mnt/backup.  Please post if you have any questions or if anything is unclear! 
- Chiraag

---

### Post by Shujah on 2009-09-27
for day to day backups grsync is good. Nothing too fancy but it has a nice simulation option and once paths are set all it takes is a single click to backup. Limitation is that it can be tiresome if the data you want to backup is spread over too many directories (though you can manually 'exclude=stuff' in advanced options).

---

### Post by scouser73 on 2009-09-27
For backing up I use [[COLOR="Red"]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html"), the tutorial shows you how to use it and in my opinion I think it's an excellent program for backing up data.

---

### Post by chaanakya_chiraag on 2009-09-27
The thing is, I've tried using all of these graphical programs and, for me, none of them gave me as much control as I needed.  I just wanted to back up my home directory to a Samba share, and NONE of those programs could even access a network share - very annoying.  That's when I just sat down and created a script that does what I need it to.  Nothing like the command line to give you control!
- Chiraag

---

### Post by odinb on 2009-09-27
Thanks for the responses so far.

@SuperSonic4:

This requires manual intervention, I would prefer an automated solution.
As to run it at startup, I would hardly ever get any backups, since my machine is on 24/7, and is only rebooted for kernel updates and such.


@StuartN & chaanakya_chiraag:
You are absolutely right that command line is the most powerful, but that does not help if your spouse cannot/willnot dedicate the time to learn it.
A GUI-solution is better here.

I also think that this is one of the major reasons for slow/missing broad Linux/Ubuntu adapting, too many standard tasks require you to use a command line, and if it does not, the GUI version is lacking features, is non-obvious or slow to use. Even if you and I are OK with the occasional terminal hacking, the broad majority is not.


Finally ended up trying Back In Time ([http://backintime.le-web.org/](http://backintime.le-web.org/)), seems to do what I need it to, and is very easy to use.
It seems to be better than TimeVault (no special namingconvention) and more updated than FlyBack. It also seems to work better than sBackup.
sBackup does seem to have one (or more) advantage(s), it can backup to remote machines using SSH.

Will see how I end up liking it.

---

### Post by chaanakya_chiraag on 2009-09-28
That's part of the reason I developed a script for backing up your home partition: to help newbies/people who are afraid of the command line. Anyway, glad you found a solution!!
- Chiraag

---

### Post by Darkwing-Duck on 2009-09-28
Here is another good backup solution using rsync. This guide should help you through the process step by step.

[http://gwos.org/udsf/doku.php/software:backup:rsync](http://gwos.org/udsf/doku.php/software:backup:rsync)

---

