---
title: "Poblem with external drive"
date: 2012-09-23
forum: General Help
---

### Post by carusoswi on 2012-09-23
I have an Iomega 1tb drive formatted for Ext4.  I use the drive to back up my photos.  I can currently access anything on the drive, but after I open up several files, the drive starts to report corrupted files.  The activity light starts flickering and never stops, the drive's icon drops off my nautilus screen, and I can no longer open files (although I can explore to them).

I thought I would copy the entire contents of the drive to a WDDigital drive that I use for that purpose, but, again, I can only copy four files before the drive reports an error in copying a file.

Once I power down the external, I can power it back up again and access any file on the drive until this problem starts all over again.

What do you think is going on.

The drive is new and has seen very little use.

Suggestions most appreciated (BTW, the info on the drive is backed up elsewhere).

Caruso

---

### Post by thnewguy on 2012-09-23
Sounds like the drive is failing. If it's new you should probably return it and get another one under warranty.

---

### Post by carusoswi on 2012-09-23
> **thnewguy said:**
> Sounds like the drive is failing. If it's new you should probably return it and get another one under warranty.

I appreciate your response, but I am skeptical about the conclusion that the drive is failing.  I am experiencing many problems right now with Ubuntu 12.04.  Right now I am responding via Win7 because a recent problem I experienced with Ubuntu has reappeared.  It will not boot up.  Trying recovery does not work, trying previous versions brings up a message about a graphics driver problem, and my wireless mouse and built-in keyboard are not functional, so I cannot even get into a previous version to explore the problem.

I will get my hands on a previous version of Ubuntu and try that before I give up on the drive.

I do appreciate your response, however.

Caruso

---

### Post by zero2xiii on 2012-09-23
Hay.

Just out of curiosity, what does creating an image from the drive using dd yield? This sounds like a usb enumeration issue, but I can't be sure without you testing a few tedious things.

Cherz

---

### Post by carusoswi on 2012-09-24
> **zero2xiii said:**
> Hay.

Just out of curiosity, what does creating an image from the drive using dd yield? This sounds like a usb enumeration issue, but I can't be sure without you testing a few tedious things.

Cherz

Sorry, but what is dd?
Thanks for the reply.
Caruso

---

### Post by alphaamanitin on 2012-09-24
```
dd
``` Is the command, data dump, (think), used to clone drives and the like.  

First, does the drive have these same type of issues in a liveCD?

Regardless, depending on how important the files are (sounds like they are pretty damn important), I would IMMEDIATELY clode the drive via the above command.

[SIZE="4"][COLOR="Red"]THIS IS IMPORTANT READ THE BELOW CAREFULLY!!![/COLOR][/SIZE]

here is a sample of the dd command ASSUMING that sdb is your external drive you want to back up and sdc is the new drive to back it up to

```
sudo dd if=/dev/sdb of=/dev/sdc bs=XXM conv=notrunc,noerror
```

[size="4"][color="Red"]NEVER SWITCH THE "IF" AND "OF" UNLESS YOU WANT TO COMPLETELY, AND IRREVERSIBLY DESTROY ALL DATA ON THE DRIVE!!!![/COLOR][/SIZE]

IF means input file, of means output file.  As I said, reverse these by accident and you just wiped the drive were NO ONE will ever recover your data, period. For, bs=XXM, XX should be a number, if you have a fast processor and bunches of RAM you can set it pretty high, 16 or 32.  This is the block size, higher number means faster cloning, but there is a max limit to your hardware.  the conv=notrunc,noerror makes it make an exact clone.  If you get errors during this process you have HD problems.  Also, it there may need to be a / after the sdb & sdc, so /dev/sdb/ and /dev/sdc/.  I don't think this is the case but I cannot remember 100%.  If it is working you will only see a blinking curser.  To check the progress follow the instructions here:

[http://linuxcommando.blogspot.com/2008/06/show-progress-during-dd-copy.html]("http://linuxcommando.blogspot.com/2008/06/show-progress-during-dd-copy.html")

It should go without saying you have to use a hard drive of equal or greater size to back it up to.  If it works perfectly, the drive will be the EXACT same, same drive name, same file structure, hell even same UUID.

AlphaA

---

### Post by carusoswi on 2012-09-29
> **alphaamanitin said:**
> ```
dd
``` Is the command, data dump, (think), used to clone drives and the like.  

First, does the drive have these same type of issues in a liveCD?

Regardless, depending on how important the files are (sounds like they are pretty damn important), I would IMMEDIATELY clode the drive via the above command.

[SIZE="4"][COLOR="Red"]THIS IS IMPORTANT READ THE BELOW CAREFULLY!!![/COLOR][/SIZE]

here is a sample of the dd command ASSUMING that sdb is your external drive you want to back up and sdc is the new drive to back it up to

```
sudo dd if=/dev/sdb of=/dev/sdc bs=XXM conv=notrunc,noerror
```

[size="4"][color="Red"]NEVER SWITCH THE "IF" AND "OF" UNLESS YOU WANT TO COMPLETELY, AND IRREVERSIBLY DESTROY ALL DATA ON THE DRIVE!!!![/COLOR][/SIZE]

IF means input file, of means output file.  As I said, reverse these by accident and you just wiped the drive were NO ONE will ever recover your data, period. For, bs=XXM, XX should be a number, if you have a fast processor and bunches of RAM you can set it pretty high, 16 or 32.  This is the block size, higher number means faster cloning, but there is a max limit to your hardware.  the conv=notrunc,noerror makes it make an exact clone.  If you get errors during this process you have HD problems.  Also, it there may need to be a / after the sdb & sdc, so /dev/sdb/ and /dev/sdc/.  I don't think this is the case but I cannot remember 100%.  If it is working you will only see a blinking curser.  To check the progress follow the instructions here:

[http://linuxcommando.blogspot.com/2008/06/show-progress-during-dd-copy.html]("http://linuxcommando.blogspot.com/2008/06/show-progress-during-dd-copy.html")

It should go without saying you have to use a hard drive of equal or greater size to back it up to.  If it works perfectly, the drive will be the EXACT same, same drive name, same file structure, hell even same UUID.

AlphaA

Thanks for this info.  I don't have time during the week to fool around with this drive, but hooked it up again this morning, and it seems to be working just fine.  I am in the process of backing everything up from that drive to a WD TV Hub drive in the basement.

The info on this drive consists of photos, digital and analog that have been digitized over the years.

The external drive, itself, has been used as a backup only.

This is off topic, but my ubuntu OS is broken at the moment (will not boot - some error message about a broken pipe).

Since I cannot access this external EXT4 volume from Ubuntu, I did a search and found a little windows ap called Ext2explore which allows me to explore and copy files/folders from the EXT4 volume to my WD TV Hub drive via Win7.

When I finish the backup, I will probably reinstall Ubuntu on my dual-boot laptop to fix whatever problem has caused it to misbehave.

In all my years of working with computers, I've never had an Ubuntu installation act up like this one has - don't know what suddenly caused the problem.

My laptop is relatively new - an Asus G74 purchased this past February.

Sorry for the off topic, but hoping that my problem has vanished.

Will look to this thread in the future if it rears its head again.

Thanks to all.

Caruso

---

