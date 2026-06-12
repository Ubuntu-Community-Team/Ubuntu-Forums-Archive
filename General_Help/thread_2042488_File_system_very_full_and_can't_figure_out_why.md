---
title: "File system very full and can't figure out why"
date: 2012-08-14
forum: General Help
---

### Post by krumpy on 2012-08-14
I'm running 12.04 on both my laptop and desktop.  Both systems have separate partitions for /home and ./, however on my laptop root is ~9 GB, while on my desktop it's 71GB.  

It never used to be that large (~10GB previously), but it was complaining about space after I made the upgrade 11.04.  I'm not using much of my HD so I just expanded the partition.  However, it's complaining about space again and 71GB seems way too big for just the OS.  I can't figure out what's going on.  I thought maybe something got messed up with mounting my /home directory and now that's somehow mounted under root.  I've attached the results of disk analyzer (in the attachment), df, and du below:

Output from df -h:
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        77G   71G  2.3G  97% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           793M  1.1M  792M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  152K  2.0G   1% /run/shm
/dev/sda7       391G   66G  306G  18% /home
/dev/sdb1       3.9G  2.6G  1.3G  69% /media/401C-F38D
/dev/sdc1       3.3G  402M  2.9G  13% /media/Kindle
/dev/sdg1       3.8G  1.5G  2.4G  38% /media/CANON_DC
/dev/sr0        171M  171M     0 100% /media/CANON_IJ

Output from du -h --max-depth=1 ./:
72K    ./tmp
60G    ./home
18M    ./etc
8.4M    ./bin
4.0K    ./dev
9.0M    ./sbin
4.0K    ./selinux
8.3G    ./usr
0    ./proc
58M    ./boot
1.6M    ./root
4.0K    ./mnt
4.0K    ./cdrom
1.9G    ./var
286M    ./lib
0    ./sys
16K    ./lost+found
64G    ./media
4.0K    ./srv
1.2M    ./run
134G    ./

---

### Post by arnott on 2012-08-14
Your /home is 60G. Where is it mounted ?

---

### Post by Bucky Ball on 2012-08-14
Well, this can be a problem is using the 'Upgrade Release' function. The upgrade needs headroom as it needs to download and store things before installing. It will then delete that stuff when finished and you should have the room back. 

I had 8.04 on 10Gb and attempted to upgrade to 10.04 through update manager. Same deal, same complaints. I created another partition on a different drive and just did a clean install. Fine.

Not sure why you are getting the complaints now, though, but that explains why in the first instance. 15Gb should be more than enough for / (depending on how many apps you intend installing and what they are).

Is the issue with 'Netdrive'? If so, reveal the contents of that by clicking the triangle to the left of it.

PS: Yes, looks to me like you have everything mounted under /. Media should be there but /home should probably be further to the left (as / is) NOT under the /. If they are separate partitions I would have thought when they were both closed (by the triangle to the left) only / and /home should appear in that pane.

---

### Post by efflandt on 2012-08-15
If you mount /dev/sda5 from live/install iso, what does it show for **df -h**?  For example was there an existing /home with a bunch of stuff in it before you mounted a separate /home partition?  If so, you might want to empty that out while booted from live/install iso.

---

### Post by Bucky Ball on 2012-08-15
> **efflandt said:**
> If you mount /dev/sda5 from live/install iso, what does it show for **df -h**?  For example was there an existing /home with a bunch of stuff in it before you mounted a separate /home partition?  If so, you might want to empty that out while booted from live/install iso.

Makes sense. Could also copy the folders over to the /home partition, kill the directories in the directory /home and create symlinks in there connected to the directories now in the /home partition!

If you follow me. ;)

---

### Post by drs305 on 2012-08-15
Some of the commands and tips in this thread may also help you sort things out:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by krumpy on 2012-08-15
Thanks for taking a look at this everyone, but I've figured this out.  It boils down to me being kind of an idiot.  /home is indeed a separate partition and is mounted properly.  We just moved and I forgot to plug my NAS into the router, so when my daily backup script runs using rsync it was creating a local backup.  I've since modified my backup script to check that the drive is mounted before running.  The ./ partition is now only 12G. 

df -h

Filesystem                      Size  Used Avail Use% Mounted on
/dev/sda5                        77G   12G   61G  17% /
udev                            2.0G   12K  2.0G   1% /dev
tmpfs                           793M 1000K  792M   1% /run
none                            5.0M     0  5.0M   0% /run/lock
none                            2.0G  156K  2.0G   1% /run/shm
/dev/sda7                       391G   80G  291G  22% /home
/dev/sda3                       108G   81G   28G  75% /media/OS
MyBookWorld:/DataVolume/Public  929G  259G  670G  28% /media/netdrive

---

### Post by Bucky Ball on 2012-08-15
Ha! Good news you figured that out cause I don't think we ever would have got there!

Enjoy the setup and catch you round the forums. ;)

---

