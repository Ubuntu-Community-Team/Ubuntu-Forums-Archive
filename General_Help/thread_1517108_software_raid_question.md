---
title: "software raid question"
date: 2010-06-24
forum: General Help
---

### Post by blur xc on 2010-06-24
I've been reading a lot that Ubuntu's software raid in many ways can be better than a fake raid- and seeing how a true hardware raid is way out of my price range, I think I want to try it out...

I was wondering, if you are trying to make a raid array, do you need to start with blank disks, or can you start wit a drive that already has data on it?  Does the file system type matter?

I would create this for data storage, in particular my photos folders, and I don't plan on putting any boot partitions on the raid array.  So, if some time in the future say I wipe my os and do clean install, how hard is it to access the existing raid array from the new os?

Thanks,
BM

---

### Post by john newbuntu on 2010-06-25
You do not necessarily have to start with blank disks but you need a partition that can host raid data(linux raid auto).  If the partition already has data on it, you will have to move it out of the way.  Once the raid array is completely set up, you can copy it back in.  You would typically format the array after it is created.

When you do a clean install of Ubuntu (obviously on non-raid partitions), assuming that all your raid partitions are mounted, you will have to install the raid software, mdadm and run a scan to auto detect the existing arrays.  This should create the mdadm.conf with the old array details.  (In some cases though you will have to append this information to mdadm.conf).  You would then set up any fstab entries and reactivate the array.

---

### Post by Drenriza on 2010-06-25
I must honestly say, if you dont use hardware raid, i dont see a point.

And doing it over your chipset is = asking for trouble.
Im saying a pci / pci-e raid controller. You can get these for 57$

---

### Post by blur xc on 2010-06-25
> **Drenriza said:**
> I must honestly say, if you dont use hardware raid, i dont see a point.

And doing it over your chipset is = asking for trouble.
Im saying a pci / pci-e raid controller. You can get these for 57$

I was under the impression that those inexpesive "hardware" raid cards, of the on mobo raid setups (which my motherboard supports) are really fake raids in disguise, that have all the disadvantages of a real rad and a software raid, with no advantages.

In the end, no matter which route taken, don't you get the same thing, which in my case is a decreased risk in loss of data?  I'm not looking for maximum performance, just a relaibe way to store hundreds of gigs, and eventually tb's of data.

I take lots of pictures- in the past 6 years I think more than 60,000.  My storage needs accelerate over time, as ever new latest and greatest camera increases image files sizes considerably.  I was thinking a raid 5 because as I understand you can just grow the array as you need more space.

Thanks,
BM

---

### Post by john newbuntu on 2010-06-25
I guess the concern with software raid is that the cpu does all the work that a raid controller otherwise would have done.  Same with firmware based raid or fakeraid.  Certainly for a production type high availability system, a high-end hardware raid is the way to go.  But for other situations, especially when cost is the criteria, software raid should be ok with with modern processors.
The one advantage with fakeraid is that it takes care of multiboot systems while software raid does not.  Also, with software raid, you do have portability in that you could easily move over your array disks to a newer system (having same OS) and get it up and running soon.
Whichever raid you choose to use, always back your data up.  There is absolutely no substitute for this.

---

### Post by Drenriza on 2010-06-26
> **blur xc said:**
> I was under the impression that those inexpesive "hardware" raid cards, of the on mobo raid setups (which my motherboard supports) are really fake raids in disguise, that have all the disadvantages of a real rad and a software raid, with no advantages.

In the end, no matter which route taken, don't you get the same thing, which in my case is a decreased risk in loss of data?  I'm not looking for maximum performance, just a relaibe way to store hundreds of gigs, and eventually tb's of data.

I take lots of pictures- in the past 6 years I think more than 60,000.  My storage needs accelerate over time, as ever new latest and greatest camera increases image files sizes considerably.  I was thinking a raid 5 because as I understand you can just grow the array as you need more space.

Thanks,
BM

The risk of having raid on mobo, is. What do you think will happen if your mobo someday dosent work, or you need to move your raid to another system? (a new mobo).

When all your raid setup is on your old mobo, this is what happends. (you cant take the raid setup with you, when it is konfigured in the mobo)

changing mobo, for any reason. = your raid setup is on your old mobo. 1st time you boot your system, the new raid will "think" the disks are blank, and will start to over-write existing data. = data corruption, and eventually blank disks or disks that cant be rescued. 

This is why you use a PCI controller of high quality, that you can take to any new mobo. Without losing data.

That the CPU does all the work in a raid system, arnt a biggie. The problem is when you need to change mobo, for any reason.
Or your chip-set dies. your bios dies. bios battery dies = prolems.

---

