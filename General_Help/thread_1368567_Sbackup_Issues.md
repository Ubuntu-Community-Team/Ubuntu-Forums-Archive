---
title: "Sbackup Issues"
date: 2009-12-30
forum: General Help
---

### Post by IlliniGuard on 2009-12-30
I'm trying to backup /home so that I can do a fresh install of Karmic. Under the "Destination" tab on Sbackup, I selected a "custom local backup directory," my portable hard drive. Without reading the directions, I hit "Backup Now" before hitting "Save." I then hit save and then Backup Now. I got the usual pop up telling me the process number etc.
I was able to find the process in the system monitor. I got a pop up saying that my hard drive was out of space. The process is listed under "Zombie" status.

1st question: Wherever Sbackup saved it to was apparently not my external hard drive, because I now have no space left on my hard drive! How do I find the backup and delete it so I can get some space back?

2nd: How do I get Sbackup to actually save to my hard drive?

Thanks so much!

---

### Post by plucky on 2009-12-31
> 1st question: Wherever Sbackup saved it to was apparently not my external hard drive, because I now have no space left on my hard drive! How do I find the backup and delete it so I can get some space back?


Look in **/var/backup** not "/var/backups"

Open a terminal and post output of ```
df -hT
```

Good Luck

p.s. Don't know the answer to question 2

---

### Post by IlliniGuard on 2009-12-31
When I tried to open up /var/backup, it said that I do not have the permission necessary to view the contents.

df -hT yields the following:
```
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda3     ext3     61G   55G  3.0G  95% /
udev         tmpfs    497M  276K  497M   1% /dev
none         tmpfs    497M  376K  497M   1% /dev/shm
none         tmpfs    497M  132K  497M   1% /var/run
none         tmpfs    497M     0  497M   0% /var/lock
none         tmpfs    497M     0  497M   0% /lib/init/rw
```

---

### Post by plucky on 2010-01-01
> When I tried to open up /var/backup, it said that I do not have the permission necessary to view the contents.


You will need to be in superuser mode.
Open a terminal and ```
gksudo nautilus
``` enter your password and then navigate your way to the **var/backup** and see what is in there.

If you delete anything,remember to delete the trash file as well to regain the disk space.

Good Luck

---

### Post by IlliniGuard on 2010-01-01
When I opened up /var/backup and deleted it (it was there, and exactly the size I expected), the file did not appear in the recycle bin and the space has not been reclaimed on the hard drive (according to the system monitor).

---

### Post by plucky on 2010-01-02
Were you in Nautilus when you deleted it? In sudo mode the Trash goes to a different location than user Trash.

If so check /root Trash.See this [link](http://ubuntuforums.org/showthread.php?t=898573&highlight=drs305) for cleaning up your Trash.

Good luck

---

### Post by IlliniGuard on 2010-01-06
Precious hard drive space reclaimed! (Funny how when I bought this computer 3+ years ago I though 100GB would be plenty.)

Thanks so much! I appreciate all the help!

---

