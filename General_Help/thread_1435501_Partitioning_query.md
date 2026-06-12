---
title: "Partitioning query"
date: 2010-03-21
forum: General Help
---

### Post by bigseb on 2010-03-21
Can one extend a partition backwards. What I mean is currently my disc looks like this: Windows 7 = 75Gb, Ubuntu 75Gb. I want to decrease the Windows 7 partition to 50Gb and extend the Ubuntu partition to 'absorb' the balance. Any ideas?

---

### Post by wqawasmi on 2010-03-21
> **bigseb said:**
> Can one extend a partition backwards. What I mean is currently my disc looks like this: Windows 7 = 75Gb, Ubuntu 75Gb. I want to decrease the Windows 7 partition to 50Gb and extend the Ubuntu partition to 'absorb' the balance. Any ideas?

Not sure if I fully understand, but what you can do is download gparted:

```
 sudo apt-get install gparted 
``` 

From there, start it up, right click your windows partition, and shrink it to the size you want.

You'll be left with un-allocated space, from there, right click your Ubuntu partition and click extend, choose the ammount and there you go.

If you have trouble shrinking the Windows partition, then just shrink it from Windows it's self, go back into Ubuntu, and extend the Ubuntu partition with the un-allocated space.

---

### Post by drs305 on 2010-03-21
Take a look at this post I made a while back in response to an installation bug. Start with the "basic rules" section, as what preceeds it probably doesn't apply and is just background:
[ Expanding an Ubuntu System Partition  ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by bigseb on 2010-03-21
Thanks guys. Here is what the current state of affairs is (in its entirety):
[ATTACH]150906[/ATTACH]
A lot of empty space there too... ideally I'd like to clean that up as much as possible, then the shrinking/extending thing...

I will try shrinking via the Windows Partition Manager, then with Gparted which I already have if WPM doesn't do it...

---

### Post by bigseb on 2010-03-21
Ok the WPM doesn't do what I want. And Gparted doesn't make sense, it won't remove those pesky little bits inbetween (see attachment above).

An alternative would be to repartition the whole drive then reinstall everything from scratch. Then I would have to save all my drivers and settings somewhere though. I can't always download from scratch.

---

### Post by RedRat on 2010-03-21
Before you repartition your ntfs partition, backup all of your files, just in case. Also run your defragmenter program in Windows, try to get all your fragmented files together. I would suggest you use something like Diskeeper, a commercial program, to do this. I believe it can move all the files to the start of the Windows partition. The Windows internal defragmenter merely defragments the files more or less where they are.

---

### Post by kaligus on 2010-03-21
The only way I know to do exactly what you want is to carefully pick both wondows and linux partition sizes and since they both allocate space differently that is a tricky ordeal on a good day.

Even formatting brand new drives from scratch with those two OS always leaves little bits laying about if you are not very careful.

This is something to do with 'cluster' sizes in windows *or* 'inode' sizes in linux.

I have forgotten how exactly to alter these sizes but making the two OS have the same allocation size which is evenly divisible on the hard drive into the desired number of partitions is the only way I have found to eliminate the little stragglers.

---

### Post by srs5694 on 2010-03-21
Your Linux partition is a logical partition inside an extended partition. This means that, after you resize the Windows partition, you must resize the extended partition and only then will you be able to resize the Linux partition.

Also, GParted won't resize a partition that's currently in use. Thus, you must reboot to an emergency disc to do this work. You may also need to disable swap space if the emergency disc notices swap space on your hard disk and attempts to use it.

---

### Post by bigseb on 2010-03-22
Sounds like I'll have nothing but hassles by repartition now. So to door number two: get my nvidia drivers and other bits and pieces onto a flash drive, boot into windows, delete the linux partition(s), create a partition of the size I want, install windows into that new partition, boot into new windows installation, format the original (now enlarged) partition and install Linux there.

Phew!

Question now is how do I get all my drivers and stuff so I don't have to download them all again? I only have so much bandwidth to use a month and mines cutting it close...

---

### Post by srs5694 on 2010-03-22
> **bigseb said:**
> Sounds like I'll have nothing but hassles by repartition now. So to door number two: get my nvidia drivers and other bits and pieces onto a flash drive, boot into windows, delete the linux partition(s), create a partition of the size I want, install windows into that new partition, boot into new windows installation, format the original (now enlarged) partition and install Linux there.


Your "door number two" option is *far* more hassle than resizing an existing Linux installation! The only area in which the partition resizing option is more trouble is in creating a full backup of Windows in case of problems -- and that's something you should do in any event.

---

### Post by bigseb on 2010-03-22
> **srs5694 said:**
> Your "door number two" option is *far* more hassle than resizing an existing Linux installation! The only area in which the partition resizing option is more trouble is in creating a full backup of Windows in case of problems -- and that's something you should do in any event.
Actually I just finished the door number 2 option. Whole deal took a little over 4 hours but its done. Turned out exactly how I wanted it so I'm happy :p

---

