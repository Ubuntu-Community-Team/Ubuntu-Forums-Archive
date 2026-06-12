---
title: "Unable to boot into Windows after failed Ubuntu installaton"
date: 2012-05-21
forum: General Help
---

### Post by meijin3 on 2012-05-21
Okay guys, we've got some big problems here. I tried installing Ubuntu onto my friend's HP laptop and now we can no longer boot into Windows. I'm going to give you the steps we took leading up to the failed installation and then steps we took to attempt to fix what was wrong as well as any error messages I recorded.

-I partitioned his hard drive using the built-in disk manager that comes with Windows
-I booted Ubuntu from the CD and attempted to install it to my new partition
-It gave me an error warning that I did not select a drive for swap (wasn't entirely sure how to make one so I forged  ahead because there was a lot of RAM on the computer)
-Ubuntu would not install so we decided to just install it through Wubi.
-Rebooted PC to boot into Windows but it suggested that we do start-up repair
-Startup repair required a CD so we tried to boot normally and got a quick flash of a blue screen followed by a reboot
-Created a repair disc and started startup repair but were informed that the drive with Windows 7 had 0 MBs. (This obviously could not be correct as this drive was untouched but it could be that it was not reading the correct drive).
-Attempted system restore but was greeted with the following error code:  0x8007001f

And that's where we are so far. If anybody could please help, I would more than appreciate it!

---

### Post by wilee-nilee on 2012-05-21
HP's commonly come with 4 primary partitions, if you try to add another you can switch the HD to dynamic.

Boot a ubuntui live cd, open gparted take a screen shot and post it, there are some tools that might fix this but we need to know what is going on. If there is more then 1 HD use the dropdown in the top right corner in gparted to get all of them on a post.

The 12.04 release looks as if wubi is there, but just tells you to reboot to a live cd.

---

### Post by meijin3 on 2012-05-21
Hey guys, I'm leaving my friend's house now but he is creating an account and will be logging in soon so please help him out! His username will be "vikingboi".

---

### Post by vikingBoi on 2012-05-21
here's the screen shot. hopefully you can figure it out

---

### Post by wilee-nilee on 2012-05-21
> **vikingBoi said:**
> here's the screen shot. hopefully you can figure it out

Welcome to the forums.

So the sda1 being unknown might be better identified with a script we often run. Run these commands and a results.txt will appear in the home of the live cd, copy all the text, open a reply and click on the # in the reply panel, and paste the text between the code tags.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
``` ```
chmod a+x bootinfoscript
``````
sudo bash bootinfoscript
```

---

### Post by vikingBoi on 2012-05-21
i don't really know what i'm doing so could you break it down for me a little more please

---

### Post by wilee-nilee on 2012-05-21
> **vikingBoi said:**
> i don't really know what i'm doing so could you break it down for me a little more please

Sure no problem, open a terminal use the top button in the left panel, type in terminal. Run each command as a right click copy and paste in the terminal.

Then open that search again and type home, in home will be the results.txt, open it by clicking on it, highlight all the text right click then hit copy.

Open a reply and look in the reply's top panel for this # it will create what looks like this   [ code][/code] left click between them then right click paste.

---

### Post by meijin3 on 2012-05-21
> **vikingBoi said:**
> i don't really know what i'm doing so could you break it down for me a little more please

Open terminal (ctrl+alt+T) and copy&paste these commands into it and follow the rest of the steps

Edit: ninja'd by the sensei

Edit 2: To give a little more background info, we deleted the partition that we created when trying to install Ubuntu which is why there are 3 partitions (he's running Ubuntu from a live cd).

---

### Post by wilee-nilee on 2012-05-21
> **meijin3 said:**
> Open terminal (ctrl+alt+T) and copy&paste these commands into it and follow the rest of the steps

Edit: ninja'd by the sensei

Edit 2: To give a little more background info, we deleted the partition that we created when trying to install Ubuntu which is why there are 3 partitions (he's running Ubuntu from a live cd).
 
I suspected that.

---

### Post by vikingBoi on 2012-05-21
here it is, sorry it took a while had to do something

```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda1 starts at sector 63. The info in boot sector on 
                       the starting sector of the MFT is wrong. According to 
                       the info in the boot sector, sda1 has 407551 sectors, 
                       but according to the info from fdisk, it has 1984 
                       sectors.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 409600. But according to the info from 
                       fdisk, sda2 starts at sector 2048. The info in boot 
                       sector on the starting sector of the MFT is wrong. 
                       According to the info in the boot sector, sda2 has 
                       1119524863 sectors, but according to the info from 
                       fdisk, it has 407551 sectors.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 1119934464. But according to the info from 
                       fdisk, sda3 starts at sector 409600. According to the 
                       info in the boot sector, sda3 has 309260287 sectors, 
                       but according to the info from fdisk, it has 
                       1119524863 sectors.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  82 Linux swap / Solaris
/dev/sda3             409,600 1,119,934,463 1,119,524,864  42 SFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        A45092A05092792E                       ntfs       SYSTEM
/dev/sda2        F2DEC541DEC4FEBB                       ntfs       
/dev/sda3        9C08E50108E4DAF2                       ntfs       New Volume
/dev/sda4        D4D6A083D6A06786                       ntfs       RECOVERY
/dev/sda5        DE81-5B00                              vfat       HP_TOOLS
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

MFT Sector of sda1

00000000  46 49 4c 45 30 00 03 00  e0 22 10 00 00 00 00 00  |FILE0...."......|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  02 00 ff ff 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  62 50 54 91 31 fb cc 01  62 50 54 91 31 fb cc 01  |bPT.1...bPT.1...|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  62 50 54 91 31 fb cc 01  |........bPT.1...|
000000c0  62 50 54 91 31 fb cc 01  62 50 54 91 31 fb cc 01  |bPT.1...bPT.1...|
000000d0  62 50 54 91 31 fb cc 01  00 40 00 00 00 00 00 00  |bPT.1....@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  3f 00 00 00 00 00 00 00  |........?.......|
00000120  40 00 00 00 00 00 00 00  00 00 04 00 00 00 00 00  |@...............|
00000130  00 00 04 00 00 00 00 00  00 00 04 00 00 00 00 00  |................|
00000140  21 40 55 42 00 f8 ff ff  b0 00 00 00 50 00 00 00  |!@UB........P...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  01 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 20 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |. ..............|
00000180  08 10 00 00 00 00 00 00  21 01 54 42 21 01 fd fd  |........!.TB!...|
00000190  00 9b 3f 09 80 fa ff ff  ff ff ff ff 00 00 00 00  |..?.............|
000001a0  00 00 04 00 00 00 00 00  21 40 55 42 00 f8 ff ff  |........!@UB....|
000001b0  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 05 00  |....P.....@.....|
000001c0  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  21 01 54 42 21 01 fd fd  00 9b 3f 09 80 fa 02 00  |!.TB!.....?.....|
00000200
MFT Sector of sda2

00000000  46 49 4c 45 30 00 03 00  32 68 0d 70 01 00 00 00  |FILE0...2h.p....|
00000010  01 00 01 00 38 00 01 00  c8 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  56 01 ff ff 00 00 00 00  10 00 00 00 60 00 00 00  |V...........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  92 db 16 ab 2e fb cc 01  92 db 16 ab 2e fb cc 01  |................|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  92 db 16 ab 2e fb cc 01  |................|
000000c0  92 db 16 ab 2e fb cc 01  92 db 16 ab 2e fb cc 01  |................|
000000d0  92 db 16 ab 2e fb cc 01  00 40 00 00 00 00 00 00  |.........@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 50 00 00 00  01 00 40 00 00 00 01 00  |....P.....@.....|
00000110  00 00 00 00 00 00 00 00  bf e7 00 00 00 00 00 00  |................|
00000120  40 00 00 00 00 00 00 00  00 00 7c 0e 00 00 00 00  |@.........|.....|
00000130  00 00 7c 0e 00 00 00 00  00 00 7c 0e 00 00 00 00  |..|.......|.....|
00000140  33 20 c8 00 00 00 0c 42  a0 1f ff 46 32 02 00 ff  |3 .....B...F2...|
00000150  b0 00 00 00 70 00 00 00  01 00 40 00 00 00 05 00  |....p.....@.....|
00000160  00 00 00 00 00 00 00 00  08 00 00 00 00 00 00 00  |................|
00000170  40 00 00 00 00 00 00 00  00 90 00 00 00 00 00 00  |@...............|
00000180  08 80 00 00 00 00 00 00  08 80 00 00 00 00 00 00  |................|
00000190  31 01 ff ff 0b 11 01 ff  31 01 67 24 fe 31 01 44  |1.......1.g$.1.D|
000001a0  06 11 31 01 0e e7 2b 41  01 b8 2c 97 00 41 01 dc  |..1...+A..,..A..|
000001b0  fe 9d 04 41 01 f5 e8 fd  fb 41 01 04 3c fe 03 00  |...A.....A..<...|
000001c0  ff ff ff ff 00 00 00 00  01 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  31 01 ff ff 0b 11 01 ff  00 45 5c 08 80 fa 56 01  |1........E\...V.|
00000200

========= Devices which don't seem to have a corresponding hard drive: =========

sdb
```

---

### Post by wilee-nilee on 2012-05-21
No problem, there are several users on now that are really good at this lets wait for their comments as well.

 Do you have a recovery or install disc for the windows install if needed?

---

### Post by westie457 on 2012-05-21
Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  82 Linux swap / Solaris
/dev/sda3             409,600 1,119,934,463 1,119,524,864  42 SFS][/CODE]
Whoa there. MAJOR PROBLEM. Somehow your hard drive has been converted to 'Dynamic' which is Windows proprietry. Only Windows can work with it however not even Windows can install to the hard drive. It is possible to re-convert it back to a normal drive but is a task filled with danger to your files, ie - you might lose them completely.

Get all of your personal files off that hard drive and put them somewhere safe (dvd, USB drive or external hard drive.

Am now going to find the procedure to re-convert the partitions. worst-case scenario from here is to completely wipe the hard drive and reinstall everything including Windows.

If you have a recovery partition on the hard drive back that up as well. This is very important.

EDIT:

Have found what is probably the best thing to use here.
[http://www.partitionwizard.com/free-...n-manager.html](http://www.partitionwizard.com/free-...n-manager.html)

This is a free program and some people have had success using it. There is an on-line help section that covers disk conversion. The whole process is best done with Windows running. Cannot stress enough now how important it is to back things up in case it goes the way of the pear.

---

### Post by meijin3 on 2012-05-21
> **westie457 said:**
> Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  82 Linux swap / Solaris
/dev/sda3             409,600 1,119,934,463 1,119,524,864  42 SFS][/CODE]
Whoa there. MAJOR PROBLEM. Somehow your hard drive has been converted to 'Dynamic' which is Windows proprietry. Only Windows can work with it however not even Windows can install to the hard drive. It is possible to re-convert it back to a normal drive but is a task filled with danger to your files, ie - you might lose them completely.

Get all of your personal files off that hard drive and put them somewhere safe (dvd, USB drive or external hard drive.

Am now going to find the procedure to re-convert the partitions. worst-case scenario from here is to completely wipe the hard drive and reinstall everything including Windows.

If you have a recovery partition on the hard drive back that up as well. This is very important.

EDIT:

Have found what is probably the best thing to use here.
[http://www.partitionwizard.com/free-...n-manager.html](http://www.partitionwizard.com/free-...n-manager.html)

This is a free program and some people have had success using it. There is an on-line help section that covers disk conversion. The whole process is best done with Windows running. Cannot stress enough now how important it is to back things up in case it goes the way of the pear.

Can this be done without Windows running? The whole problem is that we can't boot into it in the first place.

---

### Post by vikingBoi on 2012-05-21
> **wilee-nilee said:**
> No problem, there are several users on now that are really good at this lets wait for their comments as well.

 Do you have a recovery or install disc for the windows install if needed?

i do have repair disk that you can make from your computer but it doesn't work because it says that a device is disabled. almost like the system recovery information can't be accessed just like windows. i can order a recovery disk from hp if needed though but it will cost money

---

### Post by wilee-nilee on 2012-05-21
> **vikingBoi said:**
> i do have repair disk that you can make from your computer but it doesn't work because it says that a device is disabled. almost like the system recovery information can't be accessed just like windows. i can order a recovery disk from hp if needed though but it will cost money

Did you perchance make a full backup, a full image off the HD?

With the HD being turned dynamic this may or may not be fixable, way beyond my knowledge area really.

Even the best at this stuff on the forum can at best give links on apps that work for some and not others, with a dynamic conversion.

If you have a full image back up you could slip that back in after after wiping the HD of the dynamic stuff, just an option so asking.

---

### Post by westie457 on 2012-05-22
Hi the program mentioned in my earlier post has an option to create a bootable CD. [http://www.partitionwizard.com/download.html](http://www.partitionwizard.com/download.html)

Do you have access to an external drive or another drive to use as internal? It **must** be the same size or bigger for this cloning operation, also make sure it has nothing of personal value on it because it will be wiped of all information and have the contents of the currently unusable hard drive written to it. Once the hard drive has been copied disconnect the original. We will be working on the copy. If the repair procedures work then they can be used on the original, if they fail then the original can be cloned again for the next step.

The command to use is something like this ```
dd if=/dev/sda of=/dev/sdb bs=4096
```
I am assuming here that SDA is the messed up drive and SDB is the extra one connected, ensure that you get this the right way round otherwise the wrong drive will be copied.

See ```
man dd
``` for more info.

Drive has been cloned, yes? Good.
Boot using the 'Partition Wizard' cd you created earlier and convert the partitions back to 'Primary'. If successful try to boot the converted drive into Windows. You will know if the conversion is successful because Windows will throw a fit because some of the hardware has changed. This is normal behaviour from Windows. The next stage will be to repeat the procedure on the original drive.

Post back here with the news, good or bad for the next installment.

---

### Post by meijin3 on 2012-05-22
Hey guys, thank you so much for your help! We ended up buying a restore disc from HP and backed up all the files. We're going to re-image the computer and start over. Thanks so much for your time!

---

### Post by wilee-nilee on 2012-05-22
> **meijin3 said:**
> Hey guys, thank you so much for your help! We ended up buying a restore disc from HP and backed up all the files. We're going to re-image the computer and start over. Thanks so much for your time!

Cool, enjoy. ;)

---

