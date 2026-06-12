---
title: "GRUB no longer boots anything"
date: 2010-07-24
forum: General Help
---

### Post by Dr_Rent on 2010-07-24
I am very much new to the world of Linux, and I just wanted to try out the popular Ubuntu flavor alongside my existing Windows 7 installation. Things worked well at first and I seemed to have the dual boot setup working, until I was notified that there were updates available and advised to install them. I did so, but somewhere along the way something went terribly wrong. When it asked me to restart, and I did, nothing happened. I was not offered the choice of OS, and the screen simply sat there, blank. I'm thinking there might be a problem associated with updating grub, but I don't know how to fix that. Any suggestions?

---

### Post by geoffjay on 2010-07-24
Load up a live CD, launch a terminal and enter:

sudo grub-install /dev/sda
sudo grub-update

This suggestion comes with no warranty, if you're not using sda for system installation you could make things worse.

---

### Post by bcbc on 2010-07-25
> **Dr_Rent said:**
> I am very much new to the world of Linux, and I just wanted to try out the popular Ubuntu flavor alongside my existing Windows 7 installation. Things worked well at first and I seemed to have the dual boot setup working, until I was notified that there were updates available and advised to install them. I did so, but somewhere along the way something went terribly wrong. When it asked me to restart, and I did, nothing happened. I was not offered the choice of OS, and the screen simply sat there, blank. I'm thinking there might be a problem associated with updating grub, but I don't know how to fix that. Any suggestions?

If you installed with wubi (installed from within windows), you may have installed grub to your drive MBR. I've noticed a few wubi problems recently - coinciding with a grub-pc update where it asks you to select where to install grub?

Anyway the fix should be simply to reinstall the windows boot loader - either from a windows repair disk (run 'fixmbr' for xp, or 'bootsect.exe /fixmbr' for vista/7). Or if you have an ubuntu cd you can use the lilo bootloader instead of windows. But if you have the ubuntu cd it's better to run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") so we can see for sure.

---

### Post by fruitmozhi17 on 2010-07-26
try to use live cd....

---

### Post by jagsb on 2010-07-26
> **bcbc said:**
> If you installed with wubi (installed from within windows), you may have installed grub to your drive MBR. I've noticed a few wubi problems recently - coinciding with a grub-pc update where it asks you to select where to install grub?

Anyway the fix should be simply to reinstall the windows boot loader - either from a windows repair disk (run 'fixmbr' for xp, or 'bootsect.exe /fixmbr' for vista/7). Or if you have an ubuntu cd you can use the lilo bootloader instead of windows. But if you have the ubuntu cd it's better to run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") so we can see for sure.

I am also an absolute beginner to UBUNTU and are also facing similar problem like dr rent. I used windows xp prof and UBUNTU 8.04 for some time untill i faced following problem. If i chose to boot windows, the windows restart the PC without completing the boot process. If i chose to boot UBUNTU, the terminal sh>grub appears am not able to do anything. I have now booted from live CD. I have run boot info script as advised by you and the results are as follows

```

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda7/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda8 starts at sector 245762433.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf3ebf3eb

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750   312,560,639   271,594,890   f W95 Ext d (LBA)
/dev/sda5          40,965,813   112,647,779    71,681,967   7 HPFS/NTFS
/dev/sda6         112,647,843   184,329,809    71,681,967   7 HPFS/NTFS
/dev/sda7         184,329,873   245,762,369    61,432,497   7 HPFS/NTFS
/dev/sda8         245,762,433   312,560,639    66,798,207   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       f2873789-a919-4ce4-885c-4b8d0f58a0ee   ext4                                     
/dev/sda1        229836639836359F                       ntfs                                     
/dev/sda5        4A98BDB698BDA0BD                       ntfs       D                             
/dev/sda6        B0240A172409E0E8                       ntfs                                     
/dev/sda7        52B876D0B876B1D9                       ntfs       New Volume                    
/dev/sda8        FA50-51A0                              vfat       New Volume                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options



================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu"


I am OK with reinstalling or upgrading to 10.4 , but cant do this as i cant create a CD cause i am booting from live CD. 

REQUEST HELP AT THE EARLIEST.

THANKS

---

### Post by vitothegreat on 2010-07-26
Use EasyBCD.

---

### Post by bcbc on 2010-07-26
> **jagsb said:**
> I am also an absolute beginner to UBUNTU and are also facing similar problem like dr rent. I used windows xp prof and UBUNTU 8.04 for some time untill i faced following problem. If i chose to boot windows, the windows restart the PC without completing the boot process. If i chose to boot UBUNTU, the terminal sh>grub appears am not able to do anything. I have now booted from live CD. I have run boot info script as advised by you and the results are as follows

<snip>

I can't see anything wrong from the bootinfoscript. The wubi says unknown filesystem ext4, but 8.04 would have been ext3 (so not sure if there is a problem there or not). I have no idea why windows is rebooting. I suggest creating a new thread since your problem is different to the Original Poster.

---

### Post by Dr_Rent on 2010-07-27
[LEFT]bcbc's fix worked out great. I did in fact install Ubuntu using Wubi, so I suppose this is a bug with the way the Wubi installer interacts with the Ubuntu software updater for grub? In any case, thank you for the advice.
[/LEFT]

---

### Post by bcbc on 2010-07-27
> **Dr_Rent said:**
> [LEFT]bcbc's fix worked out great. I did in fact install Ubuntu using Wubi, so I suppose this is a bug with the way the Wubi installer interacts with the Ubuntu software updater for grub? In any case, thank you for the advice.
[/LEFT]

The wubi installer works. It's the grub update. It's supposed to recognize wubi, and they even have a special version of various parts of grub to prevent this sort of problem, but for some reason, they just can't get it right.

I suspect that it's only affecting people who don't install wubi on their windows partition. e.g. your windows main drive is C: but you install wubi on D:   
Maybe you can comment on your particular setup and confirm this for me? Then I can report this to the devs.

Thanks

---

### Post by skooter1121 on 2010-07-27
If you are dual booting, Ubuntu and Win 7, and your PC is a recent Dell PC, with their software 'Dell Data Restore' installed, your MBR will be overwritten in 3 days or less depending on how often you reboot. Which results in 'no module name found' on restart. Use the boot cd listed previously, boot into Win 7, and remove 'Dell Data Safe'. Then repair MBR to boot  Win 7 first. Then in Ubuntu manage the MBR with startupmanager (sudo apt-get install startupmanager if you don't have it installed. Reinstall Grub2

-SK

---

### Post by colin.p on 2010-07-27
> **skooter1121 said:**
> If you are dual booting, Ubuntu and Win 7, and your PC is a recent Dell PC, with their software 'Dell Data Restore' installed, your MBR will be overwritten in 3 days or less depending on how often you reboot. Which results in 'no module name found' on restart. Use the boot cd listed previously, boot into Win 7, and remove 'Dell Data Safe'. Then repair MBR to boot  Win 7 first. Then in Ubuntu manage the MBR with startupmanager (sudo apt-get install startupmanager if you don't have it installed. Reinstall Grub2

-SK

Glad I found your post, I installed 10.04 X64 last night and when I got home from work today, I got the "no module name found".
I went to [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392) to get instructions on how to get 7 to boot up. Now tomorrow I will have to figure out how to re-install grub. If that doesn't work, I will do what I should have done in the first place and "nuke" the whole drive and install 10.04 and the heck with windows.

edit: just to add, I did get rid of Dell's Data Safe as well.

---

### Post by Trent T on 2010-07-28
Thanks, geoffjay!

I replaced the Xandros Linux side of my laptop with Ubuntu 9.10 about a month ago, and have had trouble with Norton AV on the Win XP side damaging my bootloader.  

Your first command, 
sudo grub-install /dev/sda

successfully reinstalled Grub2, and I am back in business.
For some reason, the command 

sudo grub-update

was not recognized-- But I'm not arguing with success!:D

Thanks again,

Trent T
==============

> **geoffjay said:**
> Load up a live CD, launch a terminal and enter:

sudo grub-install /dev/sda
sudo grub-update

This suggestion comes with no warranty, if you're not using sda for system installation you could make things worse.

---

### Post by geoffjay on 2010-07-28
Glad to hear that you got it working, upon reading that I realize that I mixed up the update command, it is actually update-grub. That's useful to know if you want to change any settings in grub2, eg. resolution for startup, and adding another OS to the list.

---

### Post by Dr_Rent on 2010-07-30
You are absolutely right, bcbc; that's the setup I'm using. I'm sticking with the Windows bootloader for now, since it's not giving me any problems.

---

