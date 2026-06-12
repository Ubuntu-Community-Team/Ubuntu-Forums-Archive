---
title: "24 GB Root directory running lw on Disc space"
date: 2011-12-28
forum: General Help
---

### Post by SuperFreak on 2011-12-28
I allocated 24 GB of space for my root directory partition(with separate Home and Swap partitions) and I am getting a low space warning coming up. I have Ubuntu 10.10 64 bit installed.
Can somebody help me find out how all this space is being taken up and how to clear it.

edit: a few screen shots one showing a folder with 128 TB of used space. Don't understand what is going on here

ed 2: rebooting cleared the kde file and freed up 8 gb of space. Should my root folder really be using 15 GB of space as Gparted says. I have lots of programs loaded but this still seems high

---

### Post by 2F4U on 2011-12-29
I would suggest that you enter this command in a terminal

```
df -h
```

I don't trust these GUI programs.

There is another useful command that helps to find the largest subfolders, for example

```
du -h /home
```

---

### Post by zero2xiii on 2011-12-29
Hay,

I have a 40gig allocation for my / (root) folder and a 250gig drive for my /home partions and my root has only 8% free space. So its not impossible. How many apps have you got installed? And is there any servers installed on the computer or maybe programs you run as root that create temp files?

Cherz

---

### Post by SuperFreak on 2011-12-29
```
david@ :~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              25G   15G  7.9G  66% /
none                  998M  280K  997M   1% /dev
none                 1004M   12K 1004M   1% /dev/shm
none                 1004M  332K 1004M   1% /var/run
none                 1004M  4.0K 1004M   1% /var/lock
/dev/sda7              53G   22G   29G  43% /home
/dev/sda6             749G  197G  552G  27% /media/Data
/dev/sdb5             1.9T  493G  1.4T  27% /media/Music
/dev/sda1             100G   28G   73G  28% /media/sda1
david@ :~$ 


```

This seems to show me that I have 15 GB used and 7.9GB free in my root partition which I already knew. Home is another partition entirely. Is it possible to see what the largest files in root are?

Thanks

---

### Post by mcduck on 2011-12-29
You can use the following command to list total sizes of directories and files (sorted from largest to smallest):

```
du -hs * | sort -hr
```

Run that in /, then cd to the largest directory, run again etc until you find where the space is used.

...or just use the Disc Usage Analyzer, it should be installed by default and gives you an easy graphical view of where the space is being used.

---

### Post by SuperFreak on 2011-12-29
I tried the command you gave (first I changed directories to / ) but I got cannot read permission denied

```
david@ :~$ cd /
david@ :/$ du -hs * | sort -hr
du: cannot read directory `etc/cups/ssl': Permission denied
du: cannot read directory `etc/ssl/private': Permission denied
du: cannot read directory `etc/ppp/peers': Permission denied
du: cannot read directory `etc/chatscripts': Permission denied
du: cannot read directory `home/david/root': Permission denied
du: cannot read directory `home/david/var/cache/ldconfig': Permission denied
du: cannot read directory `home/david/var/cache/system-tools-backends/backup': Permission denied
du: cannot read directory `home/david/var/log/gdm': Permission denied
du: cannot read directory `home/david/var/log/samba/cores': Permission denied
du: cannot read directory `home/david/var/tmp/kdecache-root': Permission denied
du: cannot read directory `home/david/var/spool/cron/crontabs': Permission denied
du: cannot read directory `home/david/var/spool/cron/atspool': Permission denied
du: cannot read directory `home/david/var/spool/cron/atjobs': Permission denied
du: cannot read directory `home/david/var/spool/cups': Permission denied
du: cannot read directory `home/david/var/lib/polkit-1': Permission denied
du: cannot read directory `home/david/var/lib/gdm': Permission denied
du: cannot read directory `home/david/var/lib/mysql': Permission denied
du: cannot read directory `home/david/var/lib/squeezeboxserver/cache/MySQL/slimserver': Permission denied
du: cannot read directory `home/david/var/lib/squeezeboxserver/cache/MySQL/mysql': Permission denied
du: cannot read directory `home/david/var/lib/sudo': Permission denied

```

By Disk Usage Analyzer do you mean the Disk Utility under the Administration menu. If so I don't see how to examine individual directories just the entire partition.

I am resigning myself to the likelihood that I have too many programs installed and will unistall some of the never used ones.

---

### Post by mcduck on 2011-12-29
Run the command with sudo if required. You'll still get some warnings about certain special files and probably stuff from /proc but just ignore them, they aren't really anything relevant (the special files that usually give warnings are rather few and small ones, and /proc is just a virtual filesystem and doesn't even exist on your drive)

No, I don't mean the Disk Utility, there really is a separate application called "Disk Usage Analyzer". It should be installed by default, and listed under the "Accessories" category. If you can't find it, look for "baobab" in Ubuntu's repositories to install it.

---

### Post by SuperFreak on 2011-12-29
Thank you McDuck
Disk Usage Analyzer proves to be just the thing I needed to show where my bigger folders were (usr and shr)

---

### Post by mcduck on 2011-12-29
No problem, it's a really nice tool indeed. :)

Just keep in mind that it will by default scan *all* available filesystems, not just a single partition, which works great for finding where the space is being used but often causes confusion when people try to use it to check the used/available space. You can still do that, though, just go to Edit/Preferences and disable all the other devices than the one you wish to scan.

It also has some know issues with virtual filesystems, it tends to count stuff like locations mounted through GVFS and encrypted home directories twice, once for the actual encrypted data on the drive and then again for the virtual filesystem used for the unencrypted access. Not much of a problem as long as you are aware of it (and it's easy to spot if that happens).

Edit: I just noticed you were wondering about the strange sizes of certain locations... Don't even bother checking things like used/available space of /proc, it's not actually located on your hard drive, it's a virtual filesystem presenting information about running processes and the system itself. (if you look at the drive when your Ubuntu system is not running /proc is just an empty directory). [http://en.wikipedia.org/wiki/Procfs]("http://en.wikipedia.org/wiki/Procfs") Same applies to some other system directories as well (/proc, /sys, /dev, /run and any GVFS or Fuse mounted location, for example).

---

