---
title: "Wiped 1TB HD with USB startup disk creator"
date: 2012-01-16
forum: General Help
---

### Post by amanpreetsarna on 2012-01-16
Hi all, 

I (quite stupidly) ran into a huge problem whilst running USB startup disk creator when trying to update my Ubuntu. I mistakenly clicked erase disk when my external Seagate HD (1TB) was selected, rather than my USB drive. As soon as I had realised this I pulled the USB cable out of my HD, but when I reinserted it Ubuntu mounted it automatically as "1 TB Filesystem" (rather than "Expansion Drive") and it was completely empty. 

I would imagine that the Startup Disk Creator formatted my HD, but if I can see an empty drive now mounted on Ubuntu, is there any hope (e.g. using Testdisk/PhotoRec) of recovering any data?

Thanks to all in advance!

Aman

---

### Post by iponeverything on 2012-01-16
I would not throw in the towel without giving PhotoRec and Testdisk a shot.

---

### Post by pretty_whistle on 2012-01-16
And you may only get* part* of your data back rather than *all.*

---

### Post by amanpreetsarna on 2012-01-16
Thank you for the responses so far! Just to update things, I'm running testdisk at the moment. USB Startup Disk Creator formatted my drive from NTFS to FAT32. Am currently trying to use Testdisk to look for a NTFS partition lurking about.

As an aside, I'm sure the same thought runs through the minds of anyone who has lost data - next time I will backup more often.

---

### Post by pretty_whistle on 2012-01-16
> **amanpreetsarna said:**
> Thank you for the responses so far! Just to update things, I'm running testdisk at the moment. USB Startup Disk Creator formatted my drive from NTFS to FAT32. Am currently trying to use Testdisk to look for a NTFS partition lurking about.

As an aside, I'm sure the same thought runs through the minds of anyone who has lost data - next time I will backup more often.
Good luck.
:)

---

### Post by Mark Phelps on 2012-01-17
I recently had a similar problem in that an NTFS partition got formatted -- and solved it by (1) reformatting it back to NTFS, and (2) using GetDataBack for NTFS to recover all the directories and files.  This is an MS Window utility -- which is not free.

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, my suggestions are the following (based on my experience at doing this successfully):
1) In Windows, download and install the trial version of GetDataBack for NTFS from Runtime Software.
2) Connect your reformatted drive.
3) Run GetDataBack in deepest discovery mode.
4) Check the filesystem display to see if the directories and files were found.
5) Try to open some of the files to confirm the contents are OK
6) If they are, you will have to purchase it to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, BTW, last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

### Post by amanpreetsarna on 2012-01-21
Thanks for the advice! I used GetDataBack Trial Version, but it wasn't able to recover usable files for some reason (perhaps I was not using it correctly).

I think you were right about Windows utilities - after having no real luck with testdisk/photorec, I went back to chkdsk (which I have used plenty of times in the past), and it was able to fix the original NTFS partition so the files were readable. Got back almost everything apart from some films (which I have as DVD anyway!)

Thanks again!

---

### Post by sudodus on 2012-01-21
Good luck with ***GetDataBack***. As *Mark Phelps* wrote, you must buy it to make it to do the actual recovery. If there is a lot of valuable data, I think you should buy it ;-)

A free alternative is ***PhotoRec***. It can recover files of several kinds (probably all kinds you need to recover) by searching for file headers directly on the drive. It can use, but need not, any information about the file system. So if the partition table is destroyed, but you know there was NTFS, tell it to PhotoRec.

Furthermore, the files names and the directory structure are lost. Probably PhotoRec finds a lot of files for you, but it is a huge job to rename them and organize them into directories. Maybe a good choice is to look for one file type each time.

*Edit: Glad you managed so well with good old **chkdsk*** :KS

---

### Post by Mark Phelps on 2012-01-21
> **amanpreetsarna said:**
> Thanks for the advice! I used GetDataBack Trial Version, but it wasn't able to recover usable files for some reason (perhaps I was not using it correctly).

GetDataBack has several operational modes -- and they're not intuitive.

To get it to work, you have to right-click on the desktop icon and choose Run as administrator.

Then, I would first try the bottom choice: I want to recover deleted files.

It will search for a while, and then present you with a list of historical file systems.  You can choose one after another, and it will then search using that filesystem.  When it finds stuff , it is able to preserve the directory structure and file contents.

IF that finds nothing, you can try the choice: systematic file damage -- and see if that does any better.

---

