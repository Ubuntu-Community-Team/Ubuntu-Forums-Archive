---
title: "Full harddisk (seems to be in root)"
date: 2010-03-30
forum: General Help
---

### Post by Mistril Merendras on 2010-03-30
Hi, 

I just installed UBUNTU on my PB Laptop. I am new to this, but had my share of windows experience.

I used a partition of 30GB to install UBUNT and now (within a week or so) it sais the disk is full. I think that would be pretty impossible..but i would like to find out whats taking up this space. I cannot find it though.

I ran discus...it sais:

Mount           Total         Used         Avail      Prcnt      Graph
/               28.37 GB     25.32 GB      3.06 GB    89.2%   [*********-]
/sys                0 KB         0 KB         0 KB     0.0%   [----------]
+onnections         0 KB         0 KB         0 KB     0.0%   [----------]
+rnel/debug         0 KB         0 KB         0 KB     0.0%   [----------]
+l/security         0 KB         0 KB         0 KB     0.0%   [----------]
/dev            943.4 MB       264 KB     943.2 MB     0.0%   [----------]
/dev/shm        943.4 MB       220 KB     943.2 MB     0.0%   [----------]
/var/run        943.4 MB       192 KB     943.2 MB     0.0%   [----------]
/var/lock       943.4 MB         0 KB     943.4 MB     0.0%   [----------]
+ib/init/rw     943.4 MB         0 KB     943.4 MB     0.0%   [----------]
+media/data    218.93 GB    156.67 GB     62.25 GB    71.6%   [*******---]
+infmt_misc         0 KB         0 KB         0 KB     0.0%   [----------]
+uter/.gvfs         0 KB         0 KB         0 KB     0.0%   [----------]
+dia/cdrom0     540.0 MB     540.0 MB         0 KB   100.0%   [**********]


That would mean my "/  " is full isn it? But the "/  " is the root, yes? How can i find the files or app that is takin up this space? 

i tried "Disk Usage Analyzer", but it didnt help that much.

---

### Post by bigsmitty64 on 2010-03-30
Are you using 10.04 Lucid? If so, you're not alone:

[http://ubuntuforums.org/showthread.php?t=1442300](http://ubuntuforums.org/showthread.php?t=1442300)

I don't think it's figured out yet over there either, but at least you can follow that thread also, hopefully someone will figure it out. Good luck

---

### Post by plucky on 2010-03-30
This [link](http://ubuntuforums.org/showthread.php?t=898573) might help.

What version of Ubuntu are you running?

Good Luck

---

### Post by Mistril Merendras on 2010-03-30
THANKS! I SOLVED IT! 
THANKS TO [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573).
It was my Thrash. Allthough the commands didn't do the job (maybe i made a type error) nautilus erased the trash. 
Now i try using this to keep the thrash in check: 
[http://ubuntuforums.org/showthread.php?t=698649&highlight=trash](http://ubuntuforums.org/showthread.php?t=698649&highlight=trash)

My UBUNTU version:

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic

Result of emptying thrash:

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda6     ext4     29G  3.2G   24G  12% /
udev         tmpfs    944M  264K  944M   1% /dev
none         tmpfs    944M  220K  944M   1% /dev/shm
none         tmpfs    944M  192K  944M   1% /var/run
none         tmpfs    944M     0  944M   0% /var/lock
none         tmpfs    944M     0  944M   0% /lib/init/rw

---

### Post by bigsmitty64 on 2010-03-30
> **Mistril Merendras said:**
> THANKS! I SOLVED IT! 
THANKS TO [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573).


Theres one for the bookmarks! Glad you sorted it out!

---

