---
title: "cant boot to win7 from grub / win7 partition doesn't appear in ubuntu"
date: 2011-08-23
forum: General Help
---

### Post by joshuav on 2011-08-23
i have ubuntu 10 and win 7 dual booting on one hdd, all of a sudden grub says error no such partition when i select windows at the boot menu. 

and i cant get to the win7 partition from ubuntu 
(to play music and stuff, this used to work, places, mount filesystem, 250 gigs whatever). 

i've tried the stuff in these links and nothing has worked so far

[http://unnigg.in/blog/2010/11/25/windows-7-boot-option-missing-in-grub-ubuntu-10-04/](http://unnigg.in/blog/2010/11/25/windows-7-boot-option-missing-in-grub-ubuntu-10-04/)

[http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/](http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/)

partition info

sudo fdisk -l /dev/sda

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       29094   233697523+   7  HPFS/NTFS
/dev/sda2   *       29095       30401    10498477+  83  Linux

so any help would be great, thanks

edit: if nothing else works is there a safe way to remove grub and just immediately boot to windows?

---

### Post by oldfred on 2011-08-23
Sometimes windows needs a chkdsk. Can you get to the repair mode by pressing f8 as soon as you click on windows in grub. Some said it is difficult to "catch" the f8 key with grub chainload as it is quick.

Post this to see if you have other issues.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.


If you want to repair or boot Windows you have to have the boot flag (active partition) on the windows partition sda1. Grub does not use boot flag. You can use gparted, Disk Utility or command line to move boot flag.
#set boot flag on for sda1 (off on others):
sudo sfdisk -A1 /dev/sda

---

### Post by joshuav on 2011-08-23
i used 'sudo sfdisk -A1 /dev/sda' and it moved the boot flag so now it goes straight to windows, and that's good enough for now.

thanks for the help :)

---

### Post by loolooyyyy on 2011-08-23
> **joshuav said:**
> i used 'sudo sfdisk -A1 /dev/sda' and it moved the boot flag so now it goes straight to windows, and that's good enough for now.

thanks for the help :)

if you want your ubuntu back use the live disc move the boot flag back
run ubuntu and do a "sudo update-grub"

---

### Post by oldfred on 2011-08-23
Grub does not use boot flag, leave it on the windows partition.

But you will have to reinstall grub2's boot loader to the MBR.

Basically the same instructions in all three of these:
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by joshuav on 2011-09-11
bump!

on a live usb right now.

same kind of problem again, i booted to a ubuntu live install usb to test it and when i restarted it didn't boot back in to win7.

so i came back to the usb and changed the boot flag but that didn't work.

and i'm worried about my data on the win7 drive, i can't mount it in ubuntu so i can't back it up.

it shows up in disk utility as unknown 250 drive or whatever and gparted says that's were the boot flag is.

help

---

### Post by YesWeCan on 2011-09-11
Would you post the RESULTS.txt from running this
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
It will show the details of your boot set-up and will allow us to diagnose the problem much more quickly. :)

---

### Post by joshuav on 2011-09-11
results 

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......sb.:...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 15264 of /dev/sdb1 for its 
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

/dev/sda1    *             63   467,395,109   467,395,047   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2004 MB, 2004877312 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     3,913,191     3,913,130   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL


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
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
cat: /tmp/BootInfo0/BLKID_summary: No such file or directory

---

### Post by oldfred on 2011-09-12
Did you delete the Linux partition with testdisk or something else? Or do you have partition table issues also.

Ubuntu will not mount a NTFS partition that needs chkdsk. Did you run that as suggested before? Does f8 from the lilo boot get you to a Windows repair screen. You have to run & rerun chkdsk until there are no errors as it does not fix everything on one pass.

If you have another Windows or know someone that does you can make a repairCD to run the chkdsk.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

