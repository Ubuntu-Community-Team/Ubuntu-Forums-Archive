---
title: "I lost my partitions...  :("
date: 2010-08-14
forum: General Help
---

### Post by rnfel on 2010-08-14
Hi Guys

This morning, my hard drive looked something like this - Windows Vista on a partition of around 100 GB (NTFS), Ubuntu 10.04 (ext3)on a partition of around 80 GB, 4 GB swap and a partition of around 40 GB (NTFS) containing videos and music and stuff like that.  I wanted to resize the Ubuntu partition to around 30 - 40 GB and add the remaining space to the 40 GB partition.

I successfully reduced the Ubuntu partition using the Partition Manager app that comes with Ubuntu, but I was unable to add that to the NTFS partition.  After a merge failed, I was no longer able to access the 40 GB partition.  I tried restoring that with testdisk, and now I can't access anything!  GRUB fails to load, and when running from the live CD of 9.04 (only version I had on CD) my Ubuntu partition and 40 GB data partition no longer shows up.  I have over a 100 GB of free space instead.  

Can someone please help me recover my data?  I'll be extremely grateful!

For the record, I had an external drive plugged in while running testdisk.

Thanks & Regards,
RF Nel

---

### Post by Rubi1200 on 2010-08-14
Hi,
please boot the computer with the LiveCD and choose to try in live mode, not install.

Click on the link at the bottom of my post.

Follow the instructions and post the results back here.

Thanks.

---

### Post by deserthowler on 2010-08-14
Do you have more details of your partition table?  What is the partition name of each drive and how are they arranged?  I have had some problems with this before and have found operator error involved.

Earl

---

### Post by rnfel on 2010-08-14
> **deserthowler said:**
> Do you have more details of your partition table?  What is the partition name of each drive and how are they arranged?  I have had some problems with this before and have found operator error involved.

Earl

Hi Earl

Thank you for your reply.  My knowledge of partitioning is very limited, but I can remember that the Windows partition came before the others, and the one of the missing partitions was called Data.  The swap partition is also missing, and I can't remember the name of the primary Ubuntu partition.

Regards

---

### Post by Quackers on 2010-08-14
rnfel have you tried Rubi1200's suggestion?

---

### Post by rnfel on 2010-08-14
> **Rubi1200 said:**
> Hi,
please boot the computer with the LiveCD and choose to try in live mode, not install.

Click on the link at the bottom of my post.

Follow the instructions and post the results back here.

Thanks.

Hi Rubi

Thanks for your reply.  I download the script and executed it, the output was as follows:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

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
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x435621ad

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000   7 HPFS/NTFS
/dev/sda2           3,074,048   247,271,423   244,197,376   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2AEAA1D4EAA19D17                       ntfs       WinRE                         
/dev/sda2        9080A48E80A47C7A                       ntfs       Vista                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

Regards

---

### Post by rnfel on 2010-08-14
> **Quackers said:**
> rnfel have you tried Rubi1200's suggestion?

Hi Quackers

I was busy downloading and executing the script while you were typing your post.  :)

Regards

---

### Post by Quackers on 2010-08-14
Yes, I see that our posts "crossed" :-)

---

### Post by Rubi1200 on 2010-08-14
I hope that Quackers or someone else can correct me if I am wrong, but it looks like you may have lost those other partitions.

You have a 250GB drive and Windows ends here
> 247,271,423 

There may be recovery options, but I would first backup what you have before trying anything else.

---

### Post by Quackers on 2010-08-14
rnfel you said 
"I successfully reduced the Ubuntu partition using the Partition Manager app that comes with Ubuntu,"
Did you manage to do that from within Ubuntu? In other words, whilst Ubuntu was running.

---

### Post by rnfel on 2010-08-14
> **Quackers said:**
> rnfel you said 
"I successfully reduced the Ubuntu partition using the Partition Manager app that comes with Ubuntu,"
Did you manage to do that from within Ubuntu? In other words, whilst Ubuntu was running.

Yes, Ubuntu was still running at that stage.  After that, I couldn't merge the free space with the partition that I wanted to resize, so I played around with moving my partitions to get the free space next to the partition I wanted to resize.  After that, I got an error (not sure what it said, unfortunately) while trying to merge.  I installed testdisk, and I must've done something very wrong when running that...  Afterwards, I couldn't get to the bootloader anymore, and the Partition Manager on the live CD shows empty space, instead of my partitions.

---

### Post by Quackers on 2010-08-14
As far as I understand it, you shouldn't be able to resize a partition that is in use. I would expect such an action to fail. That seems strange to me, but maybe I am wrong.
Looking at your output file above I would agree with Rubi1200 and say that your hard drive seems to be only half used. I would imagine though, that you should be able to get Windows booting again - if you can get the machine to boot from your recovery disc (or maybe a downloaded windows repair disc).

---

### Post by rnfel on 2010-08-14
> **Quackers said:**
> As far as I understand it, you shouldn't be able to resize a partition that is in use. I would expect such an action to fail. That seems strange to me, but maybe I am wrong.
Looking at your output file above I would agree with Rubi1200 and say that your hard drive seems to be only half used. I would imagine though, that you should be able to get Windows booting again - if you can get the machine to boot from your recovery disc (or maybe a downloaded windows repair disc).

I agree that I should be able to at least get Windows back up and running, but most of my work is on the Ubuntu partition and all my music, videos, e-books, etc is on the other partition that got lost.  I would really, really hate to lose all that.  Since I haven't used the 'empty' space, all of my data should still be there, in theory.  The issue is with recovering it...  I think you are right.  I probably couldn't resize the partition because it was mounted.  I should've realised that.

---

### Post by Rubi1200 on 2010-08-14
If you want to restore the Vista bootloader and get back into Windows you can take a look here:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Scroll down to the relevant section.

I am not sure, and cannot guarantee, what will happen to the "empty" space you are seeing.

I think running testdisk from a LiveCD may still be an option, but proceed with caution.

---

### Post by Quackers on 2010-08-14
Although I have heard of it, I have never used Testdisk. I may be wrong, but I suspect that any damage has been caused by that program, rather than the resize. Unfortunately you are now into the area of recovering lost data from damaged/deleted partitions. This is an area I have not delved into, so am unable to offer any advice at all.
Maybe someone will come along who is better informed in this area.
Good luck.

---

### Post by rnfel on 2010-08-14
> **Rubi1200 said:**
> If you want to restore the Vista bootloader and get back into Windows you can take a look here:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Scroll down to the relevant section.

I am not sure, and cannot guarantee, what will happen to the "empty" space you are seeing.

I think running testdisk from a LiveCD may still be an option, but proceed with caution.

I backed up what little data I still had access to, so now I'm going to try testdisk again.  Keep your fingers crossed!

---

### Post by rnfel on 2010-08-14
I am pleased to report that I was able to recover my data using testdisk!  GRUB, however, is still broken.

---

### Post by arpanaut on 2010-08-14
That's great news! 
Grub is not going to work without a viable working Ubuntu install, Grub is installed onto the MBR of the drive, but "looks" to the /boot directory on the installation for the information about what to boot, where it is and how to boot.
So without a proper install you are out of luck with booting from grub.
If you did not recover your Ubuntu partition, you will need to reinstall.

You might want to get the windows bootloader back on your Win install to make sure it's working.

Thanks to oldfred:
> from liveCD you can install a windows boot loader:

Restore basic windows boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR  
Some more info to restore bootloaders:

[http://ubuntuforums.org/showpost.php?p=6391959&postcount=1](http://ubuntuforums.org/showpost.php?p=6391959&postcount=1)

---

### Post by Quackers on 2010-08-14
That's great news rnfel :-)

---

### Post by Rubi1200 on 2010-08-14
> **rnfel said:**
> I am pleased to report that I was able to recover my data using testdisk!  GRUB, however, is still broken.
Excellent news!!!

I think arpanaut is correct about the current situation. Get Windows up and running again and then reinstall Ubuntu.

Good luck!

---

### Post by Marky-boy on 2010-08-14
I'm in a similar boat, only more complicated!

I had Windows 7 64-bit, UbuStudio 10.04 on ext4 with encrypted home folder, and then a residual Vista recovery partition that was there when I got the computer (and will never use again).

I ran GParted 0.5.2-9 Live CD, intending to try and shrink the ext4 partition to make an ntfs partition on which to store music files etc so win7 could see them.

Noticed a bunch of space to the left of Windows 7 partition, so set a sequence of gparted tasks to first move the win7 partition to the left and then expand it to take up the room to the right to butt up against the ext4, then resize the ext4.

I ran into errors, can't recall exactly what they said, but couldn't restart machine. And then panicked when checking the Gparted site to find out that a whole bunch of 0.5.x releases had bugs.

I've managed to use a bunch of live recovery CDs (Knoppix, RIPLinux, Ubu 10.04 Live CD) and can see my drives. I just can't get them to boot. I even managed to decrypt my ubuntu home folder and extract some files - however what I really need is my Thunderbird folders - and these had read-write errors.

I may have goofed up reinstalling Grub2, trying to get Ubuntu back up and running. Now all I get on reboot is a grub prompt.
 
<Tried just now to download this boot info script, but link is taking me to a canonical 404 page...?>

Ok found the script, but can;t open results in gedit due to a character set issue. Could open in OpenOffice Writer - but after the sda2/boot/grub/grub.cfg heading it is nothign but gobbledygook.


Results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   196,796,239   196,796,177   7 HPFS/NTFS
/dev/sda2         196,796,313   585,087,296   388,290,984  83 Linux
/dev/sda3         601,581,568   625,135,615    23,554,048   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C1C662B04BD60EE                       ntfs                                     
/dev/sda2        6accef10-df35-4e3a-bec1-659a1f2a9e10   ext4       Ubuntu                        
/dev/sda3        F0049BC0049B886C                       ntfs       RECOVERY                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5476F31F76F30112                       ntfs       FreeAgent_Silver              
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/Ubuntu            ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda2/boot/grub/grub.cfg: =========================== 
```

example of grub.cfg:

```
&#8508;&#20292;&#21571;&#20569;&#8261;&#21576;&#19533;&#20512;&#16981;&#18764;&#8259;&#11554;&#12079;&#13143;&#12099;&#17455;&#17492;&#18464;&#19796;&#8268;&#11828;&#8240;&#29268;&#28257;&#26995;&#26996;&#28271;&#27745;&#12079;&#20037;&#15906;&#15370;&#21576;&#19533;&#2622;&#18492;&#16709;&#15940;&#2314;&#19772;&#21573;&#8257;&#21576;&#20564;&#17709;&#21841;&#22089;&#8765;&#20291;&#21582;&#20037;&#11604;&#22868;&#17744;&#8226;&#20291;&#21582;&#20037;&#15700;&#29730;&#30821;&#12148;&#29800;&#27757;&#8251;&#26723;&#29281;&#25971;&#15732;&#29813;&#11622;&#8760;&#2622;&#15369;&#18772;&#19540;&#15941;&#12092;&#18772;&#19540;&#15941;&#2314;&#19772;&#21573;&#8257;&#16718;&#17741;&#8765;&#17735;&#17742;&#16722;&#20308;&#8786;&#17184;&#20047;&#17748;&#21582;&#8765;&#28751;&#28261;&#26191;&#26982;&#25955;&#28462;&#26482;&#13088;&#12846;&#8224;&#21800;&#26990;&#10616;&#15906;&#2314;&#21308;&#22868;&#17740;&#21536;&#20569;&#15685;&#29730;&#30821;&#12148;&#29539;&#8819;&#2622;&#15369;&#11553;&#2605;&#2313;&#28736;&#26465;&#8293;&#8315;&#24941;&#26482;&#28265;&#8250;&#11824;&#14647;&#28265;&#32032;&#2314;&#20489;&#17746;&#31520;&#26144;&#28271;&#11636;&#24934;&#26989;&#31084;&#8250;&#19490;&#25193;&#29285;&#29793;&#28521;&#8302;&#25939;&#26994;&#8806;&#32032;&#2314;&#20489;&#31520;&#27936;&#29281;&#26983;&#11630;&#28514;&#29812;&#28015;&#8250;&#11824;&#14384;&#28265;&#32032;

```


So - am i screwed?

All I want to do is log in to ubuntu, copy out some files from my home directory, and then nuke the entire hard disk and start again.

Any help hugely appreciated.

Mark

---

### Post by rnfel on 2010-08-15
> **Marky-boy said:**
> I'm in a similar boat, only more complicated!

I had Windows 7 64-bit, UbuStudio 10.04 on ext4 with encrypted home folder, and then a residual Vista recovery partition that was there when I got the computer (and will never use again).

I ran GParted 0.5.2-9 Live CD, intending to try and shrink the ext4 partition to make an ntfs partition on which to store music files etc so win7 could see them.

Noticed a bunch of space to the left of Windows 7 partition, so set a sequence of gparted tasks to first move the win7 partition to the left and then expand it to take up the room to the right to butt up against the ext4, then resize the ext4.

I ran into errors, can't recall exactly what they said, but couldn't restart machine. And then panicked when checking the Gparted site to find out that a whole bunch of 0.5.x releases had bugs.

I've managed to use a bunch of live recovery CDs (Knoppix, RIPLinux, Ubu 10.04 Live CD) and can see my drives. I just can't get them to boot. I even managed to decrypt my ubuntu home folder and extract some files - however what I really need is my Thunderbird folders - and these had read-write errors.

I may have goofed up reinstalling Grub2, trying to get Ubuntu back up and running. Now all I get on reboot is a grub prompt.
 
<Tried just now to download this boot info script, but link is taking me to a canonical 404 page...?>

Ok found the script, but can;t open results in gedit due to a character set issue. Could open in OpenOffice Writer - but after the sda2/boot/grub/grub.cfg heading it is nothign but gobbledygook.


Results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   196,796,239   196,796,177   7 HPFS/NTFS
/dev/sda2         196,796,313   585,087,296   388,290,984  83 Linux
/dev/sda3         601,581,568   625,135,615    23,554,048   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C1C662B04BD60EE                       ntfs                                     
/dev/sda2        6accef10-df35-4e3a-bec1-659a1f2a9e10   ext4       Ubuntu                        
/dev/sda3        F0049BC0049B886C                       ntfs       RECOVERY                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5476F31F76F30112                       ntfs       FreeAgent_Silver              
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/Ubuntu            ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda2/boot/grub/grub.cfg: =========================== 
```

example of grub.cfg:

```
&#8508;&#20292;&#21571;&#20569;&#8261;&#21576;&#19533;&#20512;&#16981;&#18764;&#8259;&#11554;&#12079;&#13143;&#12099;&#17455;&#17492;&#18464;&#19796;&#8268;&#11828;‰&#29268;&#28257;&#26995;&#26996;&#28271;&#27745;&#12079;&#20037;&#15906;&#15370;&#21576;&#19533;&#2622;&#18492;&#16709;&#15940;&#2314;&#19772;&#21573;&#8257;&#21576;&#20564;&#17709;&#21841;&#22089;&#8765;&#20291;&#21582;&#20037;&#11604;&#22868;&#17744;•&#20291;&#21582;&#20037;&#15700;&#29730;&#30821;&#12148;&#29800;&#27757;&#8251;&#26723;&#29281;&#25971;&#15732;&#29813;&#11622;&#8760;&#2622;&#15369;&#18772;&#19540;&#15941;&#12092;&#18772;&#19540;&#15941;&#2314;&#19772;&#21573;&#8257;&#16718;&#17741;&#8765;&#17735;&#17742;&#16722;&#20308;&#8786;&#17184;&#20047;&#17748;&#21582;&#8765;&#28751;&#28261;&#26191;&#26982;&#25955;&#28462;&#26482;&#13088;&#12846;†&#21800;&#26990;&#10616;&#15906;&#2314;&#21308;&#22868;&#17740;&#21536;&#20569;&#15685;&#29730;&#30821;&#12148;&#29539;&#8819;&#2622;&#15369;&#11553;&#2605;&#2313;&#28736;&#26465;&#8293;&#8315;&#24941;&#26482;&#28265;›&#11824;&#14647;&#28265;&#32032;&#2314;&#20489;&#17746;&#31520;&#26144;&#28271;&#11636;&#24934;&#26989;&#31084;›&#19490;&#25193;&#29285;&#29793;&#28521;&#8302;&#25939;&#26994;&#8806;&#32032;&#2314;&#20489;&#31520;&#27936;&#29281;&#26983;&#11630;&#28514;&#29812;&#28015;›&#11824;&#14384;&#28265;&#32032;

```


So - am i screwed?

All I want to do is log in to ubuntu, copy out some files from my home directory, and then nuke the entire hard disk and start again.

Any help hugely appreciated.

Mark

Can't you see the files and copy them to an external source while using the Live CD?

---

### Post by Marky-boy on 2010-08-16
Sadly not. I got close - but there were heaps of read-write errors. I don't know if it's possible but it's almost as if the FAT has lost track of where some of the files actually are.  That, or the GParted balls up has nuked my hard disk - though other tools didn't seem to find any issue with the actual disk.

Am close to just nuking it all, and reinstalling. Kinda sad, dampens my enthusiasm for Ubuntu - which I've been on since 7.04

---

### Post by Quackers on 2010-08-16
Have you run sudo update-grub at all?

---

### Post by Marky-boy on 2010-08-16
from where? The grub prompt I am left with on restart?

---

### Post by Quackers on 2010-08-16
From a terminal on the Live CD?

---

### Post by Marky-boy on 2010-08-16
sudo grub-update gives me
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

---

### Post by Quackers on 2010-08-16
It looks like your root partition isn't mounting. Unfortunately, if that is the case I don't know what you can do about it. Maybe someone more knowledgable than me can offer some advice.

---

### Post by Marky-boy on 2010-08-17
Thanks quackers. Appreciate the help.

I've given this enough time. Gonna blast the whole hard disk and re-do. *sigh*

---

