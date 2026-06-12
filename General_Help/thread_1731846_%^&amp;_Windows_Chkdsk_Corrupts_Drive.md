---
title: "%*^&amp; Windows Chkdsk Corrupts Drive"
date: 2011-04-17
forum: General Help
---

### Post by s3MA00RRNY on 2011-04-17
Okay, so I've been having this problem for a while now, and it's driving me nuts. Sometimes when I start Windows (7) it says it needs to check the drive for consistency. I scramble to stop it whenever possible, because it always decides to delete random files every time I run it. It recently decided to delete one of my assembly language projects. Thankfully I had it somewhere else in my Linux partition, mainly because I don't trust Windows anymore. Any ideas on how to fix this problem?

---

### Post by wilee-nilee on 2011-04-17
> **pcdude2143 said:**
> Okay, so I've been having this problem for a while now, and it's driving me nuts. Sometimes when I start Windows (7) it says it needs to check the drive for consistency. I scramble to stop it whenever possible, because it always decides to delete random files every time I run it. It recently decided to delete one of my assembly language projects. Thankfully I had it somewhere else in my Linux partition, mainly because I don't trust Windows anymore. Any ideas on how to fix this problem?

Something is wrong with the windows install possibly, if it was me I would have what is needed backed up and just reinstall it. Could be a hd with damaged areas and it is just slowly getting worse, hard to say really.

Have you just let the chkdsk run all the way the files are not deleted but put in a .0000 file something like that name anyway.

---

### Post by s3MA00RRNY on 2011-04-17
Yeah, that's the first thing I would have thought, but guess what (probably should have said this in the OP), I've had it do the very same thing to me before, forcing me to REINSTALL.

I did let it run all the way. Very few of the files it deleted were placed in the found folders.

I know the HD is fine. I've tested it before, and plus I very recently accessed the files that were deleted.

---

### Post by Mark Phelps on 2011-04-18
Don't mean to be discouraging, but had this happen recently to me -- Win7 PC got stuck in forced chkdsk loop on every boot.  Even tried removing the drive, connecting it to another PC, and running chkdsk there until it quit finding errors.  Replaced back in the original PC -- chkdsks again!

Had to wipe the partition and reinstall from backup.

Suggest you contact sevenforums.com (Windows 7 forum) for assistance with the Win7 problem.  They have help sections and tutorials.

---

### Post by s3MA00RRNY on 2011-04-18
Should I try contacting Microsoft as well, considering I've had it happen more than once? :D:D:D

---

### Post by s3MA00RRNY on 2011-04-23
Just to rule anything out, I shifted the roles of my hard drives. My primary drive is now my backup, and my backup is my primary. I also cleared Windows (it was pretty badly damaged anyway). I'll let you know how it goes.

---

### Post by Mark Phelps on 2011-04-25
Also, although it can be a pain, do NOT format an empty NTFS partition in advance, especially with Linux utilities.

Win7 is picky about it's OS partition formatting, so it's best to let Win7 do its own formatting as part of the install.

And yeah, on a clean drive, that will leave you with a new "boot" partition for Win7, but you can migrate the boot files into the Win7 OS partition using EasyBCD and remove the "boot" partition when done (to reclaim the space).

---

### Post by s3MA00RRNY on 2011-04-26
That's a good point, but that also brings up another issue I have. If I use Windows 7 (or Vista) to format, it blows up my first logical partition, which right now is the one for Linux root.

---

### Post by coffeecat on 2011-04-26
> **pcdude2143 said:**
> If I use Windows 7 (or Vista) to format, it blows up my first logical partition, which right now is the one for Linux root.

Yes, I've managed to get the XP and Vista installers to do that (in simulations) after helping in threads where Windows installers have done ridiculous things to logical partitions. I found that the Vista installer can remove the first logical partition (sounds like what happened to you) but the XP installer rewrites the partition table so that the first logical partition is designated primary but sitting inside an extended - which, of course, is impossible.

My experience must be different from Mark Phelps. I have had no problem installing Windows to primary NTFS partitions created with Gparted. I have done this for XP, Vista and Windows 7 and each have worked happily in the partition created by this Linux utility. It's probably the only safe course to take when you have logical partitions present because you can't risk the Windows installer reformatting anything in this situation.

---

### Post by s3MA00RRNY on 2011-05-13
Just wanted to say that I haven't had any problems recently, and I've been in Windows quite a few times to play Portal 2 over the past few days. I'll still have to do some more testing to be sure though...

---

