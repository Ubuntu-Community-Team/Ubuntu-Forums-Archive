---
title: "Is there a way to safe-destroy all HDD data ( like, zero-filling ) ?"
date: 2009-07-22
forum: General Help
---

### Post by credobyte on 2009-07-22
Ok, I've a box which runs Windows XP and I want to get rid of it along with all my HDD history. What's the best way to destroy ALL data on my HDD so no one would ever be able to restore a single byte from it ? 
I mean, I will need it for installing Ubuntu - don't suggest me to throw it out of the window :D

Anyone ?

---

### Post by Cheesemill on 2009-07-22
Try DBAN
[www.dban.org]("http://www.dban.org")

---

### Post by credobyte on 2009-07-22
> **Cheesemill said:**
> Try DBAN
[www.dban.org]("http://www.dban.org")

Thnx, tough, there's a problem .. I can't download it ( SourceForge is broken or files removed ).

---

### Post by philcamlin on 2009-07-22
[http://download.cnet.com/Darik-s-Boot-and-Nuke-for-CD-and-DVD/3000-2094_4-10151762.html]("http://www.dban.org/download:popcorn:")

---

### Post by Shazaam on 2009-07-22
With todays forensic tools I think it will still be possible to get SOME info off of the hd platters after a software wipe. In that situation rendering the platters to dust is the only way to be sure they cannot be read.
If all you are after is a relatively clean slate I second using  dban or something similar.

---

### Post by bacil on 2009-07-22
use old and trusted

```
dd if=/dev/null of=/dev/YOURHDD
```

use full hdd not partition if you want to destroy whold disk or partiton if you only want to wipe out partition eg. /dev/sda and /dev/sda1 for partition

---

### Post by piratebill on 2009-07-22
> **Shazaam said:**
> With todays forensic tools I think it will still be possible to get SOME info off of the hd platters after a software wipe. In that situation rendering the platters to dust is the only way to be sure they cannot be read.
If all you are after is a relatively clean slate I second using  dban or something similar.

Not entirely true.  Read this tutorial on data sanitation here:
[http://cmrr.ucsd.edu/people/Hughes/DataSanitizationTutorial.pdf](http://cmrr.ucsd.edu/people/Hughes/DataSanitizationTutorial.pdf)

This tool ([http://cmrr.ucsd.edu/people/Hughes/HDDEraseWeb.zip](http://cmrr.ucsd.edu/people/Hughes/HDDEraseWeb.zip)) will work great (if you can get it to detect your hd, it has issues with sata).  Dban while not completely perfect passes Gov standards to wipe a drive.

---

### Post by credobyte on 2009-07-22
> **Shazaam said:**
> With todays forensic tools I think it will still be possible to get SOME info off of the hd platters after a software wipe. In that situation rendering the platters to dust is the only way to be sure they cannot be read.
If all you are after is a relatively clean slate I second using  dban or something similar.

Well, if someone could find a file with song lyrics, screw it ! All I want to do is to ensure that it will not be possible to recover media files and similar, some sort of illegal stuff ( currently I've a clean XP install, tough, PC is old and there have been a bunch of various dirty file operations ).

> **bacil said:**
> use old and trusted

```
dd if=/dev/null of=/dev/YOURHDD
```use full hdd not partition if you want to destroy whold disk or partiton if you only want to wipe out partition eg. /dev/sda and /dev/sda1 for partition

And how many times you would recommend to execute this command ( I know it takes time to complete ) ?

---

### Post by whoop on 2009-07-22
> **bacil said:**
> use old and trusted

```
dd if=/dev/null of=/dev/YOURHDD
```

use full hdd not partition if you want to destroy whold disk or partiton if you only want to wipe out partition eg. /dev/sda and /dev/sda1 for partition
And do that a couple of times, if you are paranoid (/dev/random):-)

---

### Post by bacil on 2009-07-22
> **credobyte said:**
> .......

And how many times you would recommend to execute this command ( I know it takes time to complete ) ?

it depends what you need one run  surely destroys partition table and mbr plus overwrites original data with 0. 

if you want to destroy it completely i would probably used something simillar to volume shreder form HDS .. (this product is for eterprise storage sytems) and is certified by MoD :-)

it does couple of passes and overwrites sectors with random data so it could be scripted ..

something like ... create random file ... use random file as if= in dd ... (file is randomly generated to size of replaced disk) and give it couple of passes

---

### Post by bacil on 2009-07-22
> **whoop said:**
> And do that a couple of times, if you are paranoid (/dev/random):-)


Oh thats even better :-) then my script :-) use /dev/random

---

### Post by piratebill on 2009-07-22
> **bacil said:**
> Oh thats even better :-) then my script :-) use /dev/random

NOTE:
/dev/random will take longer than /null

---

### Post by bacil on 2009-07-22
But overwrites what ever is on your disk with random data :-) ... and you can speed it up a bit using bs

---

### Post by piratebill on 2009-07-22
> **bacil said:**
> and you can speed it up a bit using bs

Really?  What do you mean by bs?

---

### Post by bacil on 2009-07-22
```
dd if=/dev/random of=/dev/sda bs=1024
``` 

this way each pass of dd will do block of 1024 bits insteaad bit by bit bs=block size

---

### Post by michy99 on 2009-07-22
Some people claim that data can even be recovered after being over-written multiple times. If this is true, then I will never have to buy storage again! When my disk gets full, I just wipe it and use the space for new files. If I ever need one of my old files, I will just use one of those amazing recovery techniques to get it back!

---

### Post by piratebill on 2009-07-22
> **michy99 said:**
> Some people claim that data can even be recovered after being over-written multiple times. If this is true, then I will never have to buy storage again! When my disk gets full, I just wipe it and use the space for new files. If I ever need one of my old files, I will just use one of those amazing recovery techniques to get it back!

That used to be true for older drives.  For modern drives (after 2003..ish...) that isn't an issue anymore.  the pdf I linked to talks about this I believe

---

### Post by bacil on 2009-07-22
You still can on specialised devices recover some overwritten data thats why storage companies have to comply with rules for data shreding.

you will never get 100% of your data.recovery is based on residual magnetism and it is not stable through out disk. 

so  3 passes of dd with dev/random will certainly generate disk urecoverable. 

commercial shreders always do at least 3 passes on each disk

---

