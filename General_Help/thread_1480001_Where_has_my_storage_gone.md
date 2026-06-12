---
title: "Where has my storage gone?"
date: 2010-05-11
forum: General Help
---

### Post by captainpotato on 2010-05-11
Hello,

I'm trying to solve a problem that has been annoying me for some time, but now it's reached the point of being critical - my storage has disappeared!

My system is a Kubuntu 9.10 install that, after KDE started playing up, was switched over to Gnome for the desktop. Other than the issue that I'm having, it's running fine.

I have two hard drives: a 160GB drive that contains / and a 500GB drive with a random collection of folders (photos and music mainly). /home is on the 160GB drive.

The 500GB drive is fine - I know exactly what is happening with it, but the 160GB drive is a mystery, as it has now has no free space at all on it. This is the breakdown of the folder sizes:
/bin: 5.1MB
/boot: 69MB
/dev: 448MB
/etc: 10.5MB
/home: 6.1GB
/lib: 462MB
/opt: 638.9MB
/root: almost nothing at all
/sbin: 7.4MB
/sys: 576.2MB
/usr: 3.5GB
/var: 2.1GB

The swap partition is 4GB; the main partition has around 155GB, according to cfdisk.

df lists the following:

Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sda1            149352384 141969840         0 100% /
udev                    771296       336    770960   1% /dev
none                    771296      2328    768968   1% /dev/shm
none                    771296        92    771204   1% /var/run
none                    771296         4    771292   1% /var/lock
none                    771296         0    771296   0% /lib/init/rw
/dev/sdd1            976760032 256609044 720150988  27% /media/Expansion Drive____
/dev/sdb1            484535504 416432708  43683596  91% /media/disk
/dev/sr2                 12020     12020         0 100% /media/VIRGIN BROADBAND

/dev/sdd1 is an external drive; /dev/sr2 is my 3G modem.

Anyway, that is what I can find on the system. The 160GB drive should have a huge amount of free space, but doesn't. Any idea where the space could be - and how do I recover it?

---

### Post by muteXe on 2010-05-11
Those folders you listed... Are you sure they are the only folders present on your sda1?

---

### Post by sbergman on 2010-05-11
Hi ,

I've noticed that df gives slightly different results when you run it as a user as compared to when you run it as root.

try: sudo df
and see what you get.

In my case the difference was only about 4K

My guess, is that theres a large file somewhere that the user doesnt have access to so when you 'df' as a normal user it isnt picked up. But thats just a guess....

---

### Post by john newbuntu on 2010-05-11
If you haven't already done so, from the root directory run:
```
du -xk | sort -n 
```
Look at the output from the bottom up and see if you can spot the culprit file/directory.

---

### Post by captainpotato on 2010-05-11
> **muteXe said:**
> Those folders you listed... Are you sure they are the only folders present on your sda1?

That was my first thought too, but unless I'm an idiot (very possible), I can't see what else there could be. There's nothing else hidden away with the mount points.

To make sure, I've run the Disk Usage Analyzer, and did discover another 5.3GB in a folder mounted on /media but that's it. I was going to attach an image of the output (but the system won't let me save the grab due to the lack of space), but to me it all looks fine to me. Other than for the fact that I'm missing a heap of storage - the total capacity is listed as 142.4GB,of which 135.4GB is used, but the sum of it all lists only 17.0GB.

There clearly *must* be something else, but I'll be buggered if I can find it.

The only thing I can think of is that I am running CrashPlan for backups, but I'm backing up to an external drive for that, and looking through the preferences for it, I cannot see anywhere that suggests that it is using the 160GB drive for backing up. And in any case, it needs a mount point to store the files, and there's nothing that I can see that it could be using.

---

### Post by captainpotato on 2010-05-11
> **sbergman said:**
> Hi ,

I've noticed that df gives slightly different results when you run it as a user as compared to when you run it as root.

try: sudo df
and see what you get.

In my case the difference was only about 4K

My guess, is that theres a large file somewhere that the user doesnt have access to so when you 'df' as a normal user it isnt picked up. But thats just a guess....

Unfortunately this hasn't detected anything else different.

---

### Post by captainpotato on 2010-05-11
> **john newbuntu said:**
> If you haven't already done so, from the root directory run:
```
du -xk | sort -n 
```
Look at the output from the bottom up and see if you can spot the culprit file/directory.

Thanks - I've never heard of this command before.

Okay, it looks like CrashPlan has been using the drive for backing up, in addition to the external drive, but mounting it on /media, in addition to the usual / mount point. I've found 129GB of rogue files there, which were only viewable to root.

Once I've cleared up some space (having checked that I'm not wiping my only backups), I'll obviously need to work out why it's been mounting the internal drive, when I've told it to only use the external drive.

Thanks!

---

