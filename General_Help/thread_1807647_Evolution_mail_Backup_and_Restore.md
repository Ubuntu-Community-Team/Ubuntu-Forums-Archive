---
title: "Evolution mail Backup and Restore"
date: 2011-07-19
forum: General Help
---

### Post by SVWander on 2011-07-19
HELP! I had installed Ubuntu 11.04 on my MSI WIND U100. Unity or some other program caused it to freeze after unplugging or plugging the ac adapter. I posted questions as to how to work around the problem but no one had any ideas. Since I am on a trip and using battery power I had to reinstall Ubuntu 10.04 (the netbook edition). All is going well and the power management is working but I can't restore the backup of Evolution mail! Can anyone tell me how to get it Evolution restored. I have evolution-backup.tar.gz stored on my desktop but get an error message telling me it is not a valid backup file. Thanks.

---

### Post by mirx on 2011-07-19
This should test the file:
gzunzip -c evolution-backup.tar.gz |tar tf evolution-backup.tar.gz

---

### Post by SVWander on 2011-07-19
> **mirx said:**
> This should test the file:
gzunzip -c evolution-backup.tar.gz |tar tf evolution-backup.tar.gz

Thanks for the reply! I ran the command and it scrolled hundreds of files on the screen but no error messages that I could see.

---

### Post by dcstar on 2011-07-20
> **SVWander said:**
> HELP! I had installed Ubuntu 11.04 on my MSI WIND U100. Unity or some other program caused it to freeze after unplugging or plugging the ac adapter. I posted questions as to how to work around the problem but no one had any ideas. Since I am on a trip and using battery power I had to reinstall Ubuntu 10.04 (the netbook edition). All is going well and the power management is working but I can't restore the backup of Evolution mail! Can anyone tell me how to get it Evolution restored. I have evolution-backup.tar.gz stored on my desktop but get an error message telling me it is not a valid backup file. Thanks.

It is very doubtful that you can use a 11.04 backup in a 10.04 system, they are **different** versions of Evolution.

You should be able to manually extract the .evolution folder and recover the mail folders etc., but you there is no guarantee it will work.

---

### Post by johnaaronrose on 2011-08-09
I've seen somewhere that the backup file has to be placed on the same directory of a new PC as that it was originally written to (i.e. another PC) e.g. /home/user. Have you tried that?

---

