---
title: "Creating Dual Boot with Breezy and Win98"
date: 2006-03-31
forum: General Help
---

### Post by MilkMoney on 2006-03-31
Here is a great link I am planning on following...

[http://users.bigpond.net.au/hermanzone/p2.htm](http://users.bigpond.net.au/hermanzone/p2.htm) 

Now, I would like to know if when I put the breezy cd in, and I choose the option to format my HD, does it erase everything on my hard drive that is stored in the win98 portion, or is this data still going to be there?

---

### Post by nanotube on 2006-03-31
well, if your win98 is not stored on a separate partition, then yes, it will erase your win98 stuff. 
so if you dont have a separate partition for win98, you should defrag your disk, and then create a separate empty partition to install ubuntu on.

---

### Post by MilkMoney on 2006-03-31
The hard drive is not partitioned yet. I was under the impression that the ubuntu cd would do this. (You can tell I know very little about partioning as I have never done it) Is there a way (short of buying partition magic) to partition the HD without erasing the files that are on it. Ya see, there is nothing really on this old PC that I care about. Just a lot of music files that I would rather not lose. It's not critical or anything that I keep them so I don't want to go through the trouble of backing it up or transferring it to a storage drive (You can see the files aren't that important). If I had a choice I want to keep them. 

So in short, I have to partition the HD first, then install breezy on the other part. Okay, I got that. I just want a quick way to partition. I can't fdisk it cuz that will reformat everything. Is there another way?

---

### Post by dcstar on 2006-03-31
[QUOTE=MilkMoney]The hard drive is not partitioned yet. I was under the impression that the ubuntu cd would do this. (You can tell I know very little about partioning as I have never done it) Is there a way (short of buying partition magic) to partition the HD without erasing the files that are on it. Ya see, there is nothing really on this old PC that I care about. Just a lot of music files that I would rather not lose. It's not critical or anything that I keep them so I don't want to go through the trouble of backing it up or transferring it to a storage drive (You can see the files aren't that important). If I had a choice I want to keep them. 

So in short, I have to partition the HD first, then install breezy on the other part. Okay, I got that. I just want a quick way to partition. I can't fdisk it cuz that will reformat everything. Is there another way?[/QUOTE]
If there is an existing OS on the disk then it IS partitioned, you have to shrink the existing partition to make room for another one.

Have a look at:

[http://ubuntuforums.org/showthread.php?t=119049](http://ubuntuforums.org/showthread.php?t=119049)

---

### Post by MilkMoney on 2006-03-31
[QUOTE=dcstar]If there is an existing OS on the disk then it IS partitioned, you have to shrink the existing partition to make room for another one.

Have a look at:

[http://ubuntuforums.org/showthread.php?t=119049](http://ubuntuforums.org/showthread.php?t=119049)[/QUOTE]

So in short, I can just put the ubuntu disk in the drive, boot it up, go through the process, and shrink the windows portion from 20gb to 15gb. This will allocate 5 gb space for ubuntu (this is all i need for experimentation) and let the disk do the work?

---

### Post by justleen on 2006-03-31
[QUOTE=MilkMoney]So in short, I can just put the ubuntu disk in the drive, boot it up, go through the process, and shrink the windows portion from 20gb to 15gb. This will allocate 5 gb space for ubuntu (this is all i need for experimentation) and let the disk do the work?[/QUOTE]

Breezer will not let you resize your win partition during an install.
You can use the Gparted live CD for this, or boot up the ubuntu live-cd en do it with parted.
Once you have resized ity, you can run the install and let it do its thing.

---

### Post by nanotube on 2006-03-31
what justleen said.
but you Have to defrag your drive first. what repartitioning with gparted (or anything else, like partitionmagic) does is chop of a piece of the hd off the end of your existing partition, to create a new partition.
if your drive is not defragmented, that means that your files can be all over the drive, even if it is not full - so some of your stuff could be residing at the end of your existing partition.
once you defrag, all your files will be moved to the front of the drive, leaving the end to be empty, so that it can be safely "chopped off" with gparted. :)

makes sense?

---

### Post by plors on 2006-03-31
if you use gparted you don't have to defrag first, the resizer will take care of that. please make sure you use the latest gparted. [http://gparted.sourceforge.net]("http://gparted.sourceforge.net/").

---

### Post by nanotube on 2006-03-31
hey plors
didnt know that about gparted. that's cool.
but how do you use the latest gparted, if booting from the livecd? does that have a sufficiently recent gparted on it?

---

### Post by plors on 2006-03-31
it's usually best to use the [gparted livecd]("http://gparted.sourceforge.net/livecd.php"). It's only 25 MiB in size and it contains the latest software.

---

### Post by MilkMoney on 2006-03-31
Once gparted is downloaded, how do I run it? Is there a program that runs it? Do I need to save it to a cd and then run it from a fresh boot from there? Once again, I am totally new to partitioning so forgive my noobish questions. Any help would be appreciated. You all have been very helpful so far.

---

