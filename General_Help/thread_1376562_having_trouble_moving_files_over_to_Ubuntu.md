---
title: "having trouble moving files over to Ubuntu"
date: 2010-01-09
forum: General Help
---

### Post by the_egg_man on 2010-01-09
I'm brand new to Ubuntu/Linux. Right now i'm doing what i think they call a "dual boot" meaning when i turn my PC on, i can choose Vista or Ubuntu 9.10. I'm trying to get all my music/movies/pictures over to Ubuntu, and that's where my problem starts. I have over 25 gigs of music, 9 gigs of pics, and about 100 gigs of video/movies. I can go into Vista and move them over to my external hard drive, but when I try to create a new desktop folder on Ubuntu and then move them from ext. hard drive to the Ubuntu desktop, it's saying there's not enough room. Does anyone know where i can put my media in Ubuntu, so I can easily access my movies/music without having to plug in my ext hard drive each time? 

Any help at all would be appreciated. 

Thanks!

(and other than this issue, i'm liking Ubuntu a lot.)

---

### Post by michy99 on 2010-01-09
If your files are on your Vista partition, you can set it to automount when you boot and then you will be able to easily access your files. This page shows one way to auto mount your Windows partition:

[http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14](http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14)

---

### Post by the_egg_man on 2010-01-09
so, when i look at "Storage Device Manager" it says i only have one partition, "sda." Judging from that article, am I to assume it won't work?

---

### Post by michy99 on 2010-01-09
sda is the drive. The partitions on it will be sda1, sda2, etc.

If you are dual booting with Vista and Ubuntu, you have to have at least two partitions. If you open a terminal and enter this command, what is the output?```
sudo fdisk -l
```Note: that is a lower-case L at the end, not the number 1.

---

### Post by the_egg_man on 2010-01-09
so, i had to google to figure out how to even pull up the terminal for the 
"apt-get" thing, (showing you how novice i really am.) but, here's what came back...

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

Thanks for the help on this!

---

### Post by the_egg_man on 2010-01-09
and i think i may have just screwed up my ext. hard drive while trying to run that program. i plugged it back in and got the following error:

"Unable to mount FreeAgent Drive

Error Mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount/dev/sdg1 on /media/sdg1"

:(

---

### Post by michy99 on 2010-01-09
It looks like you typed in the command incorrectly. You can copy it from the box and paste it into the terminal to make sure you get it right.

Anyway, I looked at the screenshot of the Storage Device Manager on that page, and I think you just need to click that little triangle beside sda to show the partitions.

---

### Post by the_egg_man on 2010-01-09
okay, i copied it (not sure how i messed up such a basic command.)

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf22c39a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2017    16201521    7  HPFS/NTFS
/dev/sda2   *        2018       77825   608927760    7  HPFS/NTFS

---

### Post by SecretCode on 2010-01-09
You don't have a Linux partition on that drive. Meaning either: you have another hard drive where you've installed Ubuntu, or you installed it "inside" Windows using wubi (quite likely).

When you've booted into Ubuntu, on the "Places" menu, do you have any entries after "Computer" (and before "Network") that might represent those two partitions?

If not, we can easily mount them.

(It looks like /dev/sda1 is a recovery partition so you would want to mount /dev/sda2.)

---

### Post by michy99 on 2010-01-09
If you installed inside of Windows using Wubi, which is what it looks like, then your Windows files are listed under "Host". You don't have to mount anything else to access them.

---

### Post by the_egg_man on 2010-01-09
i do, i have "Recovery" and Free Agent Drive (which is my ext. hard drive.) i didn't think i was running it inside windows, but again, i'm brand new to all of this...

---

### Post by michy99 on 2010-01-09
Well, actually a Wubi install doesn't run inside windows, but it is installed inside your Windows partition as one big file. I don't care for that setup myself, but like I said, all your Windows files can be found under "Host" so don't worry about mounting anything.

---

### Post by the_egg_man on 2010-01-09
i went to the ubuntu site, downloaded/burned ISO file, then ran it. does that help?
and where would I find "host" it's not under "Places"?

---

### Post by michy99 on 2010-01-09
Look under Computer in Places and see if host is there.

---

### Post by superstalker on 2010-01-09
Did you install Ubuntu on the 13 gig partition or the 600gig partition?

---

### Post by the_egg_man on 2010-01-09
awesome!!! thanks so much, i found it and most of my files. 

seriously, thanks so much!

i'm going to keep test-driving ubuntu, and if it keeps impressing me and i can learn the ropes, how would i move all these files to ubuntu and get vista off my pc altogether? is that possible/recommended?

---

### Post by michy99 on 2010-01-09
Yes it is possible. Whether you want to keep Windows as a dual boot or get rid of it all together is a personal choice. A lot of people keep it around for one or two programs that they need or like. I finally dumped my XP about two weeks ago. It was just taking up space.

---

### Post by the_egg_man on 2010-01-09
so, i'm looking at all my files in the host section, but it's still not letting me copy them to desktop, saying there's not enough space. so, will i just need to settle for the fact that i'll have to go digging through all those folders to find my stuff, or will dropping Vista clear up more space allowing me to keep all my vids/mp3/pics directly on my desktop?

my wife is even less tech-savvy than myself, and i'm trying to make it easy for to find whatever movie or photo album she's looking for.

---

### Post by SecretCode on 2010-01-09
When you're running ubuntu, please enter the following two commands in a Terminal and post the output here:
```
df -h
sudo fdisk -l
```

---

### Post by michy99 on 2010-01-09
I would just leave the files where they are and make a bookmark to them in Places

---

### Post by superstalker on 2010-01-09
Go to you vids/mp3/pictures map, drag it onto the desktop and your done.

---

### Post by the_egg_man on 2010-01-09
brent@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G  9.0G  6.4G  59% /
udev                  1.6G  324K  1.6G   1% /dev
none                  1.6G  1.6M  1.6G   1% /dev/shm
none                  1.6G  116K  1.6G   1% /var/run
none                  1.6G     0  1.6G   0% /var/lock
none                  1.6G     0  1.6G   0% /lib/init/rw
/dev/sda2             581G  415G  167G  72% /host
/dev/sda1              16G   16G   11M 100% /media/Recovery
brent@ubuntu:~$ sudo fdisk -l
[sudo] password for brent: 

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf22c39a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2017    16201521    7  HPFS/NTFS
/dev/sda2   *        2018       77825   608927760    7  HPFS/NTFS

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       60801   488384001    7  HPFS/NTFS

---

### Post by superstalker on 2010-01-09
**You have an external harddrive that has your multimedia.**
You can automount it to your computer, using pysdm (reply #2) 

**You wish to copy them to your Ubuntu Home Folder.**
 If you do that the files will not be accesible by Windows.

**When you try to do copy you get an error.**
If you go to places -> Computer and rightclick on the partiton that has Ubuntu, how much free space do you have?

---

### Post by SecretCode on 2010-01-09
> **the_egg_man said:**
> ```
brent@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G  9.0G  6.4G  59% /
...
/dev/sda2             581G  415G  167G  72% /host
...
```

Because you have a wubi install, you only have 17GB in your root (/) partition, with only 6.4G free. You aren't going to be able to copy many files here ... and even if you do, you'll run into problems.

I think you should leave the files where they are and create mount points or symlinks (shortcuts) for easy finding.

Or you should partition your hard drive and install Ubuntu directly in a partition.

Either way, you'll probably need some help - and that's no problem!

---

