---
title: "GRUB Problems"
date: 2012-01-26
forum: General Help
---

### Post by hogar_pg on 2012-01-26
Hi folks!

I recently reinstalled my computer (dual boot, Win 7 64bit and Ubuntu 10.04.2 64 bit) due to HDD upgrade. I first installed Win and after that Ubuntu. It recognized Win partition OK, and everything went well. As I use Ubuntu 99% of the time and Windows only for gaming, I did not booted Win for a while, to find out that I can't boot it. GRUB reports errors:

```

error: no such device <device no.>
error: no such partition
```After which it returns me to OS selection menu. Ubuntu boots with no problems. I found a possible solution on the internet recommending the following fix:

```

bootrec.exe /fixboot
bootrec.exe /fixmbr
```After which I boot directly into Win 7 without GRUB menu. So, I repaired GRUB as per this instructions ( [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) ) but now I get same error message if I try to boot Windows. Any ideas? THanks!

---

### Post by raja.genupula on 2012-01-26
open your terminal and give me the output of 
```
sudo update-grub
```:D

---

### Post by hogar_pg on 2012-01-26
output of sudo updae-grub:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-38-generic
Found initrd image: /boot/initrd.img-2.6.32-38-generic
Found linux image: /boot/vmlinuz-2.6.32-37-generic
Found initrd image: /boot/initrd.img-2.6.32-37-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done


```

---

### Post by nipunshakya on 2012-01-26
^^^^ after grub-update and a restart , are u still unable to boot windows?

---

### Post by hogar_pg on 2012-01-26
Yes. I get the same error messages....

---

### Post by nipunshakya on 2012-01-26
hi. Please post your boot info script results after reading the following thoroughly:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)


Note:if you want a graphical tool to repair your startup, i would suggest you run following commands in terminal:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
```then: 
```
sudo apt-get install -y boot-repair && boot-repair
```Run the boot repair tool and try the recommended repair and restart....

more info here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Read the article under the title '2nd option : install Boot-Repair in Ubuntu'.

**I would suggest you first post your boot info script to actually highlight your issue with booting to windows... and then see what can be done to repair it.**

Regards,WinuxUser

---

### Post by hogar_pg on 2012-01-26
> **WinuxUser said:**
> if you want a graphical tool to repair your startup, i would suggest you run following commands in terminal:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
```then: 
```
sudo apt-get install -y boot-repair && boot-repair
```Run the boot repair tool and try the recommended repair and restart....

more info here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Read the article under the title '2nd option : install Boot-Repair in Ubuntu'.
Goodluck.

Regards,WinuxUser

Which is exactly what I did after fixing Windows and messing with GRUB. And the results where unchanged.

---

### Post by nipunshakya on 2012-01-26
Then you might want to post the result of your boot info script(see above post of mine)....sorry i was editing my last post..but slow internet here...took time to load...nevermind though...

Regards,WinuxUser

---

### Post by hogar_pg on 2012-01-26
And this is output of boot_info_script.sh:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

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
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   406,734,847   406,528,000   7 NTFS / exFAT / HPFS
/dev/sda3         406,749,735 1,465,144,064 1,058,394,330  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048   957,808,639   957,806,592 Data partition (Windows/Linux)
/dev/sdb2     957,808,640   977,340,415    19,531,776 Swap partition (Linux)
/dev/sdb3     977,340,416 3,907,029,134 2,929,688,719 Data partition (Windows/Linux)

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        1E2E44BF2E4491A7                       ntfs       System Reserved
/dev/sda2        34464B1D464ADF6C                       ntfs       
/dev/sda3        5c2dc0f7-fef4-40ac-8163-558ca18ffcb3   ext4       Multimedia 1
/dev/sdb1        3a08a078-1304-4d1c-987b-d315ba9d7517   ext4       
/dev/sdb2        83ae2459-9db6-4d58-ab79-650bff88f2dd   swap       
/dev/sdb3        92fb8776-707e-475e-877d-e867233dedbe   ext4       Multimedia 2
/dev/sdc1        34f4fd23-0de1-47bf-b382-a8e58ee87604   ext4       Multimedia 3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /Windows/sda1            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/Multimedia_1      ext4       (rw)
/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb3        /media/Multimedia_2      ext4       (rw)
/dev/sdc1        /media/Multimedia_3      ext4       (rw)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 3a08a078-1304-4d1c-987b-d315ba9d7517
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 3a08a078-1304-4d1c-987b-d315ba9d7517
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 3a08a078-1304-4d1c-987b-d315ba9d7517
    linux    /boot/vmlinuz-2.6.32-38-generic root=UUID=3a08a078-1304-4d1c-987b-d315ba9d7517 ro   quiet splash noapic nolapic
    initrd    /boot/initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 3a08a078-1304-4d1c-987b-d315ba9d7517
    echo    'Loading Linux 2.6.32-38-generic ...'
    linux    /boot/vmlinuz-2.6.32-38-generic root=UUID=3a08a078-1304-4d1c-987b-d315ba9d7517 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-37-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 3a08a078-1304-4d1c-987b-d315ba9d7517
    linux    /boot/vmlinuz-2.6.32-37-generic root=UUID=3a08a078-1304-4d1c-987b-d315ba9d7517 ro   quiet splash noapic nolapic
    initrd    /boot/initrd.img-2.6.32-37-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 3a08a078-1304-4d1c-987b-d315ba9d7517
    echo    'Loading Linux 2.6.32-37-generic ...'
    linux    /boot/vmlinuz-2.6.32-37-generic root=UUID=3a08a078-1304-4d1c-987b-d315ba9d7517 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-37-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 3a08a078-1304-4d1c-987b-d315ba9d7517
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 3a08a078-1304-4d1c-987b-d315ba9d7517
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1E2E44BF2E4491A7
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=3a08a078-1304-4d1c-987b-d315ba9d7517 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=83ae2459-9db6-4d58-ab79-650bff88f2dd none            swap    sw              0       0

#skrivanje System Reserved particije iz Windows 7
/dev/sda1 /Windows/sda1 ntfs defaults,umask=777 0 0

#rucno mount-ovanje Multimedia particija pri dizanju sistema

/dev/sda3 /media/Multimedia_1 ext4 defaults   0   0
/dev/sdb3 /media/Multimedia_2 ext4 defaults   0   0
/dev/sdc1 /media/Multimedia_3 ext4 defaults   0   0

--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 382.127399445 = 410.306170880  boot/grub/core.img                             1
 304.729122162 = 327.200403456  boot/grub/grub.cfg                             2
 126.411113739 = 135.732899840  boot/initrd.img-2.6.32-37-generic              2
 111.981639862 = 120.239370240  boot/initrd.img-2.6.32-38-generic              2
 382.292060852 = 410.482974720  boot/vmlinuz-2.6.32-37-generic                 1
 382.303684235 = 410.495455232  boot/vmlinuz-2.6.32-38-generic                 1
 111.981639862 = 120.239370240  initrd.img                                     2
 126.411113739 = 135.732899840  initrd.img.old                                 2
 382.303684235 = 410.495455232  vmlinuz                                        1
 382.292060852 = 410.482974720  vmlinuz.old                                    1


```

---

### Post by oldfred on 2012-01-26
Their used to be some issues that Windows software would write into the sectors after the MBR that grub2 also uses for booting with core.img.

Since you have multiple drives it is better to have your Windows boot loader on the Windows drive and your Ubuntu boot loader on the Ubuntu drive and in BIOS boot from the Ubuntu drive.

Your sdb is also gpt and with gpt grub needs a space to install core.img as there is no space after the MBR. You just need a small 1MB  bios_grub partition on sdb.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
BIOS Boot Partition of 1 MiB for partition alignment.

The bios_grub can be anywhere on drive. So just shrink your last partition by 1MB with gparted and create a 1MB partition. Use set flags to flag it as bios_grub. Then installs of grub will automatically find that partition and use it.

Your Windows looks correct.

But there was a bug in grub with older versions of Ubuntu that boot from a gpt drive.It had trouble finding a msdos drive.
gpt drive with MBR drive for 10.04 or before. Fixed in 10.10
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:GTP_MS_DOS](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:GTP_MS_DOS)

Oldfred filed that bug before doing his research and there is one fix in the bug report. But meieifra, one of the authors of the boot script had seen the error enough he posted another (better) fix.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:GTP_MS_DOS](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:GTP_MS_DOS)

Edit:
Download and use the newest gparted, either its own liveCD or a newest Ubuntu with the latest gparted it has.

---

### Post by hogar_pg on 2012-01-26
Oldfred, you gave me an idea which I tested and now it works:

In BIOS I disabled sdb & sdc hard drives and using Windows 7 install DVD repaired mbr with:

```
bootrec.exe /fixboot
bootrec.exe /fixmbr
```

After I enabled sdb & sdc HDDs I can select from BIOS which OS I boot, which is good enough for me. Now only remaining question is: how do I remove Windows 7 from GRUB menu? 

Thanks all for your help and interest!

---

### Post by oldfred on 2012-01-26
If you fix the msdos issue in grub, then you can always boot with grub and choose Windows if you want. Then you only need to use BIOS to choose which to boot is there is an issue with the Ubuntu drive.

You can turn off os-prober so it does not look for other installs. Or use these alternatives.

HOWTO: Grub Customizer Updated for grub 1.99
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html) 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or change executeable bit so it does not run:
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by nipunshakya on 2012-01-27
I had a different view regarding that issue of hogar....but i guess **oldfred** saved the day for me again...i didn't know that much about those **oldfred** suggested...sorry for late reply coz have  blackouts here for 12 hrs a day....anyways, flad to know **oldfred **saved you ....Happy Linuxing

Regards,WinuxUser

---

### Post by hogar_pg on 2012-01-28
THank you both for your effort! I turned off os-prober and it makes me happy now! Cheers!

---

### Post by nipunshakya on 2012-01-29
just remembered....Cheers...Happy Linuxing

---

