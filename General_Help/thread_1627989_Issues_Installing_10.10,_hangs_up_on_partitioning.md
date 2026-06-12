---
title: "Issues Installing 10.10, hangs up on partitioning"
date: 2010-11-22
forum: General Help
---

### Post by thahamer on 2010-11-22
I am attempting to install v. 10.10 onto my netbook which does not have a CD rom. I created the USB drive using Universal USB Installer. 

When I boot and run off the USB without installing it seems to work fine.

On the other hand, when i attempt to install to the HD, it hangs up just before getting to the screen where I would Delete the current partitions and choose where to install. I have a strange feeling it has to do with Gparted trying to read the USB drive but I cannot be sure.

Thanks

---

### Post by lmarmisa on 2010-11-22
I do not know Universal USB installer.

I prefer to create a USB drive using the Startup Disk Creator facility of the Ubuntu 10.10 Live CD.

You will need another PC with a CD/DVD drive in order to create this startup pendrive.

---

### Post by Mark Phelps on 2010-11-22
IF your netbook came with Windows 7 preloaded, and it already has the limit of 4 partitions on the drive, the installer is always going to hang at partitioning because there's nothing it can do.

It runs off the USB because it's not concerned about partition limits when it's running in LiveCD mode.

Run it again in LiveCD mode, open a terminal, enter "sudo fdisk -lu" (that's a lowercase L, not a one), and post the results back here.

IF you already have the 4-partition limit in place, it's going to be a LOT of work getting Ubuntu installed.

---

### Post by thahamer on 2010-11-22
> **Mark Phelps said:**
> IF your netbook came with Windows 7 preloaded, and it already has the limit of 4 partitions on the drive, the installer is always going to hang at partitioning because there's nothing it can do.

It runs off the USB because it's not concerned about partition limits when it's running in LiveCD mode.

Run it again in LiveCD mode, open a terminal, enter "sudo fdisk -lu" (that's a lowercase L, not a one), and post the results back here.

IF you already have the 4-partition limit in place, it's going to be a LOT of work getting Ubuntu installed.

It came preinstalled with XP not 7.

I ran the command and here are the results:


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e762533

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   306616589   153308263+  83  Linux
/dev/sda2       306616590   312576704     2980057+   5  Extended
/dev/sda5       306616653   312576704     2980026   82  Linux swap / Solaris

Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 22 sectors/track, 4137 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7827455     3909696    b  W95 FAT32

Disk /dev/sdc: 500 MB, 500695040 bytes
3 heads, 34 sectors/track, 9587 cylinders, total 977920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1             239      977919      488840+   6  FAT16

---

### Post by thahamer on 2010-11-22
> **lmarmisa said:**
> I do not know Universal USB installer.

I prefer to create a USB drive using the Startup Disk Creator facility of the Ubuntu 10.10 Live CD.

You will need another PC with a CD/DVD drive in order to create this startup pendrive.

Would this make a difference for my problem? If so I am willing to try it out. I have a PC with a CD/DVD drive.

---

### Post by bonixavier on 2010-11-22
If that's the problem, fire up a [Gparted Live]("http://gparted.sourceforge.net/livecd.php") session, do all your partitioning there and specify manual partitionng in the install.

Edit: Is keeping Windows considered necessary?

---

### Post by thahamer on 2010-11-22
> **bonixavier said:**
> If that's the problem, fire up a [Gparted Live]("http://gparted.sourceforge.net/livecd.php") session, do all your partitioning there and specify manual partitionng in the install.

Edit: Is keeping Windows considered necessary?

Are you asking for me? If so I want to get rid of windows completely

---

### Post by bonixavier on 2010-11-22
> **thahamer said:**
> Are you asking for me? If so I want to get rid of windows completely
So you boot from the Live Gparted CD. Just go clicking enter until you reach a graphical environment. When you get there, select the disk you want to use (sda probably), delete all the partitions and make a solid 4 partitions scheme:
```
200MB partition (you can use any ext here because it will be your boot partition and won't be needing journaling. In doubt, pick ext4). When installing, assign its mount point to /boot
30GB ext4 primary partition. This will be your system partition. When installing, assign it / as its mount point.
I don't know how much RAM you have, but a 1-4GB swap partition would do the trick. Remember to select swap as the file system. The installer will automatically recognize this partition.
The rest as an ext4 partition. This will be your personal partition and will store all your personal files. It's very convenient to keep it separate from the system partition so that you won't lose your stuff if you need to reinstall or change your distro.

```
In this case, all the partitions can be primary. As you have two other HDs, you can let them for your distro-hopping.

So, when installing Ubuntu, make sure you select something like "Manually Select Partitioning scheme (advanced)" and assign the appropriate mount points to them. You can safely install the boot-loader to /dev/sda.

If the problem was really in the partitioning, this will fix your problem.

---

### Post by thahamer on 2010-11-22
> **bonixavier said:**
> So you boot from the Live Gparted CD. Just go clicking enter until you reach a graphical environment. When you get there, select the disk you want to use (sda probably), delete all the partitions and make a solid 4 partitions scheme:
```
200MB partition (you can use any ext here because it will be your boot partition and won't be needing journaling. In doubt, pick ext4). When installing, assign its mount point to /boot
30GB ext4 primary partition. This will be your system partition. When installing, assign it / as its mount point.
I don't know how much RAM you have, but a 1-4GB swap partition would do the trick. Remember to select swap as the file system. The installer will automatically recognize this partition.
The rest as an ext4 partition. This will be your personal partition and will store all your personal files. It's very convenient to keep it separate from the system partition so that you won't lose your stuff if you need to reinstall or change your distro.

```In this case, all the partitions can be primary. As you have two other HDs, you can let them for your distro-hopping.

So, when installing Ubuntu, make sure you select something like "Manually Select Partitioning scheme (advanced)" and assign the appropriate mount points to them. You can safely install the boot-loader to /dev/sda.

If the problem was really in the partitioning, this will fix your problem.

What I find strange is that, when i try to open GParted with the USB still in the computer, it briefly opens and then closes again, and the light on the USB drive flashes as if it is being read. 

On the other hand, when i just unplugged the USB right before opening gparted, gparted opens fine.

Could there be an issue with Gparted attempting to read the USB?

---

### Post by bonixavier on 2010-11-22
It could. AFAIK, they're considered hard-drives. Could you install Ubuntu now?

---

### Post by thahamer on 2010-11-22
> **bonixavier said:**
> It could. AFAIK, they're considered hard-drives. Could you install Ubuntu now?

I am partitioning now Im just confused by 
When installing, assign its mount point to /boot

---

### Post by thahamer on 2010-11-22
When i tried to apply the changes i recieved an error

"An error occured while applyig the operations"

---

### Post by bonixavier on 2010-11-22
> **thahamer said:**
> I am partitioning now Im just confused by 
When installing, assign its mount point to /boot
OK. You'll pick manual partitioning during the install of Ubuntu. Then you'll have to manually (duh!) select each partition and click "Edit Partition" then you'll have something like this (the screenshot is from [an old release tutorial]("http://www.dedoimedo.com/computers/ubuntu-install.html"), but the principle is the same):

[IMG]http://www.dedoimedo.com/images/computers_new_1/ubuntu-install-partitioning-new-param.jpg[/IMG]

See the mount point there right above cancel and ok? Scroll it. For the first partition (around 200MB), you'll pick "/boot"
For the second (between 20 and 30GB), you'll pick "/"
And for the last (rest of disk space, 100 and something GB), you'll pick "/home"

Is it clear now?

> **thahamer said:**
> When i tried to apply the changes i recieved an error

"An error occured while applyig the operations"
Does it say what the error was?

---

### Post by thahamer on 2010-11-22
> **bonixavier said:**
> OK. You'll pick manual partitioning during the install of Ubuntu. Then you'll have to manually (duh!) select each partition and click "Edit Partition" then you'll have something like this (the screenshot is from [an old release tutorial]("http://www.dedoimedo.com/computers/ubuntu-install.html"), but the principle is the same):

[IMG]http://www.dedoimedo.com/images/computers_new_1/ubuntu-install-partitioning-new-param.jpg[/IMG]

See the mount point there right above cancel and ok? Scroll it. For the first partition (around 200MB), you'll pick "/boot"
For the second (between 20 and 30GB), you'll pick "/"
And for the last (rest of disk space, 100 and something GB), you'll pick "/home"

Is it clear now?


Does it say what the error was?


When i click Save Details for the error, it closes gparted and doesnt allow me to choose where i would like to save the details

---

### Post by bonixavier on 2010-11-22
> **thahamer said:**
> When i click Save Details for the error, it closes gparted and doesnt allow me to choose where i would like to save the details
Are you trying to open a Live Gparted disk or the Gparted that comes within Ubuntu's disk? If it's the latter, I'd strongly recommend switching to the one provided by Gparted. For one, it's a Debian system, which makes it way more stable.

Another thing, before you burned it to the flash drive, did you check its md5sum? Sometimes we get some problems because our download was defective because of whatever reasons.

---

### Post by thahamer on 2010-11-22
> **bonixavier said:**
> Are you trying to open a Live Gparted disk or the Gparted that comes within Ubuntu's disk? If it's the latter, I'd strongly recommend switching to the one provided by Gparted. For one, it's a Debian system, which makes it way more stable.

Another thing, before you burned it to the flash drive, did you check its md5sum? Sometimes we get some problems because our download was defective because of whatever reasons.

I clicked the link in this thread and made a bootable USB with Gparted.

I redownloaded the zip a second time, because i was worried about a corrupt DL. Is there w way to check the md5sum on my windows pc where I have been making the boot drives?

---

### Post by bonixavier on 2010-11-22
[Ubuntu's guide]("https://help.ubuntu.com/community/HowToMD5SUM") recommends[ winMD5Sum]("http://www.nullriver.com/products/winmd5sum").

---

### Post by thahamer on 2010-11-22
I checked the md5sum on the zip and it said "md5 check sums are different" redownloaded from a different mirror and got the same message

---

### Post by bonixavier on 2010-11-22
> **thahamer said:**
> I checked the md5sum on the zip and it said "md5 check sums are different" redownloaded from a different mirror and got the same message
There's probably something wrong with your net / computer. It may be that your download of Maverick was corrupted as well and that's causing your problems.

Just to make sure, try using a different md5sum program. Google suggests [Md5sums for Windows]("http://www.pc-tools.net/win32/md5sums/") and [md5summer]("http://www.md5summer.org/"). I can vouche for none.

---

### Post by thahamer on 2010-11-22
> **bonixavier said:**
> There's probably something wrong with your net / computer. It may be that your download of Maverick was corrupted as well and that's causing your problems.

Just to make sure, try using a different md5sum program. Google suggests [Md5sums for Windows]("http://www.pc-tools.net/win32/md5sums/") and [md5summer]("http://www.md5summer.org/"). I can vouche for none.

ran it a second time and it came back fine, which i guess brings me abck to square one

---

### Post by bonixavier on 2010-11-22
> **thahamer said:**
> ran it a second time and it came back fine, which i guess brings me abck to square one
This has gone beyond what I can do to help you. Sorry. Try posting your problem at linuxquestions.org

---

### Post by thahamer on 2010-11-22
> **bonixavier said:**
> This has gone beyond what I can do to help you. Sorry. Try posting your problem at linuxquestions.org


Thank you very much for your help. I appreciate it

---

### Post by thahamer on 2010-11-23
Interesting enough, I tried this with two relatively new USB drives and had failure with both. I then got out a much older 1gb USB drive and tried this again, without changing any steps. This time I am in the middle of the install and it seems to be working perfectly. I will update if it works but that would really make me question what is different between the USB drives

---

