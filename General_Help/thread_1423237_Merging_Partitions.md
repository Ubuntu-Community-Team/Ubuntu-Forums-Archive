---
title: "Merging Partitions"
date: 2010-03-06
forum: General Help
---

### Post by xtremesupremacy3 on 2010-03-06
Hey there people!

Okay, I know what your thinking, why start another thread on this when so many exist, but mine has a specific question or doubt that remains unanswered.

I have Karmic on my pc and used to have a backup partition, which is now unallocated. However, the problem I have is that the order of my partitions are as followed (left to right):

146.59 Gb Unallocated
Sda6 139.37Gb (Ext4) Root partition
Sda7 (Linux Swap)
Sda5 (Linux Swap)
(See screenshot provided)

Now I know I can merge the two through Gparted on the LiveCD, but...

Here's my question:

Everyone so far has had Ubuntu partition first, THEN unallocated. I on the otherhand have first the Unallocated, THEN Ubuntu partition.

If I was to merge this using Gparted on the LiveCD, is it:

1) Even possible
2) Mess Grub up
3) Have bad consequences.

Thanks for your help
Arthur

---

### Post by oldfred on 2010-03-06
Moving the start of your root partition can lead to issues. You also have two swaps, I would find out which fstab is using and delete the other (or change it)

I would either make it /home and move home there which adds space or make it a data partition with some or all of your data folders that are in /home.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by ajgreeny on 2010-03-06
The order of partitions in ubuntu is not really important, so rather than mess around with moving your root partition backwards on the disk, which is what you would be doing by adding the space to to root, just make a new ext3 or ext4 partition for data and automount it at boot time with an appropriate line in your /etc/fstab file.

If you really want to merge the unallocated into root, it can be done, but make sure you have good backups, just in case, and be prepared to wait several hours, possibly, for it to be carried out.

The alternative is just to wait a couple of months for lucid, and then backup everything, wipe everything, and then do a clean install with a separate /home partition at that time.

---

### Post by louieb on 2010-03-06
Its ok to have Linux installed anywhere on the hdd but if you want to move it to the front of the drive thats ok too.  

It will mess up GRUB - no problem -easily fixed.

One way to do it that reduces the chance of data corruption.

With Gparted run from the live CD. 

Right click on sda6 - select copy   
Right click on the unallocated space - select paste 
[Gparted Documentation - Copying]("http://gparted.sourceforge.net/larry/move/move.htm")  

When done you will have an exact copy - guessing the new partition will be sda1. The things you have to fix 1) is they both will have the same UUID. and GRUB will have to changed to  boot the new partition. 

change the UUID on the old partition with tune2fs (important note the uppercase -U) 

```
sudo tune2fs -U random /dev/sda6
```fix GRUB - [Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275") 

See if every thing works - if so then you can delete the old partition and grow the new to fill it now unused space.
  
Or you could just make a new partition in the unused space and move your data to it.

---

### Post by xtremesupremacy3 on 2010-03-06
> **louieb said:**
> Its ok to have Linux installed anywhere on the hdd but if you want to move it to the front of the drive thats ok too.  

It will mess up GRUB - no problem -easily fixed.

One way to do it that reduces the chance of data corruption.

With Gparted run from the live CD. 

Right click on sda7 - select copy   
Right click on the unallocated space - select paste 
[Gparted Documentation - Copying]("http://gparted.sourceforge.net/larry/move/move.htm")  

When done you will have an exact copy - guessing the new partition will be sda1. The things you have to fix 1) is they both will have the same UUID. and GRUB will have to changed to  boot the new partition. 

change the UUID on the old partition with tune2fs (important note the uppercase -U) 

```
sudo tune2fs -U random /dev/sda7
```

fix GRUB - [Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275") 

See if every thing works - if so then you can delete the old partition and grow the new to fill it now unused space.
  
Or you could just make a new partition in the unused space and move your data to it.

I have to admit, this sounds a brilliant idea, this way i reduce the chance of having major data loss problems which I dont want since I have to use this for my university work and sounds rather ideal in the case of an unexpected problem.

I am not going to mark this as solved just yet until it's been done successfully and then others with this problem may learn from it, so far i am more than impressed with the number of responses in so little time...Thank you all, so much!

P.S. Just to confirm, when you say sda7 I suppose you mean sda6 since otherwise I would be copying a swap partition?

---

### Post by louieb on 2010-03-06
Brain fart - yes I met the current root partition. sda6 - will edit the original post

---

### Post by xtremesupremacy3 on 2010-03-14
Hello,

Sorry its been a while but I've been stuck doing uni work.
Anyway...here are the results.

I followed your guide which worked perfect, exactly as stated, except it was a nightmare with Grub...it hated me.
After having copied the partition to sda1, and having then deleted sda6(dumb of me)...it told me it couldnt find a device...so after a lot of messing around it worked up to the point where I got the list of OS's but it couldnt find the /.
So it meant reconfiguring that and then I was ready to go.

So if you need to do this, dont take the poster above me's advice on Grub lightly, make sure you know what to do at that stage.

But anyway, it turns out it was all in vain, due to the fact that because the unallocated space and the swaps are located under the sda3 branch, it wont let me merge...I hope maybe someone can give advice on that...please see the screenshot attached.

At this point it would be solved for most, but not for me due to the sda3 thing.

Thanks
Arthur

---

### Post by oldfred on 2010-03-15
It requires two parts. An extended partition is a container but is still a partition, so you have to move it to the right so It only holds the swaps. Then the unallocated will be in the primary area next to sda1. You can check fstab to see which swap is used and also deleted the other one.

---

### Post by xtremesupremacy3 on 2010-03-15
Well, that did the trick, I FINALLY have my harddrive back.

Thank you all so much for your help!

Arthur

---

