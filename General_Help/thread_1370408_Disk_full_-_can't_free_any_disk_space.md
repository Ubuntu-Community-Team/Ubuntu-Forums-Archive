---
title: "Disk full - can't free any disk space"
date: 2010-01-02
forum: General Help
---

### Post by meatychunks on 2010-01-02
Hi,

I'm running mythbuntu 9.04 and am having an issue with disk space.

I try 'rm' various log files but the space I free up lasts less than a minute before the disk reports as being full once more.

df -Th | sort gives:
> 
/dev/sda1     ext3    8.3G  7.9G     0 100% /
/dev/sda6     ext3    138G  125G  6.3G  96% /music
/dev/sda7      xfs    783G  617G  167G  79% /videos
/dev/sdb2      xfs    344G  242G  103G  71% /recordings
/dev/sr0       udf    7.5G  7.5G     0 100% /media/cdrom0
Filesystem    Type    Size  Used Avail Use% Mounted on
lrm          tmpfs    881M  2.2M  879M   1% /lib/modules/2.6.28-16-generic/volatile
tmpfs        tmpfs    881M     0  881M   0% /dev/shm
tmpfs        tmpfs    881M     0  881M   0% /lib/init/rw
udev         tmpfs    881M  152K  881M   1% /dev
varlock      tmpfs    881M     0  881M   0% /var/lock
varrun       tmpfs    881M  408K  880M   1% /var/run


There's nothing enormous in /var/log and my trash and the root trash are empty.

I'm curious as to why size and used fields are not the same despite 100% usage being reported on sda1...

Any help always appreciated.

---

### Post by PeEllAvaj on 2010-01-02
As to why Use% and Avail are reporting conflicting things, I assume this has to do with the fact that in Linux, if a file is still in use when you delete it, it isn't actually deleted until the computer is done with it.

You could get really fancy and figure out what files are still open on your system with lsof, but I would recommend you try something simpler.

Go into a folder that is full (such as your / right now), and type "du -s | sort -n", and this will give you a list of the sizes of all of the folders at that level.  Pick the biggest / most unusual one and recurse.  When you find things you can delete, delete them.  If I had to guess, I would say that your /home/ folder is filling up with something.

There are gui apps and ways of doing this recursively, but this should give you enough data to isolate the problem.

Good luck!

---

### Post by meatychunks on 2010-01-02
Thanks.

The du command gives me:
> 
du: cannot access `./proc/27085/task/27085/fd/3': No such file or directory
du: cannot access `./proc/27085/task/27085/fdinfo/3': No such file or directory
du: cannot access `./proc/27085/fd/3': No such file or directory
du: cannot access `./proc/27085/fdinfo/3': No such file or directory
1039720846	

...which isn't telling me much. Any further hints?

My home folder is only 98Mb.

---

### Post by fraktalek on 2010-01-02
You didn't wait long enough for "du" to produce actual results.

I'd suggest rather ```
du -h /
``` it will produce *h*uman readable numbers and I guess the sorting isn't really necessary..

//EDIT: 
It takes along because it computes sizes for all the directories. It will be faster if you use the command directly on those directories which are on the / mount point. Then use du -sh so that it tells you only the size of the whole directory including subdirectories but without reporting sizes of all the subdirectories.

---

### Post by prshah on 2010-01-02
> **meatychunks said:**
> I try 'rm' various log files but the space I free up lasts less than a minute before the disk reports as being full once more.

Clearing log files will not free up much space. Try removing apt-downloaded installation DEBs with the command```
sudo apt-get clean
``` Or simply delete all files in /var/cache/apt/archives/

[s]Also try emptying the trash (or delete /.Trash-1000 or similar directories).[/s] Ok you've already done that.

You can use baobab (Disk Usage Analyzer) to figure out what is taking the maximum space on your disk.

---

### Post by rnerwein on 2010-01-02
hi meathychunks
i agree with peEllavaj - if there is a file is removed but still openend from by a process the du kommand can't see it but df do. du reads from the directories and df is reading from the filesystem.
the only way to figure out what's going on (without a reboot ) is the usage of lsof (i'll prefere the lsof because i want to see why is there - if it is - a file in use but removed and who is the owner and the process of this file !!!. before all this action have a look at /var/crash if there is a huge vmcore ?
don't worry about the error messages of ur du command on /proc - this was a race condidition - the pid was "stat" and the process was gone before du can read the data.
ciao
   richi

---

### Post by meatychunks on 2010-01-02
No, I got no more from the du command... bit of messing about got me some more useful information, but nothing particularly enlightening.

I managed to reboot, but even after deleting another 32Mb of data before hand in order to backup my mysql database, it was full a couple of minutes later.

I'd already tried apt-get clean, but there was nothing to do. I'd also already tried baobab - or rather I tried to install but couldn't keep sufficient free disk space to install it.

Thanks for all your assistance but, whilst I hate walking away from an unsolved mystery, I simply can't spend any more time on this - I've been at it all day. I've finally resorted to restoring from a November backup...

Thanks again.

---

### Post by drs305 on 2010-01-02
This is a fairly thorough guide on finding out what is taking up space, how to find it and get rid of it:

[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

