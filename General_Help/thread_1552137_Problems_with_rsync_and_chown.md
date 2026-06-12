---
title: "Problems with rsync and chown"
date: 2010-08-13
forum: General Help
---

### Post by cj13579 on 2010-08-13
Hi all,

I'm getting the following error message when running rsync to perfrom a backup from my 1st HDD to my 2nd, internal, HDD:

```
rsync: chown "/media/backup/....." failed: Operation not permitted (1)
```

Permission on both the source and the destination are set to 777.

The rsync command I am running is:

```
rsync -a --progress --delete --log-file=/var/log/rsync/$(date+%d%m%Y).log /source/dir /media/backup
```

The strange thing is when I cd into /media/backup it looks as though everything has copied accross. 

Any ideas what this mighjt be?

---

### Post by aeiah on 2010-08-13
what filesystem does your external drive have?

---

### Post by cj13579 on 2010-08-13
Its vfat.

---

### Post by cj13579 on 2010-08-13
I'm thinking that the file system may be the issue. I have been reading about and [ this thread]("href="http://ubuntuforums.org/showthread.php?t=1550872"") suggests that this might be what is causing the issue. I shall try this on Monday as box is at work and report back.

---

