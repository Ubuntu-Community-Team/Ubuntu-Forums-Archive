---
title: "Cant find data in Mounted drive"
date: 2010-02-21
forum: General Help
---

### Post by getknk on 2010-02-21
Hi friends,
I'm a newbie and I've installed ubuntu in my virtualbox
I'm trying to mount a second partition and used to do as..


sudo mkfs.ext3 /dev/sdb
sudo mount -t ext3 /dev/sdb /media/data2

I've successfully mounted the drive, but cant view the data !!
I checked 
cd /media/data2 
and I can find only "lost+data" directory , but definitely data is present 

Can you please help me in finding the missing step?
Thanks again
yes2exams

---

### Post by jamesisin on 2010-02-21
Did you create a folder in /media called data2?

[http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587)

---

### Post by getknk on 2010-02-21
Yes mate..
"data2" is inside /media

and I can "cd" to /media/data2


Also, the data is still existing..
coz when i put a df -k, the size shows the data used..

---

### Post by miegiel on 2010-02-21
> **getknk said:**
> Hi friends,
I'm a newbie and I've installed ubuntu in my virtualbox
I'm trying to mount a second partition and used to do as..


sudo mkfs.ext3 /dev/sdb
sudo mount -t ext3 /dev/sdb /media/data2

I've successfully mounted the drive, but cant view the data !!
I checked 
cd /media/data2 
and I can find only "lost+data" directory , but definitely data is present 

Can you please help me in finding the missing step?
Thanks again
yes2exams

```
sudo mkfs.ext3 /dev/sdb
```
Makes (mk) a new file system (fs) on your disk (in windows land it's called *[COLOR="Red"]formatting[/COLOR]*). Besides (as far as I know) you shouldn't make a file system on your disk but always make them in a partition.
eg:
```
sudo mkfs.ext3 /dev/sdb**[COLOR="Red"]1[/COLOR]**
```

You also don't mount disks, you mount partitions. So it should have also been :
```
sudo mount -t ext3 /dev/sdb**[COLOR="Red"]1[/COLOR]** /media/data2
```

---

### Post by jamesisin on 2010-02-21
Did this drive previously have data on it?  If you formatted that drive (as miegiel indicated above) then you have formatted over you data.  This data may still be recoverable but we will have to use different tools.

If you take a look at the link I provided above it contains complete instructions for adding a second drive to your Ubuntu machine.  I would go over those steps just to make sure that you didn't skip a step or misdirect a step along the way.

---

### Post by getknk on 2010-02-21
> **miegiel said:**
>  Besides (as far as I know) you shouldn't make a file system on your disk but always make them in a partition.


This is slightly bit more complex. Since I'm using virtualbox, I'm using it as "Primary Slave" and it comes up as /dev/sdb 
But even in this case, when i mount an entire disk, it should show the contents right?

But last time, i made it to work somehow.. searching.
but forgot to write down :(

---

### Post by jamesisin on 2010-02-21
Whether virtual or actual a drive is a drive and a partition is on a drive.  That hierarchy should exist regardless.  There are issues in attempting to mount a partitionless drive.  Even when a drive contains one partition, this relationship still generally exists (ie, the partition may not fill every bit of the drive).

Does Disk Utility recognize it as containing a partition?

---

### Post by getknk on 2010-02-22
> **jamesisin said:**
> 

Does Disk Utility recognize it as containing a partition?

how to check that mate?

I fear, since I've installed as a virtual disk (vdi) volume, and my system C:\ drive space has gone down, it might be the reason the vdi data is not show?

---

### Post by jamesisin on 2010-02-22
Disk Utility is located at System &#8212;> Administration &#8212;> Disk Utility.

Are you trying to access your c: from the Ubuntu virtual system?

---

### Post by getknk on 2010-02-26
> **jamesisin said:**
> Disk Utility is located at System —> Administration —> Disk Utility.
thanks mate..

> **jamesisin said:**
> 
Are you trying to access your c: from the Ubuntu virtual system?
No no.. I meant to say since ubuntu is installed in virtual system, a size reduction to parent windows OS will have a negative impact?

---

### Post by jamesisin on 2010-02-26
You want to reduce the size of your Windows partition?  That is possible to do without damaging files contained therein.  I recommend using gparted (available as a free CD download or included in the Ubuntu installer CD).  You will want to back up your data just in case.  Also, I recommend shrinking the partition from the right toward the left (from the end of the drive toward the beginning).

None of this should effect your Ubuntu VM.  The VM is essentially one file (two arguably) and as long as you don't delete that file you'll be ok.  Gparted is designed to move data out of the way rather than simply moving the partition edge over that data.

---

