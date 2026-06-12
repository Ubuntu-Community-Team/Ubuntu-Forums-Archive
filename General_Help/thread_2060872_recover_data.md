---
title: "recover data"
date: 2012-09-21
forum: General Help
---

### Post by then_dude on 2012-09-21
Hello everybody,  i got two questions, both involve data recovery.   

my brother has deleted his partition table of an windows NTFS harddisk, but has done nothing more.   i wonder what is the best software for


[LIST=1]
[*]get the partition table back. i would like a linux software which can cope with as much file systems as possible.
[*]if it is not possible to get back the partition table. i'm looking for a decent recovery software. Is it possible to recover the directory structure and the files within, also to recover with the correct file names ?
[/LIST]
thanks in advance
kind regards

---

### Post by raja.genupula on 2012-09-21
I think you Have to read this once 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Deepak A on 2012-09-21
You can recover data or partitions using System rescue CD.
Download it from the link below and give it a try. 

[http://space.dl.sourceforge.net/project/systemrescuecd/sysresccd-x86/3.0.0/systemrescuecd-x86-3.0.0.iso](http://space.dl.sourceforge.net/project/systemrescuecd/sysresccd-x86/3.0.0/systemrescuecd-x86-3.0.0.iso)

Familiarize with the available tool in System rescue CD,
[http://www.sysresccd.org/System-tools](http://www.sysresccd.org/System-tools)


*testdisk* is a nice tool and will be useful while recovering data. 



Deepak

---

### Post by Mark Phelps on 2012-09-21
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

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

Your data ... your money ... your choice.

---

### Post by Concepts1231 on 2012-09-25
Hi,

Your Question is so common and i also face this problem i just want to refer you what i used for my solution of partition recovery .

I search it in Google and find that useful for me you can also try this software which is known as **kernel for partition recovery**

Hope this information help you Good Luck

---

