---
title: "******* Need urgent help on file recovery *******"
date: 2010-01-26
forum: General Help
---

### Post by cas007 on 2010-01-26
Hi to all of you.

Very new to the forum because of a SPECIFIC issue that I need to get answered.

I live in the USA and my mother lives in the UK. She recently had trouble with her Win XP Pro Toshiba laptop, where the machine would not go past the welcome screen. 


I got her to buy an external Seagate backup drive (with backup software). I also instructed her as to which folders to backup and where they were.

All files and folders were backed up apart from the Outlook Express folder, under Documents/settings/User ......

The friend that was helping her told her not to back these files up, as they may have viruses. So, without myself being advised (I used to build Windows machines for a living), after she failed to back this folder up to the external drive, she installed Ubuntu 9.10 on to this machine, which 'wiped out' the Windows System.

My urgent question is: Can the Outlook files still be recovered without any undue trouble through the Ubuntu Desktop, or do I have to have her reinstall the Windows XP OS for her machine? She has the recovery disc from Toshiba, but am wondering if she needs the full Windows XP Pro disc. The Ubuntu OS was installed Sunday night (24th January 2010)

I have told her to not use the machine until she gets a new HD for her laptop from me (raw). She can then install Ubuntu onto that. I have told her to send me the old drive to see what I can do to recover the files.

I do not understand anything about the Ubuntu/Linux file system, and how to recover files from a different OS than Windows.

I do know that Ubuntu/Linux is far superior to Windows, but I need to get this sorted out as it is causing much stress and inconvenience.

Any help would be a godsend. Thanks in advance.

---

### Post by t4thfavor on 2010-01-26
If she installed Ubuntu over the XP partition then no, they are not recoverable as the installer formats the drive to another filesystem.

The Outlook files are gone even if you reinstall windows. 

The only question is what would you do with them if you did get them back as they are a windows file format?

This is also why you use IMAP for your email so when you reload your machine, you can just hook the email client back up, and viola your email is back.

---

### Post by cas007 on 2010-01-26
If she got them back I would have her use Thunderbird to have them imported into that program, or I would have her send the recovered files to me and then I would import them into Thunderbird. Hopefully, Thunderbird's file format will alow these emails to be read irrespective of whether the OS is Windows or Linux/Ubuntu.

---

### Post by t4thfavor on 2010-01-26
Sorry though, I think they are gone forever. But like I said to keep this from happening in the future see if her email provider offers imap or imaps. I know gmail does. 

and most other providers will as well.

---

### Post by Elfy on 2010-01-26
You could try using testdisk - but you might have lost them. 

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Try a search on the forum for testdisk, a search with uboontu gets this

[http://preview.tinyurl.com/ylbguxz](http://preview.tinyurl.com/ylbguxz)

The most important thing is to not use the hdd until you can try and get the data back.

---

### Post by teward on 2010-01-26
From experience, by formatting a drive with a new filesystem or anything, 99.955% of the time you will lose everything and not have anything useable.

The outlook files are gone dude, unfortunately.

---

### Post by PRC09 on 2010-01-26
I have used both of the following pieces of software to recover files from formatted hard drives.I just found diskdigger(free) a little while ago and has worked really well for photo recovery,havent tried for other types. Disk Internals(not free) does recover virtually everything,even the stuff people dont want recovered.....Outlook express files when recovered may need extra software to read them tho as they are still in .dbx format if it is OE 5/6.

[http://dmitrybrant.com/diskdigger](http://dmitrybrant.com/diskdigger)

[http://www.diskinternals.com/partition-recovery/](http://www.diskinternals.com/partition-recovery/)


Edit:Also a link for email reader

[http://www.mitec.cz/mailview.html](http://www.mitec.cz/mailview.html)

These are all for use in windows as I am still learning my way around Ubuntu....

---

### Post by Quarkrad on 2010-01-26
I have never tried to recover files where the HD was formated with another file system but I have had great success where I have reformatted a winxp HD with a c:/format and done a fresh install of winxp.  I used a piece of software called getdatabask (for fat or ntfs) -it got all my files back from the old system!  It may not like ext4 but might be worth a try!

---

### Post by cas007 on 2010-09-18
Well, to everyone out there with a similar problem, or a problem that they will have in the future the files WERE recovered.

For a recap:

40Gb Hard disk originally had Windows XP installed. Outlook Express folders not backed up by accident, but they were needed as important info was in them.

Ubuntu 9.10 (and subsequently to 10.04) installed from Live CD and was installed onto the full 40GB size of the hard drive, thereby 'wiping out' the existing Windows installation. 

When this was found out by me (I was in the US at the time) I instructed the hard drive be removed immediately from machine pending recovery operations. This was done (see below).

Posted the request as post #1.

Some suggestions were given.

Went and found the solution by myself.

I used a Seagate Replica External Hard drive by prying it open and replacing the internal 250Gb drive with the 40Gb drive that needed the files recovered. I used a C600 Dell Latitude Laptop running Windows XP SP2 to do this recovery. I attached the Seagate Replica via USB (v1.1). 

I had tried using another generic external enclosure from a no-name company through Maplins (UK), but the enclosure did not have very good electronics as the overwritten Windows partition, where the Outlook Express files had been found, was not seen by the program (the one that had been found when the 40GB drive had been put inside the Seagate Replica). So I put the 40 GB drive back into the Seagate Replica enclosure. (If anyone is wondering how I discovered that the two external enclosures were of different qualities in how they were built, I had used the Seagate because I did not realise that my mum had bought a no-name external enclosure, and she was out at the time of me doing this so she could not tell me that she had one. Otherwise I would have used this cheap one and would not have discovered this problem - thinking that the program was at fault or not able to do the job because of the overwrite problem).

I came across and tested EASEUS Data Recovery Wizard, found that it recovered data from a large variety of partition types and that it 'saw' the files that need to be recovered. So I obtained a copy and recovered _**all**_ Outlook Express files and folders. An operation that took about 12 hours in total (mostly because of indexing the file systems on the Hard Disk).

So anyone who says that files cannot be recovered when overwritten by a different file system does not understand how file systems work. Having been through this experience I can attest to the fact that files are never really lost. I have seen files 5 or more years old in the recycle bin after they were deleted. You can get this program your self and run it in demo mode and see what it finds. Pretty amazing.:)

So do take note. The name brand enclosures are more expensive because they are BETTER than the cheaper, generic ones. Without the Seagate this recovery would not have happened

---

### Post by ottosykora on 2010-09-18
yes this can be possible sometimes , explicitly in situation like yours. Having fat/ntfs system first, formating to ext? after.
The problem is not the formating itself, the files could be recovered then by many software, but here we have to know, that windows writes to the disk starting from beginning of the disk and attempts to write all data consecutively. This was initially meant to be defragmented.
But linux systems will write somewhere in the middle of the allocated space, little here, little there, well yes I know there is system behind it, but doing that, they will leave lot of untouched space between own linux data, particularly on the beginning and end of the partition. If the lost windows file is in such untouched space, possibility is fair to get it back. Particularly, if such files are at beginning of the partition where linux will not try to write much if there is space elsewhere.
I know that there are some urban legends around, that someone can retrieve really overwritten data, but this is nonsense. In such cases the data was simply found on places where the other software did not write anything yet. And since simple operating system installation will use some 10 percent of such 40g disk the probability is rather big that files can be recovered.
And if the original was placed at beginning of the partition (windows) and next is linux (starting write from the middle somewhere) the chances is even bigger to find many fragments. And files from Outlook Express (not outlook pst!) are relatively easy to be recovered.


BTW: this is also the reason, why not needed hard drives should be physically destroyed rather then formated, wiped and what ever if sensitive nofs can be on them . Wiping drives to day with their big chache is geting really difficult.

---

