---
title: "Applied Upgrades, Now Ubuntu Won't Boot"
date: 2010-12-16
forum: General Help
---

### Post by gswetsky on 2010-12-16
About a year ago or more, I installed 32 bit Ubuntu 8 from an iso file through Windows 7.  I don't remember much about the installation, but it installed a dual boot which didn't say Grub or anything and didn't seem to have any options other than for a memory test.  Ubuntu apparently runs as a Windows file on the NTFS partition.  However it works, it runs exactly like I would expect Linux to run including the ability to mount the Windows file system and have its own IP address which sees my entire LAN.

Anyhow, by now I hope you know what I have because I don't.  I've periodically applied upgrades as they appeared including several new kernels.  It has always applied the upgrades properly.  Right now ccleaner reports the program version as 10.04-rev 189.

I booted Ubuntu up today after not having used it for several months.  I searched for upgrades to programs and it found 99 upgrades which I applied.  After all the upgrade patches were applied, I was told to reboot.  I assumed it had applied another kernel, so I complied.  That was the last I saw of my precious Ubuntu.

Windows 7 still boots properly, however if I down arrow and select Ubuntu, two lines of text flash really fast on the screen and the computer reboots to the dual boot screen.  I've tried typing 'e' at the dual boot and that does nothing.

Number one, if anyone out there knows what I have and if there's any was to repair it, that's the way I'd like to proceed because I have a lot of customization in my Ubuntu.  My other alternative is to go in and delete Ubuntu.  That is supposed to remove the program and set everything back to the way it was.  Truth be told, I'm rather squeamish on this alternative.  I'd rather not lose Windows in the process.

Thanks,
Gerry

---

### Post by mastablasta on 2010-12-16
you use a wubi install and you can't and shoulnd't upgrade in that.
 
well maybe you can but there are some special commands needed. this is solution for upgrade from 10.04 to 10.10: [http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)
 
You might want to consider a separate partition in which to install Ubuntu. It is much safer, faster and easier than this virtualization.
 
Think about it if you have your OS running in one fiel and if that one file gets corrupted all your owrk, data and stuff stored in that OS will be lost.

---

### Post by theasprint on 2010-12-16
1. Is it neccesary to access your files in your Ubuntu?
2. Did you use a Wubi install?

One way to check if u use Wubi is that your bootloader is from Microsoft and you are not using grub bootloader to choose your OS during startup.

to mastablasta: I suppose ubuntu doesn't self-upgrade itself to a newer version (10.04 to 10.10) automatically in the update manager does it? Unless you choose to update normal releases in update manager under settings.

---

### Post by bcbc on 2010-12-16
It's best to post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") - but I suppose you don't have an Ubuntu CD you can boot from...

You said you first installed with version 8.xx that would mean you are using grub legacy to boot. 
What are the contents of:
  c:\ubuntu\disks\boot\
  c:\ubuntu\disks\boot\grub\
  c:\ubuntu\winboot\

---

### Post by gswetsky on 2010-12-16
First of all, thank you all for your help.  I'll answer bcbc......

> **bcbc said:**
> It's best to post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") - but I suppose you don't have an Ubuntu CD you can boot from...

I have my original DVD that I loaded Wubi from.  I just ran Ubuntu from it.  However, this method doesn't write anything to the hard drive.  I don't know if it would allow me to create the file from bootinfoscript or even download the file.

> You said you first installed with version 8.xx that would mean you are using grub legacy to boot. 
What are the contents of:
  c:\ubuntu\disks\boot\
  c:\ubuntu\disks\boot\grub\
  c:\ubuntu\winboot\c:\ubuntu\disks\boot\grub <--There are no files in this folder
c:\ubuntu\winboot\ contains wubildr, wubildr.cfg and wubildr.mbr.  All bear a date stamp of 07/05/2010.

When Wubi booted properly it gave me a choice of which kernel I wanted to boot.  If it installed 10.1, shouldn't I still get a choice so I can boot from a previous kernel?

I found the Wubi home page and their forum [Edit: Apparently no forum].  Should I be posting over there instead of here?

Thanks,
Gerry

---

### Post by bcbc on 2010-12-16
> **gswetsky said:**
> First of all, thank you all for your help.  I'll answer bcbc......



I have my original DVD that I loaded Wubi from.  I just ran Ubuntu from it.  However, this method doesn't write anything to the hard drive.  I don't know if it would allow me to create the file from bootinfoscript or even download the file.

c:\ubuntu\disks\boot\grub <--There are no files in this folder
c:\ubuntu\winboot\ contains wubildr, wubildr.cfg and wubildr.mbr.  All bear a date stamp of 07/05/2010.

When Wubi booted properly it gave me a choice of which kernel I wanted to boot.  If it installed 10.1, shouldn't I still get a choice so I can boot from a previous kernel?

I found the Wubi home page and their forum [Edit: Apparently no forum].  Should I be posting over there instead of here?

Thanks,
Gerry

So it's unlikely you installed release 8.xx - more like 10.04. Your problem is described in the [wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") (problem #2, fix#1, permanent fix)

It's totally OK to download and save files in a Live environment. Nothing will be saved after you shutdown/reboot but you'll be able to connect to the net and post the results of the bootinfoscript.

---

### Post by gswetsky on 2010-12-16
Got it!  Is this what we're looking for?

Gerry

ubuntu@ubuntu:~/Desktop$ cat RESULTS.txt
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0420403c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   625,139,711   624,932,864   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       521ddce0-53bb-4fc7-9829-5222aeb6297c   ext4                                     
/dev/sda1        E004068604066040                       ntfs       System Reserved               
/dev/sda2        8E1407D21407BC69                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

---

### Post by bcbc on 2010-12-16
OK go to the thread I mentioned:  [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) - look for **Problem #2**, then **Solution #1**. Follow everything it says but substitute **sda[COLOR="Red"]2[/COLOR]** wherever it says **sda[COLOR="red"]1[/COLOR]**.

That should get it booting again. Once it's booting, go back to that thread and look further down for the **Permanent Fix**. 

If you have any issues - a command returns an error or you are unsure about something, post back here before continuing.

---

### Post by gswetsky on 2010-12-16
Alas.....  The mount -o loop /media/win/ubuntu/disks/root.disk /mnt command presented me with "Unknown filesystem type 'EXT4'".

Are we sunk?

Gerry

---

### Post by bcbc on 2010-12-16
> **gswetsky said:**
> Alas.....  The mount -o loop /media/win/ubuntu/disks/root.disk /mnt command presented me with "Unknown filesystem type 'EXT4'".

Are we sunk?

Gerry

what version of Ubuntu are you running (your live environment)? If it's prior to 9.10 it probably isn't aware of ext4 filesystems.

---

### Post by bcbc on 2010-12-16
Actually try specifying '-t ext4'
i.e. sudo mount -t ext4 -o loop /media/win/ubuntu/disks/root.disk /mnt

and see what it says. You might need to fsck it:
sudo fsck /media/win/ubuntu/disks/root.disk (but do not do this if it is mounted)

---

### Post by gswetsky on 2010-12-16
Well, before I do that, my original install was Ubuntu 8 and I suspect you're correct about not knowing what EXT4 is.  Do you suppose with all the intervening upgrades, the '-t ext4' might work?

After I got the error message, I opened up a graphics display of my mounted filesystem and when I clicked on root.disk, it gave me an error message stating it didn't recognize the filesystem type.

Gerry

---

### Post by bcbc on 2010-12-16
I think it's more likely that the root.disk is 'dirty'. So fsck might fix that.

what's the output of "uname -a" or "lsb_release -a"

---

### Post by gswetsky on 2010-12-16
> **bcbc said:**
> I think it's more likely that the root.disk is 'dirty'. So fsck might fix that.

what's the output of "uname -a" or "lsb_release -a"
Well, let's see.....
uuname outputs ubuntu 2.6.24-19 generic #1 smp wed jun 18 14:43:41 utc 2008 i686 gnu/linux

Forgive me if I use the wrong case/spacing.  I wrote all this stuff down.

lsb_release yields.....

No lsb modules are available
Distributor ID: ubuntu
Release: 8.04
Codename: hardy

Using -t ext4 in the mount command gives the same message as before.  It doesn't know what ext4 is.

Finally fsck on an unmounted /media/...../root.disk gives us root.disk has unsupported feature(s) extents FEATURE_I9 huge_file gdt_checksum dir_nlink extra_isize
Finally it says e2fsck: Get a newer version of e2fsck

So whaddaya think now?  It's not like I have anything irreplaceable on this implementation.  It's mostly customization that I have to do by memory.

Gerry

---

### Post by bcbc on 2010-12-16
Well, you get to decide :)

Basically you're going to have to either get a Ubuntu CD/USB that supports ext4, or you can reinstall. I think it's always good to have a rescue disk handy - and you're going to have to download an .iso anyway if you reinstall - so you might as well go for the repair.

Whatever you choose, if you end up reinstalling Wubi make sure you don't update packages grub-pc and grub-common (they fall under "Recommended" updates - you can uncheck them each time you're prompted, or just lock the version in Synaptic).

---

### Post by gswetsky on 2010-12-17
Well thank you for all the help, mon ami.  Before I retired from Unisys in 2001, I was a field service tech and worked with Unix a lot.  I like to keep my skills up.

I found a program, ext2explore that allows me to go through Ubuntu and bring files down to my Win 7 desktop.  I just brought my .profile down.

Gerry

---

