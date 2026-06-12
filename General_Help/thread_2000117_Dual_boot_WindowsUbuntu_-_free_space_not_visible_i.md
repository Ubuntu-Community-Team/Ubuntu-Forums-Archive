---
title: "Dual boot Windows/Ubuntu - free space not visible in Windows"
date: 2012-06-09
forum: General Help
---

### Post by Yogesh_P on 2012-06-09
Hi All

I had dual boot Windows7/Ubuntu10.04 combination on my dell laptop. My hard disk drive is 500GB of which 90GB was allocated to Ubuntu10.04. I recently formatted my Ubuntu to Ubuntu 11.04 and changed partition size from 90GB to 40GB manually in order to append that extra free space into Windows 7. Now I do not see 50GB free space either in Windows 7 disk management tool or in Ubuntu 11.04. Can someone please let me know how to recover that space, I would prefer to use that space in Windows7.

Regards

---

### Post by Basher101 on 2012-06-09
> **Yogesh_P said:**
> Hi All

I had dual boot Windows7/Ubuntu10.04 combination on my dell laptop. My hard disk drive is 500GB of which 90GB was allocated to Ubuntu10.04. I recently formatted my Ubuntu to Ubuntu 11.04 and changed partition size from 90GB to 40GB manually in order to append that extra free space into Windows 7. Now I do not see 50GB free space either in Windows 7 disk management tool or in Ubuntu 11.04. Can someone please let me know how to recover that space, I would prefer to use that space in Windows7.

Regards

Run Gparted and make a screenshot of it, then post it here so i can get an idea of your partition table.


regards

---

### Post by echo6 on 2012-06-09
The space is there, you just need to allocate it to your filesystem.

Depending on how your disk is partitioned this is reasonable straightforward.


Gparted should allow you to see the free disk space, allow you to resize your Windows filesystem to  make use of the extra space.

---

### Post by Yogesh_P on 2012-06-09
> **Basher101 said:**
> Run Gparted and make a screenshot of it, then post it here so i can get an idea of your partition table.

regards

Here is the screenshot from gparted

[IMG]http://imageshack.us/photo/my-images/837/screenshotox.png[/IMG]

[http://imageshack.us/photo/my-images/837/screenshotox.png/](http://imageshack.us/photo/my-images/837/screenshotox.png/) 
(I don't see an image in post so I am not sure if its the problem with my browser, direct link works though)

It shows ~47GB unallocated space. When I click new I get option to convert it into a partition in different formats ext2/etc. If I make it ntfs from Ubuntu itself instead of making it ext4 can I access that partition from Ubuntu as well as Windows 7 ?

Also I already have 2 partitions in Windows but I get error when I try to create more partitions within Windows. Will creating ntfs partition in Ubuntu work with Windows as it will have 3 partitions to deal with.

Regards

---

### Post by Fuzzv on 2012-06-09
You should be able to, using gParted, create an NTFS partition from the unallocated space that's usable in both Windows and Ubuntu.

---

### Post by Jaskaran498 on 2012-06-09
Dude...
I have tried this method with windows xp. But i am new to ubuntu. I dont know it'll work with ubuntu or not. But it should work.
There are two methods i am giving to you. One should work. **Do this at your own risk. Although it should not cause any troubles and is tested by me.**
Boot into Windows 7 as Windows 7 has inbuilt disk manager that works pretty well.

The disk space you freed is still unallocated (means its there but not implemented for use).
To use it, do following-->

Open Control Panel. In search box type "Partition" without quotes. 

Click to open "Create and Format Hard Disk partitions".
In newly opened dialog box, youll see your hard disks and their memory info.

The unallocated (unused) space will be available in one of boxes below disk info with title "Unallocated" and mostly green colored background.
Right click the hard disk partition you want to expand (windows 7 installed partition in your case) and click "Expand". Enter your choices and click Expand. Wait a little.
Its done. You should now be able to use your space.


If "Expand" option is unavailable when you right click Windows 7 partition, do this-->
Right click Unallocated Disk space area (Green Colored), Select "Create New simple volume". Enter the full free disk space as memory for new partition. Click OK. Now youll see a new partition. Right Click it and Delete it!!! (Its not a useless step). Again, you'll see free disk space below (unallocated) in a green box. Right click partition with windows 7 and click "Expand". Enter amount to free disk space available and click "Expand". It should give you your space back.

Hope this helps.

---

### Post by Basher101 on 2012-06-09
> **Jaskaran498 said:**
> Dude...
I have tried this method with windows xp. But i am new to ubuntu. I dont know it'll work with ubuntu or not. But it should work.
There are two methods i am giving to you. One should work. **Do this at your own risk. Although it should not cause any troubles and is tested by me.**
Boot into Windows 7 as Windows 7 has inbuilt disk manager that works pretty well.


You kidding me? The windows disk utility killed my Ubuntu partition twice in my setup....i have my disk like this: Windows7 |Ubuntu | 900 GB storage | test partition 

Ubuntu is like on the other side of the disc, yet when i use the windows disk utitlity, the ubuntu partition became unallocated. I will never, ever use that again to partition my disk. Gparted is the way.

Just format the unallocated space with Gparted to NTFS and you can use it.


regards

---

### Post by Jaskaran498 on 2012-06-09
> **Basher101 said:**
> You kidding me? The windows disk utility killed my Ubuntu partition twice in my setup....i have my disk like this: Windows7 |Ubuntu | 900 GB storage | test partition...


Okay dude, Didnt knew it that this is what happens with dual boot windows 7 and ubuntu.
I already said that earlier, this method i tested on dual boot windows 7 and xp, not ubuntu, so i didnt knew outcomes. Ofcourese, you are more experienced and know more.
Anyways...
Thanks for the info. It will be useful for me in future.

---

### Post by Basher101 on 2012-06-09
> **Jaskaran498 said:**
> Okay dude, Didnt knew it that this is what happens with dual boot windows 7 and ubuntu.
I already said that earlier, this method i tested on dual boot windows 7 and xp, not ubuntu, so i didnt knew outcomes. Ofcourese, you are more experienced and know more.
Anyways...
Thanks for the info. It will be useful for me in future.

Maybe i should note that all partitions (except Windows) are inside an extended one..so if you set up partitions inside an extended one, DO NOT BY GOD'S MERCY use the windows disc utility, it WILL mess up your Ubuntu...otherwise, if all partitions are Primary, this does not happen. In that case the Windows disc utility is fine for use (but Gparted is still far superior)

regards


p.s. i have tons of expirience with partitioning, so if you have any questions, hit me with a PM

---

### Post by Jaskaran498 on 2012-06-09
> **Basher101 said:**
> Maybe i should note that all partitions (except Windows) are inside an extended one.... p.s. i have tons of expirience with partitioning, so if you have any questions, hit me with a PM

Thanks dude I am using gparted now. It really is superior!!! Its awesome:)

---

### Post by SaalamAndre on 2012-06-09
Hi guys, its any new exam on DTI ?

---

