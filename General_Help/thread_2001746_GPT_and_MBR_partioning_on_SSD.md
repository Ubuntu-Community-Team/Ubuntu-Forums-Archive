---
title: "GPT and MBR partioning on SSD"
date: 2012-06-11
forum: General Help
---

### Post by diiggidy on 2012-06-11
I just bought a new SSD that I plan to install Ubunutu to but have run into a few problems. In my computer right now I have an MBR partitioned SSD running windows 7, along with a 500gb HDD. I've been researching quite a bit, and it seems that GPT is recommended for SSD's in ubuntu. However, my main question is if it's possible to dual boot an MBR SSD and GPT SSD from the same bootloader? Will I be able to put both OS's in GRUB and simply pick what I want to run and that's it? Or will I have to switch between UEFI and BIOS modes? I know that GPT is designed to run in EFI, but is it also able to run in BIOS mode?

Also, I think I have the SSD alignment stuff down but have yet to actually partition. I know the easiest way the do MBR is probably load the live CD and use fdisk to partition. But if I choose to do GPT which is recommended what's the best way to do this? I read that Gparted is not so user friendly, and gdisk doesn't come on the live CD.

Thanks

---

### Post by Cheesemill on 2012-06-11
I use my GPT partitioned SSD along with an ms-dos partitioned HD in a dual boot with no problems, GPT works fine with a BIOS boot as long as you create a 2MB BIOS boot partition (type EF02) on it.

To set up the partitions before installation just use the Ubuntu live CD and run gdisk to create your partitions.

---

### Post by diiggidy on 2012-06-11
So the BIOS boot partition will go on the SSD with ubuntu correct? And my problem is that the Ubuntu live CD I have does not come with gdisk and won't allow me to install

---

### Post by Cheesemill on 2012-06-11
Correct.

You can install gdisk when running the Live CD:
```
sudo apt-get update && sudo apt-get install gdisk
```

For reference here is my SSD partitioning:
```
root@quantal:~# gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.4

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 125045424 sectors, 59.6 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 5F162C6C-7C86-4A8C-BD06-9035051937FE
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 125045390
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            6143   2.0 MiB     0700  BIOS boot partition
   2            6144        83892223   40.0 GiB    0700  root
   3        83892224       125045390   19.6 GiB    0700  home
```

---

### Post by Redblade20XX on 2012-06-11
For additional references: [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

-Red

---

### Post by diiggidy on 2012-06-11
I ran the command to download gdisk and everything looked like it was downloading correct, but then when I try to use it I get a message saying it is still not installed. When installing I did get the message "E: Some indexfiles failed to download. They have been ignored, or old ones used instead." Any suggestions?

---

### Post by diiggidy on 2012-06-11
Since I'm running the live CD, do I have to specify where to download gdisk for it to use?

---

### Post by oldfred on 2012-06-11
I use gdisk to list partitions, but have used gparted to create my gpt partitioned drives. Older versions of gparted did not start at 2048, but new versions do. 

gparted
 Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning. You use set flags - bios_grub to convert bios_grub partition to ef02 which only shows in gdisk.

---

### Post by diiggidy on 2012-06-11
When I try to make the boot partition in Gparted, it will not let me set flags. I should create a 2mb, unformatted partition for the boot partition correct? When I do this there is no option to set a flag, and once I create it the manage flags buttons won't highlight. I am booting from the 11.10 live cd as I couldn't get the latest versions GUI to boot properly

---

### Post by oldfred on 2012-06-11
A bios_grub is not a boot partition, just an unformated partition for core.img from grub2. You probably cannot create a boot flag on a unformated space. I can be 1MB (or even less as all it is for is core.img). But 1 or 2MB is for the new partition spacing for large drives and SSDs.

I do not use a /boot partition and in gpt you are not supposed to create a boot flagged partition except for efi. With gpt gparted, it uses the boot flag to create a efi partition (ef00), but that is not the same as a boot flag in MBR.

---

### Post by diiggidy on 2012-06-11
So just to make sure this is what my partitioning should look like.

/dev/sda (Windows 7)
100 MiB ntfs
119.14GiB ntfs

/dev/sda (Ubuntu)
2MiB unformatted (start sector 2048)
34GiB ext4 (/)
6GiB ext 4 (/home)

/dev/sdc (HDD)
328GiB ntfs (start sector 2048)
106GiB ext4 (/data)
4GiB linux-swap
27.76 GiB unallocated

Also, I was wondering if I should consider making a partition for /var and /tmp? I have 16gb of RAM, and was thinking about putting them on a ramdisk but I don't want it to use too much. Also, it's my understanding that I can store appdata and userdata stuff in the /home and then all my user documents such as music and videos in /data, I just don't know how to accomplish this. Thank you for all your help

---

### Post by oldfred on 2012-06-11
If you are using Windows and Ubuntu on the same drive with gpt you have to boot with UEFI. (or is Ubuntu on sdb?)

I like to keep each drive independently bootable. Or all required folders and the MBR on the same drive. So if a drive fails I can boot another drive. It may give errors about not mounting data partitions from the failed drive but should still boot. I keep /home inside / (root) but have very little data in /home. All data is in a shared NTFS data partition for the data I may want in Windows and in a ext3 data partition for all my new data as I use XP almost not at all now.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

```
fred@fred-Precise:~$ sudo df -h
[sudo] password for fred: 
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd3        28G  8.2G   19G  31% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           791M  1.1M  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  124K  2.0G   1% /run/shm
/dev/sda1        55G   36G   20G  64% /mnt/cdrive
/dev/sdc2       100G   29G   72G  29% /mnt/shared
/dev/sdc6        97G   41G   51G  45% /mnt/data

```

My new SSD is sdd, sda is my old XP, and sdc has my data partitions.

---

### Post by diiggidy on 2012-06-11
I'm sorry, yes Ubuntu is sdb not sda

---

### Post by diiggidy on 2012-06-11
I'm confused how you keep /home inside of root, could you explain this more? And if I understand this correctly, I am simply linking the folders in /home to the files in /data? Is this all that code is doing is making this linking quicker or am I missing something?

Also, if possible I would like to be able to have my HDD interchangeable between Windows 7 and Ubuntu. I would like to be able to mount and have all my music, movies, and files on each operating system automatically. If I just partition the whole HDD as ntfs will I be able use it like this? Also, I have some games installed to the HDD on Windows right now, will this be a problem? I could create another partition to keep all my music and files on, and use this as /data if that would be better?

---

### Post by oldfred on 2012-06-11
I do not know about games, but you can link a folder in a NTFS partition into /home. Linux has to have Linux formats for system partitions but can use NTFS for data. Linux partitions let you set ownership & permissions at a detail level. With NTFS you only set a default set of permissions when mounting it.

So I replace the folder in /home that is Music with a link. The link is from where I mount the NTFS partition in Ubuntu, I use /mnt/shared for NTFS and /mnt/data for other data. I only have folders in each data partition's top level. And each folder is linked into /home. Then my /home really only has some small amounts of data and the hidden .files & .folders. And any .folder that starts to get a lot of data may get moved also.

I use /mnt/data, but you can use /media/data. The main difference is /mnt will not show in Nautilus' left panel. With /media it will show. But if linking all the folders it can get confusing if shown twice in differnt places. I can drill down and find the mount but it is not directly shown.

---

### Post by diiggidy on 2012-06-12
Okay I think I have it all down now. I'm at the "Installation Type" screen and have one more question. Which device and which partition do I want to install the boot loader too?

---

### Post by oldfred on 2012-06-12
Computers can only boot from a MBR (unless you have the new UEFI). So you want to install the grub2 boot loader to the MBR of the drive you install Ubuntu into. Then set BIOS to boot from that drive.

You do not want to install to a partition except in unusual cases. Grub2 does not like to be installed to a partition and will complain. It will be less reliable if in a partition and you have to be booting from some other boot loader that is in the MBR.

sda, sdb, sdc etcwhich are drives,  not sda1, sda2 sdb3 etc which are partitions.

---

### Post by diiggidy on 2012-06-12
So since i'm installing Ubuntu to sdb, simply installing the bootloader to /dev/sdb will do the trick?

---

### Post by diiggidy on 2012-06-12
I'm unsure how to install the bootloader to the MBR. I attempted to install it to /dev/sdb but it said there was an error. You stated that I cannot install it to a partition, so I don't know where else to choose from.

---

### Post by oldfred on 2012-06-12
We seem to be seening more of the cannot install issue. Not sure why. A few BIOS do have locked secuity BIOS setting to prevent writing into the MBR which you should check.

If you install to a partition it will still not boot. Did you have a bios_grub partition, unformated with bios_grub flag or in gdisk ef02? Not having that can cause issues also.

You can install to sdc also but it really should be in sdb. Either way set BIOS to boot from drive you install to.

---

### Post by diiggidy on 2012-06-12
I have the unformatted bios grub partition, but I still don't understand how to put the flag on it

---

### Post by diiggidy on 2012-06-12
I got Ubuntu to install, and GRUB is working and was auto-configured to include windows 7 as well. However, when I choose to boot into Ubuntu, all I get is a black screen. When installing, I had to use the nomodeset option from the splash screen to get the GUI to appear when booting the live cd. It appears that this is still the problem, but I don't know how to fix it now as I don't have the nomodeset option anymore.

---

### Post by oldfred on 2012-06-12
You have to add it to the grub menu entry.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

If you are not adding a propritary driver like the nVidia then you can permanently add the nomodeset entry in /etc/default/grub, but post back for details, if thats what you want.

---

### Post by diiggidy on 2012-06-12
Okay great. I was pressing shift and nothing was happening but the e worked. I got Ubuntu booted fine now and the Update Manager has popped up. However, my wired connection is not working. While running the live CD the internet was working fine, but now that i'm running the installation it will not connect to the internet. When I try to connect to the wired connection, it says "Disconnected". Also, will the nVidia driver be installed from the Update Manager, or will I have to get it off the nVidia website?

---

### Post by oldfred on 2012-06-12
Do not know why wired connection may not work especially since it worked on liveCD.

If nVidia, Ubuntu has one designed to work with Ubuntu. If you download the nVidia one directly it may be one version newer but you have to recompile on every update.

---

### Post by diiggidy on 2012-06-12
I still cannot figure out the internet issue. When I boot into Ubuntu, the wireless connection icon keeps flashing up and down like it's searching for a wireless network, and then a popup shows that says "Wired network Disconnected- you are now offline"

---

### Post by oldfred on 2012-06-12
I am in gnome-panel, so not sure exact command in Unity. But you want to open the Network Connections application and look at the wired connection. Click on it and see what settings it has. Under IPv4 settings it should be automatic (DHCP). Are you connecting to a router or directly to a cable modem? Cable company used to take 15 or 20 minutes to connect to a new device, your router should be immediate.

---

### Post by diiggidy on 2012-06-12
ipv4 was set correctly. I am connecting to the router, which is also the modem i'm pretty sure. Should I try resetting the router and my computer?

---

### Post by oldfred on 2012-06-12
Often one of the first things I try when network has issues. Shut computer down normally and then power cycle the modem, see if its lights come back normally. One should be the ethernet connection from the computer when you restart it and it should flicker with activity.

---

### Post by diiggidy on 2012-06-12
I reset the modem and computer and am still having the same issue. Also, when I boot into Windows I connect with no issues

---

### Post by diiggidy on 2012-06-12
Is it possible that I need to install the drivers for my ethernet port on my motherboard myself? Except this wouldn't make sense because it worked using the live cd

---

### Post by oldfred on 2012-06-13
I only know basics on Ethernet issues. You would do better to post a new thread with the type of Ethernet card/chip and your issue of not connecting.

Include this info so others can help directly:

 sudo lshw | grep -m 1 -A 25 "*-network"
lspci
#but I do not like to post HWaddr or Mac address as it is unique and someone can spoof yours
ifconfig eth0

#Note: Do not mix network interface file method and gui Network Connections as they can conflict
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
dmesg | grep eth0

If a driver was on CD it should have installed, but may also be possible to update from CD into install.

---

### Post by diiggidy on 2012-06-14
I figured out the issue with the ethernet and I have everything up and running fine. However, I just opened Gparted to make sure where I put my /data partition and realized something went wrong. I created a 94gb partition on my HDD for /data, but when I installed somehow it was mounted as /boot. I didn't specify where to put /boot because I thought it wasn't advised for SSD's. But, during install the partition I intended for /data is actually /boot now. Is there anything I can do?

---

### Post by oldfred on 2012-06-14
Technically you can move the boot files back into / (root), edit fstab (remove /boot entry) & reinstall grub. But unless you understand the details, it might just be easier to reinstall.

I did move boot files to a /boot years ago and changed everything around and it worked. But literally 5 minutes later I realized I wanted a grub (back with grub legacy) only partition for booting multiple installs and moved everything back.

---

### Post by diiggidy on 2012-06-14
Can you explain exactly what /boot is? Also, why is it recommended not to have it so SSD's and why's it exist if you can get away without it. Since I do have a partition that is mounted at /boot now on my HDD, can I just shrink it and create a different one and mount it as /data?

---

### Post by oldfred on 2012-06-14
All the folders in Linux can be different partitions. Back in the early days most of the partitions were on separate partitions or drives as the drives were small. Most installs were servers and sometimes you had to isolate certain functions.

In recent times you may need a /boot with an older PC with a BIOS boot limit of 137GB. Grub legacy could not read RAID, LVM, some formats, nor encrypted partitions, so you needed a separate /boot. Grub2 can read most directly with add in modules, but some may still want a separate /boot. 

For most desktops a separate /boot is not required and just complicates repairs and adds some space management issues.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

I have not heard /boot is recommended for SSDs. But with gpt partitioning you do need a bios_grub partition for grub2 to install correctly.

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

---

### Post by diiggidy on 2012-06-14
I'm confused how the partition I created for /data was instead mounted as /boot. I did not specify a place for /boot when installing and thought it would just take care of itself but it didn't.

I have a partition on my HDD for Windows that is formatted as ntfs. It is possible for me to read and write to this partition in Ubuntu correct? If I were to make a much larger partition out of this windows one, could I simply mount this as /data in Ubuntu and then link to it from home? So basically I have one big partition that I use to store my files in from Windows and Ubuntu. And this won't screw anything up in Windows? Also, I plan to upgrade Ubuntu so it would be best to create a separate /home folder correct?

So my partition would look something like this..

sdb
bios_grub partition
/ (root)
/home

sdc
/data (Also for use in Windows)

I'm also planning on mounting /tmp and /var/tmp to RAM since I have 16gb to spare. Lastly, what would be the easiest way to reinstall with these new partitions? On my last install, I couldn't get 12.04 live cd to boot so I went back down to 11.10, installed it, and then updated to 12.04 but would prefer not the do this again. And is there any way I can make sure that I don't mount a /boot somewhere accidentally again?

Thanks a lot for all your help

---

### Post by diiggidy on 2012-06-20
Any thoughts?

---

### Post by oldfred on 2012-06-20
I always partition in advance with gparted either from LiveUSB or a separate download of the newest gparted liveCD.

If partitions are created in advance then you use manual install to choose which partition is / and which is /home and what formats. If swap does not exist you may want it but with lots of RAM you may never use it. Some suggest just having a little swap speeds boot as it has to search and not find it, others say with lots of RAM they never use swap, so they do not create it. I would not put swap on the SSD anyway.

This is my SSD, but I hope to get a new UEFI system and may move it, so I also created an efi partition as well as the bios_grub. I just install with two / partitions so I can test the new version while primarily booting current.

```
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sdd: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  316MB   315MB   fat32                 boot
 2      316MB   317MB   1049kB                        bios_grub
 3      317MB   30.2GB  29.9GB  ext4         Precise
 4      30.2GB  60.0GB  29.9GB  ext4         Quantal

```

All my data is in data partitions on other rotating drives, but I keep /home inside root.

---

### Post by diiggidy on 2012-06-20
So since my first install got screwed up with the /boot, it would just be easiest to boot the live CD and repartition the drive? Repartitioning does "remove" everything on the drive correct?

Also, by keeping /home inside of root do you just mean that you didn't create a /home partition so its simply inside of root? And if I want to mount /tmp and /var to RAM, do I have to do anything before installing, or do all of this after installation.

Lastly, when I tried loading the 12.04 live cd I could not get it to boot right. I'd get the splash screen with the keyboard on the bottom, but it would freeze after that. I'm pretty sure it's because of the Nvidia graphics and nomodeset adjustment I need, but I don't even get to the screen to switch to nomodeset on the 12.04 cd. Do you have any suggestions? It would be much easier just to install straight from the 12.04 cd for me. Thanks

---

### Post by oldfred on 2012-06-20
To get option screen on liveCD you have to hit any key as soon as it starts, when the keyboard & user icons appear at the bottom of the screen.

The install process has not changed much, so this can be still used as a SSD (or flash) install guide.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

No, I did not create a separate partition for /home as mine only has the hidden user settings used a lot by the system. All data is in /mnt/data in a partition on the rotating drives. Even with .wine for Picasa, my /home is about 1GB and most of that is .wine.

---

### Post by diiggidy on 2012-06-21
Okay, I have reinstalled Ubuntu 12.04 and everything is working well I think. I just want to make sure I've done everything correctly. First, here's the gdisk of my SSD and I just want to know if it's aligned correctly?
```
sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 117231408 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 47E754A4-D350-4708-8EDD-71A6667AF957
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117231374
Partitions will be aligned on 2048-sector boundaries
Total free space is 3981037 sectors (1.9 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            6143   2.0 MiB     EF02  
   2            6144       104863743   50.0 GiB    0700  
   3       104863744       113252351   4.0 GiB     0700 
```
Here's my fstab, I'm just wondering if everything is done correctly? I've mounted a few things to RAM; is there anyway to check if these actually are in the RAM? Also, have I enable TRIM correctly for the SSD? I enabled it on root and /home.
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=23e087ae-b2a3-4e37-8315-4f824e914b3a /               ext4    errors=remount-ro,noatime,discard 0       1
# /data was on /dev/sdc1 during installation
UUID=F4547EC3547E87DE /data           ntfs    defaults,umask=007,gid=46 0       0
# /home was on /dev/sdb3 during installation
UUID=d8fbe296-6166-4005-9c2f-8c1de23bea94 /home           ext4    noatime,nodiratime,discard,defaults        0       2
none /tmp     tmpfs nodev,nosuid,mode=1777 0 0
none /var/tmp tmpfs nodev,nosuid,mode=1777 0 0
none /var/spool tmpfs defaults,noatime,mode=1777 0 0
none /var/log tmpfs defaults,noatime,mode=0755 0 0
```

Lastly, how can I check to see if journaling is enabled on the SSD?

---

### Post by oldfred on 2012-06-21
This says you do not also need nodiratime.

How to Tweak Your SSD in Ubuntu for Better Performance
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)
See comment: There’s no reason to use BOTH noatime and nodiratime, using noatime implies nodiratime.
[http://techgage.com/print/enabling_and_testing_ssd_trim_support_under_linux](http://techgage.com/print/enabling_and_testing_ssd_trim_support_under_linux)

I do not not know how to check journaling. The command to turn it off was in previous post.

---

