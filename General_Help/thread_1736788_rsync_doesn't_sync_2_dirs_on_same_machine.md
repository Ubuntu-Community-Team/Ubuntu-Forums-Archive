---
title: "rsync doesn't sync 2 dirs on same machine?"
date: 2011-04-22
forum: General Help
---

### Post by standingbear on 2011-04-22
Hi,

I am trying to learn and play with rsync.  Started the rsync daemon with the following setting in /etc/rsyncd.conf

```

motd file = /etc/rsyncd.motd
log file = /var/log/rsyncd.log
pid file = /var/run/rsyncd.pid
lock file = /var/run/rsync.lock

[toydocs]
   path = /home/jim/rsynctoys
   comment = Jim's toy docs
   uid = 0
   gid = 0
   read only = no
   list = yes
   hosts allow = 129.0.0.1/0
   auth users = jimbo
   secrets file = /etc/rsyncd.scrt
   strict modes = false

```where /home/jim/rsynctoys has a directory tree of files, and the file /etc/rsyncd.scrt says
```
jimbo:jimbo
```but when I tried to rsync using another directory on the same machine under the same account (~/toy2/ which is empty) as the destination, it doesn't sync up:
```

jim@jimac: rsync --recursive --progress --delete --verbose --dry-run rsync://jimbo@127.0.0.1:873/toydocs ~/toy2/
=============================
|   this is my rsync MTOD             |
============================
Password: 
receiving incremental file list

sent 59 bytes  received 405 bytes  61.87 bytes/sec
total size is 0  speedup is 0.00 (DRY RUN)

```i am wondering why it doesn't try to copy the files to ~/toy2/   is it because I created the directory toy2 after I created ~/synctoys/ and populated files in it?  but I didn't use the --update option.

---

