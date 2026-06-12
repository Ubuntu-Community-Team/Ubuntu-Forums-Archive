---
title: "filesystem too small"
date: 2009-07-09
forum: General Help
---

### Post by mulduvar on 2009-07-09
I just installed ubuntu on my computer and figured that it would install on a 140g partition that I had ready for it, but it only seems to have taken 20g (or 2g it confuses me when i look at all this different stuff) and now its too full to install any updates, or hold any additional files (or run at a decent speed)

I'm wondering what's the best course of action for getting the filesystem partition to take up more of my hdd. Should I just reformat it, or is there a handful of code I can use to tell it to resize itself?

i typed df -h in my terminal and got this output
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   63M  98% /
tmpfs                 1.4G     0  1.4G   0% /lib/init/rw
varrun                1.4G  104K  1.4G   1% /var/run
varlock               1.4G     0  1.4G   0% /var/lock
udev                  1.4G  172K  1.4G   1% /dev
tmpfs                 1.4G   84K  1.4G   1% /dev/shm
lrm                   1.4G  2.4M  1.4G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdc1             7.5G  3.2G  4.4G  42% /media/RALLY2
/dev/sda2             143G   17G  126G  12% /media/disk
/dev/sda3             141G   95M  140G   1% /media/disk-1

/dev/sda2 is my xp partition, so I wanna make /dev/sda3 part of my ubuntu partition. Thanks

---

### Post by wpshooter on 2009-07-09
I think you meant to say that you installed it on a 140G drive not partition.

It appears that you made the size of the Ubuntu partition only 2.3g.  Too small !!!

Needs to be about 10 to 15gb.

You should first go into Windows and run scandisk and defrag about twice and then reboot to the Ubunt live CD and use GPARTED to resize the Ubuntu partition to a greater amount.

P.S. - Another thing you need to do is make yourself a SEPARATE /home partition.  Might also want to make a /SWAP partition while you are at it, if you don't have one.

---

### Post by mulduvar on 2009-07-09
Okay, I'll come back later to tell you how that goes, thanks

---

### Post by mulduvar on 2009-07-09
> **wpshooter said:**
> 
P.S. - Another thing you need to do is make yourself a SEPARATE /home partition.  Might also want to make a /SWAP partition while you are at it, if you don't have one.

Alright, currently defragging my c: drive in windows.

it only sees the c: and e: hard drives, but not any other partitions when i look at it from my computer. is this normal? I can see them though when i look at my hard drive properties.

About your edit, how would you suggest i allocate the 142gb i have for these 3 drives?

---

### Post by mulduvar on 2009-07-10
Gparted couldn't resize the ubuntu partition for some reason, so i just deleted the empty partition and all ubuntu partitions, and partitioned them correctly upon installation of ubuntu.

---

