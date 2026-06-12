---
title: "Spontaneous deletion or invisible lurking?"
date: 2011-06-10
forum: General Help
---

### Post by merely on 2011-06-10
Greetings to you all. This is my first post. Apologises if I sound  rankly newbieish - I have very little understanding of the subsystems of  computers. I would struggle with DOS (though maybe triumph with a good  guide and sustained application).

So: - I tired of Windows last month, and decided to take the plunge into  Ubuntu. The installation went well, and I have been using version 11.04  ever since, keeping Windows on my computer in case I needed another OS  for some reason. 

Yesterday evening, disaster struck. My laptop froze -  this does happen  from time to time, but never before to such ill effect as what hapened  when I rebooted it. For I was deposited in a netherworld called GNU  Grub. 

I get the impression that it cannot locate some necessary 'kernel'. I believe it has said so a few times. I've no clue how to locate the drive it is on, or to tell the Grub where that is. Or...how to express to it my wish that it load it once it knows. 

Anyway, I read that ubuntu might be repairable if I prepared a windows  live cd. I used a pendrive instead, and was able to boot it from there.  However, investigating all the folders and drives recognised by  Nautilus, although I see those of Windows I do not see those of my  already-installed ubuntu. Where are they?

At one point I wished to see what happened if I tried to reinstall from  that pendrive. It was claimed that I would first have to uninstall a  copy already in place. Why is it recognising that it exists, yet not  allowing me to see its documents in nautilus, for all that it  acknowledges windows' folders?

Sorry if this is a bit wandering. My question condenses to: I really,  really would like to get past GNU Grub and save my files. Can any of you  provide any suggestions? I would be very grateful.

---

### Post by Rubi1200 on 2011-06-10
Hi and welcome to the forums :-)

To help us get a better overview of what is going on please do the following:

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

### Post by merely on 2011-06-10
Hello again. Thank you for your directions - it was a great relief to enter a command and for what you predicted to occur.

I did not end up opening 'Try ubuntu without any changes', because it was not among the prompts. 'Run ubuntu from usb' is hopefully very similar?

The contents of RESULTS.txt are:

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => HP/Gateway is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /Boot/bcd

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........,.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 1418004 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   216,578,047   216,577,985   7 NTFS / exFAT / HPFS
/dev/sda2         216,578,048   231,176,191    14,598,144   7 NTFS / exFAT / HPFS
/dev/sda3         231,184,384   234,438,655     3,254,272   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8039 MB, 8039300608 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15701759 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             44    15,679,439    15,679,396   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2098605C60385D0F                       ntfs       
/dev/sda2        CE2ACD972ACD7CC9                       ntfs       HP_RECOVERY
/dev/sda3        44F85166F8515770                       ntfs       OS_TOOLS
/dev/sdb1        6016-C08A                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/2098605C60385D0F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/OS_TOOLS          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sr0         /media/BBCDVD2508        udf        (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,umask=0077,dmode=0500)


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
            ?? = ??             syslinux/vesamenu.c32                          2

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected



Does it look possible to recover my documents?

(Apologies, I seem to have used the code tags wrongly. I see how I should have done it now, but there seems no redress in editing.)

---

### Post by Rubi1200 on 2011-06-10
Thanks for posting the results. First, I will explain what I see in the results and then outline what I think you need to do to achieve what you want.

So, you have Windows installed with the remnants of either a failed Wubi install or a damaged Wubi install:
Here it is on sda1:
> Boot files:        /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr
You are missing the root.disk and swap.disk that Wubi needs to boot the Ubuntu install.

Based on what you posted the first time round, I suspect those files have been moved by Windows possibly after a disk check.

To confirm this, boot into Windows and enable the Hidden Files and Folders option as the first step:
[http://www.howtogeek.com/howto/windows-vista/show-hidden-files-and-folders-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/show-hidden-files-and-folders-in-windows-vista/)

Once that is done, go to the root of the C drive and look for a folder called something like C:\found.000

If the root.disk and swap.disk files are there we can move them back. If not, you need to use the search function to try and find them:
[http://windows.microsoft.com/en-US/windows-vista/Tips-for-finding-files](http://windows.microsoft.com/en-US/windows-vista/Tips-for-finding-files)

If you do find the files, please put them back in the Ubuntu folder at the root of the C drive using the following structure:
\ubuntu\disks\root.disk
\ubuntu\disks\swap.disk 

After this, make a copy of the root.disk and put it somewhere safe such as an external medium.

You should now be able to reboot and access the Ubuntu installation.

---

### Post by merely on 2011-06-12
Thank you so much, your advice worked perfectly!

Most grateful.

---

### Post by Rubi1200 on 2011-06-12
No problem, you are more than welcome :D

Enjoy!

---

