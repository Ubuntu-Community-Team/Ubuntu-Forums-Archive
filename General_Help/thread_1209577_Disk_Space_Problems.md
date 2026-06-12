---
title: "Disk Space Problems"
date: 2009-07-10
forum: General Help
---

### Post by imartinon on 2009-07-10
Hi Guys,

Hope you can help me here with this issue, I have an Ubuntu Jaunty 64 OS with 8 GB or RAM and a Seagate 500 GB as the main HDD, and I have a slave drive of 80GB that every time I try to copy a big file it tells me the the file is too big and that there is no space on it. I got to mention that the secondary drive has only 32GB of usage and it has over 40 GB of free space. This is a FAT32 drive partitioned and formatted with Geparted. I have tried to repartitioned it and reformat it over and over and the problem always comes.

I hope you guys can help.
Thanks

---

### Post by merlinus on 2009-07-10
fat has a limit of 4G for one file.  Try formatting the hdd as ntfs.

---

### Post by drs305 on 2009-07-10
How large is "big"? fat32 max file size is 4GB. Here is a reference:
[http://en.wikipedia.org/wiki/File_Allocation_Table]("http://en.wikipedia.org/wiki/File_Allocation_Table")

---

### Post by imartinon on 2009-07-10
> **drs305 said:**
> How large is "big"? fat32 max file size is 4GB. Here is a reference:
[http://en.wikipedia.org/wiki/File_Allocation_Table]("http://en.wikipedia.org/wiki/File_Allocation_Table")

Good Point, usually I am trying to move 6+ GB files, will try using NTFS thanks.

---

### Post by Gizenshya on 2009-07-10
^^^ what they said.

I've had this problem many times using ISO's and drive backup images.

What I usually do is just split them up into chunks, though.  you can do this via commandline easily, as long as you have free space.  That way you don't have to format the drive.  Most of my drives are NTFS now, though.  Imn the past, I kept many in FAT32 because some Linux distros I used had trouble writing to and sometimes reading from NTFS volumes, but that is not an issue anymore.

---

