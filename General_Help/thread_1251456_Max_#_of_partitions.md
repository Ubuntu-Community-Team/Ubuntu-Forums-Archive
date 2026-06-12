---
title: "Max # of partitions"
date: 2009-08-27
forum: General Help
---

### Post by Muscovy on 2009-08-27
I'm just about to pick up a new computer. It's got a 250 GB SATA drive. Due to reasons of useage and organisation, I would ideally run 3 Linux and 2 Windows partitions (5 full-out OSs), but I've heard there's a limit to 4. What is the max?


  Edit: Amount of data isn't an issue.

---

### Post by bchurchill on 2009-08-27
You can have only four primary partitions becasue of how BIOS/bootloaders work (it's annoying).  However, a primary partition can also be extended to have several logical partitions.  Windows needs to be installed on primary partitions, but Linux couldn't care less.  So you'll probably have:

primary partition #1: Windows
primary partition #2: Windows
primary partition #3: linux swap, maybe boot, and 2-3 others of your choice.

In general the ubuntu partitioner will take care of the details for you.

---

### Post by jerome1232 on 2009-08-27
4 primary partitions, but you can make logical partitions, you can make alot of them. I think 26 is the safe limit but I've heard of 100+.

basically Window must be on primary partitions soooo you would want

sda1 win1
sda2 win2
sda3 extended partition (means you can put logical partitions in it)
    sda5 swap
    sda6 linux1
    sda7 linux2
    sda8 linux3

---

### Post by chriskin on 2009-08-27
does anyone know by the way why windows wants the partition to be primary?

---

### Post by jmszr on 2009-08-27
muscovy,

This should be of help: [https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

---

### Post by Muscovy on 2009-08-27
From what I understood about logical partitions, I thought they were another drive, like Z:. That solution may work, because one of them is an Ubuntu partition for doing things like compiling LiveCDs which tend to be a nightmare to clean short of a reinstall. Or do I not understand logical partitions?

  Another way I can narrow it down is the second Windows partition. It's Windows Vista, and the only reason I have it is because I couldn't get out o buying it with my laptop, and I can't upgrade to W7. It seems a waste to get rid of, but I'dbe perfectally happy to have it unbootable, so long as I can wipe a space for it and restore it.

---

### Post by Muscovy on 2009-09-13
I don't know what I'm doing here.

  Here's a modified and precise list of all systems I want to run:
-Windows 7 (installed)
-Ubuntu 9.04 (installed)
-Fedora 11
-Ubuntu 9.04
  The reason I have 2 Ubuntus is some compiling operations I've done leave debris that me/root can't touch, and I need to reinstall to clean up.

  I assumed I'd be fine since I decided to just scrap Vista since I'd never use it, I'd have 4 and be fine. However, I tried putting Fedora on, and it needs 2 new partitions and I can only make 1 more. I can't see how I can make logical partitions in my current setup. I think I could do it if I reinstall everything, but there's no way I need to.

  Here's my partition layout. Bold is primary.
unallocated - (1 MB)
[B]/dev/sda1 - A 100 MB partition that W7 apparently needs.
/dev/sda2 - 7 main.[/B]
unallocated - (69 GB)
**/dev/sda3**
- /dev/sda5 - Ubuntu
- /dev/sda6 - Swap
unallocated - (8 GB)

  How do I add logical partitions?

---

### Post by Topsiho on 2009-09-13
> **Muscovy said:**
> 
  Here's my partition layout. Bold is primary.
unallocated - (1 MB)
[B]/dev/sda1 - A 100 MB partition that W7 apparently needs.
/dev/sda2 - 7 main.[/B]
unallocated - (69 GB)
**/dev/sda3**
- /dev/sda5 - Ubuntu
- /dev/sda6 - Swap
unallocated - (8 GB)

  How do I add logical partitions?

From what you write here you have two primary partitions, sda1 and sda2
Then you have two logical partitions already, sda5 and sda6, which must be sitting in a container, called an extended partition, which I gather is sda3.

So you can create only one primary partition more, as room for the fourth is taken by sda3. And in sda3 you can create a lot (I don't know exactly how many) of logical partitions just by choosing logical during the process of creating the partitions.

Topsiho

---

### Post by bodhi.zazen on 2009-09-13
Ubuntu does not like ti if you have more then 15 partitions. You will start to get complaints from gparted.

---

