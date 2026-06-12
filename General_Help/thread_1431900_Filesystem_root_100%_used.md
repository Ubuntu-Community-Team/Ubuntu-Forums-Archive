---
title: "Filesystem root 100% used"
date: 2010-03-17
forum: General Help
---

### Post by vdmc01 on 2010-03-17
Hi all

Last week the volume root fills up to 100%. During the weekend I freed up 1.5GB but a couple of days later the fs is full again. I can use some help here pls. I use Server 9.04. Output of the df command:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/vasl01-root
                     237198024 237196628         0 100% /
tmpfs                   505960         0    505960   0% /lib/init/rw
varrun                  505960       736    505224   1% /var/run
varlock                 505960         0    505960   0% /var/lock
udev                    505960       168    505792   1% /dev
tmpfs                   505960         0    505960   0% /dev/shm
lrm                     505960      2560    503400   1% /lib/modules/2.6.28-18-server/volatile
/dev/sda5               233335     42291    178596  20% /boot
/dev/sdb             480721640 440276716  16025596  97% /media/hdb
/dev/sdc1            961424040 388661224 523925220  43% /media/mybookusb
overflow                  1024         0      1024   0% /tmp

I tried several things already, emptied tmp, remove package files that I don´t need, remove OO, then some space is available but it looks like it´s taken up immediaytely.

Is there a way to search for large files or files that have changed in the last 2 days?
Any other suggestions and help appreciated.
Peter

---

### Post by srs5694 on 2010-03-17
Try this:

```

cd /
sudo du -s * | sort -n

```

This will give you a list of files and directories sorted by size, with the biggest ones at the bottom. If you see humongous directories but not humongous files, cd into the big directories and repeat the du command until you find where the space is being used. If it turns out to be something you don't recognize, especially outside of your /home directory, post back before deleting it.

---

### Post by mikemelen on 2010-03-17
paste the o/p of

#cd /
#du -csh ./*

---

### Post by oldfred on 2010-03-17
A couple of other alternative commands:

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

Check that you do not have a backup running that you thought was going somewhere else. Another is a run away log file with repeating errors.

---

