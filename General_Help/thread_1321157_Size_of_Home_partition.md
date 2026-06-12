---
title: "Size of Home partition"
date: 2009-11-09
forum: General Help
---

### Post by Kdar on 2009-11-09
What should I make the size of my home partition? I have 250 GB on my laptop.

---

### Post by ranch hand on 2009-11-09
Well, that is kind of an open question.

Do you want to use the whole drive for one OS?

Do you want to have 5 or 6 OS' on the drive?

---

### Post by Kdar on 2009-11-09
sorry that I forgot to specify.
I am only using one OS, Ubuntu.

Should I split the size for /home and /root partition equally?

Can I adjust those partitions later? (if I will be short on space in one or another?)

---

### Post by tommynz1975 on 2009-11-09
15 GB should be enough for / partition 
using the rest for /home
excluding what is wanted for /swap


good luck with partitioning

---

### Post by ranch hand on 2009-11-09
I would, on a drive that size, give the / partition about 30Gb (this is huge but things are slightly faster if your partitons are less than 50% full) and put it first on the drive.

Make the rest of your drive one "extended" partition.

Within it, create a swap partition, say 1Gb at the end of the drive.

The rest of the free space you can use for /home.

I would do this with the Live CD before installing and then choose the "manual" option in the partitioner and tell it which partitions to use for what by right clicking on them and clicking on "edit" or "change" depending on your Ubuntu version.

Take your time, remember to breath, if you screw up you can do it again it is an empty drive. 

Your / partition being a primary is pretty well stuck but the partitions within the extended are very flexible.  You should always back up your data before resizing/moving, indeed doing anything to your partitions.

The most important thing is HAVE FUN.

---

### Post by Kdar on 2009-11-09
Thanks guys for your help.

PS. a question.. most software installation will be installed in / or /home?

---

### Post by ranch hand on 2009-11-09
Most "system" stuff goes in the / partition.  A lot of configuration stuff goes in the /home partition.  Programs do not take up the room my imagine.  This is mainly text type stuff.

If you get the "source" material too, default setting, it takes up a good bit of room.

If you use a lot of add on programs, all the more reason to make the / partition a large one.  You have the room.

You can have a very functional OS with 40Gb total.  You have 250Gb.  Be generous to your / partition, it does the work.  /home is where your files are and what you see.  You would not see it if not for the "efforts" going on in your / partition.  Let it breath.

---

### Post by darrelsanchez23 on 2009-11-09
hi there. 

can i ask a manual on how to partition ..

---

### Post by ranch hand on 2009-11-09
I think that if you run a search for "partitioning" in a search engine, or using the forum search function, you will find all the information that you need.

If you install gparted you could also look at he help file.  It is quite good.  I would read it all before asking questions as then you would have some idea what you want to know.

Gparted should not be used on the drive you are on, so if you only have one drive you may think that you do not want it.  It is a real handy place to get info on your partitions.

Partitioning on a single drive is done from your live CD.  It  has gparted on it.

---

### Post by darrelsanchez23 on 2009-11-09
ok tnx for that cause i have an error after installing ubuntu 6.10 i formatted the whole drive but after restart it says ERROR LOADING GRUB 15...


TNX SIR

---

### Post by falconindy on 2009-11-09
Program installations are typically split between /lib and /usr, depending on what the payload is.

> this is huge but things are slightly faster if your partitons are less than 50% full
This isn't an NTFS/FAT partition. Assuming its Ext3 (or most other journaling FS's), you're fine up to about 80-85%. After that, the journal has to work a little harder to find room to write. 15g should be ample for root. I had to work hard on Ubuntu to get my root to surpass 10gb. The few times it did, it was because of the dump files leftover after a kernel compile.

---

### Post by ranch hand on 2009-11-09
My 6 month old / on this 9.04 install that I am currently on is 15Gb.  It is 51% right now.

Ext4, which is the default for 9.10, is made to handle larger drives (into the Tb range).

---

### Post by falconindy on 2009-11-09
> **ranch hand said:**
> My 6 month old / on this 9.04 install that I am currently on is 15Gb.  It is 51% right now.

Ext4, which is the default for 9.10, is made to handle larger drives (into the Tb range).
Sounds like 15GB is ample room for an Ubuntu install, then.

Depending on the block size you use to format an Ext3 partition, it will support anywhere from 2TB to 16TB. It's true that Ext4 will support a larger volume and max file size, but if anyone here is creating an array larger than 16TB or messing around with files larger than 16GB, chances are they know what they're doing and won't be posting here. It's also likely they're **not** using an Ext FS.

Ext4 doesn't provide anything shockingly awesome or fantastic over Ext3. The performance is roughly the same, and if you're talking about formatting a large drive, there are better options than the Ext series -- namely XFS.

---

### Post by running_rabbit07 on 2009-11-10
This is how my 250GB HDD is set up. I leave a lot of room in the / partition because I like to add a lot of programs. I have used up to 19GB at one time.

---

### Post by ranch hand on 2009-11-10
Looks like it will work to me.

One thing you must remember.  This is Linux.  You can ask advice and get it in good faith.  But we are an opinionated bunch.

The important thing is that it is YOUR box, and you are FREE to do it YOUR way.  This is my box and I assure you I do it my way.

I bet that this is something that falconindy and I agree on 100%.

That and HAVE FUN.

Now, where is your 10.04testing install going?

---

### Post by running_rabbit07 on 2009-11-10
> **ranch hand said:**
> Now, where is your 10.04testing install going?

Good old VBox.

---

### Post by Roasted on 2009-11-10
My main rig is running on 500gb drives, and my root partition is 25gb. I have every application installed I would ever want, and yet I'm using like 29% of my root partition space.

Not telling you what to do, but I'm letting you know what I currently use and what I'm experiencing as an FYI to yourself in case that's the size you want to use, etc.

---

### Post by ranch hand on 2009-11-10
> **running_rabbit07 said:**
> Good old VBox.
Well at least you have plenty of room for it.

I am on an upgrade to 10.04testing right now.  I am using it as my daytime OS.

---

### Post by running_rabbit07 on 2009-11-10
> **ranch hand said:**
> Well at least you have plenty of room for it.

I am on an upgrade to 10.04testing right now.  I am using it as my daytime OS.

I'll have to give it a spin.

---

### Post by Slim Odds on 2009-11-10
> **ranch hand said:**
> My 6 month old / on this 9.04 install that I am currently on is 15Gb.  It is 51% right now.

Ext4, which is the default for 9.10, is made to handle larger drives (into the Tb range).

ext3 has a max volume size of 16 TiB

---

### Post by ranch hand on 2009-11-10
> **Slim Odds said:**
> ext3 has a max volume size of 16 TiB
Yes, this is true.  It is also true that if you have large files it is going to struggle compared to ext4.

The larger the storage and with larger files ext4 will be a LOT faster.  It is faster on my little 320Gb drives with few large files.  I have demonstrated that for myself by installing 9.04 on ext3 and ext4 next to each other and trying them out.

I have no problem with ext3.  I see no reason for people to have problems with ext4 other than some vague rumors circulating on the web.

All problems attributed to ext4, that I have seen, could easily have occurred on ext3 and not been the fault of ext3 but something else.

If folks want to store movies on ext3 they sure can and have it spread over several blocks.  That is fine.

Heck, I am a ranch hand, I prefer horses for moving cattle.  Lots of folks like dirt bikes and 4 wheelers.

---

### Post by paynek716 on 2009-11-12
> **ranch hand said:**
> Make the rest of your drive one "extended" partition.

Within it, create a swap partition, say 1Gb at the end of the drive.

The rest of the free space you can use for /home.

I have seen a few of your posts where you suggest an extended partition for everything but the root directory. What is the advantage or disadvantage of this approach?

I have a 500GB on my laptop with 2GB RAM. Current partitions (all are logical, not extended):
- 30GB 	etx3	Linux root
- 10GB		swap
- 407GB	ext3	home
- 53GB	ntfs	Windows Vista

I know that is a huge swap but I have room to spare. I am considering a repartition to have an NTFS data drive I can share with Vista and Ubuntu. I will probably move to something like:
- 30GB ext3 root (logical)
- extended partition for 10GB swap and and 307GB home
- 100GB ntfs data (logical)
- 53GB ntfs Vista (logical)

---

### Post by running_rabbit07 on 2009-11-12
> **paynek716 said:**
> I have seen a few of your posts where you suggest an extended partition for everything but the root directory. What is the advantage or disadvantage of this approach?

I have a 500GB on my laptop with 2GB RAM. Current partitions (all are logical, not extended):
- 30GB     etx3    Linux root
- 10GB        swap
- 407GB    ext3    home
- 53GB    ntfs    Windows Vista

I know that is a huge swap but I have room to spare. I am considering a repartition to have an NTFS data drive I can share with Vista and Ubuntu. I will probably move to something like:
- 30GB ext3 root (logical)
- extended partition for 10GB swap and and 307GB home
- 100GB ntfs data (logical)
- 53GB (logical)

The only reason I know of is most systems don't support more than 4 primary partitions.

---

