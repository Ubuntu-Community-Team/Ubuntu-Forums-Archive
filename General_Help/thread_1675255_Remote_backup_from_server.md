---
title: "Remote backup from server?"
date: 2011-01-25
forum: General Help
---

### Post by neokyle on 2011-01-25
I need to have a directory from my server be backed up to my home desktop every 24 hours. Ive been using winscp to copy the directory to my desktop but it gets tedious, it would be nice to just crontab something that backs up my directory for me.

My server is running ubuntu 9.10 64 bit

My desktop is running windows 7 64 bit

Ive tried using rsync but i have no idea what to enter for localhost and user, and nothing i try seems to work.

---

### Post by neokyle on 2011-01-26
24 hour bump :)

---

### Post by sisterdorothy on 2011-01-29
> **neokyle said:**
> I need to have a directory from my server be backed up to my home desktop every 24 hours. Ive been using winscp to copy the directory to my desktop but it gets tedious, it would be nice to just crontab something that backs up my directory for me.

My server is running ubuntu 9.10 64 bit

My desktop is running windows 7 64 bit

Ive tried using rsync but i have no idea what to enter for localhost and user, and nothing i try seems to work.

I'm using linux machines on both ends of a backup like you describe and I use rsync and crontab.  But I don't know how it would work with win7.  However, I did a little searching and found [http://www.windows7download.com/win7-cwrsync/jqaclzji.html](http://www.windows7download.com/win7-cwrsync/jqaclzji.html) --wonder if that would work for you? It's a combo of cygwin and rsync.  ...In my backup script, this is how it looks:

rsync -avz -e ssh myusername@serverIPnumber:/home /media/hdd-label/backup-directory

But again, don't know how it works on windows....could be quite different.

---

### Post by neokyle on 2011-01-29
Yes i have tried a similar script to that with no success.

I,ll look into rwsync

I really dont care how i get the backup onto my machine as long as i can do it at least every 24 hours. Hopefully I can get something working.

Thanks for the reply :)

---

### Post by cjhabs on 2011-01-29
If you mount the windows folder onto your Ubuntu server first, you can use rsync. For example:


```
sudo mount -t smbfs /win_server/win_share /media/local_folder -o file_mode=0777,dir_mode=0777,user=username%password
rsync -au /path_to/source_folder/ /path_to/mounted_folder
```

The username/password are for the windows authentication.

---

