---
title: "incremental backup with rsync"
date: 2012-05-10
forum: General Help
---

### Post by sjmikeb on 2012-05-10
Good morning,

I am attempting to implement an incremental system backup for our server via rsync.  I want to preserve the previous version of changed files in a backup directory tagged with the current time.  I get a syntax error when I use what I thought should work to accomplish this, only the pertinent part of the command as follows:
rsync --backup --backup-dir=`date`

I can make this work with a literal directory, but haven't been able to make it create a directory based upon the date, I get a syntax error.

Any suggestions?

Much appreciated

---

### Post by lukeiamyourfather on 2012-05-10
This might help which has some examples.

[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)

Also if you haven't yet, check out duplicity which creates incremental backups and is built using rsync.

[http://duplicity.nongnu.org/](http://duplicity.nongnu.org/)

---

### Post by CharlesA on 2012-05-10
echo the entire thing. My bet is there is a space in there that will mess things up if you do not put quotes around it.

---

### Post by drmrgd on 2012-05-10
Duplicity looks really nice.  Just to throw another option out there, check out [rsnapshot]("http://rsnapshot.org/"), another rsync backup utility.  I've been using that for a while, and really like how easy and efficient it is.  

I sort of like how Duplicity encrypt the backup too, though.  I might have to check that out myself.

---

### Post by CharlesA on 2012-05-10
> **drmrgd said:**
> Duplicity looks really nice.  Just to throw another option out there, check out [rsnapshot]("http://rsnapshot.org/"), another rsync backup utility.  I've been using that for a while, and really like how easy and efficient it is.  

I sort of like how Duplicity encrypt the backup too, though.  I might have to check that out myself.
rsnapshot is really good too, but I've used a script that is similar to rsnapshot but gets the job done too. ;)

---

### Post by sjmikeb on 2012-05-10
Thanks everyone, I will check the apps you suggest as well, but found this works:

rsync --backup --backup-dir="`date`"

---

### Post by CharlesA on 2012-05-10
Adding quotes makes it escape the spaces.

I would also suggest using "$(date)" instead of "`date`" for readability reasons.

---

