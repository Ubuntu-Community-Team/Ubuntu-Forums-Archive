---
title: "backup to external drive but exclude external"
date: 2012-02-12
forum: General Help
---

### Post by qwertyjjj on 2012-02-12
I am trying to follow this guide for backing up my drive:
[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

However, I need to make the tar file on the external drive as I do not have much space left. What command can I use for that?

tar -cvpzf backup.tar.gz --exclude=/backup.tar.gz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/dev /

---

### Post by k999 on 2012-02-12
You included a command, isn't that working? It should exclude /mnt and /media, if your external drive is mounted on /media/SOMETHING, which is normal, you should be ok.

---

### Post by qwertyjjj on 2012-02-12
> **k999 said:**
> You included a command, isn't that working? It should exclude /mnt and /media, if your external drive is mounted on /media/SOMETHING, which is normal, you should be ok.

it seems to just stop halfway and hang.

Hangs on this file:
/home/.ecryptfs/j/.Private/ECRYPTFS_FNEK_ENCRYPTED.FWbCcx8jEZ.P5-QT9idn7gGdoBr87t5.q96UB5m6V9OWW9NgrFicd608DE--/ECRYPTFS_FNEK_ENCRYPTED.FWbCcx8jEZ.P5-QT9idn7gGdoBr87t5.q96UPO8wCTKnUOOha42dPPTth---/ECRYPTFS_FNEK_ENCRYPTED.FWbCcx8jEZ.P5-QT9idn7gGdoBr87t5.q96U8dOmVrH.U8xMu9g8Wr13GE--

---

### Post by sleepyhollows on 2012-02-12
Isn't it about time to move away from tar (Tape ARchiver) ?

7z is a very flexible, and far better than tar because compression is seamless, not an after thought.
[http://a32.me/2010/08/7zip-differential-backup-linux-windows/](http://a32.me/2010/08/7zip-differential-backup-linux-windows/)

---

