---
title: "What does this mean &quot;no space left on device&quot; when I have plenty of space?"
date: 2009-09-18
forum: General Help
---

### Post by MountainX on 2009-09-18
```
/etc/cron.daily/mlocate:
/usr/bin/updatedb.mlocate: I/O error while writing to `/var/lib/mlocate/mlocate.db.j59ncn': No space left on device
run-parts: /etc/cron.daily/mlocate exited with return code 1

```

/var is not out of space and I do not see any device out of space...

```
$ df -h
[FONT=Courier New]Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/vgA-lvRoot_crypt
                       50G   26G   24G  53% /
tmpfs                 4.0G     0  4.0G   0% /lib/init/rw
varrun                4.0G  2.6M  3.9G   1% /var/run
varlock               4.0G     0  4.0G   0% /var/lock
udev                  4.0G  3.0M  3.9G   1% /dev
tmpfs                 4.0G     0  4.0G   0% /dev/shm
lrm                   4.0G  2.4M  4.0G   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sdf1             317M   41M  276M  13% /boot
/dev/sdf2             917G  260G  611G  30% /nopct
/dev/mapper/vgB-lvHome_crypt
                      201G   53G  149G  26% /home
/dev/mapper/vgC-lvTmp_crypt
                       30G  173M   30G   1% /tmp
/dev/mapper/vgC-lvVar_crypt
                       25G   13G   12G  52% /var[/FONT]

```

---

### Post by MountainX on 2009-09-19
bump

---

### Post by utnubuuser on 2009-09-19
Try googling "no space left on device ubuntu"  -- I've seen threads about this subject on this forum fairly recently and how to reset.

---

### Post by MountainX on 2009-09-19
SOLVED:

The df command shows I have about 12 GB available

[FONT=Courier New]Filesystem Size Used Avail Use% Mounted on
/dev/mapper/vgC-lvVar_crypt
25G 13G 12G 52% /var[/FONT]

The mlocate.db file is 12 GB in size:
/var/lib/mlocate/mlocate.db: 12G

running /etc/cron.daily/mlocate creates a temporary mlocate.db, and apparently this temporary file was also about 12 GB, thereby using up all my free space.

Anyone want to comment on why mlocate.db would be so large?

---

### Post by chitowner2 on 2012-02-21
> **MountainX said:**
> SOLVED:

The df command shows I have about 12 GB available

[FONT=Courier New]Filesystem Size Used Avail Use% Mounted on
/dev/mapper/vgC-lvVar_crypt
25G 13G 12G 52% /var[/FONT]

The mlocate.db file is 12 GB in size:
/var/lib/mlocate/mlocate.db: 12G

running /etc/cron.daily/mlocate creates a temporary mlocate.db, and apparently this temporary file was also about 12 GB, thereby using up all my free space.

Anyone want to comment on why mlocate.db would be so large?


I have a similar problem not yet resolved but here is what I know;

mlocate.db is a list of all files on your PC, used by an app called mlocate in a terminal session (eg "locate ----"). 

Probably it is proportional to the size of the directories on the machine, but I am told there is a way to trim or limit what mlocate scans to create the db, which I plan to do, thus removing stuff that inflate the size of the db.

If you do not use locate though, you can uninstall it and that will delete the db:
sudo aptitude purge mlocate

CT

---

### Post by oldos2er on 2012-02-21
Closed, necromancy.

---

