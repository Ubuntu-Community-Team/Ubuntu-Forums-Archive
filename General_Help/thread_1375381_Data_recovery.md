---
title: "Data recovery?"
date: 2010-01-07
forum: General Help
---

### Post by dragos240 on 2010-01-07
Hi.

I saved a file of an image. This file was overwritten by a faulty program (paint-mono). Is there a way I can recover an older version?

---

### Post by dragos240 on 2010-01-08
Hi, uh, could someone help me :(.

---

### Post by bodhi.zazen on 2010-01-08
If the file was over written, no I doubt recovery is possible.

If it is simply deleted, possible

[DataRecovery - Community Ubuntu Documentation]("https://help.ubuntu.com/community/DataRecovery")

---

### Post by dragos240 on 2010-01-08
Maybe I should do more backups.

---

### Post by bodhi.zazen on 2010-01-08
> **dragos240 said:**
> Maybe I should do more backups.

Hate it when that happens :(

---

### Post by lisati on 2010-01-08
> **bodhi.zazen said:**
> Hate it when that happens :(

Isn't it the way it goes? You diligently make backups for ages, all is well for a while, then for some reason you forget or get lazy (maybe your backup HDD is getting full), and something happens and you wish you had kept up with maintaining your backups!

Speaking of which, must be time for me to do some housekeeping on my backup drives.......

---

### Post by bodhi.zazen on 2010-01-08
> **lisati said:**
> Isn't it the way it goes? You diligently make backups for ages, all is well for a while, then for some reason you forget or get lazy (maybe your backup HDD is getting full), and something happens and you wish you had kept up with maintaining your backups!

Speaking of which, must be time for me to do some housekeeping on my backup drives.......

Indeed , yes, this is a lesson one keeps re-learning :(

Which is why backups are best managed as automated tasks.

---

### Post by dragos240 on 2010-01-08
> **bodhi.zazen said:**
> Indeed , yes, this is a lesson one keeps re-learning :(

Which is why backups are best managed as automated tasks.

Like a cron job? I never backup anyway.

---

### Post by bodhi.zazen on 2010-01-08
> **dragos240 said:**
> Like a cron job? I never backup anyway.

Yes, take a look at rsync , it will perform incremental backups and is fast.

You can have a /data directory that you back up with rsync over ssh if you wish to keep it on a central server.

[http://www.linux.com/archive/feature/113847](http://www.linux.com/archive/feature/113847)

Obviously there are other methods, and you can use rsync without a central server, but rsync is fast, easy, and versatile.

---

### Post by dragos240 on 2010-01-08
> **bodhi.zazen said:**
> Yes, take a look at rsync , it will perform incremental backups and is fast.

You can have a /data directory that you back up with rsync over ssh if you wish to keep it on a central server.

[http://www.linux.com/archive/feature/113847](http://www.linux.com/archive/feature/113847)

Obviously there are other methods, and you can use rsync without a central server, but rsync is fast, easy, and versatile.

So it can create dd images?

---

### Post by bodhi.zazen on 2010-01-08
not that I know of, dd images are more to back up the entire installation. Such a back up is quite large and possibly unecessary.

I back up files in /data , /etc , and /var/www (or similar data locations), + mysql. The resulting backup is much smaller then a dd image.

Of course there are other advantages of a dd image. If you want to back up your partitions take a look ar partimage or similar.

Personally, I figure I can re-install the OS, and with updates I do not really want or need an image of the partition, all I want the the data and config files.

---

