---
title: "Advice on external hard drive"
date: 2011-02-07
forum: General Help
---

### Post by petersull on 2011-02-07
I have a dual boot laptop running ubuntu 10.01 and Windows Vista Home Basic. I need some cheap extra storage to supplement the nearly full 60Gb internal hard disk.

In order to store data from both Windows and ubuntu, do I need a particular type of external hard drive or special formatting or partitioning?

If the hard drive route is particularly complicated, maybe I would be better off with a couple of USB flash drives. One for Windows and one for ubuntu.

Any advice on this would be much appreciated.

Best regards, Pete.

---

### Post by simonmoon42 on 2011-02-07
Are you going to be using the data on both platforms? Like sharing music and pics. Or is the data Windows and Ubuntu specific? If the data is platform specific I would recommend separate devices. Mostly because I don't trust Windows checkdisk, Anti-Virus and the like to leave my Linux stuff alone. Maybe I should take off my tin-foil hat, but better safe than sorry.

---

### Post by coldraven on 2011-02-07
Just buy an external USB drive.
They usually come formatted FAT32 which can be read buy Ubunbtu and Windows.
However the maximum file size using FAT32 is 4GB (minus one byte AFAIR).
So if you want to store movies you need to format it to NTFS. Simply done using gparted.
Just make sure that you select the correct drive from the drop down in the top right corner of the gparted window.
My 1TB USB drive (samsung story) works fine with both OSs.

---

### Post by glene77is on 2011-02-07
> **coldraven said:**
> 
Just buy an external USB drive.
. . .  My 1TB USB drive (samsung story) works fine with both OSs.

Cold, 
My advice also.    :p
I use three USB external HD, with no problems.

---

