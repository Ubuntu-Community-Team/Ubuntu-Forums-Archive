---
title: "add unallocated space to partition"
date: 2010-10-03
forum: General Help
---

### Post by joehc on 2010-10-03
Hi, 
I have 2 partitions: 
- Partition 1 = xp and ubuntu 
- Partition 2 = private matters (movies, pictures, etc.) 

I successfully obtained 5 gb of unallocated space from xp I would like to add to my partition 2. 

but inside gparted I can't partition 2 to increase, even though I have not mounted XP partition or 2 - I can only make 2 partition smaller and not bigger. 

Is it because my swap partition is in the way or? I can not figure it out 

Here is a picture showing my partitions: [http://img713.imageshack.us/img713/3861/screenshotcx.png](http://img713.imageshack.us/img713/3861/screenshotcx.png) 

Can anyone help me? 

thanks in advance 
/ Joe

---

### Post by coffee412 on 2010-10-03
> **joehc said:**
> Hi, 
I have 2 partitions: 
- Partition 1 = xp and ubuntu 
- Partition 2 = private matters (movies, pictures, etc.) 

I successfully obtained 5 gb of unallocated space from xp I would like to add to my partition 2. 

but inside gparted I can't partition 2 to increase, even though I have not mounted XP partition or 2 - I can only make 2 partition smaller and not bigger. 

Is it because my swap partition is in the way or? I can not figure it out 

Here is a picture showing my partitions: [http://img713.imageshack.us/img713/3861/screenshotcx.png](http://img713.imageshack.us/img713/3861/screenshotcx.png) 

Can anyone help me? 

thanks in advance 
/ Joe

Because your linux partition is seperated from the free space by windows partitions you cannot add the extra space to Ubuntu.

You must first have the unallocated space next to the linux partition. 

I would recommend that you backup your data and reinstall so that your first partition on the drive is the boot partition, Then the windows partition, Then the linux partition followed by swap.

For info here is a thread that talks about a similar situation:

> [http://ubuntuforums.org/showthread.php?t=724881&page=2](http://ubuntuforums.org/showthread.php?t=724881&page=2)


---

### Post by Elfy on 2010-10-03
There is no need at all to reinstall to move some space about generally.

Partition 1 and 2 are not of any real use other than to describe what you want.

Please open a terminal and run ```
sudo fdisk -l
``` post the output here.

---

### Post by joehc on 2010-10-03
> **coffee412 said:**
> Because your linux partition is seperated from the free space by windows partitions you cannot add the extra space to Ubuntu.

You must first have the unallocated space next to the linux partition. 

I would recommend that you backup your data and reinstall so that your first partition on the drive is the boot partition, Then the windows partition, Then the linux partition followed by swap.

For info here is a thread that talks about a similar situation:

Thanks for the quick answer. But i'm not sure I understand, but I'll reinstall when 10.10 is out, but how do I determine which partition should be first when I reinstall...can I do this within the installation of 10.10....so it should be like this order:
partition 1 (xp+ubuntu) + swap + unallocated space + partition 2?

then I can resize partition 2 in gparted?

EDIT:
My output:


joe@joe-laptop:~$ sudo fdisk -l
[sudo] password for joe: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x660d7bd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        3825        9729    47431912+   7  HPFS/NTFS
/dev/sda2             640        3824    25583512+   f  W95 Ext'd (LBA)
/dev/sda5             640        1917    10265503+   7  HPFS/NTFS
/dev/sda6            1918        3739    14633984   83  Linux
/dev/sda7            3740        3824      682731   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Elfy on 2010-10-03
Ok - you need to do this from a livecd.

Run the partition editor 

Right click the swap partition - turn it off

Now you'll be able to work with the extended partition.

Move the unallocated space so that the extended (sda2) can be grown, once that has finished the unallocate space will be _inside_ the extended and available for to grow whichever partition you need to.

Edit - backups can come in handy if partition editing goes awry ...

---

### Post by joehc on 2010-10-03
> **forestpiskie said:**
> Ok - you need to do this from a livecd.

Run the partition editor 

Right click the swap partition - turn it off

Now you'll be able to work with the extended partition.

Move the unallocated space so that the extended (sda2) can be grown, once that has finished the unallocate space will be _inside_ the extended and available for to grow whichever partition you need to.

...and just turn on the swap again? If this works, I'm more than grateful! 
Both, thanks for the answers.

---

### Post by coffee412 on 2010-10-03
> **forestpiskie said:**
> Ok - you need to do this from a livecd.

Run the partition editor 

Right click the swap partition - turn it off

Now you'll be able to work with the extended partition.

Move the unallocated space so that the extended (sda2) can be grown, once that has finished the unallocate space will be _inside_ the extended and available for to grow whichever partition you need to.

Hey, Just wanted to thank you also. I will add that to my knowledge base. Normally I dont ever run into this problem even on a dual boot system with windows. But then again I have large hard drives so it doesnt really rear its ugly head.

Thanx again,

---

### Post by ibuclaw on 2010-10-03
> **joehc said:**
> Thanks for the quick answer. But i'm not sure I understand, but I'll reinstall when 10.10 is out, but how do I determine which partition should be first when I reinstall...can I do this within the installation of 10.10....so it should be like this order:
partition 1 (xp+ubuntu) + swap + unallocated space + partition 2?

then I can resize partition 2 in gparted?


Firstly, boot from a LiveCD. You cannot repartition when the filesystems are in use (see the locked key symbol in your screenshot).

Secondly, you are going to have to ***move*** some filesystems first before you can ***expand*** the partition you've set aside for music and videos.

The order you'll probably have to do it in is:
[LIST=1]
[*]Expand sda2 to the left so that it fills the entire 5GB unallocated space.
[*]Move sda5 to the left as far as you can.
[*]Move sda6 to the left as far as you can.
[*]Move sda7 to the left as far as you can.
[*]Shrink sda2 from the right so that there is 5GBs of unallocated space in the centre.
[*]Expand sda1 to fill the 5GB space
[/LIST]
Bare in mind this may take several hours, and disruption in the operation could loose/corrupt data on the Windows, Ubuntu or Data partition.

Regards

---

### Post by Elfy on 2010-10-03
> **ibuclaw said:**
> Firstly, boot from a LiveCD. You cannot repartition when the filesystems are in use (see the locked key symbol in your screenshot).

Secondly, you are going to have to ***move*** some filesystems first before you can ***expand*** the partition you've set aside for music and videos.

The order you'll probably have to do it in is:
[LIST=1]
[*]Expand sda2 to the left so that it fills the entire 5GB unallocated space.
[*]Move sda5 to the left as far as you can.
[*]Move sda6 to the left as far as you can.
[*]Move sda7 to the left as far as you can.
[*]Shrink sda2 from the right so that there is 5GBs of unallocated space in the centre.
[*]Expand sda1 to fill the 5GB space
[/LIST]
Bare in mind this may take several hours, and disruption in the operation could loose/corrupt data on the Windows, Ubuntu or Data partition.

Regards

This 

I didn't see the image link when I first looked.

You will need to turn off the swap though regardless.

Given all the work you're going to do the other simple and quick option is to just make a partition out of the 5Gb unallocated space ;)

---

### Post by joehc on 2010-10-03
> **ibuclaw said:**
> Firstly, boot from a LiveCD. You cannot repartition when the filesystems are in use (see the locked key symbol in your screenshot).

Secondly, you are going to have to ***move*** some filesystems first before you can ***expand*** the partition you've set aside for music and videos.

The order you'll probably have to do it in is:
[LIST=1]
[*]Expand sda2 to the left so that it fills the entire 5GB unallocated space.
[*]Move sda5 to the left as far as you can.
[*]Move sda6 to the left as far as you can.
[*]Move sda7 to the left as far as you can.
[*]Shrink sda2 from the right so that there is 5GBs of unallocated space in the centre.
[*]Expand sda1 to fill the 5GB space
[/LIST]
Bare in mind this may take several hours, and disruption in the operation could loose/corrupt data on the Windows, Ubuntu or Data partition.

Regards

Thanks for the answer - I see now that it takes a lot work, and I think I'm just going to let it be. Unless I can add the allocated space to my ubuntu partition without "hard work" My ubuntu partition is sda6. Can I add unallocated space to sda6 from a live cd without moving the others patitions?

---

### Post by Elfy on 2010-10-03
> Can I add unallocated space to sda6 from a live cd without moving the others patitions?No - it needs to be next to it so it can be added.

---

### Post by john newbuntu on 2010-10-03
Needless to say, after the exercise in post #8, adjust the UUIDs in /etc/fstab and re-install grub if you are grub-booting. Or use grub rescue mode commands.  Slightly lesser pain in adding that space to Ubuntu partition.  Moving is inevitable unless you just need that 666MB of swap :)

All this for 5GB of NTFS !! I agree with forestpiskie just stick an NTFS partition in the unallocated space.  Move 5GB of hopeful junk/least used files from sda1 and/or sda5 and move on with life.  About time for a new disk although it is your call.

---

### Post by joehc on 2010-10-03
> **forestpiskie said:**
> No - it needs to be next to it so it can be added.

Okay so through live cd I expand sda2 to the left so that it fills the entire 5GB unallocated space. 
Then I move sda5 to the left as far as I can. 
Then I shrink sda2 from the right so that there is 5GBs of unallocated space in the centre. 
Then I expand sda6 to fill the 5gb space.
Right?

In this way I won't be in contact with sda1 so I definitely can't lose in of my data on sda1? 

Really appreciate you for guiding me.


> **john newbuntu said:**
> Needless to say, after the exercise in post #8, adjust the UUIDs in /etc/fstab and re-install grub if you are grub-booting. Or use grub rescue mode commands.  Slightly lesser pain in adding that space to Ubuntu partition.  Moving is inevitable unless you just need that 666MB of swap :)

All this for 5GB of NTFS !! I agree with forestpiskie just stick an NTFS partition in the unallocated space.  Move 5GB of hopeful junk/least used files from sda1 and/or sda5 and move on with life.  About time for a new disk although it is your call.
I know - maybe I should just throw some junk on it, but I like to learn something about it - I am curious :)

---

### Post by Elfy on 2010-10-03
> **joehc said:**
> I know - maybe I should just throw some junk on it, but I like to learn something about it - I am curious :)

I can understand that - but partition editing isn't one of the things I would choose to do unless absolutely necessary :) 

I, at one point, had 2 or 3 odd logical partitions in between other ones - I let them be ...

---

### Post by joehc on 2010-10-03
> **forestpiskie said:**
> I can understand that - but partition editing isn't one of the things I would choose to do unless absolutely necessary :) 

I, at one point, had 2 or 3 odd logical partitions in between other ones - I let them be ...
Okay - i'll start to save up some money for a new laptop with a bigger HD. Meanwhile I'll put my music on the allocated space. 

Everyone thanks! :)

---

### Post by srs5694 on 2010-10-03
> **joehc said:**
> Can I add unallocated space to sda6 from a live cd without moving the others patitions?

No, but you may be able to do something almost as good: Create a new partition in that space and use it for something. For instance, you could use it as /var or /tmp space, or use it as swap space (deleting /dev/sda7 and absorbing its space into /dev/sda6). If you want it to be accessible from Windows, it'll show up as another drive letter in Windows (E: or F: or whatnot). If you use it in place of an existing Linux directory, you'll have to move data from the existing directory to the new space, edit /etc/fstab, and restart. There are several online guides for how to do this sort of thing (try a Web search on "linux moving directories to partitions" or some such), so consult one or more; if you get it wrong, the system might not boot or you might end up with space being consumed unnecessarily. If you want it to be accessible from Windows, you'll probably not use it in place of an existing Linux directory, which will simplify things; you'll just have to decide where to mount it as a new directory, or let the GNOME auto-mounter put it in a subdirectory of /media.

The biggest drawback to this configuration, aside from the risks of setting it up if you want to use it to store something that's currently in Linux, is that you might run out of space on the new partition if you try to put too much in it. For instance, right now your /usr directory might hold 4GB of data, so you might think it would be a good one to move; however, if you do this and then add a few big packages, you might suddenly need 6GB in /usr, and the new partition might then be too small. The /var and /tmp directories often hold large temporary files, so their needs can change suddenly. If it's to be used mainly from Windows, it'll mainly just be a bit awkward, since you'll need to figure out what to put on C: (or other partitions you've already got) and what to put on the new ones.

Overall, I'd say it might not be worth the hassle to try this; from your screen shot, it appears you've got plenty of free space on all your existing partitions, so you're not really in dire need of that space right away, unless you're planning to add files or OSes that will consume much of that space in the near future. If, some months down the road, you do need the space, you'll be in a better position at that time to decide how to reconfigure your partitions. I mention the possibility at all simply in case you do plan to add files in the near future, or in case somebody else is in a similar situation but has more immediate use for the space.

---

