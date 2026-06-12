---
title: "cron jobs not running"
date: 2010-09-01
forum: General Help
---

### Post by davidstoll on 2010-09-01
I've seen other posts about this, but I was not able to find one that helped me...so forgive me if this type of issue has been addressed.

My...
/etc/cron.hourly
/etc/cron.weekly
etc/cron.monthly
and
/etc/crontab # custom entries

are not running.  I believe this "broke" when I updated to 10.4, which was a little over a month ago...or so.

It appears that the crontab has been accessed and run (based on the access date getting updated every so often), but none of the jobs are running, but have been previously for 2 years.

Could someone please give me a hand?  I'm running MythBuntu 10.4 (XFCE).

---

### Post by davidstoll on 2010-09-02
more info...


```
$ sudo /etc/init.d/cron start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service cron start

Since the script you are attempting to invoke has been converted to an 
Upstart job, you may also use the start(8) utility, e.g. start cron
```


So, I tried this (I guess it changed on 10.4?)...
```
$ sudo service cron start
start: Job is already running: cron
```

So, supposedly the deamon is running, but nothing inside crontab or inside the cron.xxxxxx is running.

---

### Post by bodhi.zazen on 2010-09-02
Can you post your cron entries ?

Most problems occur when one does not use the full path.

---

### Post by davidstoll on 2010-09-02
> **bodhi.zazen said:**
> Can you post your cron entries ?

Most problems occur when one does not use the full path.

Thank you for mentioning that...I think I'm on the right path to figuring out the problem because you kicked my brain.  The issue is not actually in the crontab file, it's a script that crontab calls.  I commented them out one by one and found one that seemed to make the entire crontab not function.

It seems to be an rsync related issue (not rsync itself...user error).  I am trying to (one way copy) files.  Maybe I should just use cp, but if the file changes, I want it to be re-copied.

Anyway, I think the problem is that sometimes the folders it is trying to copy FROM don't exist...and I don't really have control over that.


```
#!/bin/bash
#backup downloads

set -e

rsync $* --exclude={} -r -t /download/1/ /backup/1/ --progress -v

rsync $* --exclude={} -r -t /download/2/ /backup/2/ --progress -v

rsync $* --exclude={} -r -t /download/3/ /backup/3/ --progress -v

rsync $* --exclude={} -r -t /download/4/ /backup/4/ --progress -v

```

Not sure that it matters, but the backup folders are actually samba mounts and I have to use sudo to run the script.

---

### Post by bodhi.zazen on 2010-09-02
If it fails because directories do not exist, test for them

[[ -d /backup/1 ]] || mkdir /backup/1

---

### Post by davidstoll on 2010-09-02
> **bodhi.zazen said:**
> If it fails because directories do not exist, test for them

[[ -d /backup/1 ]] || mkdir /backup/1

I can't really mess with the source folders because they are created and deleted by another program.

I also can't use the exact folder structure, because the backup location requires that it be different.

---

### Post by davidstoll on 2010-09-03
> **davidstoll said:**
> I can't really mess with the source folders because they are created and deleted by another program.

I also can't use the exact folder structure, because the backup location requires that it be different.

Looks like rsync doesn't like spaces in paths, so I think you have to double escape the space character.

I determined that rsync was probably overkill for what I wanted, so I just changed to "cp -u" and everything works.

It seems kind of strange that a script that is being called from crontab would make the entire crontab not work.  Not sure why it just doesn't error out and move to the next entry.

---

