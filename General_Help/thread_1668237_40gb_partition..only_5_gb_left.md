---
title: "40gb partition..only 5 gb left"
date: 2011-01-16
forum: General Help
---

### Post by abdusamed on 2011-01-16
I initially installed ubuntu on 40gb partition.. but since 7 months or so. now I only have 3 gigs left.

I don't know where all that space went. Yes I have downloaded couple of softwares and everything but most of them are barely 30 mb or so! 

I installed bleachit..it sayign it will only free up 800 mb..my video document folder has only 10 gig of data.. 

Is ubuntu that big? 30gb+?

plz tell me what to do.. my trash is empty...

---

### Post by muteXe on 2011-01-16
Take a look at 'df' program. 
```

man df

```

edit: and 'du'
[http://linux.byexamples.com/archives/39/checking-disk-space-using-df-and-du/](http://linux.byexamples.com/archives/39/checking-disk-space-using-df-and-du/)

---

### Post by abdusamed on 2011-01-16
```

bahie@bahie-laptop:~$ df --total 
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             39223932  31756380   5475056  86% /
none                   2005132       332   2004800   1% /dev
none                   2012492       340   2012152   1% /dev/shm
none                   2012492       240   2012252   1% /var/run
none                   2012492         0   2012492   0% /var/lock
none                   2012492         0   2012492   0% /lib/init/rw
/dev/sda4            314448276 250927340  63520936  80% /media/TreckData
/dev/sdb5            312568828 231234200  81334628  74% /media/E26090D36090B031
total                676296136 513918832 160384808  77%
bahie@bahie-laptop:~$ df --all 
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             39223932  31756384   5475052  86% /
proc                         0         0         0   -  /proc
none                         0         0         0   -  /sys
none                         0         0         0   -  /sys/fs/fuse/connections
none                         0         0         0   -  /sys/kernel/debug
none                         0         0         0   -  /sys/kernel/security
none                   2005132       332   2004800   1% /dev
none                         0         0         0   -  /dev/pts
none                   2012492       340   2012152   1% /dev/shm
none                   2012492       240   2012252   1% /var/run
none                   2012492         0   2012492   0% /var/lock
none                   2012492         0   2012492   0% /lib/init/rw
binfmt_misc                  0         0         0   -  /proc/sys/fs/binfmt_misc
cgroup                       0         0         0   -  /dev/cgroup/cpu
gvfs-fuse-daemon             0         0         0   -  /home/bahie/.gvfs
/dev/sda4            314448276 250929640  63518636  80% /media/TreckData
/dev/sdb5            312568828 231234200  81334628  74% /media/E26090D36090B031

```

um..i need more folder info

---

### Post by abdusamed on 2011-01-16
ran du... more info :)

---

### Post by cipherboy_loc on 2011-01-16
While df and du are good to a certain extent, you almost need a graphical tool for disk monitoring. That's why I prefer to use baobab (applications -> Accessories -> Disk Usage) or something of the sorts. Launching baobab from the terminal gives you the same result. With the graphical interface, it is easy to see which are the largest folders. Run it on / rather than /home.

When you set it up, did you tell it to enculturation your documents? If so then other folks are having issues with disk usage (except in the order of MBs left rather then GBs). Search the forum for a post relating to low disk space with ecryptfs.



Sorry if that wasn't clear; it is 3:00 A.M.
Cipherboy

---

### Post by muteXe on 2011-01-16
I guess you didn't wanna read the man pages...

Check out this page:
[http://www.linfo.org/du.html](http://www.linfo.org/du.html)

in particular, the section called "Using du With Filters". You can grep for 'M' or 'G' to find the large folders.  It'd certainly give you a good starting point.

---

### Post by abdusamed on 2011-01-17
the du and df command fixed my prob.. but i wish it was more gui like tuneup utilites's The disk explorer is...

---

