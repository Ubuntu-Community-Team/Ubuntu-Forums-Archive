---
title: "want a primary partition"
date: 2010-04-09
forum: General Help
---

### Post by rudi009 on 2010-04-09
[IMG]http://i44.tinypic.com/286wq46.png[/IMG]
this is what my partition table looks like right now.I want /dev/sda8 (17 gb) to be a primary partition to install windows 7.

can i do it??how??? any help would be appreciated..

---

### Post by dominiquec on 2010-04-09
Ouch. Looks like you're going to have a problem here.  Primary partitions are 1 through 4.  Your first primary partition 1 looks too small to resize.  And you won't be able to resize your extended partition unless you delete all your logical partitions first.

Unless someone else has a better idea...

---

### Post by howefield on 2010-04-09
I'd try deleting sda9, then resize the extended partition to leave a chunk of unallocated space at the end, then make that into a primary partition.

Remember installing windows will wipe your grub bootloader, so you will have that to sort.

To be honest, it might be simpler to copy all your data to another disk, and start again with the partitions as you want them, (including taking the opportunity to have a separate /home).

---

### Post by louieb on 2010-04-09
> **howefield said:**
> I'd try deleting sda9, then resize the extended partition to leave a chunk of unallocated space at the end, then make that into a primary partition...

+1 - That's what I was just about to say. BTW: the extended partition is sda2.

You can't do this from your Ubuntu hard drive install - you will need to boot to a live CD.

---

### Post by Ampi on 2010-04-09
I have to say I agree with Howefield. I think a complete repartitioning would be better. Then you can have a primary partition for Win7, an extended partition for Ubuntu and a seperate partition for /home reachable from both systems depending on the filesystem. 
So if you have an external harddisk that would be the best solution or enough space on DVDs. 

If not, try to be able to delete sda6 till sda8 (might be less space to save on an external harddisk instead of the entire computer), then add a swap partition and a the left space at the end for a primary partition for Win7. Because Win7 might need 50GB to actually function properly and yo don t have tha on sda9 alone.

---

### Post by Hikayu on 2010-04-09
Bump, same problem here. Except with sda5 inside an extended sda2 partition. How would I take sda5 out of sda2?

---

### Post by Mark Phelps on 2010-04-09
> **Hikayu said:**
> Bump, same problem here. Except with sda5 inside an extended sda2 partition. How would I take sda5 out of sda2?

Technically, you can't do that -- because even if you do create another primary following the extended partition, it won't be "sda5".  It will probably then be "sda3".

Also, you don't have 53GB of free space in which to copy over the contents of sda5 into another partition.

Doing what you want will involve a lot of work: copy off the contents of sda5, remove sda5, move the remainder of the partitions in the extended partition to the beginning of the extended partition, shrink the extended partition, create a new NTFS partition in the free space, copy back the contents of the former sda5.

HOWEVER, if that NTFS partition is the OS partition for an MS OS, especially if that OS is Vista or Win7 -- be prepared for it not booting anymore when you do that.

You're likely then to have to repair whichever boot loader is likely to be resident in that partition.

Also, since you moved that partition, whichever version of GRUB you're using will also have to be reconfigured to find the new OS partition.

---

### Post by rudi009 on 2010-04-09
i don't want to do a complete repartitioning.....how do i resize the extended partition after deleting sda8 and sda9???

---

### Post by plucky on 2010-04-09
> **rudi009 said:**
> i don't want to do a complete repartitioning.....how do i resize the extended partition after deleting sda8 and sda9???

Remember you have to turn off swap before you can do anything on the extended partition.Use the Live CD to run Gparted.The swap partition is used even on the Live CD

1. Turn off swap
2. Delete sda8
3. Delete sda9
4. Select sda2 and resize
5. Select the un-allocated space and create a new primary partition.


Good Luck

---

### Post by rudi009 on 2010-04-09
alright thanks for all the  help  I'm done installing windows,it ran fine, also reinstalled grub2 but i'm stuck once more.. windows didn't showed up in the menu.so now??:)

---

### Post by oldfred on 2010-04-09
If your windows was running ok then this should find it:

sudo update-grub

---

### Post by srs5694 on 2010-04-09
I realize I'm closing the barn door after the horses have run off, but.... There's no rule that extended/logical partitions have to come after all the primaries. Given that the disk has 15.7GB of free space at the end of the drive, I'd just turn that into a primary and install Windows there. If 15.6GB is too little space, then move /dev/sda8 and /dev/sda9 up, thus giving about 17.9GB of free space at the end of the disk that can be turned into a primary partition. (In addition to or instead of moving /dev/sda8 and /dev/sda9, one or both of them can be deleted, adding even more free space into the pool.)

Another option, albeit a much riskier one in many ways, would be to convert the disk to GPT format (using [GPT fdisk](http://www.rodsbooks.com/gdisk/) or [gptgen](http://sourceforge.net/projects/gptgen/)) and then create a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) configuration using whatever partitions you want. Windows would see a maximum of three partitions, whereas Linux would see them all. The advantage is that the three partitions Windows would see could be anywhere on the disk, and any or all of them could be logical partitions in the current configuration. (They'd become primary partitions on the MBR side of the hybrid MBR.) Hybrid MBRs are, however, flaky and potentially trouble-prone, so I recommend this only if you're really desperate for a quick solution and can't find another way to get the layout you want within a pure-MBR configuration. Also, you'll need to re-install your boot loader after converting from MBR to GPT.

---

