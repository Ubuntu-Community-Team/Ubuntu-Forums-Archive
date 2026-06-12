---
title: "Hard drive Bad sector! Need some help."
date: 2009-11-11
forum: General Help
---

### Post by Helloo1234 on 2009-11-11
Hello, 
 
I have been trying to install Ubuntu on my desktop. I needed to partition my Hard drive to be able to have a shared folder between Linux(Ubuntu) and Windows XP Home Edition. In the GParted App in "Try Ubuntu with out installing" i noticed it had a warning saying:
 
>>*Warning: The disc has bad sector. This means physical damage on disc*
>>*Surface caused by detoriation, manufacturing faults or other reasons.*
>>*The reliabilty of the disc may stay stable or degrade fast. We suggest*
>>*Making a full backup urgently by running "ntfsclone--rescue..." then*
>>*run "chkdsk /f /r" on Windows and reboot Twice! Then you can resize*
>>*NTFS safely by additionally using the--bad--sectors option of ntfs resize.*
 
Question:
 
I was wondering if anyone could  explain to me , or give me a link that explains how to perform a back up running "ntfsclone--rescue" ? Also I looked on other sites and they said that maybe my disc maybe permanently scraped. I that true?
 
Thank you for your time and help,
 
Helloo1234

---

### Post by Sin@Sin-Sacrifice on 2009-11-11
[http://man.linux-ntfs.org/ntfsclone.8.html](http://man.linux-ntfs.org/ntfsclone.8.html)

---

### Post by mr_steve on 2009-11-11
> **Helloo1234 said:**
> Hello, 
 
I have been trying to install Ubuntu on my desktop. I needed to partition my Hard drive to be able to have a shared folder between Linux(Ubuntu) and Windows XP Home Edition. In the GParted App in "Try Ubuntu with out installing" i noticed it had a warning saying:
 
>>*Warning: The disc has bad sector. This means physical damage on disc*
>>*Surface caused by detoriation, manufacturing faults or other reasons.*
>>*The reliabilty of the disc may stay stable or degrade fast. We suggest*
>>*Making a full backup urgently by running "ntfsclone--rescue..." then*
>>*run "chkdsk /f /r" on Windows and reboot Twice! Then you can resize*
>>*NTFS safely by additionally using the--bad--sectors option of ntfs resize.*
 
Question:
 
I was wondering if anyone could  explain to me , or give me a link that explains how to perform a back up running "ntfsclone--rescue" ? Also I looked on other sites and they said that maybe my disc maybe permanently scraped. I that true?
 
Thank you for your time and help,
 
Helloo1234

Generally speaking, when a disk develops a bad sector, you want to back up your files, immediately. The disk could just have one or two bad sectors, and continue to work fine for a long time, or it could start developing more and more bad sectors and become a paperweight overnight. It's impossible to know for sure.

Backup your files, start shopping for a new hard drive.

---

### Post by Mark Phelps on 2009-11-11
I take it you're trying to install 9.10, right?

Seems this new "feature" is causing lots of problems with perfectly OK hard drives.

Suggest you boot into Windows XP and run chkdsk on all your partitions.  If they come back with no errors, then you're getting "false positives" with Ubuntu 9.10.

In that case, I would try the following:
1) Download a burn a GParted LiveCD from distrowatch.com
2) Boot into the GParted Live CD
3) Use it to shrink your XP partition and to create a new partition for Ubuntu.

Reboot using the Ubuntu LiveCD, select Manual Partitioning, and see if it will then let you install.

---

### Post by fluffman86 on 2009-11-11
The SMART tools are great for a lot of things, but they've been picking up false positives and yelling that my HDD was dying for years now.  I just ignore it.

---

### Post by seeker5528 on 2009-11-11
You should do some additional checking to verify there are actually bad sectors on there, usually tools available from the manufacturers web site are preferred, commonly available in the form of an ISO image you can burn, then boot from.

If the drive is actually failing, it would be preferred to use ddrescue, it will skip the bad spots on the first pass, making additional passes later to try to get as much as possible, where ntfsclone will fail if the bad spots are not actually marked as bad in the file system.

ddrescue *infile outfile*

So if your failing disk was /dev/sda and your replacement disk was /dev/sdb the command would be:

ddrescue /dev/sda /dev/sdb

If you wanted to do a partition to a partition, or a partition to a file, you could do that too:

ddrescue /dev/sda */location/of/some/file.img*

I have not used it that way, I think you might have to create the file first:

touch */location/of/some/file.img*

In all cases the destination has to be equal to or larger than the source, or in the case of a disk or partition to a file the free space on the partition where the file is located has to be equal to or larger than the source. 

If things seem really bad, like you might lose access to the drive completely before a complete copy can be made or new bad sectors are appearing left and right, it can be preferred to mount the partition and the partition you want to copy stuff to and use something like mc (midnight commander) to copy the important files first then working through the less important ones, which can mean a lot of time monitoring the situation if there are a lot of files that can't be copied.

Later, Seeker

---

### Post by Helloo1234 on 2009-11-11
Ok thank you very very much for all the replies this will surely help alote thank you very much.

---

