---
title: "removing dual boot windows"
date: 2011-02-17
forum: General Help
---

### Post by +crypto on 2011-02-17
So I made my netbook a dual-boot machine about 2 months ago - it came with windows 7 and I added ubuntu. I've been running Ubuntu on my desktop machine for a while, so I'm pretty comfortable. 

Now I'd like to completely get rid of the windows partition on my netbook and make the whole thing ubuntu. However, I've downloaded and installed so many programs and packages and libraries that I don't want to have to do it again. Is there a way to remove the windows partition (basically expanding the ubuntu side) and keep my programs/settings/libraries/packages/etc on the linux side? Or do I have to erase the partitions and start over with a fresh install?

Thanks for your help...

---

### Post by TeoBigusGeekus on 2011-02-17
> **+crypto said:**
> Or do I have to erase the partitions and start over with a fresh install?
No.

Boot up with a live cd/usb, fire up gparted
```
gksu gparted
```
and format/expand the necessary partitions.

---

### Post by Megaptera on 2011-02-17
Just in case of hiccups, you could make a CD/DVD backup of your current 'tweaked' Ubuntu using Remastersys:

[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

---

### Post by Stephann on 2011-02-17
Congrats on ditching Windows!

First off, this is a *GREAT* opportunity for you to backup your existing system, in the event of any sort of serious crash.  My favorite backup tools are pretty simple; DD and GZIP.  Ideally, you'll have an external drive.

Boot to a live cd (or dvd or what not, the standard Ubuntu installation disc works nicely here.)  Then plug in your external hard drive, and make sure Ubuntu mounts it (usually, it's automounted in the /media directory.)  Next, you can run gparted to get a graphical view of your existing hard drive and which partitions are which (which ones are windows, which ones are Ubuntu.)  If you installed Ubuntu on one partition (the recommended 'new user' option) there should only be one, giving you something that might looks similar to: 

SDA1) EFI - (Windows 7 boot)
SDA2) Windows 7
SDA3) Ubuntu
SDA4) Swap

There might be another partition or two in there, depending on your system manufacturer (it's how they make restoration to factory settings work; it's basically just a windows installation disc.)

If your setup looks like what I've outlined, you'll want to do a disk dump of SDA3.  Make sure it's not mounted (you can type 'mount' at the command prompt to see a list of what is and isn't mounted; you can double check where your external drive is mounted at the same time.)

Now, at the command line, you'd punch in (assuming Ubuntu is at the third partition on device SDA)

sudo dd if=/dev/sda3 bs=4096 |gzip --fast > /media/EXTERNALDRIVELOCATION/ubuntu-backup-todaysdate.gzip

The command will run for a while.  There's no progress indicator, no spinning wheels or anything; the system is simply reading byte by byte the entire contents of the partition, from start to finish.  When it's finished, it'll spit out some stats on how much data it saved, and how long it took.  Depending on the partition size and disk speed, this might take ten minutes, or two hours (which is a good reason you might want to have your home directory separate from the rest of the system; a functioning Linux system with all the bells and whistles, minus your music, pictures, movies, etc is rarely larger than 10 Gigs.)  

From here, make sure you back up anything else on the machine (i.e. anything you might have in your windows partition, or from any other partitions you might have.)  Now you can wipe the entire drive, and dump the contents of your Ubuntu back to your computer.  This is a good time to consider a more sophisticated partitioning scheme - I'm happy to expand on that if you're interested in more.  But at minimum, I'd fire up Gparted, and

1) Initialize the disk (Device -> Create Paritition Table -> Apply).  Keeping an MS-DOS type partition table will make it easier to put Windows back on at some point, if you need.

2) Create a swap partition.  Four gigs should suffice for a desktop environment.

3) Create the Ubuntu/Linux partition.  It needs to be at least as large as the partition you just backed up.  Note that for this partition, you can leave it unformatted.  

Commit the changes with gparted.  In terminal, run 

sudo fdisk -l

It should indicate that your swap partition is on /dev/sda1 and your new ubuntu partition is on /dev/sda2

Now, back in the terminal, you'll run

sudo gunzip /media/EXTERNALDRIVELOCATION/ubuntu-backup-todaysdate.gzip | dd bs=4096 of=/dev/sda2

This shouldn't take quite as long as the original backup; again, it depends on how large the partition is.  When the command is finished, you should check to see if it worked.  Run

sudo fsck -f /dev/sda2

Now you need to update your bootstrap.  Switch to root:

sudo su 

Then:

mkdir /mnt/x
mount /dev/sda2 /mnt/x
mount --bind /dev /mnt/x/dev
mount --bind /sys /mnt/x/sys
mount --bind /proc /mnt/x/proc
chroot /mnt/x

This 'chroots' you into your system.  Run 

update-grub
grub-install /dev/sda 

Your system is now bootable.  Run

exit

and you'll exit your chroot environment.

Now you can run gparted to resize your ubuntu partition to occupy all of the space on your hard drive.  Again, this would be an ideal time to create a separate /home directory, though, and would make backing up your system in the future far quicker and easier.  I can outline those instructions if you're interested.

Another tip, is that you can also park a second copy of your backed up Ubuntu system on a partition near the end of your drive.  This, essentially, gives you a 'live' drive you can boot from, should you have a hiccup or run an update that breaks something substantial on your main system.  It would be as simple as creating a second linux partition with gparted, at the end of the disk, large enough to accommodate the ubuntu partition you just backed up on your external drive.  On a modern 500 gig drive, having a backup system that eats %5 of your drive can save you quite a bit of headache.

Regards,

Stephan

---

### Post by wilee-nilee on 2011-02-17
OP confirm your setup with a screen shot of gparted. We need to confirm this is a actual partitioned dual boot and not a wubi install from the live W7.

---

### Post by +crypto on 2011-02-17
Wow - thanks for all the replies, guys! Stephan, your info is awesome.

wilee-nilee, now that you mention it, I think mine is a wubi install. I suppose that complicates matters just a bit.

If i have to just wipe the drive and start all over, I can... I'd just rather not. Remastersys looks like it may be my best bet...

---

### Post by wilee-nilee on 2011-02-17
> **+crypto said:**
> Wow - thanks for all the replies, guys! Stephan, your info is awesome.

wilee-nilee, now that you mention it, I think mine is a wubi install. I suppose that complicates matters just a bit.

If i have to just wipe the drive and start all over, I can... I'd just rather not. Remastersys looks like it may be my best bet...

You can move a wubi to a regular partition.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by Stephann on 2011-02-17
I started typing a how-to on using rsync to back up your system, but realized that it was almost the same as the how-to wilee posted.  

In any event, if it starts getting more complicated, you can try and decide if it's quicker to just do a fresh installation (again, I highly recommend using at least a separate /home partition, and avoid lvm until you're much more comfortable with *nix) and configure it, than to attempt to convert the existing one.  Personally, I'd try converting it, and if it fails, you've learned a little and can start from scratch.

Good luck!

---

