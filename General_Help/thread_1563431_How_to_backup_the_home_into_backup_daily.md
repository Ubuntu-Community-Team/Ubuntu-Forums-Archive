---
title: "How to backup the /home into /backup daily?"
date: 2010-08-29
forum: General Help
---

### Post by honeybear on 2010-08-29
Hi,

I would like to backup the /home into /backup daily using crontab.

Which command should I use? I saw that rsync or cp -a could be used but what would be a fine choice for this command ?

thanks if someone knows ...

---

### Post by johnhenry on 2010-08-29
rsync works well and has the advantage over cp that it does what is known as an incremental backup - ie. it only changes what has been changed since the last backup. This makes it very fast, usually just a few seconds unless you have made massive changes. The syntax is simple -

rsync -avr --delete /path/directory/ /path/destination/

The --delete tells to to also delete anything which is no longer in the source directory.

---

### Post by albandy on 2010-08-29
it depends, do you want an incremental copy or a full copy every day?

---

### Post by honeybear on 2010-08-29
> **johnhenry said:**
> rsync works well and has the advantage over cp that it does what is known as an incremental backup - ie. it only changes what has been changed since the last backup. This makes it very fast, usually just a few seconds unless you have made massive changes. The syntax is simple -

rsync -avr --delete /path/directory/ /path/destination/

The --delete tells to to also delete anything which is no longer in the source directory.

thank you so much !!!

---

### Post by anubhavrocks on 2010-08-29
You may find this helpful:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

