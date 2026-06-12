---
title: "partition questions??"
date: 2009-09-19
forum: General Help
---

### Post by loosie on 2009-09-19
Hi, 
After initially installing Ubuntu side by side with Windows, then finding because it had so little room next to Windows, so I ditched windows.... found I still couldn't resize Ubuntu's partition, so reinstalled it in the large Windows partition.... then deleted the original, but found I was left with empty partitions and 'swaps' everywhere.... Now I have it down to one large partition with Ubuntu, one 2gb swap section in a separate 'Extended' partition, and about a quarter of the hard drive being an empty section.

So can someone tell me whether I need to change anything - eg have a 'swap' section in with the Ubuntu, rather than in a sep partition, and how I can use the spare space??

---

### Post by oboedad55 on 2009-09-19
> **loosie said:**
> Hi, 
After initially installing Ubuntu side by side with Windows, then finding because it had so little room next to Windows, so I ditched windows.... found I still couldn't resize Ubuntu's partition, so reinstalled it in the large Windows partition.... then deleted the original, but found I was left with empty partitions and 'swaps' everywhere.... Now I have it down to one large partition with Ubuntu, one 2gb swap section in a separate 'Extended' partition, and about a quarter of the hard drive being an empty section.

So can someone tell me whether I need to change anything - eg have a 'swap' section in with the Ubuntu, rather than in a sep partition, and how I can use the spare space??

You don't need any swap other than the swap partition you have. As for the extra space why not create another partition and use it for data or storage.

---

### Post by loosie on 2009-09-19
Thanks. But is there a point of having a separate partition for storage & how would I use it? Would it not be better if there was more space in the Ubuntu partition? If I can get this darstedly remote desktop worked out, I also have another machine, so not really lacking storage.

Wondered about moving the swap file into the Ubuntu partition, rather than adding another one. Originally the swap section was in an 'extended' partition with the Ubuntu, but with chopping & changing, it's now in the extended part all alone & sep to Ubuntu.

---

### Post by oboedad55 on 2009-09-19
> **loosie said:**
> Thanks. But is there a point of having a separate partition for storage & how would I use it? Would it not be better if there was more space in the Ubuntu partition? If I can get this darstedly remote desktop worked out, I also have another machine, so not really lacking storage.

Wondered about moving the swap file into the Ubuntu partition, rather than adding another one. Originally the swap section was in an 'extended' partition with the Ubuntu, but with chopping & changing, it's now in the extended part all alone & sep to Ubuntu.

There are a few things you can do. You can resize your partitions to take up the extra space.You can use the extra space to create a data partition, you know for videos, music, whatever you're into. Linux doesn't need a swap file like windows. The swap partition you already have will be used by Ubuntu. One caveat, always back up anything you want to save before re-partitioning. Usually it goes fine, but it can break things so I'm told. I hosed a windows install once because I didn't defrag the windows before I partitioned, so things can happen.

---

### Post by earthpigg on 2009-09-19
i find resizing partitions annoying.

easiest (but a bit drastic) thing to do at this point:

**back up** any/all data on that hard drive you want to retain, because we are about to wipe everything and start from scratch.

**boot** a LiveCD.

start **gparted**.

**delete every single partition**.

**apply**.

**create a new 2gb partition as swap**. (this is somewhat optional. tell us how much RAM you have and what you plan to use the computer for and we can recommend a good size. given how large hard drives are becoming, 2gb is becoming a very common size.)

**create a new 15bg partition as ext4**. (if you are concerned about hard drive space, you can probably go as low as about 7gb with this and be ok. my most bloated system ever had 9gb of data in what we will be using this partition for. my current system has 3.3gb used.)

create a new partition with **rest of space as ext4**.

**apply**.

double click '**install**' on the desktop.

when the option presents itself, select '**manually partition**'.

set your **2gb partition** to be used as **swap**.

set the **15gb partition** to have the **mountpoint of /** and give it the **'boot' flag**.

set the **last partition** to have the **mountpoint of /home**.

click **next** and continue the install.

you, sir, are ready to rock with a respectable partition scheme.



tell us the following and we can advise you on selecting the size of the / and swap partition to better suit your needs:
-RAM.
-size of hard drive.
-how much music/movies/pictures/etc you plan to put on this hard drive.
-what you plan to be using this computer for.

if you have a ridiculous amount of hard drive space and over 4gb of RAM, then it almost certainly will not make a bit of difference within reason and you can go ahead and use the values i suggested above.

---

### Post by imhotep59 on 2009-09-19
Swap must be a partition with Ubuntu (and not a file as in windows). So don't change it. If you want to increase your partition for Ubuntu using the empty space, the best way is to boot with the liveCD et to launch gparted. Then, you will be able to change the size of your partition. It is not possible to do that in your session because a partition has to be unmounted to be resized or moved...

---

### Post by loosie on 2009-09-19
Oh, hadn't heard of swap partitions until Ubuntu. I thought they were necessary for it? So I can delete that too, for more unallocated? So would there be any point in adding the unallocated to the Ubuntu partition? What's the point/advantage of keeping data in a sep partition?

---

### Post by earthpigg on 2009-09-19
> **loosie said:**
> What's the point/advantage of keeping data in a sep partition?

Windows has a swap **file**.

Linux (optionally) has a swap **partition**.

when/if you use up all your RAM, Linux will start to use the swap partition.

if you do not have a swap partition and use up all your RAM, **your computer will lock up**.

having a swap partition that never gets used will **not slow your computer down any**.

i do not have a swap partition on this computer, but i have 6gb of RAM and a small 60gb hard disk so this computer is a bit unconventional...

also, i edited my post above a bit. may want to re-read in case you where reading before i was done editing.

---

### Post by Elfy on 2009-09-19
Keep the swap as it is if I was you.

I have all my data on seperate partitions - a reinstall then won't lead to me losing data stored on the same partition as the install.

---

### Post by earthpigg on 2009-09-19
also, there is no point that i can fathom in having more than one swap partition on the same physical drive.

if you have more than one, go ahead and delete the extra ones.

check 'free -m' to ensure ubuntu is still using the one swap partition you have left as swap.

if i remember correctly, the old conventional wisdom is to put swap at the beginning of the drive. on the left in the gparted window.

buuuuuuuut im pretty sure modern hard drives lie about their geometry anyways, so i dont think that old rule of thumb really applies any more.

---

### Post by imhotep59 on 2009-09-19
> **earthpigg said:**
> 

buuuuuuuut im pretty sure modern hard drives lie about their geometry anyways, so i dont think that old rule of thumb really applies any more.

Exact, my swap is is the middle of my extended partition (between /home in ext4 and DATA in NTFS) and it works fine.

---

### Post by hal10000 on 2009-09-19
@earthpigg:

> also, there is no point that i can fathom in having more than one swap partition on the same physical drive.

If you have a big webserver or big databases or something similar running, then several swap partitions may increase your access time.

---

