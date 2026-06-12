---
title: "Copying Many Files En Masse from NTFS to NTFS, Fragmentation"
date: 2010-07-07
forum: General Help
---

### Post by curryking1 on 2010-07-07
Hi,

I have a question about copying many files from one hard drive to another at one time.

Both drives I would like to copy to and from are formatted using NTFS (I would like to access each while using Windows). Both drives are 1 TB drives. The files I would like to copy to the second drive total 800 GB.

In Windows 7, there appears to be a great deal of fragmentation on any given file when I copy files to the new drive. I assume I would get the same result if I were using XP or Vista.

My question is: If I use Ubuntu 10.04 to copy these files from one NTFS drive to the other, can I reduce the frequency of fragmentation of files? Are there any applications I can download for Ubuntu 10.04 which could decrease the frequency of fragmentation while copying?

The reason I ask is because defragmenting so many files after copying is very time-consuming. My hope is I can significantly reduce fragmentation on the first copy somehow.

Thanks for any help, cheers :)

P.S. Please assume the 1 TB drive I am copying to is empty :)

Also, this is all just for backing up files and having quick access to them if need be.

---

### Post by user38861 on 2010-09-11
CurryKing1, Quick answer.... the fragmentation under Ubuntu 10.04 (ntfs-3g) is actually even worse than with Windows XP. I ended up with 54.7% fragmentation copying to an empty 1.8TB disk... see below.
I'm really beginning to hate NTFS!

2010-09-11 09:36:54: D
*Status Report of O&O Defrag on Machine XPxxxxxx created: 11/09/2010
09:36:54*

 Report for volume (D)
*Action carried out:*     *ANALYSIS*
*Status:*     *Successful*
Start:     11/09/2010 09:36:12
Finish:     11/09/2010 09:36:54
Time taken (hh:mm:ss):     00:00:42
Volume data
Serial number:     xxxx-xxxx
Device name:     \Device\HarddiskVolume2
File system:     NTFS
Total space:     1.82 TB (2,000,396,480,512 bytes)
Free space:     897.02 GB (963,167,191,040 bytes)
Total clusters:     488,378,047
Free clusters:     235,148,240
Sectors / cluster:     8
Bytes / sector:     512
MFT length:     271581184 bytes
MFT mirror start:     244,189,023
Start of MFT reserved area:     856,832
End of MFT reserved area:     61,833,696
Volume statistics
Total no. of files:     264,717
Total no. of directories:     314
Analyzed files:     265,031
Moved files:     0
Fragmented files     before:     2,468
    after:    2,468
Degree of fragmentation:     before:     54.702
    after:    54.702

---

### Post by curryking1 on 2010-09-17
Sweet, thanks for the response. I opened this thread a while ago lol, thanks a lot for the info. I guess NTFS just likes to fragment :(

---

