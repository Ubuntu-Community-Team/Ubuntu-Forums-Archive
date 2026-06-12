---
title: "Ubuntu's Drawback For Me."
date: 2011-07-26
forum: General Help
---

### Post by aakash_scsa_hellyeah on 2011-07-26
Hey Guys, today ubuntu (installed 11.04) really disappointed me.
I was using Windows seven since many months without any problem and a friend of mine suggested me to try UBUNTU thing.
In my desktop pc i have
Pentium Core2Duo
2 SATA 320 GB (Samsung & WD)
4GB RAM
Windows 7 Is installed on WD SATA
I installed UBUNTU 11.04 from USB installer (universal usb installer) and ISO image (Downloaded from UBUNTU website)
Installer displayed an option to install UBUNTU along with existing  Windows without making changes to existing data on drive. - I preferd  choosing this option..
No other detail were given and installer began to install UBUNTU.
After the installation was complete and Ubuntu boot up to with no error i  found that all the partitions of my second hard drive (samsung SATA)  were removed and it Disk Utility shows single Ext4 version 1.0 type  Linux Basic Data partition of 
Device: /dev/sda2
Capacity:  318GB
Available :  -
Mount Point:  Mounted at /
.............................:confused::mad::mad:
Since then i havent done anything to that har disk with a hope that i'll get all my data back cause i really need it..
......................................
I am expecting a good response from help team for this post.. THANK YOU

---

### Post by bodhi.zazen on 2011-07-26
> **aakash_scsa_hellyeah said:**
> Hey Guys, today ubuntu (installed 11.04) really disappointed me.
I was using Windows seven since many months without any problem and a friend of mine suggested me to try UBUNTU thing.
In my desktop pc i have
Pentium Core2Duo
2 SATA 320 GB (Samsung & WD)
4GB RAM
Windows 7 Is installed on WD SATA
I installed UBUNTU 11.04 from USB installer (universal usb installer) and ISO image (Downloaded from UBUNTU website)
Installer displayed an option to install UBUNTU along with existing  Windows without making changes to existing data on drive. - I preferd  choosing this option..
No other detail were given and installer began to install UBUNTU.
After the installation was complete and Ubuntu boot up to with no error i  found that all the partitions of my second hard drive (samsung SATA)  were removed and it Disk Utility shows single Ext4 version 1.0 type  Linux Basic Data partition of 
Device: /dev/sda2
Capacity:  318GB
Available :  -
Mount Point:  Mounted at /
.............................:confused::mad::mad:
Since then i havent done anything to that har disk with a hope that i'll get all my data back cause i really need it..
......................................
I am expecting a good response from help team for this post.. THANK YOU

Well, first I am sorry you are having problems, hopefully there is a simple fix.

However, it is not Ubuntu's fault if you did not understand the installation process. Usually the first thing I advise when installing a new OS is to back up your data. Backups are good advice even if you are not installing a new OS.

Second step is to understand partitioning. Windows uses letters, Linux uses /dev/sda and your second disk should be at /dev/sdb

See : [http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning](http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning)

Do you see your data if you boot Windows ?

From Ubuntu, post the output of 

```
fdisk -l
```

Hopefully it is simply a matter of mounting your second hard drive and your data is intact.

---

### Post by Quackers on 2011-07-26
Presumably Windows 7 was on /dev/sda (the first hard drive in the bios)?
It seems that you may have installed Ubuntu on to the same drive, by mistake. The "install alongside" option should not have been chosen as that installs Ubuntu on the same drive.
The correct choice was to choose "something else" option and install Ubuntu to what was presumably /dev/sdb.
You should stop using Ubuntu immediately and boot from the live cd/usb and choose "try Ubuntu" so that no more writing to /dev/sda takes place.
In fact, I would suggest that you disconnect the second hard drive for the moment and just leave the one that had Windows on it.

You can then use "testdisk" to recover the partitions now lost.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

The best guide for using testdisk is this one by forum user Herman

[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

Also see above post first!

---

### Post by Joris Donders on 2011-07-26
[Installer displayed an option to install UBUNTU along with existing  Windows without making changes to existing data on drive.]

This is something the installer DOESN'T show; or you can try out Ubuntu on your pc without installing anything or you can let the installer do it's thing for making a dual-boot (Windows - Ubuntu), or you can select to whipe the disk and install only Ubuntu.

I think you've taken a bad option for you, but may I suggest that you first read some pages (about installing Ubuntu) from the Wiki before you just begin doing things you regret afterwards. 

For starters you've got to check what has happened now; is Windows still on your harddrive or did the installer from Ubuntu erase the entire disc ?

---

### Post by bodhi.zazen on 2011-07-26
> **Quackers said:**
> Presumably Windows 7 was on /dev/sda (the first hard drive in the bios)?

I clipped your post, the OP is looking for the second hard drive which should be sdb, not sda

> **aakash_scsa_hellyeah said:**
> i  found that all the partitions of my **second hard drive** (samsung SATA)

bold added by me for emphasis ;)

---

### Post by aakash_scsa_hellyeah on 2011-07-26
Thanks For The reply..
Actually now i have disconnected my first hard disk (WD SATA) and running UBUNTU directly from Samsung Disk in which data is lost that is why disk utility showing it as /dev/sda..
and yes when i checked the disk on Windows 7 it showed up only single partition of Samsung disk and giving message the disk is not formatted, do you want to format it?
And i simply clicked NO.

---

### Post by alphaamanitin on 2011-07-26
I think you will have some luck with TestDisk.  I deleted all the partitions off of my XP machine and then reformatted it to FAT32, and still managed to recover the entire drive using TestDisk.  And not just recover like copy the files to a new hard drive, I restored the hard drive's original partition table, used supergrub to restore the Windows XP bootloarder and had my machine back like nothing happened.  

I used the guide provided on the TestDisk website: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

AlphaA

---

### Post by Quackers on 2011-07-26
Ok, I'm a little lost as to what the OP is asking then. 
Presumably Windows was on sda (as it would be the only drive in there at first).
Unless the bios has been altered (no mention of that) the system can't have booted from sdb, and yet Ubuntu has booted up "directly". So Ubuntu must have gone on sda, it seems to me. 
That's why I don't understand about the second hard drive question.

So do you think sudo update-grub will find Windows? I wonder :-)

---

### Post by bodhi.zazen on 2011-07-26
> **aakash_scsa_hellyeah said:**
> Thanks For The reply..
Actually now i have disconnected my first hard disk (WD SATA) and running UBUNTU directly from Samsung Disk in which data is lost that is why disk utility showing it as /dev/sda..
and yes when i checked the disk on Windows 7 it showed up only single partition of Samsung disk and giving message the disk is not formatted, do you want to format it?
And i simply clicked NO.

Hard to give you advice if you will not post the information I requested.

My understanding is that you have two hard drives ? The first hard drive was removed ? You then installed Ubuntu ? Onto the second disk ?

Honestly I have seen more problems when users think they are smart, and start swapping hard drives, but they really do not understand what they are doing, do not bother learn how grub or partitions work, and the result is data loss.

If you wish any hope of data recovery:

1. Stop running Ubuntu. When you keep running Ubuntu from the hard drive you risk continued data loss as Ubuntu writes to the disk.

2. Plug in both hard drives.

3. Stop and read the link I gave you on partitioning.

4. Boot the live USB, unmount the swap, and run the command I gave you.

```
fdisk -l
```

5. Describe your two disks and what you expect to find on each, what were your original partitions ?

---

### Post by Mark Phelps on 2011-07-26
You're not the only person who has found the new installer to be confusing, and not the only person to have accidentally wiped out their Win7 install in the process.

However, and this is IMPORTANT, if you do not STOP using the overwritten Windows drive right now, you run the risk of not being able to recovery ANYTHING.

You need to remove that drive from your PC, find another PC, and connect the drive to that one -- so that you're not actually writing to the overwritten drive anymore.

Your path after that is up to you.  Some folks have used Testdisk and Photorec and have had really good results.  Others (like me) have had really poor results and resorted to using "native apps" to recover filesystems: MS Windows apps for MS Windows filesystems; Linux apps for Linux filesystems.

If you try Testdisk/Photorec and don't get good results, consider doing the following:
1) Connect the overwritten drive to an MS Windows PC
2) Download and install GetDataBack for NTFS from Runtime Software on that PC
3) Run GetDataBack and let it do an in-depth scan -- leaving it overnight is best.
4) If it finds the directories and files you want, you will have to purchase it to do the actual recovery.

---

### Post by aakash_scsa_hellyeah on 2011-07-26
> **Quackers said:**
> Ok, I'm a little lost as to what the OP is asking then. 
Presumably Windows was on sda (as it would be the only drive in there at first).
Unless the bios has been altered (no mention of that) the system can't have booted from sdb, and yet Ubuntu has booted up "directly". So Ubuntu must have gone on sda, it seems to me. 
That's why I don't understand about the second hard drive question.

So do you think sudo update-grub will find Windows? I wonder :-)
Exactly what i did is:
1. I was having Win7 on WD SATA drive.
2. Another drive i.e SAMSUNG SATA was also connected.
3. I made USB installation disk using UNIVERSAL USB INSTALLER.
4. Boot From USB.
5. Installed UBUNTU by selecting option "install alongside".
6. After installation when i found the partitions of SAMSUNG drive missing, i turned off my PC.
7. Boot up Windows 7. I showed All partition of WD SATA but only ! partition of SAMSUNG SATA which was asking to format it( I Disagreed to Format Prompt),
8. Disconnected WD SATA.
9. Booted UBUNTU from SAMSUNG SATA.
10. Then I started this post to get help to recover my data exactly as it was on my disk drive.

---

### Post by Quackers on 2011-07-26
Possibly the easiest way to solve all the questions is to connect both hard drives as they were before and then boot from the Ubuntu live cd/usb and connect to the internet then go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by aakash_scsa_hellyeah on 2011-07-26
```

```                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 34 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt2)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdb6 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdb7 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sdc: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 15384 of /dev/sdc for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   625,142,447   625,142,447  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34         1,987         1,954 BIOS Boot partition
/dev/sda2           1,988   621,214,878   621,212,891 Data partition (Windows/Linux)
/dev/sda3     621,214,879   625,142,398     3,927,520 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848   102,903,807   102,696,960   7 NTFS / exFAT / HPFS
/dev/sdb3         102,903,808   205,805,567   102,901,760   7 NTFS / exFAT / HPFS
/dev/sdb4         205,805,568   625,139,711   419,334,144   f W95 Extended (LBA)
/dev/sdb5         205,807,616   308,709,375   102,901,760   7 NTFS / exFAT / HPFS
/dev/sdb6         308,711,424   411,613,183   102,901,760   7 NTFS / exFAT / HPFS
/dev/sdb7         411,615,232   625,139,711   213,524,480   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        084b67d7-8a65-4e48-a23d-3a91577135fe   ext4       
/dev/sda3        2cedfcaf-ce1e-4dbb-8c3c-0c646fb272d9   swap       
/dev/sdb1        8E14339A1433846D                       ntfs       System Reserved
/dev/sdb2        6A684A246849EEFF                       ntfs       
/dev/sdb3        060C6DCA0C6DB579                       ntfs       
/dev/sdb5        F68CFCDB8CFC9779                       ntfs       New Volume
/dev/sdb6        E868048B68045B28                       ntfs       New Volume
/dev/sdb7        385437255436E4F2                       ntfs       New Volume
/dev/sdc         18E9-3A32                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc         /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt2)'
search --no-floppy --fs-uuid --set=root 084b67d7-8a65-4e48-a23d-3a91577135fe
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt2)'
search --no-floppy --fs-uuid --set=root 084b67d7-8a65-4e48-a23d-3a91577135fe
set locale_dir=($root)/boot/grub/locale
set lang=en_IN
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root 084b67d7-8a65-4e48-a23d-3a91577135fe
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=084b67d7-8a65-4e48-a23d-3a91577135fe ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root 084b67d7-8a65-4e48-a23d-3a91577135fe
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=084b67d7-8a65-4e48-a23d-3a91577135fe ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root 084b67d7-8a65-4e48-a23d-3a91577135fe
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root 084b67d7-8a65-4e48-a23d-3a91577135fe
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 8E14339A1433846D
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 204.134981155 = 219.188267008  boot/grub/core.img                             1
 134.138189316 = 144.029784064  boot/grub/grub.cfg                             1
 206.321260452 = 221.535766528  boot/initrd.img-2.6.38-8-generic               3
 204.133253098 = 219.186411520  boot/vmlinuz-2.6.38-8-generic                  1
 206.321260452 = 221.535766528  initrd.img                                     3
 204.133253098 = 219.186411520  vmlinuz                                        1

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 
--------------------------------------------------------------------------------

========================== sdc/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================== sdc: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

=============== sdc: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

---

### Post by aakash_scsa_hellyeah on 2011-07-26
> **Quackers said:**
> Possibly the easiest way to solve all the questions is to connect both hard drives as they were before and then boot from the Ubuntu live cd/usb and connect to the internet then go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
What Now????
THANK YOU

---

### Post by bodhi.zazen on 2011-07-26
> **aakash_scsa_hellyeah said:**
> What Now????
THANK YOU

First, please do not post (dump) output of commands as in your last post, attach it as a file.

Second, who are you asking ? Since you are not following my advice, I will leave you to Quackers. Quackers is competent and can help you.

If you get stuck, let me know.

---

### Post by Quackers on 2011-07-26
Ok thanks.
All your partitions are still there it seems, both Ubuntu and Windows :-)

There may be difficulties due to the fact that /dev/sda (your Ubuntu drive) has a GUID Partition Table, but /dev/sdb (your Windows drive) does not.
I'm not sure how the two will interact with each other and grub.

All I can suggest is that you reboot and, after making sure that your bios is set to boot the Ubuntu drive before the Windows drive, boot the system.

Ubuntu should boot directly, as it did earlier.
When it does, open up a terminal and run ```
sudo update-grub
``` and watch the screen as grub.cfg is configured.
You should see the Windows Loader recognised. If you do, reboot and you should get a grub menu giving you the choice of which operating system to boot.

---

### Post by kansasnoob on 2011-07-26
> **Quackers said:**
> Presumably Windows 7 was on /dev/sda (the first hard drive in the bios)?
It seems that you may have installed Ubuntu on to the same drive, by mistake. The "install alongside" option should not have been chosen as that installs Ubuntu on the same drive.
The correct choice was to choose "something else" option and install Ubuntu to what was presumably /dev/sdb.
You should stop using Ubuntu immediately and boot from the live cd/usb and choose "try Ubuntu" so that no more writing to /dev/sda takes place.
In fact, I would suggest that you disconnect the second hard drive for the moment and just leave the one that had Windows on it.

You can then use "testdisk" to recover the partitions now lost.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

The best guide for using testdisk is this one by forum user Herman

[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

Also see above post first!

**[COLOR="Red"]Oops, I see I didn't read nearly enough so ignore this.[/COLOR]**

+1!

Although I'd always begin with asking for the output of the Boot Info Script using a live CD/USB, just to be sure things are what they appear to be.

In fact, if one suspects they've lost a partition (or partitions) step #1 should be to stop using anything but live media. Then step #2 should be looking at what one actually still has.

NOTE: I just happened to stumble upon this while taking a trip to Oneiric-land while taking a break from my re-remodel so I won't be available much.

---

### Post by kansasnoob on 2011-07-26
Sorry for the interruption. I should have learned by now to read everything before responding :redface:

Chalk that up to me wanting to get my re-remodeling done and being able to return to Ubuntu-land.

AFAIK the only serious existing issue with the 11.04 installer is this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

I am following up on that with 11.10 :D

---

### Post by aakash_scsa_hellyeah on 2011-07-26
> **Quackers said:**
> Ok thanks.
All your partitions are still there it seems, both Ubuntu and Windows :-)

There may be difficulties due to the fact that /dev/sda (your Ubuntu drive) has a GUID Partition Table, but /dev/sdb (your Windows drive) does not.
I'm not sure how the two will interact with each other and grub.

All I can suggest is that you reboot and, after making sure that your bios is set to boot the Ubuntu drive before the Windows drive, boot the system.

Ubuntu should boot directly, as it did earlier.
When it does, open up a terminal and run ```
sudo update-grub
``` and watch the screen as grub.cfg is configured.
You should see the Windows Loader recognised. If you do, reboot and you should get a grub menu giving you the choice of which operating system to boot.

Alright i am going to perform these steps. But can you tell me what to do when i will get the grub menu giving me boot options.. which OS to boot.

---

### Post by Quackers on 2011-07-26
If you get to that stage use the down arrow key to highlight the Windows Loader on /dev/sdb1 and press enter.
I notice from the boot script that you have boot files for both Windows 7 and Windows XP, but Windows XP is not shown as being installed.
So, when you try the above you may get a second boot choice between Windows 7 and Windows XP, but XP will not work.

---

### Post by aakash_scsa_hellyeah on 2011-07-26
> **Quackers said:**
> If you get to that stage use the down arrow key to highlight the Windows Loader on /dev/sdb1 and press enter.
I notice from the boot script that you have boot files for both Windows 7 and Windows XP, but Windows XP is not shown as being installed.
So, when you try the above you may get a second boot choice between Windows 7 and Windows XP, but XP will not work.

Yes it all went exactly the way you said.
Now i am in Windows 7 mode started through Grb menu..
What am i supposed to do now? and yes the drives are still not visible even in Win7.
Thanks in advance.

---

### Post by Quackers on 2011-07-26
I'm not sure what you mean by "the drives are still not visible".
In Windows have you opened Disk Management console and viewed the contents of your har drives? It should show all your NTFS partitions as normal. It may have problems showing your Linux partitions accuratley though.

What is it that you now want to do exactly?

---

### Post by aakash_scsa_hellyeah on 2011-07-26
> **Quackers said:**
> I'm not sure what you mean by "the drives are still not visible".
In Windows have you opened Disk Management console and viewed the contents of your har drives? It should show all your NTFS partitions as normal. It mnay have problems showing your Linux partitions accuratley though.
 
What is it that you now want to do exactly?
 
Sorry for incomplete reply.
Actually i want my SAMSUNG SATA drives back cause the data stored in it is very important.

---

### Post by Quackers on 2011-07-26
By "drives" do you mean partitions? You want what was on the Samsung drive back?
Then stop using the Samsung drive, disconnect the Windows drive and use testdisk from the Ubuntu live cd/usb to recover the partitions.

---

### Post by aakash_scsa_hellyeah on 2011-07-26
> **Quackers said:**
> By "drives" do you mean partitions? You want what was on the Samsung drive back?
Then stop using the Samsung drive, disconnect the Windows drive and use testdisk to recover the partitions.
 
Exactly thats what i want my partitions with previous data on it.
Alright i am going to use step by step guide of testdisk. But can you please tell me that will it give the partition with same structure i mean as it was earlier or it will delete some files and give recovered data in irregular manner..

---

### Post by Quackers on 2011-07-26
If your partitions are recoverable testdisk will recover the partitions and, hopefully, the data that was in them.
How many partitions were there? Was the disk full - like the disc you wanted Ubuntu to install to?

---

### Post by aakash_scsa_hellyeah on 2011-07-26
> **Quackers said:**
> If your partitions are recoverable testdisk will recover the partitions and, hopefully, the data that was in them.
How many partitions were there? Was the disk full - like the disc you wanted Ubuntu to install to?

I had 5 partitions.
4 partitions of 49.__ GB
1 Partition of 99.__ GB
Yes The disk was almost full somewhere around 230 GB.
One more question, am i supposed to install testdisk or it is already present in live disk.

---

### Post by ddastoor on 2011-07-26
> **aakash_scsa_hellyeah said:**
> Hey Guys, today ubuntu (installed 11.04) really disappointed me.
I was using Windows seven since many months without any problem and a friend of mine suggested me to try UBUNTU thing.
In my desktop pc i have
Pentium Core2Duo
2 SATA 320 GB (Samsung & WD)
4GB RAM
Windows 7 Is installed on WD SATA
I installed UBUNTU 11.04 from USB installer (universal usb installer) and ISO image (Downloaded from UBUNTU website)
Installer displayed an option to install UBUNTU along with existing  Windows without making changes to existing data on drive. - I preferd  choosing this option..
No other detail were given and installer began to install UBUNTU.
After the installation was complete and Ubuntu boot up to with no error i  found that all the partitions of my second hard drive (samsung SATA)  were removed and it Disk Utility shows single Ext4 version 1.0 type  Linux Basic Data partition of 
Device: /dev/sda2
Capacity:  318GB
Available :  -
Mount Point:  Mounted at /
.............................:confused::mad::mad:
Since then i havent done anything to that har disk with a hope that i'll get all my data back cause i really need it..
......................................
I am expecting a good response from help team for this post.. THANK YOU



Either ther'e a mistake in the OP, or im missing siomething.. 

Windows WD (looks like /dev/sda1, primary active partition)
Samsung then should be /dev/sdb right ?

So if you installed ubuntu "side by side" with windows, then technically shouln't ubuntu just obebiently just install on /dev/sda2 ?


what i cant follow is why should the second hard disk (samsung) at /dev/sdb (not sda) be affected ???

only one of 3 possibilities are possible:
1) there's a real bug with the install side by side option(i doubt).
2) i missing something 
3) u by mistake did something else by mistake?
4) u mean something else in ur post ?

just trying to get to the bottom of this...

---

### Post by Quackers on 2011-07-26
Firstly this has all gone wrong because you tried to install Ubuntu on to one of 2 hard drives - both of which were full! There was nowhere for Ubuntu to install into without over-writing something. Do you see that?

testdisk is not installed on the live cd by default. 
From the live cd desktop open up synaptic package manager and click on Settings then Repositories. In the window that opens up put a check in the box for "universe" which is the second one down.
Close that window and click on Reload in the main Window's toolbar and let that run.
Then enter testdisk in the search box and when it appears in the main winodw right-click on it and select "mark for installation" then click on the green tick in the toolbar to apply the change.
Once installed close synaptic and open a terminal and run ```
sudo testdisk
``` then follow the guide by Herman given in my first post.
Good luck.

---

### Post by bodhi.zazen on 2011-07-26
> **ddastoor said:**
> just trying to get to the bottom of this...

The partitions are all there:

> /dev/sdb1 * 2,048 206,847 204,800 7 NTFS / exFAT / HPFS
/dev/sdb2 206,848 102,903,807 102,696,960 7 NTFS / exFAT / HPFS
/dev/sdb3 102,903,808 205,805,567 102,901,760 7 NTFS / exFAT / HPFS
/dev/sdb4 205,805,568 625,139,711 419,334,144 f W95 Extended (LBA)
/dev/sdb5 205,807,616 308,709,375 102,901,760 7 NTFS / exFAT / HPFS
/dev/sdb6 308,711,424 411,613,183 102,901,760 7 NTFS / exFAT / HPFS
/dev/sdb7 411,615,232 625,139,711 213,524,480 7 NTFS / exFAT / HPFS

They simply need to be mounted.

```
sudo mkdir /media/sdb{1,2,3,4,5,6,7}

sudo mount /dev/sdb1 /media/sdb1

nautilus /media/sdb1
```

And on ...

---

### Post by Quackers on 2011-07-26
I think we're all chasing our tails here :-)
As you say bodhi.zazen it still isn't clear to me that anything is missing!

---

### Post by aakash_scsa_hellyeah on 2011-07-26
> **bodhi.zazen said:**
> The partitions are all there:



They simply need to be mounted.

```
sudo mkdir /media/sdb{1,2,3,4,5,6,7}

sudo mount /dev/sdb1 /media/sdb1

nautilus /media/sdb1
```And on ...

Thanks for you reply.
This sounds intresting.
Although test disk have found the partitions but it will take time to recover.

If you will guide me then i can try this mounting process.
Also i have disconnected one of my hard disk (iWindows 7)
And booted up on live disk with SANSUNG disk attached so maybe the log table of boot script may show some different result.
I have added new boot scrip result here.
Please direct me to mount these partitions in best way.

---

### Post by bodhi.zazen on 2011-07-26
> **Quackers said:**
> I think we're all chasing our tails here :-)
As you say bodhi.zazen it still isn't clear to me that anything is missing!

People are jumping to conclusions without looking at what is on the partitions.

By far, from the linux side, IMO, the easiest thing to do is stop, list your partitions

```
fdisk -l
```

And then mount them and look at the data.

One can then add them to fstab if needed.

It is really a matter of guiding the OP through fstab and mounting windows partitions.

If the data is actually missing, then pursue data recovery.

I have no idea why windows does not see the ntfs partitions, that is something for a windows forums AFIK ;)

---

### Post by zero2xiii on 2011-07-26
Hay all,

Just jumping in to give a nudge. Windows WONT reconise the "other" drive (which has ubuntu on it now), since its partition table is changed during the install (it was touched on by another poster), and further, please remember wnidows CANT read EXT filesystems! The data is there, just invisible to windows. So windows WILL think the drive is unformatted.

---

### Post by aakash_scsa_hellyeah on 2011-07-26
> **bodhi.zazen said:**
> People are jumping to conclusions without looking at what is on the partitions.

By far, from the linux side, IMO, the easiest thing to do is stop, list your partitions

```
fdisk -l
```And then mount them and look at the data.

One can then add them to fstab if needed.

It is really a matter of guiding the OP through fstab and mounting windows partitions.

If the data is actually missing, then pursue data recovery.

I have no idea why windows does not see the ntfs partitions, that is something for a windows forums AFIK ;)


There is a problem with my
fdisk - l

it doesnt give any response..

---

### Post by bodhi.zazen on 2011-07-26
> **aakash_scsa_hellyeah said:**
> There is a problem with my
fdisk - l

it doesnt give any response..

You have been doing so many things I really do not know what to tell you.

Shut down your box. Plug your hard drives back in. Boot a live CD.

Then open a terminal and post the output of fdisk -l. If it shows nothing, you may need to run it as root.

```
sudo fdisk -l
```

We can then mount your partitions , examine them, and proceed from there.

When referring to partitions, I have no idea what you mean by terms such as "SANSUNG disk". The disk is either your first hard drive , sda, or your second hard drive, sdb.

Partitions are then numbered.

Of course if you pull you hard drive out, and switch them around, sda and sdb will change, we can list them by UUID.

```
sudo blkid
```

---

### Post by alphaamanitin on 2011-07-26
Hate to jump into this mess, but I noticed that in an early post by the OP, it sounds like OP was looking for some partitions in windows. OP says windows 7 wants him to format something.  OP needs to keep in mind that Windows will show linux formated partitions as being empty and raw, needing to be formatted.

AlphaA

---

### Post by bodhi.zazen on 2011-07-26
> **alphaamanitin said:**
> Hate to jump into this mess

Does not help to "jump in" without reading all the available information.

If you read up you will see 7 "missing" partitions on the second hard drive , sdb, all listed as NTFS.

---

### Post by aakash_scsa_hellyeah on 2011-07-26
> **bodhi.zazen said:**
> You have been doing so many things I really do not know what to tell you.

Shut down your box. Plug your hard drives back in. Boot a live CD.

Then open a terminal and post the output of fdisk -l. If it shows nothing, you may need to run it as root.

```
sudo fdisk -l
```We can then mount your partitions , examine them, and proceed from there.

When referring to partitions, I have no idea what you mean by terms such as "SANSUNG disk". The disk is either your first hard drive , sda, or your second hard drive, sdb.

Partitions are then numbered.

Of course if you pull you hard drive out, and switch them around, sda and sdb will change, we can list them by UUID.

```
sudo blkid
```


Here are the results of fdisk & blkid

```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda: LABEL="PENDRIVE" UUID="18E9-3A32" TYPE="vfat" 
/dev/sdb2: UUID="084b67d7-8a65-4e48-a23d-3a91577135fe" TYPE="ext4" 
/dev/sdb3: UUID="2cedfcaf-ce1e-4dbb-8c3c-0c646fb272d9" TYPE="swap" 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 2019 MB, 2019557376 bytes
63 heads, 62 sectors/track, 1009 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?      825525      936347   216435558+   7  HPFS/NTFS
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(187, 180, 14) logical=(825524, 35, 10)
Partition 1 has different physical/logical endings:
     phys=(784, 0, 13) logical=(936346, 41, 22)
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?      837691     1337809   976730017   16  Hidden FAT16
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(906, 235, 61) logical=(837690, 61, 20)
Partition 2 has different physical/logical endings:
     phys=(262, 116, 59) logical=(238226, 47, 9)
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?           1           1           0   6f  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(370, 101, 50) logical=(0, 0, 1)
Partition 3 has different physical/logical endings:
     phys=(10, 114, 13) logical=(1099582, 0, 4)
Partition 3 does not end on cylinder boundary.
/dev/sda4           12853      249498   462167897    0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(12852, 10, 45)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(249497, 17, 34)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4d8df9b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38914   312571223+  ee  GPT

```

---

### Post by aakash_scsa_hellyeah on 2011-07-26
Hey Thank You All, I got All My Partitions back with unchanged data by using testdisk6.12.
 
All Credit to you guys thank you for being so responsive.
:D:D:D:D:D:D
 
.................................
 
This was a great experience for me.
 
Can you tell me which will be the best guide to start with for learning UBUNTU or any LINUX and become as experienced as you guys are:D..

---

### Post by glene77is on 2011-08-04
> **aakash_scsa_hellyeah said:**
> 
... I got All My Partitions back with unchanged data by using testdisk6.12. ...
 This was a great experience for me.
 Can you tell me which will be the best guide to start with for learning UBUNTU or any LINUX and become as experienced as you guys are:D..


Aakash,

Welcome to the Ubuntu Forums !   
You have a good head on your shoulders, just need to get some good experience. 
Listen to what these engineers have to say,  step through it all. 

*   Linux Ubuntu will read the NTFS,  
*   but  Windows will NOT read the Linux Ext2, etc. 

Remember this part of a previous post ?
> 
OP needs to keep in mind that Windows will show linux formated partitions as being empty and raw, 
needing to be formatted.


*   You are gaining Windows and Linux perspectives,   
*   perhaps by the 'school of hard knocks',   
*   and that is a real plus when dealing with modern computer systems. 

See the tutorial secion of this Ubuntu Forum, 
See the Linux Forum for more diverse situations. 

I spent 30 years designing/writing/mucking with M$ 
and have found the last few years of Linux to be very interesting. 

On my main computer I have installed 
(1)    M$ XP (original OS),   
(2)    Ubuntu (side by side full install),  
(3)    Puppy Linux (Frugal) (squash file), 
(4)    Parted-Magic (Frugal within the XP partition) (squash file), 
(5) Tiny-Core (Frugal within the Ubuntu partition)(squash file).  
All controlled by the Ubuntu Grub2 bootloader system.       

Welcome to the Ubuntu Forums, and the FUN HAS JUST BEGUN for you !    :popcorn:

I suggest you buy another HD, a USB external, big enough to directly backup all your created data. 
Then copy all your created data directly over.   Windows Drag and Drop will get it.     :)
Then unplug the backup HD. .  

Then start probing and using your Linux system.   You will be a happy fellow.   :P

---

