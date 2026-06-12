---
title: "XP/Ubuntu from previous Vista installation"
date: 2009-07-31
forum: General Help
---

### Post by dino1515 on 2009-07-31
Hi everyone I am new to the world of Linux and I love Ubuntu. I installed it only a few days ago and it has already done more for me than Windows ever did.

My problem is this, I have a laptop with Vista already installed and therefore I installed a dual boot of Ubuntu with Vista. I would have Ubuntu running all alone except that I currently need Windows for my iPhone and also some games.

I want to completely get rid of Vista and simply have a dual boot of XP and Ubuntu because Vista is slow as Sh** and I really only want a little bit of space taken up by XP to hold my music and sync my iPhone, Vista simply takes too much space and like I said is very slow even for performing simple tasks such as syncing an iPhone.

What is the best way to go about doing this? Also I am knew so if it can be made simple that would be great! 

P.S. - I do not have an XP disk, would it be possible to download or obtain a burnt copy and use that or will this not work?

---

### Post by bilol on 2009-07-31
Hi,
(1)You have to have(purchase) a XP disc to install XP.
(2) Take all important data-back ups from the Vista and Ubuntu partitions.
(3) If you have several important packages installed in Ubuntu ,then create aptoncds. 
(4) install XP in the Vista partition by removing vista(formatting the drive) completely.
(5) install ubuntu as you did it before.
(6) reinstall the packages from aptoncds.
(7) restore the data back ups in proper place.
Thats it......

---

### Post by dino1515 on 2009-07-31
Thankyou for that. I currently do not have a windows xp disc so i will need to get one. However if I do it this way wont XP simply take over the Vista partition then leaving the partition sizes the same.

Is there a way that with my current setup I can make my Ubuntu partition considerably bigger than my Vista one so as to only have Vista for the purpose of still having windows. I have been reading tuturials on how to change partition sizes using gparted or something, however i do not understand it at all!

In short is there a simple way of making my Vista partition as small as possible and letting Ubuntu take over the free space so that Ubuntu is the core of my PC?

Thankyou again for the help.

---

### Post by dino1515 on 2009-07-31
by the way i have included a picture of my partitions. I have no idea what they mean. for instance i understand that ntfs are my Vista partitions and ext3 is linux but what is linux swap, unallocated and why does vista seem to have a second partition.

I want the majority of this to be for my linux os and just a small amount for Vista!

---

### Post by merlinus on 2009-07-31
The second vista partition may well be a recovery one installed by the OEM.  If you want to shrink vista's partition, then delete temp files and defrag several times, and use its disk management tool.  Then you can add the space to linux.

Obviously, back up important data first.

When -- and if-- you install xp, you can delete the recovery partition to free up even more space.

However, given your current partitioning scheme, I would recommend that you format the freed-up space as ext3 and use it for data such as docs, music, and photos.  You might even decide to use it as /home, and there are tutorials for how to do this.

If you decide to go that route, then post back for additional instructions.

---

### Post by dino1515 on 2009-08-01
thankyou for your time, as i said im knew so what u said practically went way over my head lol, i am thinking that i will just keep vista however i want to free up as much space as possible for linux. The only thing that i will keep Vista for is to sync my iphone and for maybe a game or two? So how would I go about doing that, getting as much hard drive space across to Linux without killing my computer.

the simpler the instructions the better, thankyou again for your time.

---

