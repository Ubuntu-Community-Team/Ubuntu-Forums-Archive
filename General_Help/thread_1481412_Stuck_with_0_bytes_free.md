---
title: "Stuck with 0 bytes free"
date: 2010-05-12
forum: General Help
---

### Post by Terazilla on 2010-05-12
I've been using Ubuntu as a file server for over a year now, largely with good success.  It's also running an SVN server that I use daily.

I tried adding a new project to the repository earlier today, and was told I'm out of disk space.  Kind of weird considering I have almost nothing installed, but got weirder after I started looking for things to clear out.  No matter what I do, I'm told my home folders have 0 bytes free.

So far I've tried:

* "sudo apt-get clean" and "sudo aptitude clean" at the command line
* Checking var/logs (only 250k)
* Emptying the trash
* Deleting files from my home folder (skipping the trash)
* Applying all updates
* Rebooting

Checking my free space after all these things continues to list 0 bytes free.  I'm not a linux pro at all, and this has me baffled.  Checking permissions on the home folders still lists me as read/write privileged.  Can anyone help?

---

### Post by psusi on 2010-05-12
Do you have a separate /home partition?  What is the output of the df command in a terminal?

---

### Post by Terazilla on 2010-05-12
No, there's not a separate partition for /home.  Both home folders in total (mine and /svn) only add up to 250mb or so, almost all of that /svn.

df output looks like so (big_usb is an external USB drive):

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              9690316   9416960         0 100% /
varrun                  484628       224    484404   1% /var/run
varlock                 484628         0    484628   0% /var/lock
udev                    484628        44    484584   1% /dev
devshm                  484628        12    484616   1% /dev/shm
lrm                     484628     40000    444628   9% /lib/modules/2.6.24-27-generic/volatile
/dev/sdc1            976283280 699617280 276666000  72% /media/big_usb
overflow                  1024        36       988   4% /tmp
gvfs-fuse-daemon       9690316   9416960         0 100% /home/jstatz/.gvfs
/dev/sda3            103496400  42701904  60794496  42% /media/disk-2
```

---

### Post by psusi on 2010-05-12
Use du to drill down to find where the space is used up.  Switch to root with sudo -s, then cd / and run du -sh *.  See which directory is huge and cd into that then repeat the du -sh *.

---

### Post by jerome1232 on 2010-05-12
```
sudo du -hx --max-depth=1 /
```

That will give you a breakdown of all your folders from the root directories perspective. Let's say your run that and find a folder using extravagant amounts of space, just use du to further investigate that folder.

edit, it's also ignoring other file systems, so it won't total up spots where other drives are mounted, ie if /dev/sda3 were mounted as /mnt/mydrive, it won't total up the files in /mnt/mydrive.

ie 

```
 sudo du -hx --max-depth=1 /hugefolderThatshouldn'tBEsoHuge
```

Do you happen to run backups to a removable drive? I've seen quite a few instances where either a script or a person has ran a backup while their media was unmounted and it resulted in alot of junk at the mount point which filled their drive up.

---

### Post by Terazilla on 2010-05-12
That's more or less what I just found... I had a backup script backing up to /disk (the system partition) instead of /disk-2 (the 80gb data partition).  It'd grown too big.  Deleted that, fixed the script, and now there's 5gb free.

Still amazed I didn't see any movement in free disk space through the cleanups, deletions, and so on, but cest la vie.  Thanks much for the help folks!

---

