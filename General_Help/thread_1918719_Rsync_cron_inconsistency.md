---
title: "Rsync cron inconsistency"
date: 2012-02-01
forum: General Help
---

### Post by Uejji on 2012-02-01
Hello.

I've spent some time forum and google crawling and haven't seemed to find an answer that fits my specific situation.  Please point me in the right direction if I've overlooked a previous solution to this situation.

I administrate a simple Ubuntu 10.10 Xen VM (probably unrelated to the issue).  I have a simple script in /etc/cron.daily that performs a daily differential backup with rsync.  Here is the script:

```
#!/bin/bash

BACKUPDIR="/backup/"
FIRSTBACK=$( ls "${BACKUPDIR}" | head -n1 )
LASTBACK=$( ls "${BACKUPDIR}" | tail -n1 )
NEWBACK=$( date -d yesterday +%Y.%m.%d-%A )

cp -lr "${BACKUPDIR}/${LASTBACK}" "${BACKUPDIR}/${NEWBACK}"
rsync -ax --delete --exclude="backup" --progress / "${BACKUPDIR}/${NEWBACK}"

rm -rf "${BACKUPDIR}/${FIRSTBACK}"
```

The script runs successfully overnight, but the results are wildly different if the script is run by cron or manually.


2012.01.31-Tuesday is the backup performed in each of the following results.

Cron results:
```
# du -h --max-depth=1 2012.01.3*
4.0K    2012.01.30-Monday/mnt
4.0K    2012.01.30-Monday/dev
16K     2012.01.30-Monday/build
8.0K    2012.01.30-Monday/tmp
6.1M    2012.01.30-Monday/sbin
100K    2012.01.30-Monday/root
4.0K    2012.01.30-Monday/selinux
5.4M    2012.01.30-Monday/bin
816M    2012.01.30-Monday/var
4.0K    2012.01.30-Monday/srv
294M    2012.01.30-Monday/lib
6.2M    2012.01.30-Monday/etc
37M     2012.01.30-Monday/boot
1.6G    2012.01.30-Monday/home
4.0K    2012.01.30-Monday/proc
4.0K    2012.01.30-Monday/opt
558M    2012.01.30-Monday/usr
4.0K    2012.01.30-Monday/lost+found
8.0K    2012.01.30-Monday/media
4.0K    2012.01.30-Monday/sys
3.2G    2012.01.30-Monday

4.0K    2012.01.31-Tuesday/mnt
4.0K    2012.01.31-Tuesday/dev
16K     2012.01.31-Tuesday/build
8.0K    2012.01.31-Tuesday/tmp
4.0K    2012.01.31-Tuesday/sbin
48K     2012.01.31-Tuesday/root
4.0K    2012.01.31-Tuesday/selinux
4.0K    2012.01.31-Tuesday/bin
202M    2012.01.31-Tuesday/var
4.0K    2012.01.31-Tuesday/srv
294M    2012.01.31-Tuesday/lib
6.2M    2012.01.31-Tuesday/etc
37M     2012.01.31-Tuesday/boot
1.6G    2012.01.31-Tuesday/home
4.0K    2012.01.31-Tuesday/proc
4.0K    2012.01.31-Tuesday/opt
558M    2012.01.31-Tuesday/usr
4.0K    2012.01.31-Tuesday/lost+found
8.0K    2012.01.31-Tuesday/media
4.0K    2012.01.31-Tuesday/sys
2.6G    2012.01.31-Tuesday
```

Manual results:
```
# du -h --max-depth=1 2012.01.3*
4.0K    2012.01.30-Monday/mnt
4.0K    2012.01.30-Monday/dev
16K     2012.01.30-Monday/build
8.0K    2012.01.30-Monday/tmp
6.1M    2012.01.30-Monday/sbin
100K    2012.01.30-Monday/root
4.0K    2012.01.30-Monday/selinux
5.4M    2012.01.30-Monday/bin
816M    2012.01.30-Monday/var
4.0K    2012.01.30-Monday/srv
294M    2012.01.30-Monday/lib
6.2M    2012.01.30-Monday/etc
37M     2012.01.30-Monday/boot
1.6G    2012.01.30-Monday/home
4.0K    2012.01.30-Monday/proc
4.0K    2012.01.30-Monday/opt
558M    2012.01.30-Monday/usr
4.0K    2012.01.30-Monday/lost+found
8.0K    2012.01.30-Monday/media
4.0K    2012.01.30-Monday/sys
3.2G    2012.01.30-Monday

4.0K    2012.01.31-Tuesday/mnt
4.0K    2012.01.31-Tuesday/dev
16K     2012.01.31-Tuesday/build
8.0K    2012.01.31-Tuesday/tmp
4.0K    2012.01.31-Tuesday/sbin
52K     2012.01.31-Tuesday/root
4.0K    2012.01.31-Tuesday/selinux
4.0K    2012.01.31-Tuesday/bin
215M    2012.01.31-Tuesday/var
4.0K    2012.01.31-Tuesday/srv
5.0M    2012.01.31-Tuesday/lib
1.3M    2012.01.31-Tuesday/etc
12K     2012.01.31-Tuesday/boot
25M     2012.01.31-Tuesday/home
4.0K    2012.01.31-Tuesday/proc
4.0K    2012.01.31-Tuesday/opt
11M     2012.01.31-Tuesday/usr
4.0K    2012.01.31-Tuesday/lost+found
8.0K    2012.01.31-Tuesday/media
4.0K    2012.01.31-Tuesday/sys
256M    2012.01.31-Tuesday
```

(I have added whitespace between the days to improve readability.)

So, for some reason, rsync thinks that most of the data has changed when run by cron, but when run manually it correctly determines that only a few hundred MB have changed since the previous backup.

I understand there are environmental differences between cron and an interactive shell, but I don't understand how that might cause this situation.  The hard links are created correctly, and if rsync were replacing all of the hard links, the new backup should be over 3GB, not 2.6GB.

I am having to rerun every backup manually in the meantime, which is completely defeating the purpose of having a cron job in the first place.

I hope someone can offer some assistance.

Thanks.

---

### Post by drmrgd on 2012-02-01
I know this is not a fix for your script.  However, you might consider using [rsnapshot ]("http://rsnapshot.org/")for this.  It does exactly what you're trying to script (I think) already.  Maybe the only real difference is the naming, although I have not specifically looked at all of the naming options. 

Anyway, just my two cents until someone with real coding expertise comes along to help you fix the script.

---

### Post by Uejji on 2012-02-01
Thanks for the suggestion.  It looks like it does a lot of the things I want to ultimately do.  I'll look into it more when I have more time to dig into a new backup solution.

In the meantime, I hope I can get this rsync thing figured out.

> **drmrgd said:**
> I know this is not a fix for your script.  However, you might consider using [rsnapshot ]("http://rsnapshot.org/")for this.  It does exactly what you're trying to script (I think) already.  Maybe the only real difference is the naming, although I have not specifically looked at all of the naming options. 

Anyway, just my two cents until someone with real coding expertise comes along to help you fix the script.

---

### Post by Uejji on 2012-02-14
No ideas then?

---

### Post by papibe on 2012-02-14
Hi Uejji.

I did a couple of tests using your script: the variable LASTBACK is set with different values if it's run interactively or inside cron.

Although I don't have the same directory structure (I tested it on my /home/user), my guess is that maybe the aliases set on interactive shells could be making the difference.

It could be interesting if you log some of the partial steps, so you can track down the problem.

For example you can add to your script.
```
...
echo ----------------------------------------
echo FIRSTBACK="$FIRSTBACK" >> /path/to/log
echo NEWBACK="$NEWBACK"     >> /path/to/log
echo ----------------------------------------
...
```
And then check the file /path/to/log after running the script both ways.

Just some thoughts.
Regards.

---

### Post by Uejji on 2012-02-16
Here's my modified script.  I've also tweaked the rsync command a bit.

```
#!/bin/bash

BACKUPDIR="/backup/"
FIRSTBACK=$( ls "${BACKUPDIR}" | head -n1 )
LASTBACK=$( ls "${BACKUPDIR}" | tail -n1 )
NEWBACK=$( date -d yesterday +%Y.%m.%d-%A )

echo FIRSTBACK="$FIRSTBACK" >> /tmp/backuplog
echo NEWBACK="$NEWBACK"     >> /tmp/backuplog

cp -lr "${BACKUPDIR}/${LASTBACK}" "${BACKUPDIR}/${NEWBACK}"
rsync -ax --delete --delete-excluded --exclude="backup" --numeric-ids --relative --progress / "${BACKUPDIR}/${NEWBACK}"
```

Here's the result I get.

```
FIRSTBACK=2012.01.31-Tuesday
NEWBACK=2012.02.15-Wednesday
FIRSTBACK=2012.01.31-Tuesday
NEWBACK=2012.02.15-Wednesday
```

This is very strange.  The values are correct, but the echos happen twice, as if the script is being executed twice.  Interactively, of course, the echos only happen once.

It seems I must have a crontab misconfiguration.  I'm not running anacron on my system, so I was under the impression that I had to add /etc/crontab to root's crontab.

```
# crontab -l
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 1    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
```

Perhaps this is grossly incorrect and the source of my problems.  I've just now removed root's crontab and I'll see how that goes overnight.

---

### Post by papibe on 2012-02-16
> **Uejji said:**
> 
It seems I must have a crontab misconfiguration.  I'm not running anacron on my system, so I was under the impression that I had to add /etc/crontab to root's crontab.

That could be it. You shouldn't do that.

Start by cleaning up your root's crontab:
```
sudo crontab -r
```
And then edit root's crontab just like you were to edit yours:
```
sudo crontab -e
```
One-liner should be all what you need. For instance a typical everyday midnight backup:
```
# m h  dom mon dow   command
0 0 * * *    /path/to/your/script.sh

```
Tell us how it goes.
Regards.

---

