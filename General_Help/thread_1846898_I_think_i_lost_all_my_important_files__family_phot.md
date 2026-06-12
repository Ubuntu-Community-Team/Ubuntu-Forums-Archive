---
title: "I think i lost all my important files / family photos during 10.10 install"
date: 2011-09-19
forum: General Help
---

### Post by thetucker22 on 2011-09-19
I have a computer that wasn't booting windows XP. I inserted the 10.10 disc, didnt install and saw that the files were still there when using the demo the CD.

I then rebooted and tried installing ubuntu using the CD. It gives an option where you can keep the files/windows files and also install Ubuntu.

It is a slider, and it splits it into two partitions, your files on the hard drive and the ubuntu Os partition. This was showing 90Gb of files i wanted to keep and 70Gb of a different partition for installing Ubuntu on. I could change these values by sliding the slider.

I set it to 90 / 70, and carried on with the install.

However when i look at the partitions now it is only showing 157Gb partition and two 1.5Gb partitions. There is no sign of the intended partion, WITH ALL MY IMPORTANT FILES AND FAMILY PHOTOS. This data is very dear to me and i can't even begin to think what i would do without it.

Please could someone help me, i have followed the instructions and can't see how i could have lost the 90Gb i wanted to save. :(:(:(:(:(

---

### Post by thetucker22 on 2011-09-19
I'd like to add i'm pretty much a beginner with ubuntu but have used it before and liked it. I was trying to save this data for a family member who really needs these files, i have searched the internet for answers or for some hope, but i just don't know where to turn, really gutted this has happened.

---

### Post by computerkid2000 on 2011-09-19
If you have $100-$1200 you could look for data recovery software, they are expensive but they work 99.9% of the time (just don't install them to the same hard drive you are recovering from) other then that you could try to look for the volume in either /media or /dev 

(/media uses the uuid or how big it is, /dev uses things like sda1 sda2 sdb2 etc.)

---

### Post by jerrrys on 2011-09-19
you can try testdisk

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by thetucker22 on 2011-09-19
Thank you for your replies : )

I will try this tomorrow (too tired) 1.30am here now after trying for hours to figure out how to get my files back :s, i wonder if there are other people who have had this problem after the installation process.

---

### Post by computerkid2000 on 2011-09-19
> **thetucker22 said:**
> Thank you for your replies : )

I will try this tomorrow (too tired) 1.30am here now after trying for hours to figure out how to get my files back :s, i wonder if there are other people who have had this problem after the installation process.

Yes, it has happened many times before to many people! ;)

---

### Post by thetucker22 on 2011-09-19
Ok, well glad to hear im not the only one, but sorry to hear so many people have been affected. One last thing before i hit the sack, seeing as it has happened many times before, how successfull were they? and how likely is it i can get my files back do you think? Thanks for your help!

---

### Post by computerkid2000 on 2011-09-19
With pro programs, yes, 99.9% of the data is recovered (i dont know about the .01 percent though)

---

### Post by occams_beard on 2011-09-19
First thing, make sure you DO NOT use the computer in question. Shut it off and do touch it.  You will probably have to remove the drive from your computer and install it as a slave drive in another computer to run whatever recovery software you get. You do not want to boot to that disk under any circumstances.

I think though, you're probably SOL. If ubuntu has overwritten your windows partition, you'll be exceedingly lucky to get your data back. Worth a shot though.

At the very least, you've learned an important (albiet expensive) lesson... If you're data is as dear to you, BACK IT UP. Especially if you're going to be messing around with partitions.

---

### Post by thetucker22 on 2011-09-20
I have booted it, or else i wouldn't have known this issue in the first place. Thanks for your help, but i shouldn't be here to learn lessons, just to get my dead relatives files back. I followed the instructions, either the installation process is deliberately misleading or whoever designed it didn't test it out before releasing it. I have partitioned drives before but ubuntu specifically says use the installation to partition your drives.

It does look as if ubuntu has overwritten the original partition, that's scandalous, how can they release the ubuntu install with it being like that? Unless they are so anti windows they want delete all your files.

---

### Post by thetucker22 on 2011-09-20
Is there anyone else who has had this problem? And what did they do to fix it?

---

### Post by Slim Odds on 2011-09-20
> **thetucker22 said:**
> I have booted it, or else i wouldn't have known this issue in the first place. Thanks for your help, but i shouldn't be here to learn lessons, just to get my dead relatives files back. I followed the instructions, either the installation process is deliberately misleading or whoever designed it didn't test it out before releasing it. I have partitioned drives before but ubuntu specifically says use the installation to partition your drives.

It does look as if ubuntu has overwritten the original partition, that's f**king scandalous, how can they release the ubuntu install with it being like that? Unless they are so anti windows they want delete all your files.

I don't mean to sound callous but this issue has nothing to do with the Ubuntu installer. It's about BACKUPS.

Never, never, never install an operating system without BACKING UP the IMPORTANT files that you don't want to lose.

On another note, someday that hard drive will DIE. BACKUPS are the way you protect that data.

On another note, typically it's USER ERROR that causes these problems and not the installer.

Hope you get those files back.

---

### Post by thetucker22 on 2011-09-20
It wasn't USER ERROR it's the error of the installer. I was keeping the partition i wanted to keep seperate. I don't need to be told what i should have done, your post is worthless and infuriating, i just want to be told how to fix it.

---

### Post by gandaran on 2011-09-20
> **thetucker22 said:**
> It wasn't USER ERROR it's the error of the installer. I was keeping the partition i wanted to keep seperate. I don't need to be told what i should have done, your post is worthless and infuriating, i just want to be told how to fix it.
look try booting from live cd and start gparted then take a screenshot and post it here so we can look at the disk partitions setup.
also when installing ubuntu it better to manually partition the disk with gparted and use the manual install option where you actually choose the partition to install than to trust the installer which can fail if you are not careful. 
about recovering files your best option is to use testdisk, you will need another disk either internal or usb big enough to take everything.

---

### Post by Mark Phelps on 2011-09-20
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, my suggestions are the following (based on my experience at doing this successfully):
1) Find someone with a working Windows PC
2) Remove your drive from this PC.
3) On the Windows PC, download and install the trial version of GetDataBack for NTFS from Runtime Software.
4) Connect your old drive to this Windows PC.
5) Run GetDataBack in deepest discovery mode -- probably best to let it run overnight.
6) In the morning, check the recovery logs and see if GetDataBack was able to find your lost files.
7) If it was, you will have to purchase it to do the actual recovery.

Your data ... your money ... your choice.

And, BTW, it is not HUNDREDS of dollars for this product. Last time I checked, GetDataBack for NTFS was $80, USD.

---

### Post by patryk77 on 2011-09-20
There are some very good Free (speech AND beer) options out there you can try first.

I would get the [System Rescue CD](http://www.sysresccd.org/Main_Page) (edit: or not*) and [Backtrack Linux](http://www.backtrack-linux.org/) (Of course, ***_use another PC_*** to download/Burn them).

Personally, I would try to recover the old partition table first with testdisk (run it from the live CD). If that recovers it, you can see if you can backup your files before reinstalling.

Some data may have gotten overwritten, so for all the files you can't recover you can try to use Backtrack's Forensics tools.

Simply boot from the Live DVD in the Forensics mode, run startx if you get dropped to a shell instead of the User Interface, and explore the Applications/Backtrack/Forensics menu entries.

The most important tools will be under Forensic Carving Tools (ie: recover jpeg)

Good luck!

*Edit: Backtrack already included testdisk and as such you don't really need Sys Rescue CD

---

### Post by oldos2er on 2011-09-20
> **thetucker22 said:**
> Is there anyone else who has had this problem? And what did they do to fix it?

I edited post #10 for inappropriate language, please be careful what you post.

If the data was as important to you as you say, you must have backups. Backing up data is one of the basics of using a computer, doesn't matter which OS you use.

Hopefully photorec will work for you (it's part of testdisk). [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by David Andersson on 2011-09-20
> **Mark Phelps said:**
> In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

That may be good advice. Otherwise, if you install Ubuntu (on another harddrive, of course, with a lot of free space) there are several data recovery tools in the Ubuntu repositories. They can not recover anything that was written over by the installation, of course.

**foremost**

```
$ foremost -i /dev/XXX -o rescued_files1
```

**recoverjpeg** - only search for jpeg images

```
$ mkdir rescued_files2
$ cd rescued_files2
$ recoverjpeg /dev/XXX
```

**photorec** - in package testdisk

```
$ photorec /d rescued_files3 /dev/XXX
```

**magicrescue**

```
$ magicrescue -d rescued_files4 -r jpeg-jfif -r jpeg-exif -r png /dev/XXX
```

**scalpel** - Ignore it, no good

I have found foremost, recoverjpeg and photorec are about equally good at finding jpegs, but differs slightly and may complement each other. So if you are ambitious about it you may try all three or four and merge the results.

Also see [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Jerry N on 2011-09-20
> **oldos2er said:**
> If the data was as important to you as you say, you must have backups. Backing up data is one of the basics of using a computer, doesn't matter which OS you use.


Unfortunately, it has been my experience, over many years of computer use, that you can scream BACKUPS BACKUPS BACKUPS until you are blue in the face and most people will completely ignore you UNTIL they have lost something important to them.  Then they want you to solve their problem!  I provide free assistance to a number of people and will attempt to save their files if, and only if, the original partition is still intact. The days of recovering 10mb fat16 hard drives with Norton utilities are OVER!

Jerry

---

### Post by bhaverkamp on 2011-09-20
Are you sure? post the output from "sudo fdisk -l"

---

### Post by David Andersson on 2011-09-20
(Off topic)

> **Jerry N said:**
> you can scream BACKUPS BACKUPS BACKUPS until you are blue in the face and most people will completely ignore you
It's the same with a sign "Clean The Filter!" on the tumble-dryer. People ignore it. It *must* be accompanied with a series of *images* that shows in *minute* detail *exactly* *how* to clean the filter. Even then, if the first image shows a brush in a hand, the subject looks at his hand and there is no brush, he's lost.

(End off topic)

---

### Post by Jerry N on 2011-09-20
> **David Andersson said:**
> (Off topic)


It's the same with a sign "Clean The Filter!" on the tumble-dryer. People ignore it. It *must* be accompanied with a series of *images* that shows in *minute* detail *exactly* *how* to clean the filter. Even then, if the first image shows a brush in a hand, the subject looks at his hand and there is no brush, he's lost.

(End off topic)
Or maybe a video of the last fire caused by a clogged filter:):)

Jerry

---

### Post by jwbrase on 2011-09-21
> **thetucker22 said:**
> Thank you for your replies : )

I will try this tomorrow (too tired) 1.30am here now after trying for hours to figure out how to get my files back :s, i wonder if there are other people who have had this problem after the installation process.

Most likely. Repartitioning a drive and installing a new OS side-by-side with an existing OS on it is a risky proposition, and I'm pretty sure that everyone who's done any significant number of dual-boot installs or drive repartitions for any given pair of operating systems has a horror story of having accidentally destroyed a partition or written over an MBR. (I've done the latter myself).

I generally try to use a separate disk for any new OS I'm installing on a computer, if at all possible.

Speaking of which, are there any other disks on this computer? If so, are you sure you're looking at the right one?

Also, what are the partition types it gives for the three partitions on the drive (ext3, NTFS, FAT32, etc.)? It would be nice if you could open a terminal and post the output of "sudo fdisk -l", or post a screenshot of whatever program you used to inspect the partitions on the drive.

---

### Post by jwbrase on 2011-09-21
> **thetucker22 said:**
> It wasn't USER ERROR it's the error of the installer. I was keeping the partition i wanted to keep seperate. I don't need to be told what i should have done, your post is worthless and infuriating, i just want to be told how to fix it.

User error isn't always the user's fault. Often times the machine does exactly what you told it to do, it's just that what you thought you told it to do wasn't what you actually told it to do. And often times this is the result of a poorly designed interface that doesn't draw attention to decisions you need to make, so that you overlook something and leave it on a default setting when you actually need to change it. I speak from personal experience, having overwritten my MBR when an installer didn't draw quite enough attention to the choice of which drive to install GRUB to.

---

### Post by occams_beard on 2011-09-21
Ubuntu should put a big red warning on the disk partitioning screen about backing up. Have to imagine there are a lot of people not knowing what they are doing that end up nuking their windows partition.

On the other hand, you would think someone who knows enough to want to try Ubuntu would be knowledgeable enough to have back ups....

Either way, and I say this with no malice, it is the OPs own fault for not having his important files backed up.  He would be in the same boat had his hard drive died.

---

### Post by Slim Odds on 2011-09-21
> **jwbrase said:**
> User error isn't always the user's fault.
<cut>

You must be a politician.

---

### Post by thetucker22 on 2011-09-21
Thanks to everyone who has posted and tried to help me resolve this issue, there is a lot of information here i need to digest. I will follow the instructions and report back on any information i can give to you, and also how i'm getting on. Thanks again.

---

### Post by oldos2er on 2011-09-21
Please come back and let us know how it goes. Good luck.

---

### Post by Rasa1111 on 2011-09-21
> **thetucker22 said:**
> It wasn't USER ERROR it's the error of the installer. I was keeping the partition i wanted to keep seperate. I don't need to be told what i should have done, your post is worthless and infuriating, i just want to be told how to fix it.

Nah, he is right...
By "Backups" he doesnt mean just backing your files up on the same hard drive. 
If you have files that are very important,
you should keep them backed up on some kind of external media.
External hard drives, flash drives, dvd's, whatever. 

But having important files backed up onto EXTERNAL media , (or something separate from the disk they are on) is a big must, really. 

If a hard drive fails, it's not going to matter whether you had your stuff on a separate partition or not. 

Im sorry you lost your files.
and I hope you get them back.

 But failure to keep important files backed up on something other than the hard drive they are kept on, is "user error".

Make-
Keep-
Backups!
(not on the same hard drive), that's just silly. 

Good luck.

---

