---
title: "Boot/Grub error"
date: 2010-12-12
forum: General Help
---

### Post by Malcolm1044 on 2010-12-12
(I am a very, VERY basic computer user. I'm acquainted enough with internet usage, but know very little about computer prompting, so apologies up front if my questions seem basic)


I am having a problem with booting my computer. I have an Acer Aspire 5315, with two disks on it. I have Windows Vista installed on my C drive. To provide a little more information, I believe the version of Ubuntu my computer is running is 10.10, and it does have a CD/DVD reader. I decided to install Ubuntu on my D drive. This was done successfully, and I was able to use Ubuntu for the first couple of tries. During the last use, it required me to restart my computer after downloading updates. 

I am now stuck on a prompt screen with the following message:


[I]error: no such device: 528e577e-9e02-44f8-81d9-f1201ec9d808.
grub rescue>[/I]



After reading through various support threads, I attempted the following:

*grub rescue> ls*



which returns:

*(hd0)*



I am unclear as to how to get to the next step, and I can't access my computer until I resolve the problem. Any help would be very greatly appreciated..

---

### Post by Malcolm1044 on 2010-12-12
oh, and I don't know if this matters or not, but I think I had the Windows-Ubuntu installer program on the D drive, but I installed Ubuntu through the website.

continued reading has me scared that "ls" only returned "(hd0)", as all other examples have shown a LOT more.

---

### Post by wilee-nilee on 2010-12-12
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

If you don't have a live ISO of your installed wubi one download one and load it to a thumb or burn it to a cd as a image. Here is a down-loadable thumb loader that is MS or Linux compatible. Follow the instructions in the first paragraph.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Ask questions if needed, but think about the question first be concise.

So we have this helpful tutorial as well.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by Malcolm1044 on 2010-12-12
I want to make sure I understand the steps. Sorry, basic user.

1: Download the ISO from the first link you provided to a USB drive
2: Boot using the USB
3: Download boot script to the USB
4, Place the USB in the affected computer
5, Boot using the USB
6, Operate boot script
7, Post the results using the code tags

Is this correct? 

Second question, on the first link you provided, I see two options, "Download for Windows" and "Download for Linux". I am currently on a Vista OS. Which do I select?

---

### Post by wilee-nilee on 2010-12-12
> **Malcolm1044 said:**
> I want to make sure I understand the steps. Sorry, basic user.

1: Download the ISO from the first link you provided to a USB drive
2: Boot using the USB
3: Download boot script to the USB
4, Place the USB in the affected computer
5, Boot using the USB
6, Operate boot script
7, Post the results using the code tags

Is this correct? 

Second question, on the first link you provided, I see two options, "Download for Windows" and "Download for Linux". I am currently on a Vista OS. Which do I select?

First question #1 Generally I download the ISO separately I have a bunch of ISO's and just use Unebootin to load a thumb. It can get mixed up when loading the thumb when downloading, and I don't believe we know which Ubuntu you have installed.

All other questions are correct if your using Vista download the windows version of Unetbootin, it is named this as it runs in a Windows environment. It will load any type of ISO pretty much.

Thanks for asking the questions this way. It may be as simple as getting a MS type bootloader back in the mbr=master boot record to start with and there is one in Linux if you have no recovery disc or disc possibility but only a thumb. I don't know if the computer or you have a cd/dvd reader

---

### Post by Malcolm1044 on 2010-12-12
To provide a little more information, I believe the version of Ubuntu my computer is running is 10.10, and it does have a CD/DVD reader. I have a 2GB flash drive on me, so that seemed more convenient.

The thumb is downloading unetbootin.

Thank you a lot for helping.

---

### Post by Malcolm1044 on 2010-12-12
EDIT: never mind, I read more =P

---

### Post by Malcolm1044 on 2010-12-12
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,466,809    20,466,747  27 Hidden HPFS/NTFS
/dev/sda2    *     20,467,712    88,653,823    68,186,112   6 FAT16
/dev/sda3          88,653,824   156,299,263    67,645,440   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2031 MB, 2031091712 bytes
16 heads, 32 sectors/track, 7748 cylinders, total 3966976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     3,966,975     3,958,912   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       528e577e-9e02-44f8-81d9-f1201ec9d808   ext4                                     
/dev/sda1        A4E44F3AE49BED2A                       ntfs       PQSERVICE                     
/dev/sda2        620C48720C484371                       ntfs       ACER                          
/dev/sda3        CADE3E11DE3DF5F3                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C037-5215                              vfat       LEVISTORE                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
```

There it is. Any advice?

---

### Post by oldfred on 2010-12-12
how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

You have grub installed to the MBR and with wubi you boot thru the windows boot loader. You can reinstall the windows boot loader with a window repair CD.

But quicker & easier if you have a liveCD or USB.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

lilo works just like the windows boot loader in the MBR.

You should also have a windows repair CD.
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by wilee-nilee on 2010-12-12
Yaeh lets get the Vista bootloader back in the the mbr if you lookbat the first line in the script is says grub is there.

> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.

So since you have a cd player and reader and hopefully and an extra blank cd lets get the Vista recovery disc burnt, if you have no install disc. Run the highlighted command follow the instructions, and notice the W7 forum link for getting to the repair command line to run this one command.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr**  
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

oldfreds comments are excellent as well he includes the Linux lilo option, we just happened to post simultaneously so to speak.

---

### Post by Malcolm1044 on 2010-12-12
Will it work the same way if I put the recovery download on another thumb drive? I've got like 3 of those laying around, no CDs though.

---

### Post by wilee-nilee on 2010-12-12
> **Malcolm1044 said:**
> Will it work the same way if I put the recovery download on another thumb drive? I've got like 3 of those laying around, no CDs though.

The recovery download is very small, I have never been able to load it to a thumb, never seen anybody else do it, and many have tried. Take the road most traveled is what I say. Probably doable loading a thumb with the recovery but I'm not trying.

You saw oldfreds post though as far as using the lilo bootloader you could just do that and see if that works; and any other help from the megathread is needed in case the dual Vista and Ubuntu don't show as when working, but just Vista. Either bootloader will work, personally I'm just a load it to as stock as possible, as far as operating systems go.

---

### Post by Malcolm1044 on 2010-12-12
I was about to head to sleep since I didn't have a disk, but I figured I'd give the other method a try.

Worked like a charm, was fixed inside of two minutes. Thanks a LOT oldfred! I'm in Vista right now, and grub is working the way it was supposed to. I'll test to make sure Ubuntu is working first, and then put this as solved.

And thanks a lot Wilee for your help.

---

### Post by wilee-nilee on 2010-12-12
> **Malcolm1044 said:**
> I was about to head to sleep since I didn't have a disk, but I figured I'd give the other method a try.

Worked like a charm, was fixed inside of two minutes. Thanks a LOT oldfred! I'm in Vista right now, and grub is working the way it was supposed to. I'll test to make sure Ubuntu is working first, and then put this as solved.

Yeah thanks oldfred and to so many others as well.;)

---

### Post by oldfred on 2010-12-13
Malcolm1044, glad you have it working.

wilee-nilee, I have the neo Win7 recovery running on a thumb drive, but I was not able to do it directly from Ubuntu. I had to copy it to a CD and then copy the CD from itself to the flash drive. I then installed grub2 and it still boots, but I can boot a few other ISO with loopmount from the same flash drive.

---

