---
title: "Drive mounting inside itself over and over again?"
date: 2010-02-08
forum: General Help
---

### Post by thecheeks on 2010-02-08
Basically I have my music dir mounted at /Music. Funny thing is, my music drive is mounted INSIDE itself again and again. It's like a mirror reflecting a mirror, it doesn't end.

/Music/Music/Music/Music/Music/Music/Music/Music/Music/Music/Music/

THE ****?
/etc/fstab
>     
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=53f6a153-c801-457a-ad04-da3b5f698231 / ext3 relatime,errors=remoun$
# /dev/sda5
UUID=c1faa169-423a-4377-a176-36e2c6fce908 none swap sw 0 $
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

/dev/sdb1 /Media ext3 defaults 0 0
/dev/sdc1 /Music ext3 defaults 0 0

---

### Post by doas777 on 2010-02-08
> **thecheeks said:**
> Basically I have my music dir mounted at /Music. Funny thing is, my music drive is mounted INSIDE itself again and again. It's like a mirror reflecting a mirror, it doesn't end.

/Music/Music/Music/Music/Music/Music/Music/Music/Music/Music/Music/

THE ****?
/etc/fstab


try mounting it to a location within a folder in the root. not sure why that would effect it, but is worth a try.

---

### Post by darolu on 2010-02-08
Try using UUID instead of /dev/sdxx.
```
sudo blkid /dev/sdc1
```
Should return something like - /dev/sdc1: UUID="44D783136C69AB28" LABEL="Music" TYPE="ext3" -

Use this information to fill your fstab lines; I'd change the pass value to 1 on your sdb1 line and to 2 on your sdc1 line; also try adding this options: defaults,user,exec,rw. Read [this link]("http://www.tuxfiles.org/linuxhelp/fstab.html") if you have more questions.

Oh yeah, I forgot to add, in Ubuntu, seems that you need to mount your units within the /media directory; so try changing your mount points to /media/Media and /media/Music respectively too.

---

### Post by thecheeks on 2010-02-08
I actually just did
sudo rm -rf Music/
AND
sudo rm -rf Music

No idea why the forward slash taken out mattered, but it solved the problem.

---

