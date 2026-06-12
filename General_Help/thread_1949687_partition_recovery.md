---
title: "partition recovery?"
date: 2012-03-30
forum: General Help
---

### Post by bobman321123 on 2012-03-30
Does anyone know how to recover a parition?
It's been formatted once by me, and once by a windows installer, which refused to move past the key acceptance, so I want it back.
I don't think I've written any data over it. Any ideas?

---

### Post by oldfred on 2012-03-30
What format was it? 

Anything written overwrote what was there. But if you were installing Windows to it that would have erased everything anyway. So was it not backed up?

Test disk is in the repositories:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by bobman321123 on 2012-03-31
It had windows 7 on it, so I'd imagine NTFS.

---

### Post by ajms1989 on 2012-04-03
In most of the  cases, only some part of the data are overwritten but most of the them can be recovered using partition recovery software.  

It's doesn't matter whatever the file system is or weather any file are still left to recover or not, you just have to download & run the software. After which, it will gives you the preview of recoverable files and folders but won't let you recover it unless you buy the complete version.

Majority of software are available on web, you should be careful while choosing them.  

So just check it out and let me know the results..

Thanks
Oliver

---

### Post by Mark Phelps on 2012-04-03
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of GetDataBack for NTFS from Runtime Software in MS Windows.
5) Run GetDataBack and select the option to find Deleted files.
6) When done, browse the filesystem in the app to see if your directories and files were found.  If so, view some to confirm the contents are intact.
7) If they are, you will have to purchase GetDataBack to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, last time I checked, GetDataBack for NTFS was $80, USD.

There's also a FREE MS Windows file system recovery app known as Recuva.  You could try that first -- but my experience in MS Windows is you get what you pay for.

Your data ... your money ... your choice.

---

### Post by bobman321123 on 2012-04-03
-_- nevermind, it turns out that the partition was wiped and someone tried reinstalling windows on it *several times* before I could fix it.

---

### Post by jacobs1234 on 2012-11-21
It seems it is a little hard as you already formatted the partition twice. I had the issue before and i used partition recovery tool to get it back. you may take a try. or maybe you can use some data recovery tool to get your data back. i used EaseUS product. it helped me solve the problem.

---

