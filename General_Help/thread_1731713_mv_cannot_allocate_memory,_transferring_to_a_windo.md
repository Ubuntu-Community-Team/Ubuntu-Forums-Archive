---
title: "mv: cannot allocate memory, transferring to a windows mount"
date: 2011-04-17
forum: General Help
---

### Post by CrazeDIzzleD on 2011-04-17
So I have a backup script to automatically backup my local webserver files every day at 6AM. It was working great but now all of a sudden, it doesn't work. When I try to manually execute the script I get ```
mv: accessing 'the-file-to-move' Cannot allocate memory
```

I'm a little confused. I have 2GB of memory and only 500MB is being used. 0% of 3GB swap is being used. I'm watching the system monitor while I execute the script and don't even see a change to memory or swap. So then, how is it using too much memory?

EDIT: After a little testing I have deduced that I only get this error while trying to move a file to my Windows mount. And it can be any file. So what all of a sudden changed that I can't move a file to my mount?

EDIT2: Upon further investigation, it seems I cannot do ANYTHING to my mount. Not even ls it. I unmounted it, and using smbmount I can no longer mount it, because I get the same "cannot allocate memory". Now I'm really confused...

EDIT3: Restarting my Windows box, with the share, fixed the problem. So, why did this happen and how can I prevent it in the future?

```
#!/bin/bash

_WWW=www.tar.bz2
_MYSQL=mysql.tar.bz2
_DIR=$(date +%m-%d-%Y)
_WWWTARGETPATH=/var/www
_MYSQLTARGETPATH=/var/lib/mysql
_DESTPATH=/home/scott/backup/_BACKUP/$_DIR

mkdir /home/scott/backup/_BACKUP/$_DIR

cd $_WWWTARGETPATH
tar vfcpj $_WWW $_WWWTARGETPATH 2>> /var/log/backup.txt

mv $_WWW $_DESTPATH/$_WWW

/etc/init.d/mysql stop

cd $_MYSQLTARGETPATH
tar vfcpj $_MYSQL $_MYSQLTARGETPATH 2>> /var/log/backup.txt

mv $_MYSQL $_DESTPATH/$_MYSQL

```

---

