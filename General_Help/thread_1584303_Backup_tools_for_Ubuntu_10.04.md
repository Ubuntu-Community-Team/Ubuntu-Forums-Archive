---
title: "Backup tools for Ubuntu 10.04 ???"
date: 2010-09-28
forum: General Help
---

### Post by Robert R on 2010-09-28
Hi I was wondering if anyone can help me with doing backups apart from simple backup config tool. 
Preferably if there is a more advanced gui interface for performing backups in ubuntu. 

Does anyone know of the existence of such a tool ???

---

### Post by CharlesA on 2010-09-28
rsync/grsync.

There's also a few other backup programs (with GUIs)

---

### Post by Robert R on 2010-09-28
Do you mind if i ask what you use mr charles ??

---

### Post by TNT1 on 2010-09-28
I use a combination of Backintime, and remastersys.

---

### Post by HermanAB on 2010-09-29
I use an rsync one liner.

New users are always looking for a backup program as used in Windows.  In Linux, every fancy looking backup program is just an overly complicated front end for rsync.  Soooooo, if you want to save yourself a lot of hassle with complicated backup programs, read the rsinc man page and make yourself a one liner like everybody else does.

However, if you insist on using complicated backup programs, have a look at 'dirvish'.  It is better than most.

---

### Post by DeMus on 2010-09-29
> **HermanAB said:**
>   Soooooo, if you want to save yourself a lot of hassle with complicated backup programs, read the rsinc man page and make yourself a one liner like everybody else does.


So I am the exception again. Because I am not everybody: I use grsync which makes life so much easier.

---

### Post by SaintDanBert on 2010-09-29
If you like **rsync** based backup and restore, and want some help beyond roll-your-own scripting and command line options, consider **LuckyBackup** [ http://luckybackup.sourceforge.net/features.html ]( http://luckybackup.sourceforge.net/features.html ).

It uses the command line tools so you have bare handed access to them if you want.

Because it uses rsync, save sets can be stored anywhere your workstation can reach.

It provides a graphical interface for those routine tasks.  In fact, every backup or restore is called a "task". When you create a backup-task, it will create the corresponding restore-task for you. Armed with a set of tasks, you can "schedule" when they will run.

I learned about LuckyBackup from a commercial mag article (I'll post a link here once I find it again.)  I've enjoyed it ever since.

Enjoy,
~~~ 0;-Dan

---

### Post by Robert R on 2010-09-29
WOW all these sounds grand. Ill give them a try. 
Thanks alot folks. :D

---

### Post by ghostborg on 2010-09-29
FreeFileSync

---

### Post by Megaptera on 2010-09-29
I like a CD/DVD backup created with Remastersys, something solid and off the laptop I can keep safe just in case ....

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by CharlesA on 2010-09-29
> **Robert R said:**
> Do you mind if i ask what you use mr charles ??

I use something like this:

```

#!/bin/bash

SOURCE=/path/to/source
DESTINATION=/path/to/destination

if mountpoint -q $DESTINATION
then
 rsync --archive --itemize-changes --delete $SOURCE --exclude lost+found $DESTINATION
fi

```

My normal script is way more complicated, since it checks to see if my backup drives are already mounted and if they aren't mounts them and runs the backup.

---

### Post by SaintDanBert on 2010-09-29
> **Robert R said:**
> Hi I was wondering if anyone can help me with doing backups apart from simple backup config tool. 
Preferably if there is a more advanced gui interface for performing backups in ubuntu. 

Does anyone know of the existence of such a tool ???

In a prior life, I was Product Manager for a mainframe utility that provided these and related features.While you are researching tools, here is one other thing to think about.

What we call "backup" accomplishes several things.
[list]
[*] **FailSafe** -- makes a copy of files in case there is catastrophic loss of the original information, regardless of whether it is hardware or software error of failure or end-user mistake.
[*] **Archive** -- makes a copy of files for long term storage so that they are available at some time in the (maybe) distant future
[/list]

The terms "failsafe" and "archive" are of my choosing based on years of experience.  

With tera-byte drive costs near $100 USD, the effort to script and manage and tinker efficient and effective copy operations is easily excessive when compared to a TB-drive and wholesale duplication. 

When it comes to that duplication, the **rsync** family of utilities is really hard to beat for all sorts of reasons. Not only do you get a FailSafe copy on your external drive, but you can access individual files and folders an so have an Archive copy at the same time. Of course you need to know which files you have on which copy for your "archive" to be effective, but that is food for a different thread.

Cheers,
~~~ 0;-Dan

---

### Post by CharlesA on 2010-09-29
+1 to Dan.

---

### Post by Wtower on 2010-10-02
Also a quick info: simple backup in ubuntu reps is v0.10.5. If you need the latest version which is 0.11.2 you should add the following repository

```
deb http://ppa.launchpad.net/nssbackup-team/ubuntu lucid main
```

More info and other distros in [https://edge.launchpad.net/~nssbackup-team/+archive/ppa]("https://edge.launchpad.net/~nssbackup-team/+archive/ppa")

Among others, the new version allows multiple profiles and better removeable drive support. Personally I find it a simple and effective backup solution.

Regards

---

