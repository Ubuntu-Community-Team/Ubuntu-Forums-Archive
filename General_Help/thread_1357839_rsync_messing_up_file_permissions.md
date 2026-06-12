---
title: "rsync messing up file permissions"
date: 2009-12-17
forum: General Help
---

### Post by boazarad on 2009-12-17
I'm using rsync to sync files from a windows machine (using cygwin) to my ubuntu box. The initial sync goes through just fine, but every subsequent sync results in multiple "Permission denied" errors.


I'm running the following command on the windows box:
```
rsync -avz --no-perms -e ssh user@remote:/backup
```
(recently added the "no-perms" which seemed to help, though still not solving the problem :/

it seems that every time rsync "touches" a directory, its permissions are changed to 010 (-----r---)

any ideas?

---

### Post by dcstar on 2009-12-17
> **boazarad said:**
> I'm using rsync to sync files from a windows machine (using cygwin) to my ubuntu box. The initial sync goes through just fine, but every subsequent sync results in multiple "Permission denied" errors.


I'm running the following command on the windows box:
```
rsync -avz --no-perms -e ssh user@remote:/backup
```
(recently added the "no-perms" which seemed to help, though still not solving the problem :/

it seems that every time rsync "touches" a directory, its permissions are changed to 010 (-----r---)

any ideas?

What filesystem is on the destination?

---

### Post by boazarad on 2009-12-18
> **dcstar said:**
> What filesystem is on the destination?

The destination is ext3, source is ntfs.

---

### Post by CharlesA on 2009-12-18
What happens if you run it using sudo?

I know I had a problem where the owner wouldn't transfer over if I ran rsync -a without being root (or using sudo).

---

### Post by boazarad on 2009-12-20
Looks like I have the problem solved for now,
I'm guessing the errors were due to not passing the "--no-perms" parameter during the first few backups.

What happened later, was that since the first backup had created a directory structure of this sort:
/backup/dir1/dir2/dir3...

where dir1-3 had no read permissions set, running
```
find . -type d -exec chmod 755 {} \;
```
would only fix the permissions for dir1, while leaving dir2,dir3 and so on without the proper permissions.
I had to run the command enough times in order to traverse all the blocked directories, and now the backups seem to be going over smoothly.

Thanks a lot for your help!

---

