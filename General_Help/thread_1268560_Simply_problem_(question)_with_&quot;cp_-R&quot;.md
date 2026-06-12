---
title: "Simply problem (question) with &quot;cp -R&quot;"
date: 2009-09-17
forum: General Help
---

### Post by dchurch24 on 2009-09-17
Hi,

I have a cron job set to run at midnight to copy from my NAS to an external USB drive as a simple back up.

```


#!/bin/bash
mysqldump -u root -h localhost -pxxxxxxx xxxxxx > /home/dave/mysql.automation.dump
cp -fr mysql.automation.dump /media/disk/backup/databases
cp -fr /home/repos /media/disk/backup/repos
cp -R /media/mybook/Pictures /media/disk/backup/


```

The database dump does as expected, and get's overwritten every night. I'm sure there's a more sophisticated way of doing a mysql backup incrementally, but this works fine for me.

The problem is the Pictures folder. It seems to overwrite all of the pictures every night rather than just copying new ones.

There's around 40,000 8megapixel pictures in subfolders etc... in that directory, so this takes quite some time.

What can I change in the cp statement to make it simply error or not overwrite if the picture already exists in the destination?

---

### Post by lloyd_b on 2009-09-17
Try:```
cp -[COLOR="Red"]u[/COLOR]R /media/mybook/Pictures /media/disk/backup/
```The "u" option tells it to copy the file only if the source file is newer than the destination file, or the destination file doesn't exist.  That way the only pictures you'll be copying will be either new ones, or ones that have been modified in some way.

Lloyd B.

---

### Post by dchurch24 on 2009-09-17
Thank you very much - that's exactly what I was after!

It's still running now, but my NAS is very, very slow.

Is there a way of making it display what it's doing at the same time?

---

### Post by lloyd_b on 2009-09-17
> **dchurch24 said:**
> Thank you very much - that's exactly what I was after!

It's still running now, but my NAS is very, very slow.

Is there a way of making it display what it's doing at the same time?

If you add the "v" option switch, it turns on "verbose" mode, which will display each file as it is being copied.

FYI - "man cp" in a terminal window, and it'll give you a list of all the options, and what each of them does.

Lloyd B.

---

### Post by dchurch24 on 2009-09-17
Superb. Thanks for the tips!

Much appreciated. I did do a 'man' page, but I must have missed the verbose mode!

---

