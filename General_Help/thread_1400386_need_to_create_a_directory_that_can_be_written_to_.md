---
title: "need to create a directory that can be written to by multiple users"
date: 2010-02-06
forum: General Help
---

### Post by ThaddeusW on 2010-02-06
Hello,

I have a small ubuntu server setup and I would like to create a directory that can be written to by a select number of users. I have a backup directory setup and I want to enable my account as well as three others to be able to read/write to that directory. So far I haven't had any luck.

The owner of the backups folder, a directory on a separate disk mounted under /srv/storage, was owned by root and under the root group. I added the group backups and then changed the backups directory group to backups. I then used chown to change the backups directory to 775 to enable group members to write to it. I then tried to touch a file in the backups folder but no such luck. I did notice that when I run groups, my user account isn't shown as belonging to backups but is shown under the /etc/group file. I even made sure the GID of backups is in fact below 1000.

Anyone have an idea on how to create a shared directory that everyone can create, modify and delete any file? I believe my problem is related to the fact that root is the owner of the backups directory.

---

### Post by sandkernel on 2010-02-06
Check the permissions and ownership of the parent directories. It is possible that you changed ownerships of the backups directory but /srv/storage has permissions that are causing issues.

---

### Post by mushwars on 2010-02-06
easy.

```
sudo mkdir /storagedir
sudo chown -R <your name>:users /storagedir
sudo chmod -R 0777 /storagedir
```

that should do it.

---

### Post by Ordes on 2010-02-06
first of all, this is a a folder an second HDD in the same system right?
and you mount it under /srv...

Normally all mount points are in /media/...
---
the parent directory need to have all permissions

/media/backup
> chown userXX:groupbackup /media/backup
> if want read and write, you need 770, 
> 5 is just read and execute, so as group you cannot write, delete or change the files
> group backup need to be added to the users that are allowed to have access
> if user2 create a dir in backup, that permission will be users2:users2, so you need to $ sudo those to xx:backup if you want to interacte with user2 files.

---

### Post by ThaddeusW on 2010-02-06
Thanks for the help everyone!

> **Ordes said:**
> first of all, this is a a folder an second HDD in the same system right?
and you mount it under /srv...

Normally all mount points are in /media/...
---
the parent directory need to have all permissions

/media/backup
> chown userXX:groupbackup /media/backup
> if want read and write, you need 770, 
> 5 is just read and execute, so as group you cannot write, delete or change the files
> group backup need to be added to the users that are allowed to have access
> if user2 create a dir in backup, that permission will be users2:users2, so you need to $ sudo those to xx:backup if you want to interacte with user2 files.

/media is for removable disks that are mounted by pmount. The disk I am using is a second internal SATA disk. Its sole purpose is to act as a storage place for all of my files. /srv is not normally used but I believe its purpose is a general directory for storing server related data if one chooses to do so. I used /mnt but just decided to use /srv as it is self descriptive.

---

