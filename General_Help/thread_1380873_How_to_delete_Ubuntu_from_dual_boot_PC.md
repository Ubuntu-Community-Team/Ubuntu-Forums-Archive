---
title: "How to delete Ubuntu from dual boot PC?"
date: 2010-01-14
forum: General Help
---

### Post by abcuser on 2010-01-14
Hi,
I have installed Windows XP on computer and then Ubuntu 9.10. This two OSes are in dual boot and grub2 is boot manager.

Because [I have problems with Ubuntu accessing network](http://ubuntuforums.org/showthread.php?t=1360032) I would just like to remove Ubuntu from this PC and then assign disk space to Windows.

Is it save to only delete Ubuntu partitions, ext4 partition and swap partition, from disk using Gparted tool? I am afraid that Grub will also be deleted and so I would be unable to boot into Windows XP.
Regards

---

### Post by john newbuntu on 2010-01-14
Before giving up on Ubuntu, could you one last time uninstalling and reinstall the dhcp3-common and dhcp3-client packages from synaptic and see if your networking gets better?

---

### Post by arubislander on 2010-01-14
I doubt that'll help... 

Anyhow... to safely wipe Ubuntu it's best if you use a Windows Recovery CD to restore your Master Boot Record to what Windows expects it to be. Then you can reformat the Ubuntu partition if you wish using any means you find convenient.

---

### Post by abcuser on 2010-01-14
@arubislander, if I understand correctly boot process from turn on PC to fully start OS:
1. power on
2. BIOS turns on and searches MBR (master boot record) on disk
3. MBR loads Grub which is installed on Ubuntu partition (ext4)
In this case I could solve the problem using Windows XP boot into Command Prompt with Admin righs and execute FIXMBR command this command overwrites MBR with default Windows commands.

Grub could also be installed on MBR (don't know if this is possible). In this case I should do nothing because from Grub I could select Windows. But I am not sure that Grub is really installed on MBR and why, because there are config files on Ubuntu partition. So most probably there is just some part of GRUB program installed on MBR that calls full grub from ubuntu partition, is it?

Actually I don't know where Grub is installed. Is it on Ubuntu partition or on MBR?

@john newbuntu, I don't think this will help, because I think it is ISP vendor problem not assigning new IP address for my computer when I reboot to another OS, even if I force DHCP server to renew IP address. I just get DHCP server timeout error. But when DHCP settings for IP address expires, then ISP assigns new IP address and I can change IP in my desired OS (Ubuntu or Windows). So this looks a mess in my ISP not in my OS.

But don't worry I will not give up on Ubuntu. I have been using Ubuntu for years since Ubuntu 6.10 Edgy Eft and all versions since Edgy (Festy, Gutsy, Hardy, Ibex, Jaunty, Karmic). I have three computers at home. On one is installed only Ubuntu Karmic. On one I have dual boot with Windows XP (this is the computer I am having problem with assigning IP address, so I would just like to wipe out Ubuntu - I need Windows XP, some special programs that are not available on Ubuntu and I don't want to mess with Wine either) and the third computer is my notebook where I use Windows XP as host operating system and using Ubuntu as VirtualBox guest.

Regards

---

### Post by john newbuntu on 2010-01-14
Right. MBR is too small to hold the entire GRUB and so only a tiny portion of it resides there.  The rest is in another partition (your Ubuntu partition /dev/sdx in your case)

What arubislander is suggesting is to wipe out your entire Ubuntu partition and reformat it as say, NTFS so that you can either extend your existing windows NTFS partition or create a  new one.

As far as the MBR itself goes, you will have to wipe out GRUB using the fixmbr command in the xp recovery CD that will help you boot windows normally.

Glad abcuser that you are still with Ubuntu/Linux.

---

### Post by Brasileiro on 2010-01-22
Hi 

I had a hard time to find out how to remove the dual boot from my PC, I just wanted the XP only, and at the end I've found this [http://ubuntuforum-pt.org/index.php?topic=38429.0](http://ubuntuforum-pt.org/index.php?topic=38429.0)
as the best and simplest solution (witn no XP CD installation, and no fixmbr command, that didn't work for me, by the way):

Go to My computer->properties->advanced->Initialization->Configuration->Edit
(Note: I'm not sure if these are the names in English, yet I hope you get there).

It will open the boot.ini file, that in my computer was

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

Remove the last line (C:\wubildr.mbr = "Ubuntu") , click ok, and it should work. It did for me!!!


You can check the initialization dialog box the option standard OS, where it should show both OS before you change the boot.ini file.  And only Windows after the modification.

Restart the computer and it should go straight to windows.

I hope it helps


Valeu!

---

### Post by abcuser on 2010-01-23
Brasileiro,
_you were not using dual boot!_ You most probably installed Ubuntu using Wubi. So you did the following:
1. started Windows
2. inserted Ubuntu CD
3. installed Ubuntu
In this case you have installed Ubuntu inside Windows. Wubi just installs Ubuntu on the Windows partition in one file inside Windows NTFS file system. Wubi adds Ubuntu to Windows boot menu, so it is logical that:
1. FIXMBR didn't solved the problem in your case, because you have overwritten the exactly the same boot loader you already had, so you have no change noticed.
2. Removing boot option from c:\boot.ini file (the same as your My computer etc GUI option) did remove Ubuntu from boot menu, but it didn't remove Ubuntu from your system.

If you really want to remove Ubuntu in your case you need to go to Windows Control Panel and Add-Remove program and search for Ubuntu and uninstall it just like any other Windows application.



But in my case _I had dual boot_. I did the following:
1. Install Windows XP
2. Shutdown Windows!!!!! --> very important
3. Inserted Ubuntu CD and installed Ubuntu as dual boot.
So in my case Windows boot loader was wiped out of disk master boot record and installed some basic part of GRUP (Linux boot loader) in it and also like "john newbuntu" wrote in this thread executed GRUB from Ubuntu partition.

So in this case it does help (I have done this and it works) to insert Windows CD and start computer from CD. Then select Recovery Console, enter Administration password and execute command FIXMBR. This command overwrites GRUB in disk master boot record with Windows boot loader. Windows boot loader is then capable of staring only Windows.

So far only boot loader was removed. To free disk space (remove Ubuntu from disk and free disk space) I needed to start computer with [GParted software](http://gparted.sourceforge.net/download.php) partition tool to physically remove Ubuntu partition and to enlarge Windows partition to occupy newly freed disk space.

Regards

---

### Post by Brasileiro on 2010-01-23
Thanks abcuser


Actually I did use the wubi version that left this dual boot initialization. I´ve read a lot about the fixmbr, which I did try, but didn't work, of course it shouldn't because the problem was in the boot.ini.  

Yet I think it is a nice discussion, because it seems to me that more people are confused about this, specially those that did try the Windows CD installation and got frustrated.  

In summary, it seems something like:

1-Your installation is Wubi: fix the boot.ini.
2-Your installation is regular: use the Windows CD installation with fixmbr command.


By the way, Ubuntu Wubi version is already removed from my computer, although I wish to install the regular version, but I've got stuck in GPARTED, that didn't recgonize all the partitions made by Windows (another issue...).


Anyway, thanks, and any other comment is extremelly welcomed



Obrigado

---

### Post by abcuser on 2010-01-24
> **Brasileiro said:**
> By the way, Ubuntu Wubi version is already removed from my computer, although I wish to install the regular version, but I've got stuck in GPARTED, that didn't recgonize all the partitions made by Windows (another issue...).

Hi,
just to make clear what [Wubi](http://wubi-installer.org/) is - it is just a simple tool that installs Ubuntu operating system inside Windows and in this way behaves just like any other Windows application (it can be removed from Add-Remove Programs window etc). Wubi also installs Ubuntu inside Windows NTFS partition. Actually whole Ubuntu is stored just in one big file. Wubi was developed for non-geeky computer users, required computer knowledge is for level of installing any other Windows application. So in this case it is simple to install and also uninstall (Windows Add-Remove program) if desired.

Installing Ubuntu (or any other operating system) as dual boot or multiple boot if more then two operating systems are installed on one computer is basic design on having multiple operating systems on one PC. Every operating system is installed on separate partition and you select which operating system you would like to boot from boot menu.

If you install Ubuntu as dual boot then Ubuntu is installed on separate partition and file system is not NTFS (Windows file system), but ext4 (Linux file system - you can even change file system to something else, but for home use you need some good reason to do so).

To install Ubuntu as dual boot it requires basic knowledge of understanding disk partitions, so you need to be little bit geeky.

But in the case of Ubuntu even this process should not be difficult, because Ubuntu should recognize Windows partition, suggests to shrink it and on the shrunk part of newly freed disk space suggest to install Ubuntu partition. So partition part (GParted) should be left untouched if you don't have any special need of changing this default option. For example you can decide to install Ubuntu on one partition and /home directory (just like Windows Vista /Users directory) on separate partition - so to have system on one partition and user data on another. This requires some addition knowledge about partitioning. But most of the people (also myself) just accept default partition option and continue to install.

Advantages/disadvantages using Wubi vs. dual boot:
1. Wubi is more simple to install/uninstall for non-geeky users
2. If you use Wubi way of installing Ubuntu and Windows gets corrupted like a virus infection, you can have a trouble in Ubuntu, because Ubuntu is just a file inside Windows.
3. Ext4 is faster file system then NTFS and it also gets way less fragmented over time, so performance can be better.
4. If you have low knowledge about security, you will get problems on Windows very soon and so your data on Ubuntu (using Wubi) can get security risk too. Less security risk on dual-boot.

@Brasileiro, you wrote that Ubuntu did not recognized all Windows partitions. Are you sure that in your case Windows uses more then one partition? By default it uses only one partition. Did you manually partition disk space for Windows? Can you post print-screen of disk partitions or at least write what partition do you see and what you think you should see instead.

The basic disk partitioning system on PC is like this (it can also be some other options, but I always do the following). Just to make more clear assume you have only Windows on your system and you would like to have C: (for example for Windows system files) D: (for programs) and E: (for data). C:, D: and E: are called logical partitions.

Disk partitions:
1. create primary partition and format it using NTFS file system -> on this partition you will install Windows and partition will become known under Windows as C:
2. create extended partition (you need extended partition if you would like to create any addition logical partitions like D: or E: etc).
3. inside extended partition you can create several logical partitions, in this case you need two logical partitions. One of logical partition will become known under Windows as D: and another will become known as E:. You can format this two logical partitions using NTFS file system before Windows installs or you can do this latter after Windows is installed.

Back to dual boot. If you installed Windows as default install you have only primary partition that expands to the whole disk. Ubuntu installed using GParted tool shrinks primary partition (Windows) and creates extended partition and adds logical partition to this extended partition. Then logical partition gets formatted with ext4 Linux file system and Ubuntu installed on this logical partition.

@Brasileiro, I hope I have clarified how disk is organized. I need more info about your existing partitions to make it possible to help you, or someone else to help you. But if you don't have any good reason (like to learn about partitioning) to use dual-boot, just use Wubi and your life will be less complicated.

Hope this helps.

---

### Post by kermit99911 on 2010-01-25
Just a quick note about WUBI ... If you use ADD/REMOVE program, then its only Ubuntu that is removed. The wubi boot is still there on your system, as you will find out when you reboot. You will still get the startup OS selection screen even though you haven't got Ubuntu any longer! I noticed that in the Ubuntu folder on C:\ there is an exe program 'uninstall wubi'.. I would suggest running this before going to the Add/Remove folder. If that does not work, then it's the boot.ini that has to be edited as noted elsewhere in this thread

---

### Post by utnu on 2010-05-06
an easy way to find boot.ini is to run WinXP's Search function, and search for boot.ini in C drive.
The only trick is to be sure the checkbox is checked:
[&#8730;] Search hidden files and folders

---

### Post by abcuser on 2010-05-07
boot.ini file in Windows is located at C:\boot.ini path. This file is hidden by default, because it is system file and incorrect settings can cause Windows to not boot at all. I suggest to search the Google on how to edit boot.ini in Windows before changing it manually - it is not hard to change, but be sure you do it correctly.

---

### Post by radicalbehavioristman on 2010-05-23
> **kermit99911 said:**
> Just a quick note about WUBI ... If you use ADD/REMOVE program, then its only Ubuntu that is removed. The wubi boot is still there on your system, as you will find out when you reboot. You will still get the startup OS selection screen even though you haven't got Ubuntu any longer! I noticed that in the Ubuntu folder on C:\ there is an exe program 'uninstall wubi'.. I would suggest running this before going to the Add/Remove folder. If that does not work, then it's the boot.ini that has to be edited as noted elsewhere in this thread

If you want to delete Ubuntu from the boot menu there is a simple tool that I have used. It is called EasyBCD. You can download it from many places. I prefer CNET. I downloaded it from a site I won't mention and it downloaded spyware. I am having my own problems installing the new release of Ubuntu 9.10 inside Vista.

---

### Post by avdistribution on 2010-09-06
*just to make clear what Wubi is - it is just a simple tool that installs Ubuntu operating system inside Windows and in this way behaves just like any other Windows application (it can be removed from Add-Remove Programs window etc).*

Not true in my case. I installed ubuntu with wubi on an XP Pro machine and though ubuntu shows in "programs" and there's no separate partition for it, there's no sign of it in add/remove programs either. 
The boot screen shows both os, which suggests it installed a true dual boot. 
Being new to Linux, I specifically chose this way of doing it to make a future uninstall easier but it really isn't. 
So if anyone has a **definitive** answer on how to remove ubuntu from a machine with XP Pro and ubuntu/wubi but no separate partition or Windows add/remove option, I'd love to hear it.

---

### Post by sh0bhit on 2010-09-06
unfortunately i removed earlier ver of windows and had wubi installed in it..now while booting it shows ubuntu but its not running through it :(

can anyone solve my problem to remove wubi

---

