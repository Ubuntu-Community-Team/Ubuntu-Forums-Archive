---
title: "updatedb.mlocate running constantly - never stops"
date: 2009-08-18
forum: General Help
---

### Post by MountainX on 2009-08-18
I am running a fresh install of Jaunty. The updatedb.mlocate process is running all the time. It never stops unless I reboot (which I prefer not to do for months).

I would like to not have updatedb.mlocate running all the time. It could run nightly if it finishes in an hour or less. Otherwise, I will run it weekly (assuming it finishes in a reasonable time).

I have a 150 GB Raptor HDD, and all my main directories under /home are on an NFS mount (see info below). I have several other mounted file systems and they are mounted in different places (to make the path on my machine match the path on the server so symlinks work correctly).

The content of my /etc/updatedb.conf are:
```
PRUNE_BIND_MOUNTS="yes"
# PRUNENAMES=".git .bzr .hg .svn"
PRUNEPATHS="/tmp /var/spool /media"
PRUNEFS="NFS nfs nfs4 rpc_pipefs afs binfmt_misc proc smbfs autofs iso9660 ncpf$

```The contents of my /etc/cron.daily/mlocate  are:
```

#! /bin/bash

set -e

[ -x /usr/bin/updatedb.mlocate ] || exit 0

if which on_ac_power >/dev/null 2>&1; then
    AC_POWER=0
    on_ac_power >/dev/null 2>&1 || AC_POWER=$?
    if [ "$AC_POWER" -eq 1 ]; then
    echo >&2 "On battery power, not running today."
    exit 1
    fi
fi

##

LOCKFILE="/var/lib/mlocate/daily.lock"

trap "rm -f $LOCKFILE" EXIT

if [ -e "$LOCKFILE" ]; then
    echo >&2 "Warning: $LOCKFILE present, not running today."
    exit 1
else
    touch "$LOCKFILE"
fi

##

# See ionice(1)
if [ -x /usr/bin/ionice ] &&
    /usr/bin/ionice -c3 true 2>/dev/null; then
    IONICE="/usr/bin/ionice -c3"
fi

$IONICE /usr/bin/updatedb.mlocate
```

examples of my mounted file systems are:
```
/backups
/shared
/home/myuser/Documents
/home/myuser/Pictures
/home/myuser/Music
```

Here is a typical entry from /etc/fstab:
```
10.10.1.1:/home/myuser/Documents /home/myuser/Documents nfs auto,rw,rsize=8192,wsize=8192,hard,intr 0 0
```This is what iotop usually shows:
```
Total DISK READ: 0 B/s | Total DISK WRITE: 38.69 K/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO<    COMMAND                
27877 root           0 B/s   38.69 K/s  0.00 %  0.00 % updatedb.mlocate
```

I appreciate any suggestions on how to stop mlocate from running all the time.

---

### Post by MountainX on 2009-08-19
anyone have suggestions? mlocate never stops running!

---

### Post by DaithiF on 2009-08-20
Hi,
Your /etc/updatedb.conf looks like it might be truncated...the PRUNEFS line for me is:
```
PRUNEFS="NFS nfs nfs4 rpc_pipefs afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf"

```

The inclusion of nfs in that list should cause updatedb to skip your nfs-mounts by the way, which shouldn't leave very much work for updatedb to do, so I would have expected it to finish pretty quickly.

---

### Post by MountainX on 2009-08-20
> **DaithiF said:**
> Hi,
Your /etc/updatedb.conf looks like it might be truncated..

The inclusion of nfs in that list should cause updatedb to skip your nfs-mounts by the way, which shouldn't leave very much work for updatedb to do, so I would have expected it to finish pretty quickly.

Thank you. My /etc/updatedb.conf is correct. The truncation is only the result of the way I copied and pasted. Here is the actual file:
```
cat /etc/updatedb.conf
PRUNE_BIND_MOUNTS="yes"
# PRUNENAMES=".git .bzr .hg .svn"
PRUNEPATHS="/tmp /var/spool /media"
PRUNEFS="NFS nfs nfs4 rpc_pipefs afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf"

```

I also expected all my nfs-mounts would be skipped on the basis of this config; however, something is wrong somewhere. Do you have any suggested troubleshooting steps?

---

### Post by DaithiF on 2009-08-20
I would suggest running it manually in a terminal , and with the -v option so that you can see what its doing.  The -v option should make it output the paths as it is scanning them, so you can maybe see what its doing for such a long time.  Pipe the output into tee to save it to a file for inspection later too.

```
sudo updatedb.mlocate -v | tee updatedb.log
```

---

### Post by MountainX on 2009-08-20
Is there a safe/proper way to terminate the currently running mlocate process other than to kill it? Is killing it while it is running OK?

EDIT: also, what is the recommended way to remove it from cron? Just delete mlocate from /etc/cron.daily?

---

### Post by DaithiF on 2009-08-20
yes, you can just kill it.  (The worst that could happen is that its database fiile gets corrupted, in which case you could just delete it and it will happily recreate it next time it runs)

and yes, you could just remove that file from cron.daily.  Or you might want to consider moving it to cron.weekly.

But I'm sure there must be a good reason why its running for so long, (a 150gb disk should NOT require a lengthy runtime), so I'd be hopeful we'll find the reason by running it in verbose mode.

---

### Post by DaithiF on 2009-08-20
actually, a neater way to kill it may be to delete its lockfile:
```
sudo rm -f /var/lib/mlocate/daily.lock
```
since it has a trap to detect that & exit.

If you have killed it manually you'll need to remove the lockfile like above before running it again manually.

---

### Post by MountainX on 2009-08-20
no luck killing mlocate...
```
$ pgrep mlocate
27871
$ sudo kill -9 27871
$ pgrep mlocate
27871
```EDIT: just read your post about the lock file. I'll do that now. Thanks.

EDIT #2:
```

$ sudo rm -f /var/lib/mlocate/daily.lock
$ pgrep mlocate
27871
$ cat /var/lib/mlocate/daily.lock
cat: /var/lib/mlocate/daily.lock: No such file or directory

```mlocate continues to run...

EDIT #3:
I removed the cron.daily file and rebooted.
mlocate is not running upon reboot (it didn't start up right away anyway, but I assume without the cron file it will not start this time).

next I will run
```

sudo updatedb.mlocate -v | tee updatedb.log

```

---

### Post by MountainX on 2009-08-20
tee doesn't seem to be in the Ubuntu repos...

OK, so I just did this:
$ sudo updatedb.mlocate -v > updatedb.log
$ tail -f updatedb.log 

result - updatedb.mlocate ran for about 2 seconds and finished. (I really didn't even need tail.) Here's the output:

$ tail -f updatedb.log 
/var/log/installer/initial-status.gz
/var/log/installer/lsb-release
/var/log/installer/partman
/var/log/installer/status
/var/log/installer/syslog
/var/log/installer/cdebconf/questions.dat
/var/log/installer/cdebconf/templates.dat
/var/log/news/news.crit
/var/log/news/news.err
/var/log/news/news.notice

It seems the cron script that starts updatedb.mlocate could be a problem... I'm just guessing...

EDIT: I installed Ubuntu updates (new kernel), rebooted and ran updatedb.mlocate manually again. It finished in about 2 seconds (or less) again. But this time there were 197,970 new files indexed. So it was really fast!

I cannot see any problem with updatedb.mlocate itself. Any ideas what the problem could be?

---

### Post by DaithiF on 2009-08-20
ok, so the only theory I can put forward as to why it runs 'forever' under cron is to do with ionice.  

When run under cron, updatedb.mlocate gets run under ionice -c 3, which basically says only give updatedb.mlocate a chance to do its IO when nothing else on the system is doing io, and hasn't been for some defined period.  When you ran iotop you saw a data-write rate of something like 30K per second, which is a ludicrously low rate, but which might make sense as an average if it is writing its data over a very very long time, and that very very long time is because its not getting any chance to actually do its IO because its not getting any window due to ionice.

So the upshot of all this is ... try just removing the $IONICE prefix in your cron tab
```
$IONICE /usr/bin/updatedb.mlocate
```
to
```
/usr/bin/updatedb.mlocate
```

---

### Post by MountainX on 2009-08-20
Thank you for your explanation and suggestion. I will test it with IONICE removed.

---

### Post by MountainX on 2009-08-25
> **MountainX said:**
> tee doesn't seem to be in the Ubuntu repos...

OK, so I just did this:
$ sudo updatedb.mlocate -v > updatedb.log
$ tail -f updatedb.log 

result - updatedb.mlocate ran for about 2 seconds and finished. (I really didn't even need tail.) Here's the output:

$ tail -f updatedb.log 
/var/log/installer/initial-status.gz
/var/log/installer/lsb-release
/var/log/installer/partman
/var/log/installer/status
/var/log/installer/syslog
/var/log/installer/cdebconf/questions.dat
/var/log/installer/cdebconf/templates.dat
/var/log/news/news.crit
/var/log/news/news.err
/var/log/news/news.notice

It seems the cron script that starts updatedb.mlocate could be a problem... I'm just guessing...

EDIT: I installed Ubuntu updates (new kernel), rebooted and ran updatedb.mlocate manually again. It finished in about 2 seconds (or less) again. But this time there were 197,970 new files indexed. So it was really fast!

I cannot see any problem with updatedb.mlocate itself. Any ideas what the problem could be?

For the last 4 days I have been using my computer without mlocate in /etc/cron.daily/. I moved the file to /etc/cron.inactive/ (a directory I made). My original problem has not recurred, so it is clear that the problem was caused by cron running /etc/cron.daily/mlocate. 

Today, just now, I manually executed this:
```
/etc/cron.inactive$ sudo ./mlocate
```

To my surprise, it ran and completed with no problems, very much like my other manual tests above. It took just a few seconds to finish and, while running, iotop showed appropriately high IO rates.

So that leads to the conclusion that the problem occurs only when the mlocate script is called by cron.

What should I try next?

---

