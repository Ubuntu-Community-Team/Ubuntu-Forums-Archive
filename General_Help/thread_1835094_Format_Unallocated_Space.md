---
title: "Format Unallocated Space?"
date: 2011-08-28
forum: General Help
---

### Post by Thedark7 on 2011-08-28
I used Easeus Partition Master Home Edition, and I now have 32GB unallocated space on my hard drive. I want to transfer my wubi setup to that space using [this method]("http://ubuntuforums.org/showthread.php?t=1519354").

Will Ubuntu recognize the unallocated space as /dev/sda#? How would I figure out what the name (i.e. /dev/sda5) of the unallocated space/partition is? 

Also, will I need to create another partition for swap space?

THANKS!

---

### Post by Thedark7 on 2011-08-28
Okay, I'm tried to format the unallocated space and I get [this]("http://img11.imageshack.us/img11/4999/parion.png") What does it mean?

---

### Post by bcbc on 2011-08-28
You don't want dynamic disks. You cannot install Ubuntu on these and I understand it's not a reversible thing (microsoft recommends reinstalling to convert back from dynamic disks).

The prob is that you can only have a maximum of 4 primary partitions with the MBR partition table. And by creating a 5th in that free space, windows can only do it by switching to dynamic drives.

The only way you can do it without dynamic disks is to delete one of your existing primary partitions, create an extended partition in the space (a type of primary partition) and then within that extended partition you can create any number of logical partitions.

---

### Post by Thedark7 on 2011-08-28
> **bcbc said:**
> You don't want dynamic disks. You cannot install Ubuntu on these and I understand it's not a reversible thing (microsoft recommends reinstalling to convert back from dynamic disks).

The prob is that you can only have a maximum of 4 primary partitions with the MBR partition table. And by creating a 5th in that free space, windows can only do it by switching to dynamic drives.

The only way you can do it without dynamic disks is to delete one of your existing primary partitions, create an extended partition in the space (a type of primary partition) and then within that extended partition you can create any number of logical partitions.

Thanks for the reply.

So, basically, I can't install Ubuntu without deleting one of HP's partitions?

---

### Post by bcbc on 2011-08-28
> **Thedark7 said:**
> Thanks for the reply.

So, basically, I can't install Ubuntu without deleting one of HP's partitions?

No, for some reason HP like to ship computers with all four primary partitions used. So unfortunately you have to delete one if you want to dual boot on the same drive.

---

### Post by bcbc on 2011-08-28
Here's a link to an HP site: [http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/want-dualboot-4-primary-partitions-taken-what-to-do/td-p/313304](http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/want-dualboot-4-primary-partitions-taken-what-to-do/td-p/313304)

Interestingly it seems that the recovery partition depends on a special OEM bootloader (for the F11 key to work). I know my old dell had a special bootloader also - so the recovery wouldn't work without it (installing ubuntu replaces the bootloader with grub - although it's possible to use easyBCD instead).

So bear that in mind when deciding which partition to delete. And consider creating bootable recovery dvd's or something similar so you have some recovery options later.

Edit: I read the link within the link - it's not the bootloader (or not just). Even modifying the partitions will stop the built in recovery from working. So you need bootable DVDs or USB to do a factory restore.

---

### Post by thi3000 on 2011-08-29
[COLOR=DarkOrange][SIZE=4]Hmm, you have a rather odd set up there, but it's fine, it's your hard drive, anyway so[COLOR=SandyBrown] [/COLOR][/SIZE][/COLOR][SIZE=4][COLOR=SandyBrown]can you go back and repartition them[/COLOR][/SIZE] [SIZE=4][COLOR=DarkOrange]so that you have one primary for boot/system and a secondary for your recovery? That should free up the rest of your hard disk for ubuntu[/COLOR][/SIZE].

---

### Post by Thedark7 on 2011-08-29
I did quite a bit of googling, and found that I need the System partition to boot. The recovery partition can be accessed through grub, even though the F11 key might not work. I'll probably delete the HP_Tools partition (the diagnostic tools), because HP has a version of it that runs off a flash drive available for download on its website.

---

### Post by bcbc on 2011-08-29
> **Thedark7 said:**
> I did quite a bit of googling, and found that I need the System partition to boot. The recovery partition can be accessed through grub, even though the F11 key might not work. I'll probably delete the HP_Tools partition (the diagnostic tools), because HP has a version of it that runs off a flash drive available for download on its website.

That seems to be the way most people do it, but I did read that the recovery tool [also won't work if you've modified the partitions]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02085554&tmp_task=solveCategory&lc=en&dlc=en&cc=us&softwareitem=ob-80840-1&os=4063&product=4050002&sw_lang="). I recommend creating separate backup media, rather than relying on the recovery partition (even if both end up working, better to be safe than sorry).

---

### Post by Slim Odds on 2011-08-29
> **bcbc said:**
> That seems to be the way most people do it, but I did read that the recovery tool [also won't work if you've modified the partitions]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02085554&tmp_task=solveCategory&lc=en&dlc=en&cc=us&softwareitem=ob-80840-1&os=4063&product=4050002&sw_lang="). I recommend creating separate backup media, rather than relying on the recovery partition (even if both end up working, better to be safe than sorry).

+10

The FIRST thing that you should always do with a machine like this is create the DVD restore disks.

If your hard drive dies or you make a big mistake, this is your ONLY way to recover.

---

### Post by Thedark7 on 2011-08-29
> **bcbc said:**
> That seems to be the way most people do it, but I did read that the recovery tool [also won't work if you've modified the partitions]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02085554&tmp_task=solveCategory&lc=en&dlc=en&cc=us&softwareitem=ob-80840-1&os=4063&product=4050002&sw_lang="). I recommend creating separate backup media, rather than relying on the recovery partition (even if both end up working, better to be safe than sorry).

Hi,
I am going to create the recovery disks before I mess with anything, but only the F11 key will stop working, GRUB /should/ still detect the recovery partition. I'm not taking any chances though.

---

### Post by Thedark7 on 2011-09-08
Hi,

I removed one of the HP partitions and created an Ubuntu partition, am I good to use your tool to transfer wubi to that partition?

Also, the recovery manager seems to be working fine even though I've modified partitions. :D

---

### Post by bcbc on 2011-09-08
> **Thedark7 said:**
> Hi,

I removed one of the HP partitions and created an Ubuntu partition, am I good to use your tool to transfer wubi to that partition?

Also, the recovery manager seems to be working fine even though I've modified partitions. :D

Great! Good to know that the recovery still works.

So... regarding migration - I recommend creating an extended partition and then creating two logical partitions (as opposed to a single new primary partition). One for the migration and one for swap. Create the logical partitions using GParted, so you get the correct partition types. Then you can migrate to it and setup swap to allow hibernation (the swap partition must be > size of RAM for hibernation to work e.g. RAM + 1GB)

---

### Post by Thedark7 on 2011-09-08
> **bcbc said:**
> Great! Good to know that the recovery still works.

So... regarding migration - I recommend creating an extended partition and then creating two logical partitions (as opposed to a single new primary partition). One for the migration and one for swap. Create the logical partitions using GParted, so you get the correct partition types. Then you can migrate to it and setup swap to allow hibernation (the swap partition must be > size of RAM for hibernation to work e.g. RAM + 1GB)

Actually, do I need a swap partition? I don't really want one...

---

### Post by bcbc on 2011-09-08
> **Thedark7 said:**
> Actually, do I need a swap partition? I don't really want one...

No you don't need one - it's really only required to hibernate. If you have enough ram you should be okay, and you can use a swap file as well if you need it.

---

### Post by Thedark7 on 2011-09-09
> **bcbc said:**
> No you don't need one - it's really only required to hibernate. If you have enough ram you should be okay, and you can use a swap file as well if you need it.

I was going to make one anyway, but it looks like you need gparted to do so. Also, when I tried running the script, it said my new partition wasn't empty.

I want to use gparted and just take care of everything, but Ubuntu is REEAALLLY slow running off of my DVD. Can I use gparted in wubi?

---

### Post by bcbc on 2011-09-09
> **Thedark7 said:**
> I was going to make one anyway, but it looks like you need gparted to do so. Also, when I tried running the script, it said my new partition wasn't empty.

I want to use gparted and just take care of everything, but Ubuntu is REEAALLLY slow running off of my DVD. Can I use gparted in wubi?

Yes... you need to install it first (it comes on the live CD by default, but not in a normal install). So:
```
sudo apt-get install gparted
``` or if you prefer, you can do it in software centre.

(The only limitation is you cannot resize a mounted partition which is why most people use gparted from a live CD)

If you just created the partition you are migrating to it shouldn't show as not being empty. Please let me know which one it is and post the output of (lower case -L):
```
sudo fdisk -l
```
(I just want to see the type). 

If you can mount the target partition and post (replace *mountpoint* with whatever your mountpoint is):
```
df -h
ls -al /media/*mountpoint*
```

---

### Post by Thedark7 on 2011-09-10
> **bcbc said:**
> Yes... you need to install it first (it comes on the live CD by default, but not in a normal install). So:
```
sudo apt-get install gparted
``` or if you prefer, you can do it in software centre.

(The only limitation is you cannot resize a mounted partition which is why most people use gparted from a live CD)

If you just created the partition you are migrating to it shouldn't show as not being empty.

It was showing as not empty in Windows too, so I'll try gparted and get back to you.

---

