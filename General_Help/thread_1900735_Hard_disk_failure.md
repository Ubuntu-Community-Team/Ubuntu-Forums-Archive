---
title: "Hard disk failure?"
date: 2011-12-27
forum: General Help
---

### Post by marsgorski on 2011-12-27
I have a Samsung SP0802N ATA hard drive on an HP Pavilion a500n desktop. A while ago it stopped booting, after the "HP" blue BIOS screen, instead of GRUB I only get a flashing bar on the upper left corner and nothing happens.

I have an NTFS partition which I am unable to mount in the ubuntu live cd, and I had an ext3 (or ext4, maybe) partition which I was able to mount and access the files. Since then I formatted the ext3 partition to an ext4 partition but I have not been able to reinstall Ubuntu in that partition. 

Also, I enter disk utility and in SMART status I get a green dot saying disk is healthy but when I click on SMART Data and run a short self-test I get the message "Failed (Electrical)" after just a few seconds. Basically there are three things with which I am having issues:
[LIST=1]
[*]Diagnose the problem and determine if the HD is at fault and whether it is still usable.
[*]Recover data on the NTFS partition
[*]If HD is still usable, reinstall ubuntu, or at least boot Windows XP in the NTFS partition.
[/LIST]

I should also add that Disk Utility does not seem to recognize the NTFS file system (It is shown as Unknown 49 GB on the graph), but when I attempt to install Ubuntu it does recognize the partition's file system as NTFS, also when I run  fdisk -l. I am following [these instructions]("http://www.wikihow.com/Recover-a-Dead-Hard-Disk") (under Using Linux to recover your Data) but the command "mount -t auto /dev/sda2" tells me I need to specify the filesystem, so when I run "mount -t ntfs /dev/sda2" I get "The device '/dev/sda2' doesn't seem to have a valid NTFS." 

I greatly appreciate any advice. Thanks!

---

### Post by marsgorski on 2011-12-27
Anyone out there?

---

### Post by Mark Phelps on 2011-12-27
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, my suggestions are the following (based on my experience at doing this successfully):
1) Find someone with a working Windows PC
2) Remove your drive from this PC.
3) On the Windows PC, download and install the trial version of GetDataBack for NTFS from Runtime Software.
4) Connect your old drive to this Windows PC.
5) Run GetDataBack in deepest discovery mode -- probably best to let it run overnight.
6) In the morning, check the recovery logs and see if GetDataBack was able to find your lost files.
7) If it was, you will have to purchase it to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, BTW, it is not HUNDREDS of dollars for this product. Last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

### Post by Don Barzini on 2011-12-27
Did you try System Rescue CD?

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

[http://www.sysresccd.org/Online-Manual-EN](http://www.sysresccd.org/Online-Manual-EN)


The documentation contains info on how to access an NTFS drive.

If you still want to use your Ubuntu Live CD, you could also follow the instructions below and install **ntfs-3g** into your Live CD system and try to access the Windows partition .... then copy your files over the network to another machine...

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)


Good Luck.

---

