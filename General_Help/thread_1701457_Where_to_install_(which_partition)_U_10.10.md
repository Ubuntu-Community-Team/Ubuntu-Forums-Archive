---
title: "Where to install (which partition) U 10.10?"
date: 2011-03-06
forum: General Help
---

### Post by rva1945 on 2011-03-06
I will install Ubvuntu 10.10 in my netoobk, which came with a 320 GB HD already partitioned, 100GB with W7 and 220 just formatted.

I wish to install Ubuntu in the 220 GB partition, the question is, where will be the boot loader (with the options Windows 7 or Linux Ubuntu 10.10) be should be installed?

I'm running the U10.10 Live CD for installation, in Allocated drive space, options are:

1. Install alongside other operating systems
2. Erase and use the entire disk
3. Specify partitions manually (advanced)

I pick the last one (3), then this is shown:

/dev/sda, no type,  no size
/dev/sda1, type NTFS, size 104 MB
/dev/sda2, type NTFS, size 104172 MB
/dev/sda3, type NTFS, 215213 MB

Boot loader, here I have the options:

/dev/sda ATA.... (320.1GB)
/dev/sda1 Windows7 (loader)
/dev/sda2 
/dev/sda3

Question is: where to install the loader? I need the netbook to ask for an operating system to boot, the same way as the desktop PC does (Linux Ubuntu 9.10 or XP).

I can't easily configure the wireless connection, should I connect the netbook to the Internet with a wire before the installation process (for updating purposes)?

Thanks

---

### Post by TeoBigusGeekus on 2011-03-06
> **rva1945 said:**
> 
I can't easily configure the wireless connection, should I connect the netbook to the Internet with a wire before the installation process (for updating purposes)?

Yep.

The bootloader should be installed on /dev/sda, not on a partition.

---

### Post by oldfred on 2011-03-06
You also cannot install to a NTFS partition unless you are installing wubi. Your sda3 will have to be deleted and a new sda3 as an extended  partition as the container  for logicals inside it. 

Shared NTFS partition 
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

---

### Post by rva1945 on 2011-03-06
> **TeoBigusGeekus said:**
> Yep.

The bootloader should be installed on /dev/sda, not on a partition.

sda is the whole hard disk, as far as I understand:

/dev/sda ATA.... (320.1GB) 

won't that erase the partitions? Please remember, I wish the W7 partition to remain, and use the 200GB partition for Ubuntu, with dual boot ability.

My RAM is 4GB.

Thanks
Robert

---

### Post by lithopsian on 2011-03-06
Don't worry about the bootloader, it will put itself in the correct place and give you a menu that allows you to boot to windows or Ubuntu, plus a few other options.

Just check the allocations when you are finished to be sure that windows is still there, followed by the two or three ext4 partitions you are about to create for Ubuntu.

I'm not sure how oldfred has determined that you need 2GB for swap.  You may need more, if you have a lot of memory and plan to hibernate.  You may need less, if you have a lot of memory and don't plan to hibernate, but then you're hardly short of space.  For hibernation you need swap equal to the size of your RAM, plus a bit more in case you are actually swapping.  For actual swap, more than about 1GB is rarely needed because your machine will grind to a halt long before that, but 2GB is a handy safe margin in case something goes horribly wrong.

---

### Post by jerome1232 on 2011-03-06
> **rva1945 said:**
> sda is the whole hard disk, as far as I understand:

/dev/sda ATA.... (320.1GB) 

won't that erase the partitions? Please remember, I wish the W7 partition to remain, and use the 200GB partition for Ubuntu, with dual boot ability.

My RAM is 4GB.

Thanks
Robert

When you install the boot loader to sda, it's actually just installing it in the MBR of sda, the MBR is the first... 512 bytes, if memory serves correctly, of the disc, it contains the partition table and the bootloader on dos partitioning schemes.

Grub2, the default bootloader installed by Ubuntu, should detect your Windows installation and offer it as a choice alongside Ubuntu with no hitches.

---

### Post by rva1945 on 2011-03-06
> **jerome1232 said:**
> When you install the boot loader to sda, it's actually just installing it in the MBR of sda, the MBR is the first... 512 bytes, if memory serves correctly, of the disc, it contains the partition table and the bootloader on dos partitioning schemes.

Grub2, the default bootloader installed by Ubuntu, should detect your Windows installation and offer it as a choice alongside Ubuntu with no hitches.

So, I will connect the netbook to the Internet (so it will be able to update during the installation process) via a wire, run the install, selection dev/sda for boot loader.

Thanks

---

### Post by rva1945 on 2011-03-06
> **TeoBigusGeekus said:**
> Yep.

The bootloader should be installed on /dev/sda, not on a partition.

 How could I be connected to the Internet and at the same time install Ub 10.10 from the Live CD? To connect, I need to Try Ubuntu, then create the wired connection. To install, I have to re-start (and then loose the connection because it's not saved anywhere).  ?

---

### Post by oldfred on 2011-03-06
If you have the Ethernet connection and it works in the liveCD, then the installer will also find it, to run updates.

---

### Post by rva1945 on 2011-03-07
> **jerome1232 said:**
> When you install the boot loader to sda, it's actually just installing it in the MBR of sda, the MBR is the first... 512 bytes, if memory serves correctly, of the disc, it contains the partition table and the bootloader on dos partitioning schemes.

Grub2, the default bootloader installed by Ubuntu, should detect your Windows installation and offer it as a choice alongside Ubuntu with no hitches.


Well, I' m now in the process, I highlighted sda3 but it isn't enough, when clicked Forward, it says "No root file system is defined"

I think I should select the sda3 partition, click on Change, then I have these options:

Ext4 journaling file system
Ext3 journaling file system
Ext2 file system
ReiserFS journaling file system
btrfs journaling file system
FAT16 file syetem
FAT32 file system
ntfs
swap area
do not use the partition the default value, thus the message)

And mount point, I have two options /dos and /windows (?)

And simply put, I don't have any idea on what to do next.

---

### Post by rva1945 on 2011-03-07
> **jerome1232 said:**
> When you install the boot loader to sda, it's actually just installing it in the MBR of sda, the MBR is the first... 512 bytes, if memory serves correctly, of the disc, it contains the partition table and the bootloader on dos partitioning schemes.

Grub2, the default bootloader installed by Ubuntu, should detect your Windows installation and offer it as a choice alongside Ubuntu with no hitches.

OK I chose Ext4, then mount point as "/".

Then it says
"you have not selected any partitions for use as swap space..."

Only if I select /dev/sda, the New partition table buttons is enabled, when clicked,

"You have selected an entire device to partition, if you proceed...then all current partitions will be removed"

And now I'm scared to death.

---

### Post by rva1945 on 2011-03-07
> **jerome1232 said:**
> When you install the boot loader to sda, it's actually just installing it in the MBR of sda, the MBR is the first... 512 bytes, if memory serves correctly, of the disc, it contains the partition table and the bootloader on dos partitioning schemes.

Grub2, the default bootloader installed by Ubuntu, should detect your Windows installation and offer it as a choice alongside Ubuntu with no hitches.


Well, I tried "Install alongside other operating systems

Then an "Allocate drive space" window sppears, select drive: tha 320GB ATA is the only option.

"Allocate drive space by dragging the divider..."

And the 215GB partition appears partitioned as 
Files (3.2GB)
/dev/sda3 (ntfs)
107.6GB

and 

Ubuntu
/dev/sda4 (ext4)
107.6GB

Firs question: no matter how I allocate drive space, the FIles (3.2GB) remains with that 3.2GB that I don't know what that is (swap file?)

So Ubunto will automatically install where I want? So the first partition shouldn't be smaller than 3.2GB? What will be installed there? I need Ubuntu to use the whole 215 GB partition.

BUT

If I click on Use entire partition, it has the same effect as clicking on USe entire disk:

Ubuntu
/dev/sda (ext4)
320.1GB

I guess that will erase the two partitions already in the disk (100GB with W7 and 215 empty).

pls help thnks

---

### Post by oldfred on 2011-03-07
Please reread my post #3. You have to delete the NTFS partition and recreate as the extended partition. Then you can create the logical partitions in the extended.

If you create the / (root), swap & /home partitions you will not have any issues. 

but as you noticed:
Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

---

### Post by rva1945 on 2011-03-07
> **oldfred said:**
> Please reread my post #3. You have to delete the NTFS partition and recreate as the extended partition. Then you can create the logical partitions in the extended.

If you create the / (root), swap & /home partitions you will not have any issues. 

but as you noticed:
Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

Well, I couldn't wait for answers, but that's my problem. Tha fct is that I followed the steps i considered right. Ubuntu was successfully installed in /dev/sda1 ext4 281.9 GB. I thought it was going to use the already created 215GB and install a GRUB2 menu in the MBR, but it seems that W7 is gone for ever.

At least the wireless connection was correctly automatically configured, I did nothing, that's pretty good.

How could I know if there is stlll a W7 out there in its partition (albeit reduced because it was almost 100GB "from factory")

---

### Post by oldfred on 2011-03-07
If you installed to sda1 and sda1 was your windows it is gone. Did you backup your  windows install or at least the data before you installed?

Ubuntu's install would at the minimum overwrite parts of the windows install, so it would not be recoverable. If you did the full disk install it overwrote the recovery partition also.

Did you create the vendor recommended recovery DVDs and windows repairCD? If not you will have to contact vendor an see if you can get a new DVD to reinstall windows if you want it. Some charge for that service.

This will show everything installed and where it is:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

If you have some data you want to try to recover, stop using hard drive and from liveCd download photorec.

---

### Post by rva1945 on 2011-03-07
> **oldfred said:**
> If you installed to sda1 and sda1 was your windows it is gone. Did you backup your  windows install or at least the data before you installed?

Ubuntu's install would at the minimum overwrite parts of the windows install, so it would not be recoverable. If you did the full disk install it overwrote the recovery partition also.

Did you create the vendor recommended recovery DVDs and windows repairCD? If not you will have to contact vendor an see if you can get a new DVD to reinstall windows if you want it. Some charge for that service.

This will show everything installed and where it is:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

If you have some data you want to try to recover, stop using hard drive and from liveCd download photorec.

This was the "disks layout" as seen by Ubuntu prior to install:}

/dev/sda,
/dev/sda1, type NTFS, size 104 MB
/dev/sda2, type NTFS, size 104172 MB
/dev/sda3, type NTFS, 215213 MB

so sda was the whole disk. sda1 or sda2 the W7 partition, I don't know now. I wanted Ubuntu to install in sda3, the 215GB partition (when I bought the netbook, it came with a 105GB with W7 and 215GB just formatted,  wanted ubuntu in this last one).

I know the Linux team have been doing great efforts to provide friendly versions of Linux, this way gaining more and more users, but the options during the install process were really confusing.

I didn't want to loose the W7 partition just in case it would be a pain trying to configure Linux for wireless connection, fortunately I had to do nothing at all about that, it detected and configured the wireless connection right.

If I consider it necessary to have W7 running I'll install a VM.

the only thing I'll like to alter is that the partition should be 320 not 307 GB, in Disk Uility I see:

/dev/sda   is the drive, 320GB

/dev/sda1 is the 307GB ext4, with 13GB as swap space.

Isn't it 13GB too much for swap space?

---

### Post by jerome1232 on 2011-03-07
Rule of thumb for swap is double your ram, I usually don't quite go that much but if you want to be able to hibernate you need a little bit more than you have ram.

ie 3 GB's of RAM, I would do like 3.2 GB of swap if I wanted to hibernate the computer.

No matter how hard you try setting up a dual boot manually will be difficult for most people the first time around, regardless of os. (for example Windows doesn't even ask you about the boot loader, it just wipes out the one you have and installs it's bootloader, then you can't boot your other operating systems untill you reinstall whatever boot loader you had)

The more familiar you get with partitioning the easier it will come.

---

### Post by rva1945 on 2011-03-08
> **jerome1232 said:**
> Rule of thumb for swap is double your ram, I usually don't quite go that much but if you want to be able to hibernate you need a little bit more than you have ram.

ie 3 GB's of RAM, I would do like 3.2 GB of swap if I wanted to hibernate the computer.

No matter how hard you try setting up a dual boot manually will be difficult for most people the first time around, regardless of os. (for example Windows doesn't even ask you about the boot loader, it just wipes out the one you have and installs it's bootloader, then you can't boot your other operating systems untill you reinstall whatever boot loader you had)

The more familiar you get with partitioning the easier it will come.

Yes but U10.10 did waht it wanted, I remember that I chose to partition the 215GB partition in 30GB with "Files 3.2GB" (swap?) as suggested by the dialog, and the other one 185GB, but then the whole disk was used, 307 + 13GB of swap, good-bye Windows 7 partition.

---

### Post by oldfred on 2011-03-08
they have finally recognized that the use entire partition button was a issue and will have a fix by Natty beta.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

---

### Post by rva1945 on 2011-03-08
> **oldfred said:**
> they have finally recognized that the use entire partition button was a issue and will have a fix by Natty beta.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)


I can't believe my eyes, did I loose an entire W7 installation just because of a bug??? Weren't Linux OS more reliable than M$ W???

---

### Post by oldfred on 2011-03-08
Kansasnoob had a heck of time to get them to recognize it. It is not a bug, just bad instructions. It does what you tell it, but most do not understand that those instructions really mean entire drive.

---

### Post by rva1945 on 2011-03-08
> **oldfred said:**
> Kansasnoob had a heck of time to get them to recognize it. It is not a bug, just bad instructions. It does what you tell it, but most do not understand that those instructions really mean entire drive.

In my case, I could admit it might be due to misunderstanding (from newbie to less than semi-expert), but the instructions were clear in that the 215GB partition was to be used, instead, the whole 320GB hard disk was formatted to ext4.

---

### Post by jerome1232 on 2011-03-08
I usually use alternate install discs and when I do use the live cd, I just use the manual partition option. I don't trust a setup utility to make partitioning decisions for me :D.

Reading through the bug report the new ui does sound confusing! I hope it does get changed in 11.04

---

