---
title: "Recovering data with testdisk"
date: 2009-08-14
forum: General Help
---

### Post by Niw0 on 2009-08-14
Hello to all of you out there!

I thought i was going to try out ubuntu on one of my computers today but i accidently installed on the harddrive with the pictures and movies of my little daughter.
After doing some googling and reading i found the program called 'testdisk'
If i got it all right, this program should be able to recover the files from the harddrive that were there before i iccidently installed ubuntu there.

Now i don't have a clue on how im going to proceed to get my files back, i dont know anything at all about ubuntu.

So if someone could guide me through in details on how to recover my files with testdisk it would be very much appriciated.

Kind regards,

---

### Post by TotoTheDog on 2009-08-14
Unluckily I am as new as you are, but I do hope that someone is able to help you recover your lost files!  Good Luck.

---

### Post by P4man on 2009-08-14
fist of all.. boot from the livecd. dont boot the machine from the harddrive you just installed on (/ruined), as every boot/usage will further decrease your odds of retrieving anything.

If you overwrote the drive contents.. its not gonna be easy to recover anything, and certainly dont expect to retrieve everything, but its worth trying to recover what you can if you dont have backups...

If no one else chimes in, I'll try write some help on using testdisk tomorrow, but be advised, its not for the faint hearted;

---

### Post by oldos2er on 2009-08-14
_[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)_

---

### Post by Niw0 on 2009-08-14
> **P4man said:**
> fist of all.. boot from the livecd. dont boot the machine from the harddrive you just installed on (/ruined), as every boot/usage will further decrease your odds of retrieving anything.

If you overwrote the drive contents.. its not gonna be easy to recover anything, and certainly dont expect to retrieve everything, but its worth trying to recover what you can if you dont have backups...

If no one else chimes in, I'll try write some help on using testdisk tomorrow, but be advised, its not for the faint hearted;

Live cd ? I'v only booted up the machine 2 times since I'v installed ubuntu, since im aware that everything i do will decrease my chances of retrieving my files.

Regards,

---

### Post by Niw0 on 2009-08-14
> **oldos2er said:**
> _[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)_

Does this method work even if i ONLY have ubuntu on the computer, no windows installed ?
I have 3 harddrives in that computer, can i make the files re-appear on one of the other harddrives ?

Regards,

---

### Post by P4man on 2009-08-14
The cd that (i assume) you used to install ubuntu from. You can boot from that cd, and install and run testdisk from there, so you're not doing additional harm to the harddisk.

If you can, have an (external) harddisk at hand thats as big as the drive or partition you want to recover. First thing Ill try to make you do is make a byte for byte copy of the damaged disk to another medium so that we dont lose more when our testdisk attempts fail.

---

### Post by P4man on 2009-08-14
> **Niw0 said:**
> Does this method work even if i ONLY have ubuntu on the computer, no windows installed ?

Yes. But like I said, dont use the installed ubuntu, use the cd. You dont need windows at this point.

> I have 3 harddrives in that computer, can i make the files re-appear on one of the other harddrives ?


Hopefully, if there is anything to recover.

---

### Post by P4man on 2009-08-14
Ok. here goes first steps.
Boot from the live cd. You should be able to access the web, and get to this forum.

You want to make a copy of your damaged partition first. You cant use regular copy tools, as the file system (ntfs) has been wiped and partially overwritten, so we are going to use the command "dd" to make a byte for byte copy. Lets first find out what partition you are trying to recover from. Open a terminal (application > accessoiries > terminal) and type

```
sudo fdisk -l
```

copy paste the output here, and tell us what drive contains and contained what.

---

### Post by Niw0 on 2009-08-14
> **P4man said:**
> Ok. here goes first steps.
Boot from the live cd. You should be able to access the web, and get to this forum.

You want to make a copy of your damaged partition first. You cant use regular copy tools, as the file system (ntfs) has been wiped and partially overwritten, so we are going to use the command "dd" to make a byte for byte copy. Lets first find out what partition you are trying to recover from. Open a terminal (application > accessoiries > terminal) and type

```
sudo fdisk -l
```copy paste the output here, and tell us what drive contains and contained what.

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97d52873

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29697   238541121   83  Linux
/dev/sda2           29698       30401     5654880    5  Extended
/dev/sda5           29698       30401     5654848+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc19b7b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30400   244187968+   7  HPFS/NTFS
markus@markus-desktop:~$

---

### Post by Niw0 on 2009-08-14
> **P4man said:**
> Ok. here goes first steps.
Boot from the live cd. You should be able to access the web, and get to this forum.

You want to make a copy of your damaged partition first. You cant use regular copy tools, as the file system (ntfs) has been wiped and partially overwritten, so we are going to use the command "dd" to make a byte for byte copy. Lets first find out what partition you are trying to recover from. Open a terminal (application > accessoiries > terminal) and type

```
sudo fdisk -l
```copy paste the output here, and tell us what drive contains and contained what.


It's the disk thats ubuntu is installed on that contained photos and videon from when my daughter was a little baby.

Regards,

---

### Post by P4man on 2009-08-14
I know, but I dont know how the drive is called or partitioned, and I cant give you further commands to type if I dont get the output of fdisk and you dont tell me which drive and partition has ubuntu now and how it was partitioned before you installed ubuntu and where we can put an image of the damaged disk and where we can hopefully put the recovered files.

Im trying to make this easy for you; but its a fairly complicated task. I could give broad strokes, but if you've never used linux, you're not going to manage if I only tell you to "clone the damaged partitino with dd", then "install testdisk from the repo's in a live session"

---

### Post by P4man on 2009-08-14
oops sorry, disregard above msg, I missed your reply on the previous page.. hang on


> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97d52873

Device Boot Start End Blocks Id System
/dev/sda1 * 1 29697 238541121 83 Linux
/dev/sda2 29698 30401 5654880 5 Extended
/dev/sda5 29698 30401 5654848+ 82 Linux swap / Solaris

So this first drive, was it one ntfs (windows) partition before you installed ubuntu on it? And do you have a 250 (+) GB spare drive we can use to clone this one to ? I assume sdb (the current windows drive) contains data you dont want wiped

---

### Post by tgalati4 on 2009-08-14
You say you have 3 disks?  Your fdisk is only showing two disks:

/dev/sda  250 GB which has 5 partitions and presumably contains Ubuntu.
/dev/sdb  250 GB which has one partition and contains an NTFS partition, presumably formatted by windows.

You should have an extra drive (perhaps an external USB drive or thumb drive) to recover files to.  Let's call this /dev/sde (your numbering will be different)

Boot the Live CD.  Open a terminal.  ping [www.google.com](www.google.com) (control-C to quit).  This ensures you have network connectivity.

sudo apt-get install testdisk
photorec /dev/sda

Choose /dev/sde1 (or whatever your sudo fdisk -l tells you your external drive is)

Let it run.  Photorec scans the entire disk and looks for picture/video headers and follows the sector trail to reconstitute the files.

I'm not confident you find much since a typical Ubuntu installation does a quick format on the disk and then the installation will occupy the first ~3 GB of disk space.  So you will probably only able to recover anything after the first 3 GB that was overwritten.  I'm not sure how destructive the ext3 quick format is, but you will find out soon enough.

The purpose of the Live CD is to experience Ubuntu and become familiar with it before installing.  You fell into two common pitfalls.  Installing to the wrong disk or partition (wiping out something critical) and not having a backup.

Your next installation will be much smoother.

---

### Post by Niw0 on 2009-08-14
> **P4man said:**
> oops sorry, disregard above msg, I missed your reply on the previous page.. hang on




So this first drive, was it one ntfs (windows) partition before you installed ubuntu on it? And do you have a 250 (+) GB spare drive we can use to clone this one to ? I assume sdb (the current windows drive) contains data you dont want wiped

Yes it was an NTFS and i had windows on it earlier, and it was on this drive the files were on, then i installed unbuntu.
I have no current windows drive or i understood you wrong perhaps.
Yes, I'v got another 250gig.

---

### Post by Niw0 on 2009-08-14
> **tgalati4 said:**
> You say you have 3 disks?  Your fdisk is only showing two disks:

/dev/sda  250 GB which has 5 partitions and presumably contains Ubuntu.
/dev/sdb  250 GB which has one partition and contains an NTFS partition, presumably formatted by windows.

You should have an extra drive (perhaps an external USB drive or thumb drive) to recover files to.  Let's call this /dev/sde (your numbering will be different)

Boot the Live CD.  Open a terminal.  ping [www.google.com]("http://www.google.com") (control-C to quit).  This ensures you have network connectivity.

sudo apt-get install testdisk
photorec /dev/sda

Choose /dev/sde1 (or whatever your sudo fdisk -l tells you your external drive is)

Let it run.  Photorec scans the entire disk and looks for picture/video headers and follows the sector trail to reconstitute the files.

I'm not confident you find much since a typical Ubuntu installation does a quick format on the disk and then the installation will occupy the first ~3 GB of disk space.  So you will probably only able to recover anything after the first 3 GB that was overwritten.  I'm not sure how destructive the ext3 quick format is, but you will find out soon enough.

The purpose of the Live CD is to experience Ubuntu and become familiar with it before installing.  You fell into two common pitfalls.  Installing to the wrong disk or partition (wiping out something critical) and not having a backup.

Your next installation will be much smoother.

I have a third disk yes, but it's an IDE disk so i had to disconnect that one to use the IDE cabel to the dvd reader.

---

### Post by P4man on 2009-08-14
this other 250Gb is that the one we are seeing, or another external you havent connected yet?

BTW, I see you're still not on the livecd.. its really best you do so now..

im assuming the 250 sdb drive currently has no data you want to keep. If thats a wrong assumption, then dont proceed. If its correct, **from a live cd** enter this in a terminal:

```
sudo dd if=/dev/sda of=/dev/sdb bs=2048
```

this will WIPE the contents of sdb and replace it with an identical copy of the damaged drive!

If you dont want to do that, we can make a compressed image and write it without wiping the drive if you got enough free space on it, but youll have to mount the drive, so ill wait for your response

once you've done that, follow tgalati4's advice. If you mess anything up in testdisk you'll now have a post mortem backup at least of your ruined drive :s

---

### Post by P4man on 2009-08-14
> **tgalati4 said:**
> I'm not confident you find much since a typical Ubuntu installation does a quick format on the disk and then the installation will occupy the first ~3 GB of disk space.  So you will probably only able to recover anything after the first 3 GB that was overwritten.  .

on the bright side, he had windows installed on it, and no need to recover that: But im unsure if either or both windows and linux really install at the beginning of the disk. lets hope they install in similar ways

---

### Post by Niw0 on 2009-08-14
> **P4man said:**
> this other 250Gb is that the one we are seeing, or another external you havent connected yet?

BTW, I see you're still not on the livecd.. its really best you do so now..

im assuming the 250 sdb drive currently has no data you want to keep. If thats a wrong assumption, then dont proceed. If its correct, **from a live cd** enter this in a terminal:

```
sudo dd if=/dev/sda of=/dev/sdb bs=2048
```this will WIPE the contents of sdb and replace it with an identical copy of the damaged drive!

If you dont want to do that, we can make a compressed image and write it without wiping the drive if you got enough free space on it, but youll have to mount the drive, so ill wait for your response

once you've done that, follow tgalati4's advice. If you mess anything up in testdisk you'll now have a post mortem backup at least of your ruined drive :s


I'm just going to copy some files i want to keep onto another harddrive, then i can do what you said.

---

### Post by rbc on 2009-08-14
Niw0,
A couple of things to warn you about before you start, not to scare you off, but just so you don't get panicked along the way....that dd command, even going from internal drive to internal drive, is going to take a while. And after you hit Enter, the cursor is just going to sit there, blinking, until it is finished. Making this clone, though, is absolutely the smart thing to do. The photorec recovery is also going to take a while, but you sound like a patient person. And the last warning, when your friends and family find out you have photorec, and used it, they are going to be bringing every piece of digital media they have to you and asking you to please get back from photos they accidentally deleted.

---

### Post by iDIEDaLONGtimeAGO on 2009-08-14
i was using photorec to recover media files from a ntfs partitions i accidentally messed up with. I started by looking for all .amr and ,mpg files. The photorec wiki does mention that recovered files may exceed the original files in terms of filesize. But it seems extreme in my case. All my original .amr files are less than 1mb and each of the recoverd ones exceeds 200mb, and in some cases almost 600mb for 1mb original file?
 This isnt right at all, is it?
 Also i want to specifically look for .avi files but the filetypes filters in options doesnt have .avi. .mpg doesnt list any .avis. I cannot let it look for all the filetypes because it just uses way too much disk space and im short on storage. Anyway how i could selectively look for .avi files and fix the .amr issue ( if it indeed is a problem) ?

---

### Post by michy99 on 2009-08-14
> **iDIEDaLONGtimeAGO said:**
> i was using photorec to recover media files from a ntfs partitions i accidentally messed up with. I started by looking for all .amr and ,mpg files. The photorec wiki does mention that recovered files may exceed the original files in terms of filesize. But it seems extreme in my case. All my original .amr files are less than 1mb and each of the recoverd ones exceeds 200mb, and in some cases almost 600mb for 1mb original file?
 This isnt right at all, is it?
 Also i want to specifically look for .avi files but the filetypes filters in options doesnt have .avi. .mpg doesnt list any .avis. I cannot let it look for all the filetypes because it just uses way too much disk space and im short on storage. Anyway how i could selectively look for .avi files and fix the .amr issue ( if it indeed is a problem) ?

It would be better to start your own thread instead of hijacking one in the middle of fixing someone else's problem.

---

### Post by Niw0 on 2009-08-14
> **rbc said:**
> Niw0,
A couple of things to warn you about before you start, not to scare you off, but just so you don't get panicked along the way....that dd command, even going from internal drive to internal drive, is going to take a while. And after you hit Enter, the cursor is just going to sit there, blinking, until it is finished. Making this clone, though, is absolutely the smart thing to do. The photorec recovery is also going to take a while, but you sound like a patient person. And the last warning, when your friends and family find out you have photorec, and used it, they are going to be bringing every piece of digital media they have to you and asking you to please get back from photos they accidentally deleted.


The time it might take is not a problem, i got several other computers and digital devices to entertain myself with, and my family, so it's always something to do :)

---

### Post by iDIEDaLONGtimeAGO on 2009-08-14
> **michy99 said:**
> It would be better to start your own thread instead of hijacking one in the middle of fixing someone else's problem.

Actually the problems similar and im sure had i started a new thread u would have been the first one to accuse me of not looking thru the forum and and starting an unneeded thread. The least u can do if not helping is dont preach. Btw i wonder how does ur rant helps this thread, maybe another post to increase ur count ?

---

### Post by rbc on 2009-08-14
Good to hear. For what it's worth, I have always had very, very good luck using photorec for deleted files, and even partitions that have been reformatted. Your case is a tad more drastic, but I hope all goes well

---

### Post by tgalati4 on 2009-08-14
Photorec is impressive.  Yes, you sometimes get large files.  Simply open in gimp, and resave and it should truncate.  Photorec is just following a sector chain, and sometimes there are large empty blocks that get appended to a valid photo.

Of course, depending on the damage, photorec may have problems piecing a photo together, so sometimes you will get gibberish.

---

### Post by aysiu on 2009-08-14
I've used Photorec at least four times to recover deleted files, and it's worked every time, even after a reformat, even after a reimaging.

Here's a step-by-step guide on Photorec using the Ubuntu CD (screenshots included):
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles](http://www.psychocats.net/ubuntucat/recoverdeletedfiles)

---

### Post by Niw0 on 2009-08-15
> **tgalati4 said:**
> You say you have 3 disks?  Your fdisk is only showing two disks:

/dev/sda  250 GB which has 5 partitions and presumably contains Ubuntu.
/dev/sdb  250 GB which has one partition and contains an NTFS partition, presumably formatted by windows.

You should have an extra drive (perhaps an external USB drive or thumb drive) to recover files to.  Let's call this /dev/sde (your numbering will be different)

Boot the Live CD.  Open a terminal.  ping [www.google.com]("http://www.google.com") (control-C to quit).  This ensures you have network connectivity.

sudo apt-get install testdisk
photorec /dev/sda

Choose /dev/sde1 (or whatever your sudo fdisk -l tells you your external drive is)

Let it run.  Photorec scans the entire disk and looks for picture/video headers and follows the sector trail to reconstitute the files.

I'm not confident you find much since a typical Ubuntu installation does a quick format on the disk and then the installation will occupy the first ~3 GB of disk space.  So you will probably only able to recover anything after the first 3 GB that was overwritten.  I'm not sure how destructive the ext3 quick format is, but you will find out soon enough.

The purpose of the Live CD is to experience Ubuntu and become familiar with it before installing.  You fell into two common pitfalls.  Installing to the wrong disk or partition (wiping out something critical) and not having a backup.

Your next installation will be much smoother.

When i write sudo apt-get install testdisk in terminal, it says it can't find the package testdisk.

what am i doing wrong ?

---

### Post by P4man on 2009-08-15
maybe testdisk is in the universe or multiverse repositories (ie, not supported by ubuntu developpers).  You'll have to enable those repositories, it is explained in aysiu's link.

---

### Post by Niw0 on 2009-08-15
well i got the recovery process going now, i just hope i did it all right and that it hopefully can recover my files.

---

### Post by Niw0 on 2009-08-15
wooow ! It recovered all of my files that were there before the installation!

I'd like to thank all of you very much !

Kind regards,

---

### Post by P4man on 2009-08-15
Glad to hear that, you are one lucky man. Lol!

Now dont forget to make a backup this time :) and good luck with ubuntu. Im sure we'll see here again soon for some other question :D

---

### Post by Niw0 on 2009-08-16
> **P4man said:**
> Glad to hear that, you are one lucky man. Lol!

Now dont forget to make a backup this time :) and good luck with ubuntu. Im sure we'll see here again soon for some other question :D

Edit on that, i discovered that 2 films were not recovered but it was ordinary films and not any of my daughter so that's nothing, amazing program i must say!

haha yeah i probably will return with yet another question one day.

Cheers!

---

