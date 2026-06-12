---
title: "Help! &quot;error: no such partition. grub rescue&gt;&quot;"
date: 2011-10-12
forum: General Help
---

### Post by alecforrester on 2011-10-12
Hello, I'm a relatively new Ubuntu user. I'm using an HP Mini 210 netbook with a dual boot, Windows 7 Starter and Ubuntu (Natty Narwhal). When I attempt to boot my computer, I briefly see an HP splash screen, followed by the message "error: no such partition. grub rescue>". I've been reading other threads on this forum, and most people seemed to have this problem when uninstalling/installing/recovering an operating system used in their dual boot- for me, it happened completely randomly. Since my netbook doesn't have a CD drive, is there software I can boot off a flash drive to fix this problem? will it require reformatting or reinstalling windows or ubuntu? What does this error message mean, and how do I fix it? Any help would be greatly appreciated!!!

---

### Post by Rubi1200 on 2011-10-13
Hi and welcome to the forums :)

Is this a Wubi install?

You can download the ISO image of Ubuntu and install it to a USB stick:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
(there are instructions on that page how to do this).

Now, boot the computer in live mode and post the results of the boot info script (there is a link at the bottom of my post with instructions).

Thanks.

---

### Post by alecforrester on 2011-10-13
Hi Rubi!

   Thanks for responding, I'm loving Ubuntu (besides this current problem) so far, and I'm eager to learn more about it. I'm not sure what a Wubi install is. When I first installed Ubuntu about 6 months ago, I partitioned my hard drive and installed Ubuntu from a USB stick. It's been working fine since then, until the other day when I tried to boot and got the above message. So I should re-download the Ubuntu image and run it live off the USB stick instead of installing it to the computer? And the boot info script- I see the link, is that just a diagnostic reporting tool, or is it a piece of necessary software? I'm about to start the download now and give it a shot, I will report back with the results from  the boot info script.
    Thank you very much for taking the time to help me out, I really appreciate it!

                -Alec


> **Rubi1200 said:**
> Hi and welcome to the forums :)

Is this a Wubi install?

You can download the ISO image of Ubuntu and install it to a USB stick:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
(there are instructions on that page how to do this).

Now, boot the computer in live mode and post the results of the boot info script (there is a link at the bottom of my post with instructions).

Thanks.

---

### Post by experience on 2011-10-14
I ended up to the same problem. I am also using HP, mine is HP Envy 17, with RAID-0 disk. I suspect that is causing the problem.

Ubuntu 11.04 doesn't have problem booting. I have tried directly install from a USB stick, or Upgrade from a fresh install of Ubuntu 11.04. The result is same. And I also tried to fix the grub using LiveCD. However, it gives error:
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

/dev is actually mounted, the disk of my is
/dev/mapper/isw_jdbdbhajd_RAID-0
/dev/mapper/isw_jdbdbhajd_RAID-0p1
/dev/mapper/isw_jdbdbhajd_RAID-0p2
/dev/mapper/isw_jdbdbhajd_RAID-0p3
/dev/mapper/isw_jdbdbhajd_RAID-0p5
/dev/mapper/isw_jdbdbhajd_RAID-0p6

Ubuntu is installed in p5.

Thanks!

---

### Post by Rubi1200 on 2011-10-15
@alecforrester: the boot script is a diagnostic tool and can help us determine what is going on.

---

### Post by alecforrester on 2011-11-13
> **Rubi1200 said:**
> @alecforrester: the boot script is a diagnostic tool and can help us determine what is going on.


Rubi,
  
         Sorry about the delay, I've been real busy the past few weeks. I loaded Ubuntu through a USB stick as instructed, here is the results of the boot info script. Let me know if you can help me get this thing back up and running!

            Thanks again!
                       -Alec



                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       exfat
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'exfat'

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 6295296 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   201,350,671   200,941,072   7 NTFS / exFAT / HPFS
/dev/sda3         201,351,166   452,673,535   251,322,370   f W95 Extended (LBA)
/dev/sda5         299,073,536   452,673,535   153,600,000   7 NTFS / exFAT / HPFS
/dev/sda4         452,673,536   488,183,807    35,510,272   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     7,821,311     7,821,280   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3A46D1AA46D166E3                       ntfs       SYSTEM
/dev/sda2        E4167B7D167B5012                       ntfs       
/dev/sda4        76168C29168BE887                       ntfs       RECOVERY
/dev/sda5        5A88-B5FF                              exfat      New Volume
/dev/sdb1        9802-9C91                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda5

00000000  eb 76 90 45 58 46 41 54  20 20 20 00 00 00 00 00  |.v.EXFAT   .....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000040  00 80 d3 11 00 00 00 00  00 c0 27 09 00 00 00 00  |..........'.....|
00000050  00 08 00 00 00 13 00 00  00 20 00 00 a0 27 09 00  |......... ...'..|
00000060  04 00 00 00 ff b5 88 5a  00 01 00 00 09 08 01 80  |.......Z........|
00000070  00 00 00 00 00 00 00 00  33 c9 8e d1 bc f0 7b 8e  |........3.....{.|
00000080  d9 a0 fb 7d b4 7d 8b f0  ac 98 40 74 0c 48 74 0e  |...}.}....@t.Ht.|
00000090  b4 0e bb 07 00 cd 10 eb  ef a0 fd 7d eb e6 cd 16  |...........}....|
000000a0  cd 19 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  0d 0a 52 65 6d 6f 76 65  20 64 69 73 6b 73 20 6f  |..Remove disks o|
00000110  72 20 6f 74 68 65 72 20  6d 65 64 69 61 2e ff 0d  |r other media...|
00000120  0a 44 69 73 6b 20 65 72  72 6f 72 ff 0d 0a 50 72  |.Disk error...Pr|
00000130  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 72  |ess any key to r|
00000140  65 73 74 61 72 74 0d 0a  00 00 00 00 00 00 00 00  |estart..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 ff ff  |................|
000001c0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001f0  ff ff ff ff ff ff ff ff  ff ff ff 00 1f 2c 55 aa  |.............,U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Documents/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
```

---

### Post by Rubi1200 on 2011-11-13
Thanks for posting the results of the script.

What is the current status of the situation?

Are you able to boot into Windows?

I assume not, but please confirm.

You appear to have GRUB installed to the MBR but it is not pointing anywhere.

You will need to repair the Windows boot sector first before anything else.

Check with the manufacturer how to use the recovery partition to rebuild the boot sector and thus boot Windows again then we can move from there.

Let me know if you need additional assistance.

---

### Post by alecforrester on 2011-11-13
> **Rubi1200 said:**
> Thanks for posting the results of the script.

What is the current status of the situation?

Are you able to boot into Windows?

I assume not, but please confirm.

You appear to have GRUB installed to the MBR but it is not pointing anywhere.

You will need to repair the Windows boot sector first before anything else.

Check with the manufacturer how to use the recovery partition to rebuild the boot sector and thus boot Windows again then we can move from there.

Let me know if you need additional assistance.


Rubi, 

    I am not able to boot into either Windows or Ubuntu. When I turn the netbook on, I see a brief HP splash screen, and then when I would normally see the Grub interface i see the error message instead. So I'd have to reformat the netbook, reinstall windows, and then reinstall Ubuntu?

     Thanks again!

            -Alec

---

### Post by Rubi1200 on 2011-11-13
No, no.

First let's see if you can fix this before considering a complete reinstall.

See this link first:
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

And also this one:
[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=uk&docname=c01895783](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=uk&docname=c01895783)

I don't use Windows, but if you wait a bit I will ask some other users to also comment.

---

### Post by oldfred on 2011-11-13
You should just be able to install a Windows boot loader to the MBR. How did grub get into the MBR as you have wubi and wubi boots thru the Windows boot loader in the MBR of sda.

Do you have the Windows repairCD or a Linux repair or live CD or USB? You can repair Windows from a Windows repairCD or you can install a boot loader that works like the Windows boot loader in the MBR.

---

