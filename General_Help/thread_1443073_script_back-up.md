---
title: "script back-up"
date: 2010-03-30
forum: General Help
---

### Post by ecoxx on 2010-03-30
hi..everyone..i am a newbie here..

i made a script which backup /etc..here it is..

```
#!/bin/sh

# backup /etc

sudo  tar -cjvf etcbackup.tar.bz2 /etc; mv etcbackup.tar.bz2 /home/ecoxx/backup
```when i type that command in terminal everything is ok...work's perfect...

but when i made a crontab..it doesn't work...it also creates and move tarball but only few files of /etc.

what can i do...

---

### Post by Sin@Sin-Sacrifice on 2010-03-30
Are you using ```
crontab -e
``` to edit? Depending on the permissions you may have to use sudo as well.

---

### Post by ecoxx on 2010-03-30
yes i am using crontab -e with root privileges..

---

### Post by Sin@Sin-Sacrifice on 2010-03-30
Post it if you can.

---

