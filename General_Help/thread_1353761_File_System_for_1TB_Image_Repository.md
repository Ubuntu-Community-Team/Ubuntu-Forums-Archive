---
title: "File System for 1TB Image Repository?"
date: 2009-12-13
forum: General Help
---

### Post by Cuco3 on 2009-12-13
Hello.

 I want to be able to use Clonezilla to clone my client's OS installation for backup and recovery purposes. The clients' OS will vary but will mostly be Windows XP/Vista/7. I'm using a Seagate FreeAgent 1TB drive.

I tried it out already, using Ext3 filesystem on the 1TB USB HDD and Clonezilla to backup a Vista drive in order to upgrade to Windows 7. The cloning process seemed to have gone well until one program, Presto Pagemanager, suddenly broke after testing the restored HD. It was hanging on start, and when it did start, it wouldn't display thumbnail icons for some PDF files then hang when attempting to open some files. Worst part is, the program also broke on the original disk. I'm guessing something went wrong with the cloning process that affected the original. I just don't know what or how.

I tried reinstalling the program; didn't work. Same thing for uninstalling. So I gave up on it.

Which brings me here.

**1) How could the clone process affect one program and yet appear to run flawlessly?** Was it an EBKAC? All the files that didn't display thumbnails in Pagemanager checked out when they were opened. It was just the program that broke. I also noticed that IE8 was asking for the introductory preferences when loading up both the original and new HD. Does Clonezilla do something to alter the unique IDs in the original HD?

**2) What is the recommended file system for my 1TB USB HDD if I want to image Windows drives using Clonezilla?** I'd rather use Ext3 but I'd like to hear what others have to say. I have a feeling that Windows or the programs might be sensative to the type of filesystem they're placed on. Although imaging should just be copying 1s and 0s...hmm.

---

### Post by rbc on 2009-12-13
I cannot answer your more important questions, but I'll take this one:
> Was it an EBKAC?

I believe that whoever said that to you meant to say PEBKAC (**P**roblem **E**xists **B**etween **K**eyboard **A**nd **C**hair)

I hope you find some answers. With one recent exception, Clonezilla always been very reliable for me. You could try g4l (Ghost 4 Linux). Also, if you'd like to do some reading, what you want to do can be accomlished via terminal

---

### Post by NCLI on 2009-12-13
Well, we have excellent NTSC compatibility now, so why not put it to good use? If nothing else, doing that should eliminate any problems related to filesystem incompatibility.

---

### Post by Cuco3 on 2009-12-13
> **NCLI said:**
> Well, we have excellent NTSC compatibility now, so why not put it to good use? If nothing else, doing that should eliminate any problems related to filesystem incompatibility.Hi NCLI. I would except for a prior experience, about 5 months ago. I had a 80GB NTFS drive writing large files to it through Ubuntu and my system performance was severely degraded. I went to Windows to check the problem and defrag. It turns out, the entire drive was fragmented. Even with enough free space to defrag, Windows didn't want to defrag it. Since then, I've been using Ext 3 when working with large files via Linux and I've been reluctant to switch back to NTFS for that scenario.

---

### Post by Cuco3 on 2009-12-13
> **rbc said:**
> I cannot answer your more important questions, but I'll take this one:


I believe that whoever said that to you meant to say PEBKAC (**P**roblem **E**xists **B**etween **K**eyboard **A**nd **C**hair) It could go either way, according to google search for both acronyms, but thanks for the correction. :-p 

> **rbc said:**
> I hope you find some answers. With one recent exception, Clonezilla always been very reliable for me. You could try g4l (Ghost 4 Linux). Also, if you'd like to do some reading, what you want to do can be accomlished via terminalYeah, I love those "man <program>," really informative.

I just don't have the time to go through extensive testing to determine which file system would be best. I would really rather use Ext3 but need to know if Windows plays nice when restoring a cloned disk off it. Theoritically it should, since Clonezilla's only copying 1s and 0s...

---

### Post by Cuco3 on 2009-12-13
Hello.

 I want to be able to use Clonezilla to clone my client's OS installation for backup and recovery purposes. The clients' OS will vary but will mostly be Windows XP/Vista/7. I'm using a Seagate FreeAgent 1TB drive.

I tried it out already, using Ext3 and Clonezilla to backup a Vista drive in order to upgrade to Windows 7. The cloning process seemed to have gone well until one program, Presto Pagemanager, suddenly broke after testing the restored HD. It was hanging on start, and when it did start, it wouldn't display thumbnail icons for some PDF files then hang when attempting to open some files. Worst part is, the program also broke on the original disk. I'm guessing something went wrong with the cloning process that affected the original. I just don't know what or how.

I tried reinstalling the program; didn't work. Same thing for uninstalling. So I gave up on it.

Which brings me here.

**1) How could the clone process affect one program and yet appear to run flawlessly? Was it an EBKAC?** All the files that didn't display thumbnails in Pagemanager checked out when they were opened. It was just the program that broke. I also noticed that IE8 was asking for the introductory preferences when loading up both the original and new HD. Does Clonezilla do something to alter the unique IDs in the original HD?
[B]
2) What is the recommended file system for my 1TB USB HDD if I want to image Windows drives using Clonezilla?[/B] I'd rather use Ext3 but I'd like to hear what others have to say. I have a feeling that Windows or the programs might be sensative to the type of filesystem they're placed on. Although it should imaging should just be copying 1s and 0s...hmm.

---

### Post by The Real Dave on 2009-12-13
Not too sure about the program, but the whole Filesystem question is that yes, ext3 would be a good choice. Windows doesn't know its been on ext, as Clonezilla is a Linux live disk (under the skin like). It takes the image of the disk, and that image is no more Windows than an ISO is Ubuntu. Its just 1 and 0s as you said. So no, it makes no difference. 

Just be sure to read the info for Clonezilla very carefully. Know what options you need activated. I tried to just dive in head first and wiped a harddrive. With great power comes great responsibility.

---

### Post by Snow986 on 2009-12-13
I am pretty sure you have no choice but to use NTFS for windows. If you are using clonezilla from the live disc and just doing a one to one copy of a HDD then it should do all of this for you.  Just connect a blank HDD and choose source and destination correctly.  I don't know what you mean about using ext3...

---

### Post by Cuco3 on 2009-12-13
Hi Snow986.

What I mean is, for the 1TB USB HDD, which file system should be used: Ext3 or NTFS?

Yeah, Windows has no other choice but NTFS. It's the 1TB USB HDD's filesystem that I'm concerned about.

---

### Post by Snow986 on 2009-12-13
Well, (if I understand what you want to do correctly) all you should have to do is clear the 1TB, boot to the live cd, choose source disc and destination disc, then let it go.  However if you want to do multiple partitions then you should set up an identical (in size) NTFS partition on the 1TB and then do a partition to partition copy.  Make sure to choose the correct destination partition.

---

### Post by Cuco3 on 2009-12-13
> **The Real Dave said:**
> Not too sure about the program, but the whole Filesystem question is that yes, ext3 would be a good choice. Windows doesn't know its been on ext, as Clonezilla is a Linux live disk (under the skin like). It takes the image of the disk, and that image is no more Windows than an ISO is Ubuntu. Its just 1 and 0s as you said. So no, it makes no difference.Thank you, I thought the same thing, but I needed the reassurance on this from people who have more experience cloning drives than I do.

> **The Real Dave said:**
>  Just be sure to read the info for Clonezilla very carefully. Know what options you need activated. I tried to just dive in head first and wiped a harddrive. With great power comes great responsibility.Yes sir! The Clonezilla process is not very friendly/clear when asking for the source & destination disks.

Thanks Dave.

If anyone has more info to add, especially about Clonezilla altering the source (to-be-cloned) disk, please post.

---

### Post by earthpigg on 2009-12-13
when you restore the clone to the hard drive, you will be using a livecd and not windows-specific software, right?

if so, i don't see any reason why you would need to use ntfs.

in fact, i came across [this]("http://en.wikipedia.org/wiki/Btrfs") on wikipedia the other day:

> Btrfs is intended to address the lack of a file system in Linux with pooling, snapshots, checksums and integral multi-device spanning&#8212;features crucial as the use of Linux scales upward into larger storage configurations common in the enterprise.[3] It is expected to offer a feature set comparable to that of Sun's ZFS.[4] ***Chris Mason***, the principal author of the filesystem, has stated its goal was "to let Linux scale for the storage that will be available. Scaling is not just about addressing the storage but also means being able to administer and to manage it with a clean interface that lets people see what's being used and makes it more reliable."[5]

i've never used it, so i won't attest to it's quality, stability, and reliability, but it may be worth taking a look for you.

incidentally, and off topic, the name in bold is my name... but isn't me. i always have to make this clear when i submit resumes and the like so i don't get credit for something i didn't do. :lolflag:

---

### Post by Cuco3 on 2009-12-13
> **Snow986 said:**
> Well, (if I understand what you want to do correctly) all you should have to do is clear the 1TB, boot to the live cd, choose source disc and destination disc, then let it go.  However if you want to do multiple partitions then you should set up an identical (in size) NTFS partition on the 1TB and then do a partition to partition copy.  Make sure to choose the correct destination partition.Ah OK. Thanks for the advice on the multiple partitions set up. Didn't know it was like that; I thought it would also be cloned rather than just copying the partition.

---

### Post by Cuco3 on 2009-12-13
> **earthpigg said:**
> when you restore the clone to the hard drive, you will be using a livecd and not windows-specific software, right?

if so, i don't see any reason why you would need to use ntfs.

in fact, i came across [this]("http://en.wikipedia.org/wiki/Btrfs") on wikipedia the other day:



i've never used it, so i won't attest to it's quality, stability, and reliability, but it may be worth taking a look for you.

incidentally, and off topic, the name in bold is my name... but isn't me. i always have to make this clear when i submit resumes and the like so i don't get credit for something i didn't do. :lolflag:Yes, I will be using Clonezilla Live to restore the HDs. Thank you for the information.

---

### Post by cariboo on 2009-12-13
Please don't create multiple threads on the same subject, I have merged you two threads.

---

### Post by Cuco3 on 2009-12-13
> **cariboo907 said:**
> Please don't create multiple threads on the same subject, I have merged you two threads.Thanks for your help and contributions.

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
The clone image is like an iso so the file system of the backup drive isn't a concern. I use ext3 for all my drives except one NTFS to transfer files from Linux to Windows (because ext support in Windows 7/Vista is crap). The concern with your image's corrupt files is either the process or Windows itself being crap. I would have to agree that g4l is a better program as it is much like Norton ghost which I use for my Windows customers.

---

### Post by Cuco3 on 2009-12-13
> **Sin@Sin-Sacrifice said:**
> The clone image is like an iso so the file system of the backup drive isn't a concern. I use ext3 for all my drives except one NTFS to transfer files from Linux to Windows (because ext support in Windows 7/Vista is crap). The concern with your image's corrupt files is either the process or Windows itself being crap. I would have to agree that g4l is a better program as it is much like Norton ghost which I use for my Windows customers.Thanks Sin@Sin-Sacrafice. I'm still stumpped on why the program broke on the source disk, but I agree with your culprits. 

Either way, since two people recommended G4L, I'm gonna try it out. My next objective is to make a clone/iso of Windows 7 from the new HDD and restore it to the the old "Vista" HDD.

Wish me luck! I have this bookmarked to post my results for cloning the Win7 installation.

---

### Post by Cuco3 on 2009-12-14
Thanks for the help everyone.

I cloned the Win7 HDD and it worked fine, except Presto Pagemanger :), but I just put it to run under Win XP SP3 compatibility and it seems to be playing nicer than before. It still displays some thumbnails as broken but that's OK.

One thing I'd like to add is in the Vista HDD I noticed that when browsing for a file from a program, the program would hang, and would have to be forced shut down. It would happen in Outlook backup, Settings Saver for Office 2003, and one more which I can't remember atm. When I cloned and restored the Win7 image, those problems didn't arise, thankfully!

BTW, I couldn't use G4L because it only supports IDE / SCSI / SATA; I'm using a USB HDD :(. I used Clonezilla for the cloning process and it worked well enough.

---

