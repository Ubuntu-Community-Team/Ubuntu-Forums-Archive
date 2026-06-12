---
title: "ddrescue"
date: 2012-09-14
forum: General Help
---

### Post by pssturges on 2012-09-14
Hi,

My laptop got dropped from the lounge onto the tile floor and died. One of the things to break unsuprisingly was the 500gb hdd.

Strangely enough, the only way I can even get it to be recognised is putting it in a USB3.0 dock. It seems like it's pretty shredded.

It was a dual boot system (vista & ubuntu)with another NTFS partition for media. It is this partition that I'm trying to recover. None of the individual files are particularly important, but I would like to recover as much as I can with out too much time & effort.

It seems the partition table is amongst the data that has been lost. fdisk -l & blkid skips that hdd after thinking about it for a while. 

I have started running ddrescue to create an image of the entire disk. I would normally clone to another drive but I don't have a spare of sufficient size. Below is the current progress of ddrescue after about 30hours
```
phil@htpcserver:~$ sudo ddrescue -r 0 -n /dev/sdd /media/backup/hdimage.image hdrecovery.log
[sudo] password for phil: 


Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:     3835 MB,  errsize:    649 MB,  current rate:     196 kB/s
   ipos:     4484 MB,   errors:    1963,    average rate:    35260 B/s
   opos:     4484 MB,     time from last successful read:       0 s
Copying non-tried blocks...

```

As you can see, this will take about 3 months at the current rate! Using the information I could find about ddrescue, I decided to use the -r 0 option so when it finds a bad block it just quickly moves on. The -n option is supposed to make it try to read the good blocks first?

So my first question, should I change my command in some way that will speed things up significantly? As I say, I'm happy for it to spend as little time as possible trying to retreive bad data.

Secondly, as I understand it from [this]("http://ubuntuforums.org/showthread.php?t=711773") thread, once this is all done, I will need the partition table to be able to mount the image file. How can I do this if the partition table is fried?

Thanks in advance.
Phil

---

### Post by pssturges on 2012-09-23
Been going over a week. 20gb recovered, 480gb to go...

---

### Post by dcstar on 2012-09-24
> **pssturges said:**
> Been going over a week. 20gb recovered, 480gb to go...

Since the device is in an external interface you might also try the "direct" option.

The external USB device may well be using its own retry algorithm in trying to read bad blocks - but it is more likely the disk itself is just so badly damaged that simple sector reads take ages.

---

### Post by pssturges on 2012-09-24
> **dcstar said:**
> Since the device is in an external interface you might also try the "direct" option.

The external USB device may well be using its own retry algorithm in trying to read bad blocks - but it is more likely the disk itself is just so badly damaged that simple sector reads take ages.

Thanks. Yes I should have mentioned that I did manage to get it recognised by the internal sata controller. Didn't seem to make a significant difference.

Cheers

---

### Post by dcstar on 2012-09-24
> **pssturges said:**
> Thanks. Yes I should have mentioned that I did manage to get it recognised by the internal sata controller. Didn't seem to make a significant difference.

Cheers

Large mechanical shocks to a rotational disk can result in all sorts of damage like the heads making contact with the platters - basically fatal if the drive was active and spinning - through to distortion of the frame which results in misalignment (the tolerances of these things are incredibly touchy).

You may be doing well to recover any data from the drive, but one trick is to put the drive in a freezer (in a waterproof bag) for 30 minutes or so to basically change all the internal alignments and possibly allow recovery of some sectors that are cactus at room temperature.

---

### Post by pssturges on 2012-09-24
> **dcstar said:**
> Large mechanical shocks to a rotational disk can result in all sorts of damage like the heads making contact with the platters - basically fatal if the drive was active and spinning - through to distortion of the frame which results in misalignment (the tolerances of these things are incredibly touchy).

You may be doing well to recover any data from the drive, but one trick is to put the drive in a freezer (in a waterproof bag) for 30 minutes or so to basically change all the internal alignments and possibly allow recovery of some sectors that are cactus at room temperature.

Hmm. interesting. So you attempt your recovery while it's still cold I assume. Throw it back in the freezer once it warms up?

---

### Post by dcstar on 2012-09-24
> **pssturges said:**
> Hmm. interesting. So you attempt your recovery while it's still cold I assume. Throw it back in the freezer once it warms up?

You usually do it to try and recover any critical files while it's cold, if that actually works you go as long as you can before it breaks again.

The time in the freezer can vary as you need to allow the heat to be pulled out of the internal mechanics without wrecking the rest of the drive - it is usually only done in **desperate** situations!

---

### Post by pssturges on 2012-09-24
> **dcstar said:**
> You usually do it to try and recover any critical files while it's cold, if that actually works you go as long as you can before it breaks again.

The time in the freezer can vary as you need to allow the heat to be pulled out of the internal mechanics without wrecking the rest of the drive - it is usually only done in **desperate** situations!

Ok Thanks. I think I'll persavere a bit and maybe try it down the track.

---

### Post by alphaamanitin on 2012-09-24
Oh god, are you working on the original drive?  I hope it doesn't get damaged more while you are working on it.  

I would(have) suggest(ed) cloning the drive to a new drive with the dd command, using bs=16M or something to speed it up, and then working on recovery via the cloned drive.  

TestDisk is an AMAZING program to recover data.  I used it to completey and flawsly recover a Windows XP 250gb drive that some one, I swear it wasn't me, carelessly reformatted from NTFS to FAT32 using gparted, because said person forgot gparted always brings up sda after every thing it does.

AlphaA

---

### Post by pssturges on 2012-09-24
> **alphaamanitin said:**
> Oh god, are you working on the original drive?  I hope it doesn't get damaged more while you are working on it.  

I would(have) suggest(ed) cloning the drive to a new drive with the dd command, using bs=16M or something to speed it up, and then working on recovery via the cloned drive.  

I don't quite understand this. Surely at some point you have to read(or attempt to) the entire entire original disk to create the clone or image? This is what I'm trying to do with ddrescue.

> **alphaamanitin said:**
> 
TestDisk is an AMAZING program to recover data.  I used it to completey and flawsly recover a Windows XP 250gb drive that some one, I swear it wasn't me, carelessly reformatted from NTFS to FAT32 using gparted, because said person forgot gparted always brings up sda after every thing it does.
AlphaA

Haven't we all been there and had that sinking feeling when you realise what you've done!

Thanks, I'll have a look at TestDsik

---

### Post by alphaamanitin on 2012-09-24
My point about the original drive is that, yes, we have to work on the original drive to begin with, but it is safer to clone the original drive and attempt the various means of recovery from the clone. If you are able to get everything back in one go, great doesn't matter, but if you need to do multiple recover attempts and the like you increase your chance of worsening the drive condition and losing any ability to recover.

And hey, I said it wasn't me....I swear, lol.

AlphaA

---

