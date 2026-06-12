---
title: "About to set up dual-boot on HP Mini"
date: 2011-07-02
forum: General Help
---

### Post by dlrocket89 on 2011-07-02
Hi everyone,

I bought my wife an HP Mini ([http://www.bestbuy.com/site/HP+-+Mini+Netbook+/+Intel%26%23174%3B+Atom%26%23153%3B+Processor+/+10.1%22+Display+/+1GB+Memory+-+Raspberry/1783123.p?id=1218291029696&skuId=1783123](http://www.bestbuy.com/site/HP+-+Mini+Netbook+/+Intel%26%23174%3B+Atom%26%23153%3B+Processor+/+10.1%22+Display+/+1GB+Memory+-+Raspberry/1783123.p?id=1218291029696&skuId=1783123)) and want to get Ubuntu Netbook running on it.  It comes with Windows 7 Starter, which we want to retain because Netflix won't run with Linux (gives you some BS error about "your browser is compatible, but your OS isn't").  So, I'd like to dual boot.

My desktop right now runs Kubuntu, and then I can boot in XP using VirtualBox OSE.  Owing to the fact that the netbook is down on power relative to my desktop, doesn't seem like a good idea on the netbook, hence dual boot. 

I've seen a lot of "help, I just screwed this up!" threads, and since HP wasn't kind enough to send along a disc with Windows 7 on it, I need to get this right the first time.  So, I'm going to post what I'm planning to do, someone please let me know if I'm going to mess this up.  I've compiled the below looking through a bunch of previous threads. 

1) Defrag Windows drive
2) Use Windows 7 software to shrink the Windows partition
2b) Do NOT create a new partition using Windows software, just keep it unallocated
3) Boot off of USB key with Ubuntu in it, select unallocated space for install

Questions:

1) When I boot the computer up, I should get a GRUB screen asking which OS I want to boot into, correct?  
2) I'm downloading 11.04 right now...anything to watch out for?
3) I couldn't find an install file for Ubuntu Netbook, do I make that selection during the install?

Thanks!

---

### Post by mikejonesey on 2011-07-02
1. correct
2. select "ubuntu classic" as the desktop when you are at the login screen you may prefer over unity (the new look...)
3. the only difference between netbook editions and desktop editions was the ui (unity was the netbook style but is now shipped with all versions, meaning there is no netbook edition now...). Just install the desktop edition

---

### Post by dlrocket89 on 2011-07-03
So, I did what I was going to do.  When I go to install Ubuntu, it asks you to select the partition.  At that point in time, my "unallocated space" comes up as "unavailable".  
 
Any thoughts?

---

### Post by dlrocket89 on 2011-07-03
Figured out the problem.  I booted into Ubuntu (it's stupid how much better the computer runs on Ubuntu compared to Win7, even running off of the thumb drive like it is) and ran GParted.  I tried to create a new partition with the unallocated space.  It says something to the effect of "You can only have 4 primary partitions per harddrive".

I have 4, thanks to the kind people at HP:

sda1) "System" - 200MB NTFS - flagged "Boot"
sda2) <unlabeled> - 110GB NTFS - no flag, but this is the shrunk down Win7 partition
sda3) "Recovery" - 18GB NTFS
sda4) "HP Tools" - 100 MB FAT32 - labeled LBA

The exact message that comes up:

If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition first.

I know when you run Ubuntu, you have to have a swap drive too.  Can I wipe one of the partitions above, create a new primary partition, and then have the swap partition be an extended partition within that primary partition?

If I do this, which partition am I best off deleting?  sda4 seems to be the logical answer.  It contains things like BIOS updates and system diagnostics (ie, things I can get somewhere else).  

Thoughts?

---

### Post by Gyokuro on 2011-07-03
Hi

I'm an owner of a HP mini too - at first you should make the recovery dvd's for the Windows stuff in case you want go back to this OS. Then you can delete sda4 and sda3 where you can later use this free space for Ubuntu **but please note - you want be able to do a recovery via HP's function keys at boot up (in case you have problems with windows) as you have deleted the recovery partition!**! For more HD space you can shrink the remaining Windows partition but that depends what you want to do with your Ubuntu installation. Ubuntu 11.04 works fine on my HP Mini but I have replaced the HD with a bigger one and only with Ubuntu on it :)

---

### Post by dlrocket89 on 2011-07-03
K, thanks.  I think I'm going to wipe the recovery partition and say screw it.  If something bad happens, I'll just wipe everything and then install XP and Ubuntu side by side.

---

### Post by Bill Zimmerly on 2011-11-16
> **dlrocket89 said:**
> K, thanks.  I think I'm going to wipe the recovery partition and say screw it.  If something bad happens, I'll just wipe everything and then install XP and Ubuntu side by side.

Hi Dlrocket89!

I just purchased a HP Mini Glossy Black 110-3530NR, and am curious how this thread worked out for you. Do you have any words of wisdom and experience to pass on to me? (Thanks!)

Also, what Win7 program did you use to shrink the Win7 partition down?

One thing that does concern me is that I've seen strange things happen on other Ubuntu 11.04 and 11.10 machines when running Ubuntu Classic. Things like switching to another workspace and seeing windows on the previous workspace messing up the content of windows on the next one. (?)

I've seen this problem on several different machine, so I'm very "gun shy" about installing anything beyond 10.10 on my new Mini.

Any help/advice is appreciated!  :D

Sincerely,
- Bill

---

### Post by Mark Phelps on 2011-11-17
> **Bill Zimmerly said:**
> Also, what Win7 program did you use to shrink the Win7 partition down?

If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by Bill Zimmerly on 2011-11-17
Thanks Mark! ;)

> **Mark Phelps said:**
> If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

