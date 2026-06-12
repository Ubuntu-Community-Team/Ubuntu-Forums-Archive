---
title: "BaclupPC - how to backup to a separate HDD"
date: 2010-07-06
forum: General Help
---

### Post by ibates on 2010-07-06
I have installed BackupPC through the Synaptic system.  It installs well on Ubuntu 10.04 and looks as though it is just what I have been looking for.

But; although I am by no means a dummy user, I cannot for the life of me understand the vast majority of what is written in the documentation.  I would say it requires a high degree of expertise to understand what it is saying.

My problem is simple.  I need to back up to an independent HDD.  One that has no OS, and is simply a data disk.  In my case, it is /dev/sde.

How can I configure BackupPC to do this?

---

### Post by ibates on 2010-07-12
It appears you can't do this - period.

---

### Post by howwhi on 2010-09-20
May I humbly disagree with the above conclusion that one may _not_ put backuppc on a separate HDD?

I agree completely that an environment variable to point to the file location would be very nice.  Might be a suggestion you could post on the backuppc forum on sourceforge.

In the mean time, know that the major data files for backuppc are stored in the directory "/var/lib/backuppc."  As root, I did the following:
   service backuppc stop
   cd /var/lib
   mv backuppc backuppc_mv
   cp -av backuppc_mv /backup/backuppc   # a separate volume
   ln -s backuppc /backup/backuppc
   service backuppc start

Hope this helps

Howard

---

