---
title: "Deleting files, .Trash empty, disk still full"
date: 2010-09-27
forum: General Help
---

### Post by funky_uncle on 2010-09-27
So I've been getting this error message:

"The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator."

a few times, and it turns out to be because of low disk space. No worry, I empty the trash uninstall unneeded programs and clean out the downloads folder that filled up my disk. And all is ok. But not this time.

Since I can't use X, I delete stuff from the terminal, and also make sure to clean out the .Trash in both /home and /root. But still the disk is full. I delete more stuff, but it doesn't even seem to go to .Trash. It disappears, but no more disk space.

Im using Linux Mint based on Ibex.

---

### Post by xircon on 2010-09-27
Run df in a terminal and post here, also have look in /var/log with 
```
du -ch /var/log
``` in case your log files have filled up.

:Edit: Also boot off a live Cd and browse the disk.

---

### Post by funky_uncle on 2010-09-27
I wouldn't know how to copy the results of *df* here, I have to use another PC just to get logged into a GUI.

But it does say that /dev/sdb1 is 100% full (still).
1% /dev
0% /dev/shm
1% /var/run
0% /var/lock
0% /lib/init/rw
63% /media/files

*sudo du -ch /var/log* says 20M total. Is there a limit as to how big the log files can be?

---

### Post by funky_uncle on 2010-09-27
I have a backup program that runs once a week (I think), could it be that this is causing it? There's a 19Gb file in /var/backup.

---

### Post by xircon on 2010-09-27
OK so its not your log files.

Can you boot off a live CD?

---

### Post by xircon on 2010-09-27
Maybe, I haven't got that directory.

---

### Post by Zimmer on 2010-09-27
check thumbnails, too... Geeqie has a thumbnail maintenance option to save you fiddling with command line tools..
and do you still have many kernels installed?

You should only need the current and the previous kernel...

Try uninstalling old (unwanted) kernels...

---

### Post by funky_uncle on 2010-09-27
All right, I've booted from a Mandriva Live CD.

Now what? :)

edit: I managed to delete stuff via the Live CD, and am now able to log in as normal. However, the stuff I deleted the first time around is gone from the disk, but still seems to take up the same space it used to. It's not found in the .Trash folders.

---

### Post by xircon on 2010-09-28
Sorry, had to go to bed, I get up at 05:30 for work :(

Glad you got it sorted.  Install something like Baobab or kdirstat (my favourite).

Also either from a live cd do a disk check - or you can force one [https://answers.launchpad.net/ubuntu/+question/4299](https://answers.launchpad.net/ubuntu/+question/4299)

Disks do strange things when they fill up in linux!

---

