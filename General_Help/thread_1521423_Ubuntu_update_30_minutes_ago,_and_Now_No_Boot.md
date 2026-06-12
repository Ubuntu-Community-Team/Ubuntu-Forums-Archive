---
title: "Ubuntu update 30 minutes ago, and Now No Boot"
date: 2010-06-30
forum: General Help
---

### Post by JasonSilver on 2010-06-30
This is WUBI installed on (BLECH) Vista. I had two updates today-- one this morning, and one this afternoon which required a restart.

So I restarted a few minutes ago, and when I try to choose Ubuntu from the Windows bootloader, I get the following message which flashes up Extremely quickly (I had to boot 20 times to read it)

Try (hd 0,0) NTFS5: no wubilder
Try (hd 0,1) NTFS5:

Then it goes to a new screen, and says only:

Unknown command 'load font', 
File not found

Then the machine restarts and I'm back at the Windows dual boot prompt.


I have done some searching and have read t hat this is related to Wubi... what can I do to get back into Ubuntu and get back to work. :)

THANKS SO MUCH,
Jason Silver

---

### Post by JasonSilver on 2010-06-30
bump?

---

### Post by wilee-nilee on 2010-07-01
Yeah just post the script it's courtesy of another user, and the best way to dissect the problems.

Also can you boot into windows?

---

### Post by JasonSilver on 2010-07-01
I posted this on the other thread I was using, so I'll put it here too for posterity's sake.

FASCINATING!
 
I booted into Windows Vista last night, tried the chkdsk, but it would only work on reboot, so I thought, ok, let's wait and reboot later-- for now I'm going to troubleshoot some more options.

While I was in there, I thought- hey let's make Ubuntu the default OS on boot.

Then I left to go hear a great funk band play in the city.

When I checked the computer this morning, I was booted into Ubuntu. 

GO FIGURE!

---

### Post by JasonSilver on 2010-07-02
Ubuntu required a restart this morning, and again have the same problem-- 

Try (hd0,0) NTFS5: no wubilder
Try (hd0,1) NTFS5:

Then it says

Unknown command 'load font', 
File not found.

Anyone able to help me at all?

Jason

---

### Post by JasonSilver on 2010-07-02
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 61.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   212,482,047   209,408,000   7 HPFS/NTFS
/dev/sda3         212,482,048   224,047,103    11,565,056   7 HPFS/NTFS
/dev/sda4         224,047,104   234,440,703    10,393,600  17 Hidden HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1023 MB, 1023409664 bytes
32 heads, 61 sectors/track, 1023 cylinders, total 1998847 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             61     1,996,895     1,996,835   c W95 FAT32 (LBA)


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2010 MB, 2010120192 bytes
62 heads, 62 sectors/track, 1021 cylinders, total 3926016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                 515     3,885,055     3,884,541   b W95 FAT32
/dev/sdc2           3,885,056     3,926,015        40,960  84 OS/2 hidden C: drive


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       25c3d4f3-0d3c-4a6d-9449-07ea811cf1a7   ext4                                     
/dev/sda1        B07662D776629DBA                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        388866FB8866B752                       ntfs       U300 HD                       
/dev/sda3        2C983025982FEBD0                       ntfs                                     
/dev/sda4        207A90067A8FD6C6                       ntfs       HDDRECOVERY                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        CF32-F6E2                              vfat       BlueUSB                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        D861-DDFF                              vfat       Sansa e250                    
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/Sansa e250        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda2/boot.ini: ================================

[operating systems]

C:\grldr="OpenSuSE 10.2 installer"

=======Devices which don't seem to have a corresponding hard drive==============

sdd

---

### Post by Seanlol on 2010-07-02
Please code the bootscript.



>   
sda2 -- wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or soThis seems to be the problem. I'm no authority, but unless someone knows a solution, it looks like you may have to reinstall.

Could you do what it says and access the syslog to see if there's any pertinent information?

---

### Post by JasonSilver on 2010-07-02
I ran an fsck on the wubi drive, and then generated RESULTS again:

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 61.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   212,482,047   209,408,000   7 HPFS/NTFS
/dev/sda3         212,482,048   224,047,103    11,565,056   7 HPFS/NTFS
/dev/sda4         224,047,104   234,440,703    10,393,600  17 Hidden HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1023 MB, 1023409664 bytes
32 heads, 61 sectors/track, 1023 cylinders, total 1998847 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             61     1,996,895     1,996,835   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       25c3d4f3-0d3c-4a6d-9449-07ea811cf1a7   ext4                                     
/dev/sda1        B07662D776629DBA                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        388866FB8866B752                       ntfs       U300 HD                       
/dev/sda3        2C983025982FEBD0                       ntfs                                     
/dev/sda4        207A90067A8FD6C6                       ntfs       HDDRECOVERY                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        CF32-F6E2                              vfat       BlueUSB                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/loop1       /vdisk                   ext4       (rw)


---

### Post by Seanlol on 2010-07-02
interesting. In the first Bootscript it shows sda2 as being formatted as EXT4, but in this one we receive

> File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busyIs sda2 the partition with Ubuntu on it?

EDIT: Just noticed Ubuntu's not showing up at all in this bootscript. Have you tried to access the syslog yet?

---

### Post by JasonSilver on 2010-07-02
> **Seanlol said:**
> interesting. In the first Bootscript it shows sda2 as being formatted as EXT4, but in this one we receive

Is sda2 the partition with Ubuntu on it?

EDIT: Just noticed Ubuntu's not showing up at all in this bootscript. Have you tried to access the syslog yet?
I'm not sure what that means- "Access the syslog"

I can mount the drive, view all the files on it, etc... 

THe bottom line is that I am a newb, and have no idea what I'm doing-- despite the fact that I've been using Ubuntu for a few years now.

Would you mind giving me a step to step?

THanks so much
Jason

---

### Post by JasonSilver on 2010-07-02
> **Seanlol said:**
> interesting. In the first Bootscript it shows sda2 as being formatted as EXT4, but in this one we receive

Is sda2 the partition with Ubuntu on it?

EDIT: Just noticed Ubuntu's not showing up at all in this bootscript. Have you tried to access the syslog yet?
I'm not sure really which partition is which, but when I mount the wubi root.disk, all the files are accessable, so there doesn't appear to be anything wrong with it.

I zipped up the contents of root.disk (10 gigs compressed to about 4) and put it on a micro flash drive, so I'm open to reinstalling from scratch... this time WITHOUT Vista, in it's own partition.

I'm just not really sure the best way to go about this, or if something so drastic is necessary yet.

Jason

---

### Post by Seanlol on 2010-07-02
To access the syslog:
via GUI: Reports --> Event Log
via  Command Line: type *info logs*

To have the logs sent  elsewhere:
Setup --> Logging --> Configure syslog server

You can find out which partition ubuntu is on by using GParted on a Live CD. I'm gonna go ahead and guess that it is on sda2. EDIT: Duh. the bootscript says sda2/Wubi. I fail at reading. /facepalm.

> I'm not sure really which partition is which, but when I mount the wubi  root.disk, all the files are accessable, so there doesn't appear to be  anything wrong with it.

I zipped up the contents of root.disk (10 gigs compressed to about 4)  and put it on a micro flash drive, so I'm open to reinstalling from  scratch... this time WITHOUT Vista, in it's own partition.

I'm just not really sure the best way to go about this, or if something  so drastic is necessary yet.Accessing the files from another partition/live cd/etc. is completely different than booting into it.

EDIT: Reinstalling from scratch would probably be the fastest way to solve this. Even if we fix the corrupt files on your Ubuntu partition, deleting the Vista partition then moving and expanding the Ubuntu partition might re-corrupt it, thus forcing you to reinstall.

EDIT2: You also said that the Master Bootloader is on your Windows partition in your first post. This makes it a lot more complex than just deleting the Windows partition.

---

### Post by wilee-nilee on 2010-07-02
Jason your slowly destroying your set up in the way your doing things. If you would like to set up a real dual boot and have a setup that is fixable then you will be helped. 

Your a new user it seems and running processes that are not applicable for example the fsck in a wubi.

When it comes to boot problems and inexperience, just running commands and trying fixes will bork your setup, unless you know what your doing, or instructed by somebody who does. I'm not interested in trying to do anything here but help you get anything in the Ubuntu setup out/recovered and installing a dual boot.

---

### Post by JasonSilver on 2010-07-02
> **wilee-nilee said:**
> Jason your slowly destroying your set up in the way your doing things. If you would like to set up a real dual boot and have a setup that is fixable then you will be helped. 

Your a new user it seems and running processes that are not applicable for example the fsck in a wubi.

When it comes to boot problems and inexperience, just running commands and trying fixes will bork your setup, unless you know what your doing, or instructed by somebody who does. I'm not interested in trying to do anything here but help you get anything in the Ubuntu setup out/recovered and installing a dual boot.
Fair enough.

I have been following instructions on other message boards, and on the wubi guide:

> How can I access my Wubi install and repair my install if it won't boot?

Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:

sudo mkdir /win
sudo mount /dev/sda1 /win

Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

...

To check the filesystem you can use:

sudo fsck /win/ubuntu/disks/root.disk

Unfortunately, I cannot get any work done without my system up and running, and so it is more urgent for me than it is for the wonderful and busy volunteers who are answering message board posts. 

I'm very thankful for your support, and the support of others, but I want to walk the tight-rope of reading the damn manual (so-to-speak) and trying to help myself-- I've had my share of people yelling at me for not googling my own support.

So, let's see if we can get where you want to get me. What should I do first?

Jason

---

### Post by Seanlol on 2010-07-02
First, apparently my reading skills are off today. I so did not cath that fsck error.

> **JasonSilver said:**
> 

So, let's see if we can get where you want to get me. What should I do first?

Jason
One question: You said something earlier about deleting your Windows partition and going to straight Ubuntu. Do you still want to do this, or do you want us to get you to an actual Dual Boot setup?

---

### Post by JasonSilver on 2010-07-02
> To access the syslog:
via GUI: Reports --> Event Log
via Command Line: type info logs

Neither of those make sense to me (what a lost cause I am!) I didn't see a Reports menu item in the gui, and when I typed info logs in the command prompt from the LIve USB, I get a bunch of topics, apparently... ?

> To have the logs sent elsewhere:
Setup --> Logging --> Configure syslog server

Where would I send them? WHere is this Setup menu?

> Accessing the files from another partition/live cd/etc. is completely different than booting into it.

I figured as much, however I thought that might mean that editing some part of a config file somewhere might allow us to boot in. 

> EDIT: Reinstalling from scratch would probably be the fastest way to solve this. Even if we fix the corrupt files on your Ubuntu partition, deleting the Vista partition then moving and expanding the Ubuntu partition might re-corrupt it, thus forcing you to reinstall.

EDIT2: You also said that the Master Bootloader is on your Windows partition in your first post. This makes it a lot more complex than just deleting the Windows partition.

OK... I'll take your word for it. 

I'm a little nervous because it took so long to get things like my graphics tablet working, and my SKype Voip Phone... we're talking weeks of troubleshooting to get these peripherals all up. Is there any way to just copy the /apparently/ good files in the root.disk file to the root of the hard drive and be done with Vista?

Or is there something else you might recommend?

Thanks for your patience with me.

Jason

---

### Post by JasonSilver on 2010-07-02
> **Seanlol said:**
> First, apparently my reading skills are off today. I so did not cath that fsck error.


One question: You said something earlier about deleting your Windows partition and going to straight Ubuntu. Do you still want to do this, or do you want us to get you to an actual Dual Boot setup?
I'd prefer to wipe out Vista all together, but I'd prefer not to have to reconfigure my machine to work with all my peripherals.

I know, I know, I don't ask for much. ;)

Jason

---

### Post by wilee-nilee on 2010-07-02
> **JasonSilver said:**
> Fair enough.

I have been following instructions on other message boards, and on the wubi guide:



Unfortunately, I cannot get any work done without my system up and running, and so it is more urgent for me than it is for the wonderful and busy volunteers who are answering message board posts. 

I'm very thankful for your support, and the support of others, but I want to walk the tight-rope of reading the damn manual (so-to-speak) and trying to help myself-- I've had my share of people yelling at me for not googling my own support.

So, let's see if we can get where you want to get me. What should I do first?

Jason

The best thing now is to state what it is you want. do you want to have just Ubuntu, or a dual boot then post the script again.

I can appreciate your wanting to learn, but your frantically pecking away at a setup that is slowly dying from what I can see. Take a deep breath and relax.

Also post the script in code tags please there is a description in my signature and you can also just coy and paste the script to a reply highlight it then click on the # in the reply panel.

It is much more difficult to read the script when it is not in a scrolling code window.

---

### Post by Seanlol on 2010-07-02
> **JasonSilver said:**
> . 
I'm a little nervous because it took so long to get things like my graphics tablet working, and my SKype Voip Phone... we're talking weeks of troubleshooting to get these peripherals all up. Is there any way to just copy the /apparently/ good files in the root.disk file to the root of the hard drive and be done with Vista?

Or is there something else you might recommend?

Thanks for your patience with me.

Jason

I'm not too familiar with Wubi, so I may have posted the wrong thing regarding the syslog.

I'll leave most of the rest of this to the other guy in here who is more familiar with Wubi than I am. Iin my opinion, the easiest thing to do would be to take all your important files, copy them to a USB stick and just reformat the entire drive and install Ubuntu. You could have a working computer within a couple of hours. Now, if you want to go through the arduous process of getting Ubuntu to be bootable again, you'll have to consult someone who's more familiar with Wubi than I am. Skype makes a Linux client, and there are a few threads around about tablet PCs.

I would just bite the bullet and cut my losses.

---

### Post by JasonSilver on 2010-07-02
> **Seanlol said:**
> I'm not too familiar with Wubi, so I may have posted the wrong thing regarding the syslog.

I'll leave most of the rest of this to the other guy in here who is more familiar with Wubi than I am. Iin my opinion, the easiest thing to do would be to take all your important files, copy them to a USB stick and just reformat the entire drive and install Ubuntu. You could have a working computer within a couple of hours. Now, if you want to go through the arduous process of getting Ubuntu to be bootable again, you'll have to consult someone who's more familiar with Wubi than I am. Skype makes a Linux client, and there are a few threads around about tablet PCs.

I would just bite the bullet and cut my losses.
Alright, guys, let's do it. What is the best way to start?

I'm on a Toshiba Laptop, Satellite Pro U300, with no working CD ROM, I'm currently booted in a Live USB Thumb drive. I have another PC with Windows XP right next to me.

What should I do first? Double click the "Install Ubuntu 10.04 LTS" icon on the desktop?

Jason

---

### Post by wilee-nilee on 2010-07-02
> **JasonSilver said:**
> Alright, guys, let's do it. What is the best way to start?

I'm on a Toshiba Laptop, Satellite Pro U300, with no working CD ROM, I'm currently booted in a Live USB Thumb drive. I have another PC with Windows XP right next to me.

What should I do first? Double click the "Install Ubuntu 10.04 LTS" icon on the desktop?

Jason

So do you want to keep vista, I also see 3 hard drives are any of these external.
> 
/dev/sda
/dev/sdb
/dev/sdc

Now the second script shows no sdc this is why I'm asking the question about HD.

---

### Post by Seanlol on 2010-07-02
Get all the files you want to keep off of both Ubuntu and Vista. Putting htem on a USB or another PC works. Then, yes, the Install Ubuntu 10.04 button will work. From there, installing Ubuntu is really easy. Be sure to click the button to tell Ubuntu to take up the entire hard drive, and format it into ext4 (unless you prefer a different file system.

_[wilee-nilee]("http://ubuntuforums.org/member.php?u=906928")_, he said he did not want to keep Vista.

---

### Post by JasonSilver on 2010-07-02
> **wilee-nilee said:**
> So do you want to keep vista, I also see 3 hard drives are any of these external.


Now the second script shows no sdc this is why I'm asking the question about HD.

No, let's ditch Vista.

The hard drives at the time were an 8 gig MicroSD in an adapter, and a Sansa with it's own external drive slot (another 8 gig MicroSD).

I forgot to remove them when I was doing the report.

One more question: my approach to zip up the contents of the root.disk and put them on the flash drive is a good enough backup approach?

Jason

---

### Post by wilee-nilee on 2010-07-02
> **JasonSilver said:**
> No, let's ditch Vista.

The hard drives at the time were an 8 gig MicroSD in an adapter, and a Sansa with it's own external drive slot (another 8 gig MicroSD).

I forgot to remove them when I was doing the report.

One more question: my approach to zip up the contents of the root.disk and put them on the flash drive is a good enough backup approach?

Jason

I don't know about the way you have backed up the stuff you want to keep, you have done it I can't really know if it will work okay. I do know that if you access the stuff to save from a live cd and save it in it's as is form to a external you will be safe.

If you want to install Ubuntu after saving in a manner you feel comfortable with, delete the partitions you have now with gparted on the Live cd that has been booted. Then just install to one of the full HD sda would be whats best. If sdb is a second HD this can be used as a separate home later or a data HD.

Personally I feel at this point just letting the live cd do the install and the auto partitioning happen will probably serve you best.

Edit: so sdb is one of the externals as well? A full install on the sda HD, and saving method as suggested by Seanlol and myself seems to be the best route.

---

### Post by JasonSilver on 2010-07-02
Thanks for your help, guys. Here's where I currently stand.

I started off by playing around with the partitions, and trying to make a spot to upload the back ups to. I finally gave up in frustration for various reasons.

I then reinstalled from the LiveUSB, and mostly everything went well. The machine locked up after instal, and I had to do a hard reboot, but we're set.

Then I logged in, and decompressed the root.disk file to my desktop, then mounted it as /wubiDrive

I copied the files I wanted from my home folder, and so far, so good. I'm waiting for a massive update to finish before I test the Skype Phone, the GPS, the graphic tablet, etc. But, I have my original Firefox settings, so that's a good sign.

What a headache Wubi is. I think there should be some warning somewhere that Wubi is not ready for prime time. I've had four or five major issues with Wubi not allowing me to boot in.

Thanks for your help. If you're interested, I'd like to offer you any or all of my music for free (jasonsilver.com) -- it's kind of a Sarah McLachlan meets Billy Joel style.

Jason

---

### Post by wilee-nilee on 2010-07-02
Thanks for the music link, I'm a former Jazz musician, and a multi instrumentalist as well. I say former because I play all genres but prefer dissonant poly-rhythmic instrumental music at heart, usually in a full improvisational environment.

---

### Post by JasonSilver on 2010-07-02
> **wilee-nilee said:**
> Thanks for the music link, I'm a former Jazz musician, and a multi instrumentalist as well. I say former because I play all genres but prefer dissonant poly-rhythmic instrumental music at heart, usually in a full improvisational environment.
Cool! That style is a lot harder than listeners realise. ;)

Nice to meet you.

---

