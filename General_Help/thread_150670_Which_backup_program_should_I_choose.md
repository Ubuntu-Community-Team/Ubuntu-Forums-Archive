---
title: "Which backup program should I choose?"
date: 2006-03-26
forum: General Help
---

### Post by DrSkalpell on 2006-03-26
Hi!

This is my situation:
I have a laptop with valuable information which I regularly want to backup to a remote server where I am not allowed to install software.

I am looking for backup software with the following functionality:

- Does NOT need software at the server side  (I guess this could be a problem)
- Automated backup
- Backup AND restore
- Level 0 and 1 with adjustable backup schedules
- Choose which folders to backup
- SSH with key encryption

Any suggestions?

---

### Post by FryerFox on 2006-03-26
Here is a script that I used to use to quickly backup my home, etc, and www directories:

It creates home.tgz, etc.tgz, and [www.tgz](www.tgz) respectively in the /home root, which I then transfer over to external storage.

I currently use an rsync script, since this meets my needs better, and haven't spent a lot of time snazzing up the script below, but I'll spend a little time on it if anyone's interested.

```
#!/bin/bash
DIR="/var/www"
C="--exclude=$DIR"
EXCLUDE=""
tar cvpzf /home/www.tgz $EXCLUDE $DIR

DIR="/etc"
C="--exclude=$DIR"
EXCLUDE=""
tar cvpzf /home/etc.tgz $EXCLUDE $DIR

DIR="/home/myhomedir"
C="--exclude=$DIR"
EXCLUDE="$C/.Trash $C/.thumbnails $C/.mozilla/firefox/*/Cache*"
tar cvpzf /home/home.tgz --exclude=/home/*.tgz $EXCLUDE $DIR
```

Once the .tgz files are created, you can use another command to automatically ftp the files across, e.g.

scp filename.tgz host:/path/to/dir

This requires an ssh server on the host, but this is quite common. If you want, you can also set it up so that scp is automatically connected by using public-private keys (ask if you need more info).

---

### Post by FryerFox on 2006-03-26
Incidentally, you can read more about rsync'ing here:

[http://applications.linux.com/applications/04/09/15/1931240.shtml?tid=13](http://applications.linux.com/applications/04/09/15/1931240.shtml?tid=13)

---

