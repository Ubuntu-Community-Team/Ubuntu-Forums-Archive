---
title: "Dirty Hard Drive in dual boot"
date: 2012-06-08
forum: General Help
---

### Post by FoZFoRiC on 2012-06-08
I am running a dual boot system with winxp and ubuntu 12.04 and after installing ubuntu and moving some files around using ubuntu on a secondary hard drive, when going back to winxp the os says that the secondary drive is dirty.  Nothing was lost and I am not sure if that happened due to the install or moving files around.  I have never had the system report any drives as dirty before and was wondering if this is just a product of a jealous winxp or is it just something that always happens in dual boot systems or is there something I need to change in my configurations?

---

### Post by Mark Phelps on 2012-06-09
The word "dirty" means that the Windows filesystem was modified and you exited it before it had a chance to make the proper adjustments.

It's generally a BAD idea to make changes to files inside an Windows OS partition from Ubuntu.

If you can boot into Windows, run CHKDSK on the partition.  That's likely to fix it.

If you can't boot into Windows, you will need to remove the drive and connect it to a Windows PC -- and run  CHKDSK on it there.

Unfortunately, there is no way to run CHKDSK on a Windows filesystem from a Linux distro.

---

### Post by FoZFoRiC on 2012-06-11
hmm,  "a BAD idea to make changes to files inside an Windows OS partition from Ubuntu"?  Well I certainly wouldn't poke around in the program files or WinOS directories from a different os, but what does this mean for a shared drive between the two?  I have windows on c:, ubuntu on d:, and a terabyte NTFS on t: that I have all my media and project files.  If you're not really supposed to access any win partitions from ubuntu, what is the point of dual booting or even having ubuntu read NTFS?

---

### Post by jmore9 on 2012-06-11
You can read write very good on NTFS with linux today,  You cannot read write linux with windows , without a lot of work.

You cannot do maintaince on NTFS partitions from linux.  This must be done from windows.

I only have 1 of my 4 drives left in NTFS and when i replace it i will be using ext4.  As i no longer use winxp and have no intentions of paying the large amount of money needed to replace winxp pro with win7 ult. everything will be migated to ext4 as they fail.

And on the NTFS drive thats left , it is a 1 tb'er and yes i boot into winxp use the repair chioce and run the disk checker every now and then, and defrag it also.

---

### Post by Mark Phelps on 2012-06-11
> **FoZFoRiC said:**
> hmm,  "a BAD idea to make changes to files inside an Windows OS partition from Ubuntu"?  Well I certainly wouldn't poke around in the program files or WinOS directories from a different os, but what does this mean for a shared drive between the two?  I have windows on c:, ubuntu on d:, and a terabyte NTFS on t: that I have all my media and project files.  If you're not really supposed to access any win partitions from ubuntu, what is the point of dual booting or even having ubuntu read NTFS?

Note that I said Windows "OS" partition -- that is a partition Windows needs, either to boot from, or to load the OS from.  These kinds of Windows partitions are very sensitive to changes from "outside" and can easily become corrupted when that happens.

Note that I did NOT say Windows "data" partition -- these don't boot and don't load an OS, so you should be able to share these without problems.  I do this every day without any difficulties.

The only "gotcha" with sharing Windows NTFS data partition is that you need to make sure you do NOT Hibernate Windows and THEN make changes to the data partition while Windows is hibernated.  Windows stores away the partition table when hibernating.  When it awakens, it will restore the partition table from its stored copy.  IF you made filesystem changes to that partition, they may be gone, or they may be corrupted.

---

### Post by Cheesemill on 2012-06-11
> **FoZFoRiC said:**
> hmm,  "a BAD idea to make changes to files inside an Windows OS partition from Ubuntu"?  Well I certainly wouldn't poke around in the program files or WinOS directories from a different os, but what does this mean for a shared drive between the two?  I have windows on c:, ubuntu on d:, and a terabyte NTFS on t: that I have all my media and project files.  If you're not really supposed to access any win partitions from ubuntu, what is the point of dual booting or even having ubuntu read NTFS?
It's a bad idea to make changes to the **Windows** **OS** partition, using a shared data only NTFS partition is fine.

---

