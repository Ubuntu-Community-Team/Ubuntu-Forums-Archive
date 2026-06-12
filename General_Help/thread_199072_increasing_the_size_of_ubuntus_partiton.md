---
title: "increasing the size of ubuntus partiton"
date: 2006-06-18
forum: General Help
---

### Post by flankker on 2006-06-18
hi, i am currently dual booting windows and ubuntu. i created a partition for ubuntu and installed it there, but now i realised that the size i allocated is not going to be enough for the future.

so my question is how do i resize the partition? i want to shrink the windows one and increase the ubuntu one.

thanx.

---

### Post by MarinaraOfDeath on 2006-06-18
You can boot with the install disk and run QtParted again. Use the which command in a terminal to find it. Make the Windows partition smaller, which will be done non-destructively, so no data loss for *resizing* the partition. (This is not true if you *format* the partition, so review everything you've done before commiting changes!) Then you can extend the logical volume/partition Ubuntu is sitting in with the same tool. If it's in a logical partition, you'll have to make the logical volume bigger and after than add another partition or enlarge the main Ubuntu partition. 

Good luck.

---

### Post by bruce89 on 2006-06-18
Put the LiveCD in and use Gparted from it, it's in the System>Administration menu.  QTParted is in Kubuntu, not Ubuntu.

---

### Post by RRS on 2006-06-18
While using gparted from the Ubuntu live cd is okay you can also download and burn gparted as a dedicated live cd tool.
 [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

If windows is installed @ the begining of your drive (normal) then you won't be able to expand Ubuntu backwards into the freespace you create by reducing the size if your windows partition. A "quirk" of ext3 is that it can only be expanded upwards towards the end of the drive.

In post #9 of [this thread]("http://www.ubuntuforums.org/showthread.php?p=1143498#post1143498") Herman explains a work around of this that he developed and tested.

---

### Post by flankker on 2006-06-18
[QUOTE=RRS]While using gparted from the Ubuntu live cd is okay you can also download and burn gparted as a dedicated live cd tool.
 [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

If windows is installed @ the begining of your drive (normal) then you won't be able to expand Ubuntu backwards into the freespace you create by reducing the size if your windows partition. A "quirk" of ext3 is that it can only be expanded upwards towards the end of the drive.

In post #9 of [this thread]("http://www.ubuntuforums.org/showthread.php?p=1143498#post1143498") Herman explains a work around of this that he developed and tested.[/QUOTE]

thanx a lot for that link, that is exactly what i needed

---

### Post by viciouslime on 2006-06-18
[QUOTE=RRS]While using gparted from the Ubuntu live cd is okay you can also download and burn gparted as a dedicated live cd tool.
 [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

If windows is installed @ the begining of your drive (normal) then you won't be able to expand Ubuntu backwards into the freespace you create by reducing the size if your windows partition. A "quirk" of ext3 is that it can only be expanded upwards towards the end of the drive.

In post #9 of [this thread]("http://www.ubuntuforums.org/showthread.php?p=1143498#post1143498") Herman explains a work around of this that he developed and tested.[/QUOTE]
I stumbled upon this problem a few days ago. I needed to expand my /home partition into space that was before it on the drive. The solution was to use partition magic. I know it is commercial software so it isn't a solution for everyone, but just in case ayone else stumbles upon this thread it is one possible solution to consider. 

Partition magic moves the existing partition so that the free space is then at the end and then expands the partition into the free space. It would be nice if gparted could do that :) myabe one day...

---

### Post by RRS on 2006-06-18
> .....was to use partition magic. I know it is commercial software so it isn't a solution for everyone,......

The commercial aspect of Partition Magic isn't really the problem, in fact many Windows users already have it so a financial outlay isn't needed.

The problem is with the way it seems to interact with Linux partition formats, ie; poorly. Apparently data corruption can occur and results may not always be immediate. 

Because of this possibility it's use is generally not recommended in the Linux community.

I will admit to never having used it myself so my warning is from second hand knowledge only and I'm glad to hear you had no problems yourself.

Edit: typos

---

