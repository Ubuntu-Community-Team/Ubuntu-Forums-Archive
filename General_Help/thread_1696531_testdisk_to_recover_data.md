---
title: "testdisk to recover data"
date: 2011-02-27
forum: General Help
---

### Post by m91-30 on 2011-02-27
I'm trying to use testdisk to recover data from my hard drive. I installed it through the software center, but can't find the shortcut to get it to run. what am I missing?

---

### Post by Anton K on 2011-02-27
Testdisk is a console utility. You should run it in a terminal:
```
sudo testdisk
```

---

### Post by sikander3786 on 2011-02-27
Testdisk can recover partitions and if it is unsuccessful, you can still recover your files by using photorec. It won't recover the filenames though.

See here and let us know if you've got any further queries :-)

[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by m91-30 on 2011-02-27
okay, I got the program to run, but I'm unsure what steps to take to make the drive bootable, again without losing data. one thing I noticed is gparted says the partition is out of phase by ~2500bites, if I remember right. what does this mean, and how do I fix this?

---

### Post by m91-30 on 2011-02-27
plus, I can't recover anything right now because no partitions are bootable.

---

### Post by coldraven on 2011-02-27
Testdisk is a very powerful program that if used wrongly can totally ruin you drive.
As such it is very difficult to give any advice other than this.
Never play with the "advanced" features! Such as changing the number of heads, cylinders etc.
Just let it analyse your drive to find lost partitions.
Say it finds four partitions.
You can alter whether or not a partition is primary, logical etc.
Play with that.
When all four partitions show in green text you can then choose to write this to the MBR.
AFAIK the green text means that this is most likely the correct configuration of the drive.
Then hold your breath because if you get this wrong your data could be even more lost!
Testdisk has saved my skin, I sent the author a donation.

---

### Post by Quackers on 2011-02-27
Some great info here
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by coldraven on 2011-02-27
> **Quackers said:**
> Some great info here
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
Great link :)

---

### Post by m91-30 on 2011-02-27
every guide I'm finding is for recovering data after losing a partition, or reformatting without writing to the drive. maybe this is a dumb question, but would it be easier just to re partition the drive without a wipe, then go from there on the recovery?

---

### Post by m91-30 on 2011-02-28
okay, I got it to where I could write an image, but how do I open a .dd file?

---

### Post by m91-30 on 2011-02-28
Is there any easier way for me to get data off this drive now that it's fixed? I don't have a second 750 gb drive to do the image thing, is there any way for me to pick data right off the drive?

---

