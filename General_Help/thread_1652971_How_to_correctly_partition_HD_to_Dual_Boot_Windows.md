---
title: "How to correctly partition HD to Dual Boot Windows XP and Ubuntu 10.10"
date: 2010-12-26
forum: General Help
---

### Post by hi8u3ri on 2010-12-26
Hey folks.  I was hoping for some help with a simple problem that I have been unable to find a definitive answer for.

I want to dual boot Windows XP and Ubuntu 10.10.  I have read several guides on the **correct partitioning scheme** but they are not consistent in recommendations/methods.  Unfortunately, some will suggest how to partition my drive but not how to install correctly onto those partitions.

**My HD configuration (1HD):**
[LIST]
[*]1 primary partition NTFS (20GB) for Windows XP
[*]1 extended partition which contains 1 logical partition with all my data (NTFS...plenty of space)
[/LIST]

I partitioned my HD to match the scheme found here: [https://help.ubuntu.com/community/PartitioningSchemes]("https://help.ubuntu.com/community/PartitioningSchemes")

**Follwing that, I ended up with:**
[LIST]
[*]A primary NTFS partition for XP (20GB)
[*]A primary ext3 partition "just in case" (2GB)...(is this even needed?  I don't have a "recovery partition" for XP nor will I ever...)
[*]A primary ext3 partition for the GRUB bootloader (100 MB)
[/LIST]
An extended partition that contained the following:
[LIST]
[*]A logical linux-swap partition (2GB)
[*]A logical ext3 parition for Ubuntu installation (20GB)
[*]A logical NTFS partition that contains the rest of my data (from original configuration)
[/LIST]

I tried installing Ubuntu using the "Advanced" installation option where I select the partitions.  This was the preferred/more flexible way to dual boot, or so I got the feeling after reading several guides.  I was prompted where to install the boot loader.  I selected the 100 MB primary ext3 partition I created for GRUB (made sense?) and was given a warning that the size was too small.  I clicked to continue anyway, and, of course it did not work.

**So my question(s):**
[LIST=1]
[*]Did I select the wrong partition when I tried installing?
[*]Should I keep this partition scheme as is, with 6 partitions?  If so, I would like to know what mount points I should have for the new partitions I created, when needed.
[*]Is the "just in case" partition necessary, or can I get rid of it?  I will never need it with windows and didn't know why I was suggested to create it.
[*]If I return the 6 current partitions back into the 2 I started with, what is the best course of action?  I prefer not to touch the first XP partition.  I am not sure how the "automatic" resize option works but I am wary of things like that (and read it didn't work the best).  But I also wouldn't mind to use if you all suggest to.
[*]If I use the automatic resize option, how exactly does Ubuntu set itself up and change the partitions? (as in, does it create a separate primary partition, move itself to a logical partition, etc)  I feel like if I knew this I would be more comfortable using it.
[/LIST]

Well I could maybe ask more questions but I know you all are intelligent enough to understand what I am trying to do and what I've tried.  

I certainly appreciate the time!  And I am absolutely excited to FINALLY be getting away from the world of Windows.  It's been a long time coming, and maybe my next computer won't be dual-boot :)  Please let me know if I can clarify anything!

PS: Guides I've already read:
[http://www.ntechcomm.com/blog/2010/11/how-to-dual-boot-ubuntu-10-10-and-windows-xp-professional/]("http://www.ntechcomm.com/blog/2010/11/how-to-dual-boot-ubuntu-10-10-and-windows-xp-professional/")
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by mikewhatever on 2010-12-26
I think that partitioning scheme is an overkill. All you needed to add was two logical partition, one for Ubuntu (~20GB) and the other for swap (~2GB).
The bootloader should go to the MBR (/dev/sda), which is the default, otherwise, you'd have to figure out how to boot Ubuntu using the XP bootloader.

---

### Post by C.S.Cameron on 2010-12-26
Install XP.
Defragment.
Boot Live CD.
For 10.10:
When you get to partitioning, If you don't see anything you like, go Manual.
Resize Windows partition.
In 10GB of free space create / partition in ext4.
In remainder - 2GB of free space create /home partition.
In last 2GB free space create swap space.
install.

---

### Post by hi8u3ri on 2010-12-26
Okay, I was afraid if I gave the XP partition as the location for the boot loader, things might get hairy and die.  Even though I have a backup, it sucks reinstalling everything.

So both of you pretty much suggest the same thing: to leave only one primary partition (NTFS) for XP and install the boot loader there...and to have a logical partition for Ubuntu and a logical swap partition in my extended partition. (then plus another third logical partition with my existing data).

Will I need to specify a partition for /home?  I was planning to just use my already existing NTFS partition with all of my nicely sorted data :)  I have no real reason to want another place to store data.  Not sure if it is generally advised to suggest doing otherwise or if it's preference.

---

### Post by mikewhatever on 2010-12-26
It is not a requirement to have home on a separate partition, and since you'll be using a data partition, simply skip specifying home.

---

### Post by C.S.Cameron on 2010-12-26
> **hi8u3ri said:**
> Okay, I was afraid if I gave the XP partition as the location for the boot loader, things might get hairy and die.  Even though I have a backup, it sucks reinstalling everything.

So both of you pretty much suggest the same thing: to leave only one primary partition (NTFS) for XP and install the boot loader there...and to have a logical partition for Ubuntu and a logical swap partition in my extended partition. (then plus another third logical partition with my existing data).

Will I need to specify a partition for /home?  I was planning to just use my already existing NTFS partition with all of my nicely sorted data :)  I have no real reason to want another place to store data.  Not sure if it is generally advised to suggest doing otherwise or if it's preference.

Some people prefer a separate home folder when it comes to upgrading via a fresh install, some do not care.


Bootloader should go on root of the drive, ie sda not sda1

---

### Post by hi8u3ri on 2010-12-26
Thank you!

---

