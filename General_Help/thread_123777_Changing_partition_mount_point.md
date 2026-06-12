---
title: "Changing partition mount point"
date: 2006-01-30
forum: General Help
---

### Post by glave on 2006-01-30
My current partitioning is as follows:

/dev/md0        /
/dev/md1        /usr/local
/dev/md2        swap


I need to change /dev/md1 from /usr/local to /var

I'm not really sure how to go about this? The server is up and running, though I can bring it down if need be, but in testing, trying to umount /usr/local, I'm told the device is busy.... How could I go about this?

---

### Post by aysiu on 2006-01-30
You need a live CD.
Knoppix would come in handy.

---

### Post by dcstar on 2006-01-31
[QUOTE=glave]My current partitioning is as follows:

/dev/md0        /
/dev/md1        /usr/local
/dev/md2        swap


I need to change /dev/md1 from /usr/local to /var

I'm not really sure how to go about this? The server is up and running, though I can bring it down if need be, but in testing, trying to umount /usr/local, I'm told the device is busy.... How could I go about this?[/QUOTE]
With great difficulty, you want to work on directories which are used by the running system (/usr/local and /var) and it is almost impossible to find an operating mode that won't use these (even Single User would).

The advice to boot off another disk is probably your best bet.

---

### Post by glave on 2006-01-31
Duh... a live cd. Why didn't I think of that?

So, boot off the live cd, mount my partitions, edit fstab, copy files from the /usr/local partition to the /usr/local directory on the other drive.  Done?

---

### Post by glave on 2006-01-31
Arg!

I just got through doing as I listed above, I rebooted, everything looked great, but mysql failed to load. I tried loading it manually, and this is what I get:

060131 22:10:54 Can't start server : Bind on unix socket: Permission denied
060131 22:10:54 Do you already have another mysqld server running on socket: /va
r/run/mysqld/mysqld.sock ?
060131 22:10:54 Aborting

060131 22:10:54 mysqld: Shutdown Complete


Perhaps permissions of some sort?
Any ideas?

---

### Post by glave on 2006-02-01
Seems that something else is failing on bootup. atd?

Starting deferred execution scheduler...  [failed]

What would I be missing here? I booted from a live cd, mounted my / partition in one directory, mounted my /usr/local partition in another. I copied everything from the /usr/local partition mount point into the /usr/local of my mounted / partition. I verified it copied, made a backup dir on the /usr/local partition, moved the files into it, then I copied everything from the /var directory on the / partition into the /usr/local partition. I edited fstab to mount as /var instead of /usr/local and that was it!

---

### Post by Tichondrius on 2006-02-01
^^ yeah, that's pretty much it except you also need to copy all the stuff from the old /var to /dev/md1. So when you boot the live CD and mount /dev/md1 somewhere (e.g. /mnt/md1), you need to copy the old /var to there. Then remove everything from the old /var directory (so it becomes  empty).

Now, next time you boot your system, /dev/md1 will be mounted on /var and will also contain all the files that the old /var used to contain.

---

### Post by glave on 2006-02-01
Exactly. That's what I did, but it seemd when I copied things over, it didn't copy over the permisssions, more specific it looks like my owner and group permissions didn't copy.

Now I'm kinda scratching my head over what to do. I'm not sure what owners/groups I need to have set in /var and /usr/local, but I know my system isn't happy.

I appear to have mysql up and running again, but I'm still getting the deferred scheduler error, and I'm kinda nervous that other things may not be functioning and just not letting me know about it...

---

### Post by glave on 2006-02-01
Does anyone know what the proper ownership/permissions should be on files under /var and /usr/local ?

---

### Post by glave on 2006-02-01
I've parsed through my qmail installation and I believe I've repaired all the permissions it needed, as well as mysql. Can anyone lend any insight on atm (or any other perms I may have not noticed yet..)  ?

---

### Post by jordanm on 2006-02-01
Editing /etc/fstab changes what mounts by default on startup. Or use mount/umount to do it for this session only.

---

### Post by steve.horsley on 2006-02-01
Just a quick note. If you haven't already deleted the original /usr partition, they way to copy it to the new /usr location and preserve all the ownerships and permissions is **cp -a**.

---

### Post by glave on 2006-02-01
Hindsight is 20/20 on that one... :)  I'm still picking through and trying to restore permissions to what they should be, but finding out what they should be has been the challenge!

---

