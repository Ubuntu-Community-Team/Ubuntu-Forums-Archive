---
title: "Rip DVD Into ISO Using Terminal"
date: 2010-08-17
forum: General Help
---

### Post by hex444b on 2010-08-17
I've looked through many other threads for help with my problem, but I'm unable to figure it out.

I'm trying to rip a DVD into an image using the command line. It works fine using Brasero, but I'm trying to write a script that would automate the process. I currently have a set of 10 DVDs and have already ripped one successfully using Brasero so I know it's not a problem with a missing library.

Here is my original script:
```
#!/bin/bash
echo "DVD Number?"
read DISK_NUMBER
dd if=/dev/cdrom of=/home/dk/Desktop/backup$DISK_NUMBER.iso
echo "Rip Complete."
umount /dev/cdrom
eject /dev/cdrom

```

But I got this message:
```
dd: reading `/dev/cdrom': Input/output error
5600+0 records in
5600+0 records out
2867200 bytes (2.9 MB) copied, 6.34481 s, 452 kB/s
Rip Complete.
```

Seeing how the DVD is a couple gigabytes large, it's clear that the rip was not successful.

I read in [another thread]("http://ubuntuforums.org/archive/index.php/t-6509.html") that I should unmount the DVD drive before trying to rip the DVD, so I modified the script:
```
#!/bin/bash
echo "DVD Number?"
read DISK_NUMBER
[COLOR="Red"]umount /dev/cdrom[/COLOR]
dd if=/dev/cdrom of=/home/dk/Desktop/backup$DISK_NUMBER.iso
echo "Rip Complete."
eject /dev/cdrom

```

However, I got the same error message as above. 
Does anyone know what I'm doing wrong or if there is another command line tool to rip DVDs? All suggestions are welcome.

---

### Post by TeoBigusGeekus on 2010-08-17
Change this
```
dd if=/dev/cdrom of=/home/dk/Desktop/backup$DISK_NUMBER.iso
```
to this
```
dd if=/dev/[COLOR="Red"]dvd[/COLOR] of=/home/dk/Desktop/backup$DISK_NUMBER.iso
```

---

### Post by davrosuk on 2010-08-17
This is going to be the copy protection causing this (I would have thought). The link below explains how to do what you want.

[http://ubuntuforums.org/showpost.php?p=3395414&postcount=25]("http://ubuntuforums.org/showpost.php?p=3395414&postcount=25")

---

### Post by hex444b on 2010-08-17
TeoBigusGeekus: I tried that and got the same message as before:
```
dd: reading `/dev/dvd': Input/output error
5600+0 records in
5600+0 records out
2867200 bytes (2.9 MB) copied, 2.88116 s, 995 kB/s
Rip Complete.

```
And please correct me if I'm wrong, but I believe that /dev/cdrom and /dev/dvd both just point to /dev/sr0 so it wouldn't really make a difference which one I use.

davrosuk: I'll give that one a try. Thanks for the link. In that post, the vobcopy line uses "/media/cdrom0". Something interesting that I noticed is that my laptop doesn't seem to have that path with or without anything within the drive. My desktop (also running Ubuntu) shows /media/cdrom and /media/cdrom0 but my laptop only displays a directory containing the inserted DVD's information. Do you know if that method would still work if I replaced "/media/cdrom0" with "/dev/sr0"?

EDIT: When I ran ```
vobcopy -v -m /media/BACKUP
```, the process stopped working with the following message:
```
 [Warn] Had to skip 0 blocks!  [Warn] Had to skip 0 blocks!  [Warn] Had to skip 0 blocks!  [Warn] Had to skip 0 blocks!  [Warn] Had to skip 0 blocks!  [Warn] Had to skip 0 blocks!  [Warn] Had to skip 0 blocks!  [Warn] Had to skip 0 blocks!  [Warn] Had to skip 0 blocks!  [Warn] Had to skip 1 blocks!  [Warn] Had to skip 1 blocks!  [Warn] Had to skip 1 blocks!  [Warn] Had to skip 1 blocks!  ^C

```

I then tried ```
vobcopy -v -m /dev/sr0
```, but got this message:
```
[Error] Hmm, weird, the dir video_ts|VIDEO_TS on the dvd couldn't be opened
[Error] The dir to be opened was: /dev/sr0/VIDEO_TS

```

Any suggestions for all this?

---

### Post by blur xc on 2010-08-17
I was getting this error for a few weeks and have been googling like crazy trying to solve it.  I heard mention in one or two posts about dirty/scratched disks causing this problem - so as a last resort (should have been my first) I cleaned the disk w/ rubbing alcohol and a microfiber cloth and had two successful images after that.  Both disks looked clean to my eye (I have pretty good vision), and only very slightly scratched.  

Good luck-

Oh, and btw- you can get cheap microfiber wash-cloths/towels from the automotive section of your local dept store (Target for me- their sold for drying/waxing cars).

BM

---

