---
title: "Make a COMPLETE backup?"
date: 2010-02-06
forum: General Help
---

### Post by altjx on 2010-02-06
Anyone know of a bootable CD that I can make a COMPLETE backup to an external HD? I've tried Norton Ghost (it doesnt recognize my external), I've tried Image Center 5.6, it doesn't support Linux file system format, although it recognizes my external HD... Acronis TrueImage doesn't recognize the external HD either..

What I'd like to do is make an entire backup of my entire HD, partitions and all... To where I could format my drive and restore that image and have the same exact thing.

---

### Post by umechanism on 2010-02-06
I use partimage (partition image) to do exactly what you are talking about.  Google for it.  It is also included in SystemRescueCD which, if you don't have a copy of, you should.  It is free.  Google for it.

Mike

---

### Post by switch10 on 2010-02-06
umm put in any linux live cd and open a terminal and type

```
rsync -r /home/username /media/your_hard_drive
```

rsync copies hidden files by default.

This will not make an image.  It will however, backup all of the files in your home dir.  if you want to back up everything on the partition use root instead of /home/username i.e.:

```
 / 
```

---

### Post by altjx on 2010-02-06
Thanks, I'd prefer to not do it via command line on live CD though. I'm going to try PartImage, thanks =)

---

### Post by Sef on 2010-02-06
Check out [Clonezilla]("http://clonezilla.org").

---

### Post by altjx on 2010-02-06
> **umechanism said:**
> I use partimage (partition image) to do exactly what you are talking about.  Google for it.  It is also included in SystemRescueCD which, if you don't have a copy of, you should.  It is free.  Google for it.

Mike

With partimage, i'm at the screen where it shows partition to save/restore... but where does it let you select the external hard drive as the destination backup device?

---

### Post by Arand on 2010-02-07
You need to have the destination mounted, that way the destination will be something like /media/destinationdrive/partimage_backup.gz


- Arand

---

### Post by altjx on 2010-02-07
Ah, okay. I can't mount my external HD in Virtual Box to test it out and I don't have a blank CD around. I'll try it when I get home tomorrow, thanks man. I'll post back if I run into any issues

---

### Post by stinkeye on 2010-02-07
FYI partimage does not support ext4.

---

### Post by Arand on 2010-02-07
Indeed for ext4 use either dd (very inefficient) or fsarchiver, available on clonezilla, or systemrescuecd.

---

### Post by altjx on 2010-02-09
ended up using Acronis TrueImage... it backed up but wouldnt restore lol, and i needed to restore it >_<, just came back from my 4th reformat... gonna be more careful now and try partimage

---

### Post by Tristan Tonks on 2010-02-09
I always backup via cp -r, there is nothing scary about that just don't mv or rm unless you are incredibly carefull!

---

### Post by altjx on 2010-02-09
> **Tristan Tonks said:**
> I always backup via cp -r, there is nothing scary about that just don't mv or rm unless you are incredibly carefull!

Yeah I agree, thanks all =)

---

### Post by altjx on 2010-02-09
Well, it seems like partimage only lets you copy one partition per backup. I'm looking for a backup utility to make an entire sector-by-sector copy of this HD which is dual booting 2 linux operating systems

---

### Post by umechanism on 2010-02-09
Did you try dd?
[http://en.wikipedia.org/wiki/Dd_%28Unix%29](http://en.wikipedia.org/wiki/Dd_%28Unix%29)

---

