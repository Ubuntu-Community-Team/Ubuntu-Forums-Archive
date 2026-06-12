---
title: "Will this system backup strategy work?"
date: 2010-02-21
forum: General Help
---

### Post by ticket on 2010-02-21
Here's a possible method for backing up your system disc and keeping it up to date.

-  When you're happy the system is working ok, clone the system disc using the 'dd' command.

- From then on, do regular backups using rsync to capture package updates, etc. To do this, I believe you would need to boot from a live disc, and then run something like:

sudo rsync  -avx --delete /  /media/SystemBackup  
                          ^^^^^
                          Not quite right, see later posts


The first folder ref '/' is the system disc root folder, the second is where the backup disc is mounted.

The idea of using rsync is that it should be quicker than running dd again (esp. if the disc is big - hard to find small discs these days).

I don't plan to dual boot with Windows.

Will the rsync work?  
If using it with sudo, will it muck up any file permissions?

---

### Post by SecretCode on 2010-02-21
Hmm. The basic idea seems fine, but

- when you boot from a live CD, / is not the root of the OS you're trying to back up - you'd need /dev/sda1 or /dev/sda5 or whatever
- if you had /home or anything mounted on a different volume you would have to add it explicitly (the -x option limits it to one volume - and you definitely need this)
- even with sudo, you might not have read permissions on every file (/home/user/.gvfs can be a problem)


rsync -a should preserve all file permissions, don't see a problem there.

---

### Post by ticket on 2010-02-25
Hi Secret,

> when you boot from a live CD, / is not the root of the OS you're trying to back up - you'd need /dev/sda1 or /dev/sda5 or whatever

I think you may be right there!

But I don't understand how  /home/user/.gvfs  might be a problem.

Btw, I keep a basic home folder on my system disc to hold user configurations.  All my other data (docs, music, videos, etc) are on a separate data disc drive that gets backed up to an external one (via a USB connection) using rsync (no need for a live disc in that case).

---

### Post by ticket on 2010-04-25
Ah, I've found that /home/user/.gvfs has weird permissions, such that even root can't move it!  

Apparently this folder is created by the network bits.  However, there are proposals to not create it in user home, because of the backup issues it causes.

---

### Post by ticket on 2011-06-14
The correct command to use is:

```
  sudo rsync -avx --delete /media/SYSTEM/ /media/SYSTEMBAKUP
  ..........................(source).........(dest)
```

where SYSTEM is the volume name of the source disk
and SYSTEMBAKUP is the volume name of the destination disk.

More at:
[http://ubuntuforums.org/showthread.php?t=1679827&page=2](http://ubuntuforums.org/showthread.php?t=1679827&page=2)

---

