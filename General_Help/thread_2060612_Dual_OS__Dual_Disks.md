---
title: "Dual OS // Dual Disks"
date: 2012-09-20
forum: General Help
---

### Post by Scytah on 2012-09-20
Hi guys,

I am using Asus Zenbook, and I have 2 Disks in my PC.

1 HDD (Windows7 installed)
1 SSD (Free)

[IMG]http://i48.tinypic.com/2dr6lj7.png[/IMG]

I was trying to install Ubuntu on SSD alone. I used the "Something Else" option during install. But maybe I did something wrong, and winbootloader did not show me Ubuntu as option, but it loaded Win7 instantly.

So I am asking can you help me installing Ubuntu?
I actually no idea of using "Something Else"

PS: I am going to Install Ubuntu again...

---

### Post by oldfred on 2012-09-20
Even though a different brand, it seems like one of these.

 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)


You probably need to remove the RAID settings as that interferes with the Ubuntu install. LIveCD does not work with RAID and your RAID is just to cache Windows and speed it up somehow. If full RAID then you need alternative installer.

You also are showing an efi partition, so system is UEFI. You need to install Ubuntu 64 bit in UEFI mode. When you boot liveCD or USB, it should offer two choices, one efi and the other legacy/AHCI or whatevey your UEFI boot menu  sees it as. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

---

### Post by Scytah on 2012-09-20
It's like u are speaking in French... I am soory but I am not that pro Computer User. I really need to know step by step what to do.

Because last time, I ****** up my system with trying to change windows boot loader. And I cannot repair it, because I dont have any repair disk(no CD/ROM reader/writer).

So..

---

### Post by oldfred on 2012-09-20
You then should have a full image backup & a repair USB disk.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

With something else you have to create partitions in advance. Are you just creating the partitions on the SSD or having data or /home on the rotating drive?

After you have done backups do this to clear the RAID meta-data on the drive.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

When you boot 64 bit Ubuntu liveUSB from UEFI menu, you get two choices one is UEFI and the other BIOS/MBR. If Windows is in efi mode which it looks like then you must install Ubuntu in efi mode.

Because you are using a SSD, most SSD installs just have / (root) with /home on the rotating drive  or root including /home but all data on a rotating drive in data partition(s), then /home just has the hidden user configuration files. Usually new systems have lots of RAM so swap may not even be required, but many suggest some and put it on the rotating drive also.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited and if total less than about 30GB just use / not separate /home.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
I

---

### Post by Scytah on 2012-09-20
I may use this method, if I can create a Working Repair Disk on USB...

I had another Win7 PC with CdRom Writer I made a Disk and Make a USB with that disk. But it does not work.

"Version is not same with this one"

WTF? You are both Win7 Preminium-TR... I really need to find a right repair disk first***

BTW;

I am going to do partitions like this;

the HDD (/dev/sda) gets /boot
the SSD (/dev/sdb) gets /, swap, /home

---

### Post by oldfred on 2012-09-20
The version just has to be 32bit or 64 bit Windows 7. Any other version differences should not matter.

I have run chkdsk from a Windows 7 repairCD on my XP, so some repairs should not matter. 

/boot is usually very small and you can just keep it in / (root). Some newer systems may need it if creating a very large / over 100GB. But better to have smaller / and separate /home.

Swap does not really matter. The life of SSDs now is such and your actual use of the swap partition is low, so having swap on SSD is not critical but you will rarely use it. Only if editing videos may you run out of RAM if you have 4GB or more.

---

