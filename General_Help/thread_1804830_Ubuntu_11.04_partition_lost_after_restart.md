---
title: "Ubuntu 11.04 partition lost after restart"
date: 2011-07-15
forum: General Help
---

### Post by sotstas on 2011-07-15
Hey there everybody,

I am new to the forum, although I have used Ubuntu for quite a while. I decided to join as i experienced this issue I cannot resolve.

I initially installed Ubuntu 10.10 on my laptop through wubi some months ago, along with my Windows Vista and was able to dualboot just fine. In the first screen I got the Windows Vista/Ubuntu option and after selecting Ubuntu it went to grub options of different Ubuntu releases. Then about 2 months ago updated to 11.04. Still everything worked ok, but sometimes when trying to shut down or restart, instead of getting to the normal 'Shut down' messages, it went to a black screen. I shut down the laptop manually many times and still didn't have any problem when I rebooted. Until yesterday...

After a another manual shut down, now, I get the first screen of Windows Vista/Ubuntu, but when I choose Ubuntu the grub prompt command line appears. I have looked into several topics about resolving it, but I finally realised that the Ubuntu partition had disapeared. 

When using ls, the only partitions shown were the ntfs ones.
I started the LiveUsb of my initial 10.10 and went on Terminal to use sudo fdisk -lu and the only bootable devices shown are still the ntfs ones (I have 2 250GB partitions).

Any advice on how to recover my Ubuntu partition? I simply can't believe it was destryed somehow, right?

Thx in advance.

---

### Post by Rubi1200 on 2011-07-15
Hi and welcome to the forums :-)

Please do the following so we can get a better overview of what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by sotstas on 2011-07-18
Ok, this is what comes after I do as you instructed (although, this proves that it can't find my partition-my Live USB is in sdc)

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => HP/Gateway is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /boot/bcd /wubildr /wubildr.mbr

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 2010-07-21 ........>4..r>..........@...0...~.s...~...f...M.f.f....f..0~....>2}.u......
    Boot sector info:   Syslinux looks at sector 8224 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   472,254,463   472,254,401   7 NTFS / exFAT / HPFS
/dev/sda2         472,254,464   488,390,655    16,136,192   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 3980 MB, 3980394496 bytes
9 heads, 9 sectors/track, 95977 cylinders, total 7774208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          8,064     7,774,207     7,766,144   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        BA06A9BB06A978D1                       ntfs       OS
/dev/sda2        AE0A68520A68199B                       ntfs       HP_RECOVERY
/dev/sdb1        E48883EE8883BE14                       ntfs       DATA
/dev/sdc1        96DE-D9F9                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

./boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
```

---

### Post by bcbc on 2011-07-18
Manual shutdowns are really not a good idea (at any time, or on any OS). For Wubi they can be deadly as the "partition" is virtual: it's actually a single file (root.disk).

So likely it's been damaged. In the best scenario, Windows ran a chkdsk and recovered it. 

Windows moves recovered files to a directory: C:\found.000
On my windows 7 I had to change the explorer options to show hidden files and ALSO to not "Hide protected OS files" to even see this. There may be a found.000 on C:\ and also on the 'drive' you installed to. 

Look inside there and try to find the root.disk or a file called file0000.chk that matches the size of the root.disk (your Ubuntu partition)

If you can't see these, then you should run chkdsk yourself (on the windows 'drive' you installed it to) to see if it can be recovered.
From Computer, right-click on the drive you installed to, properties, Tools, check for errors, fix automatically.

You're looking to recreate the \ubuntu\disks directory and inside it there should be a root.disk (between 5-32 GB) and a swap.disk (250MB)

---

### Post by sotstas on 2011-07-19
First of all, thank you Rubi1200 ans bcbc for your answers! :)

I managed to find the dir0000.chk folder that includes the root.disk and swap.disk. Then, I created the ubuntu/disks folder once again as you instructed.

However, inside the dir0000.chk folder also exists the boot folder that includes grub. Where should I place that file?

---

### Post by bcbc on 2011-07-19
That's great news... unfortunately many people haven't been as fortunate.

The boot folder is an unused relic from the days when wubi used grub legacy (last release 9.04), but it normally goes in the disks directory:
\ubuntu\disks\boot

Full structure (including disks):

```
 Volume in drive C is OS
 Volume Serial Number is B4B7-99A8

 Directory of C:\ubuntu\disks

30/06/2011  09:21 PM    <DIR>          .
30/06/2011  09:21 PM    <DIR>          ..
14/06/2011  03:28 PM    <DIR>          boot
18/07/2011  09:27 PM    25,000,000,000 root.disk
14/06/2011  08:34 AM       268,435,456 swap.disk

 Directory of C:\ubuntu\disks\boot

14/06/2011  03:28 PM    <DIR>          .
14/06/2011  03:28 PM    <DIR>          ..
14/06/2011  03:28 PM    <DIR>          grub
               0 File(s)              0 bytes

 Directory of C:\ubuntu\disks\boot\grub

14/06/2011  03:28 PM    <DIR>          .
14/06/2011  03:28 PM    <DIR>          ..
               0 File(s)              0 bytes

```

PS for future reference - [this]("https://wiki.ubuntu.com/WubiGuide#How_to_reboot_cleanly_even_when_the_keyboard.2BAC8-mouse_are_frozen") is how to shutdown an unresponsive Wubi.

---

### Post by Rubi1200 on 2011-07-19
Just to add to what bcbc said, make a backup copy of the root.disk and save it to an external medium for safety.

Then, if this ever happens again, you can just move it back.

---

### Post by sotstas on 2011-07-19
Posting through my good old Ubuntu! :)

Thank you an amazingly great deal bcbc and Rubi1200!

You and the forums rock! :guitar:

---

### Post by Rubi1200 on 2011-08-01
Hi,
sorry for the delayed response; been super busy at work.

We are really pleased this worked for you and I hope you enjoy all your Ubuntu experiences.

Good luck :)

---

