---
title: "Ubuntu Uninstall! (temporary)"
date: 2011-12-30
forum: General Help
---

### Post by jrbrooks on 2011-12-30
I installed Ubuntu (10.04 I think) on my desktop to dual boot with Windows Vista. This has worked well for over two years but now I am so fed up with Vista that I am going to upgrade to Windows 7.
I believe I need to remove Ubuntu while I do this. I will then re-install Ubuntu later.

I believe it is easy to un-install Ubuntu but I do not know how. Could somebody assist please.

---

### Post by yetiman64 on 2011-12-30
> **jrbrooks said:**
> I installed Ubuntu (10.04 I think) on my desktop to dual boot with Windows Vista. This has worked well for over two years but now I am so fed up with Vista that I am going to upgrade to Windows 7.
I believe I need to remove Ubuntu while I do this. I will then re-install Ubuntu later.

I believe it is easy to un-install Ubuntu but I do not know how. Could somebody assist please.
No not necessary, you can install Win7 where Vista was, but it will kill the grub bootcode in the MBR (master boot records - gets overwritten by W7's install).

If you have the Ubuntu 10.04 live cd handy it is quite easy to reinstall grub back to the MBR. And when you reboot you should have both Ubuntu and Win7 to select from. Will hunt around my storage folders for some info.

Could you please post back the terminal output of

```
sudo fdisk -l
``` That is a lower case L at the end of the code. This is for checking for Wubi vs separate partition set ups of dual booting :).

**Edit**: with 10.04 from a live cd desktop open a terminal, (**note: this is not for Wubi Installs** or for Ubuntu installs with a separate /boot partition)
```
sudo mount /dev/sda**X** /mnt
``` replace **X** with the partition number grub's files are on. The fdisk command given earlier should indicate that info.

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```**Reboot and grub should load.**

To ensure windows is detected correctly, after rebooting it may pay to first boot into Ubuntu and issue the command.

```
sudo update-grub
```Restart and check the Grub menu for Windows if it wasn't there the first time.

---

### Post by jrbrooks on 2011-12-30
sudo fdisk -l gave the following.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0368103

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9730    78148608    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x33d4a52a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60834   488644110    7  HPFS/NTFS
/dev/sdc2           60834      121602   488116225    5  Extended
/dev/sdc5           60834      120429   478694400   83  Linux
/dev/sdc6          120429      121602     9420800   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3eefdcf7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30341   243712000    7  HPFS/NTFS
/dev/sdb2           30341       60802   244671488    7  HPFS/NTFS

I did not install Ubuntu from CD but downloaded directly from the Ubuntu web site

---

### Post by jrbrooks on 2011-12-30
btw can I go ahead with upgrading (I hope!) Vista to Windows 7 and sort out the dual boot stuff later?

---

### Post by yetiman64 on 2011-12-31
> I did not install Ubuntu from CD but downloaded directly from the Ubuntu web site This really has me wondering about your install with regard to Wubi. Did you burn the dowloaded iso to disc/usb or did you use it in Windows to install Ubuntu ? (we need to know that)

Wubi is an install of Ubuntu to within a file on the Windows NTFS filesystem, but the grub bootloader is installed and boots Ubuntu from that file in Windows (windows is not booted up at all, so it is actually a form of dual booting). Whereas the instructionsI am giving is for separate partition install dual booting, very different when it comes to helping out with issues.

Now what really catches my eyes from fdisk is you do have a linux partition and swap on /dev/sdc, which could be your install but I need to know for sure it is. Please consider reading the first link in my signature and posting back the results of the bootinfo.script for more information for us to go on (at least more accurately ;)). Please use code tags (the # button in the advanced editor) around the results when you post back. Cheers for now.

**P.S.** Don't go installing Win7 till you are absolutely sure you are **not** using a Wubi install, doing so will overwrite BOTH Vista and Ubuntu in one fell swoop  in such circumstances, as both OSes live in the same actual partition with Wubi.

---

### Post by jrbrooks on 2012-01-01
Happy New Year. My new year resolution is to be less stupid, especially with computers.

The original installation of Ubuntu went so smoothly that I had forgotten everything about it (age). I did, in fact, burn a CD with the .iso file and did not use Wubi. I have run the boot_info_script.sh script and created the Results.txt file. I believe I have attached the zipped file to this reply. My perusal of the file seems to indicate to me that everything is as it should be. 
Do you think that I can go ahead with the Windows 7 upgrade of Vista?

btw my experience of Ubuntu is that it is fast, does not freeze and shuts down and starts up in seconds rather than minutes compared to Vista. But it seems that I need to be able to run Windows for various things.

---

### Post by yetiman64 on 2012-01-01
As there are a couple of things I'm seeing here that others will need to see as well, I'll post your results.txt output in this post first off.

```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   156,299,263   156,297,216   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   487,426,047   487,424,000   7 NTFS / exFAT / HPFS
/dev/sdb2         487,426,048   976,769,023   489,342,976   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   977,290,267   977,288,220   7 NTFS / exFAT / HPFS
/dev/sdc2         977,291,262 1,953,523,711   976,232,450   5 Extended
/dev/sdc5         977,291,264 1,934,680,063   957,388,800  83 Linux
/dev/sdc6       1,934,682,112 1,953,523,711    18,841,600  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        701E2FCB1E2F88E4                       ntfs       
/dev/sdb1        2E7E16D37E169425                       ntfs       Mine
/dev/sdb2        54321C1B321C04A0                       ntfs       Technical
/dev/sdc1        304462B344627C0A                       ntfs       Extra
/dev/sdc5        801be6c2-cabc-49f8-a74f-fa06b7167cbf   ext4       
/dev/sdc6        826f7992-d2cf-46bf-8559-8a44be7a532a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /media/Mine              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc5        /                        ext4       (rw,errors=remount-ro)


=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root='(hd2,5)'
search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
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
set root='(hd2,5)'
search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
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
menuentry 'Ubuntu, with Linux 2.6.32-37-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    linux    /boot/vmlinuz-2.6.32-37-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-37-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    echo    'Loading Linux 2.6.32-37-generic ...'
    linux    /boot/vmlinuz-2.6.32-37-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-37-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-36-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    linux    /boot/vmlinuz-2.6.32-36-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-36-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    echo    'Loading Linux 2.6.32-36-generic ...'
    linux    /boot/vmlinuz-2.6.32-36-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-36-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-35-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    linux    /boot/vmlinuz-2.6.32-35-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-35-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    echo    'Loading Linux 2.6.32-35-generic ...'
    linux    /boot/vmlinuz-2.6.32-35-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-35-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    echo    'Loading Linux 2.6.32-34-generic ...'
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    echo    'Loading Linux 2.6.32-32-generic ...'
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    echo    'Loading Linux 2.6.32-31-generic ...'
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 801be6c2-cabc-49f8-a74f-fa06b7167cbf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 701E2FCB1E2F88E4
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdc5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=801be6c2-cabc-49f8-a74f-fa06b7167cbf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=826f7992-d2cf-46bf-8559-8a44be7a532a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 514.141582489 = 552.055320576  boot/grub/core.img                             1
 471.460071564 = 506.226397184  boot/grub/grub.cfg                             1
 514.266506195 = 552.189456384  boot/initrd.img-2.6.32-24-generic              1
 514.280284882 = 552.204251136  boot/initrd.img-2.6.32-25-generic              1
 514.338832855 = 552.267116544  boot/initrd.img-2.6.32-26-generic              1
 514.304367065 = 552.230109184  boot/initrd.img-2.6.32-27-generic              1
 514.346603394 = 552.275460096  boot/initrd.img-2.6.32-28-generic              1
 514.391555786 = 552.323727360  boot/initrd.img-2.6.32-29-generic              1
 514.407089233 = 552.340406272  boot/initrd.img-2.6.32-30-generic              1
 514.414859772 = 552.348749824  boot/initrd.img-2.6.32-31-generic              1
 514.454059601 = 552.390840320  boot/initrd.img-2.6.32-32-generic              1
 514.461856842 = 552.399212544  boot/initrd.img-2.6.32-33-generic              1
 514.469654083 = 552.407584768  boot/initrd.img-2.6.32-34-generic              1
 514.477451324 = 552.415956992  boot/initrd.img-2.6.32-35-generic              1
 514.485248566 = 552.424329216  boot/initrd.img-2.6.32-36-generic              1
 514.496826172 = 552.436760576  boot/initrd.img-2.6.32-37-generic              1
 477.282051086 = 512.477700096  boot/vmlinuz-2.6.32-24-generic                 2
 514.270278931 = 552.193507328  boot/vmlinuz-2.6.32-25-generic                 1
 514.288833618 = 552.213430272  boot/vmlinuz-2.6.32-26-generic                 1
 514.328968048 = 552.256524288  boot/vmlinuz-2.6.32-27-generic                 1
 514.325065613 = 552.252334080  boot/vmlinuz-2.6.32-28-generic                 1
 514.292610168 = 552.217485312  boot/vmlinuz-2.6.32-29-generic                 1
 514.296390533 = 552.221544448  boot/vmlinuz-2.6.32-30-generic                 1
 514.352394104 = 552.281677824  boot/vmlinuz-2.6.32-31-generic                 1
 514.312160492 = 552.238477312  boot/vmlinuz-2.6.32-32-generic                 1
 514.315937042 = 552.242532352  boot/vmlinuz-2.6.32-33-generic                 1
 514.319713593 = 552.246587392  boot/vmlinuz-2.6.32-34-generic                 1
 514.361953735 = 552.291942400  boot/vmlinuz-2.6.32-35-generic                 1
 514.399284363 = 552.332025856  boot/vmlinuz-2.6.32-36-generic                 1
 514.489025116 = 552.428384256  boot/vmlinuz-2.6.32-37-generic                 1
 514.496826172 = 552.436760576  initrd.img                                     1
 514.485248566 = 552.424329216  initrd.img.old                                 1
 514.489025116 = 552.428384256  vmlinuz                                        1
 514.399284363 = 552.332025856  vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 


```The issues (not sure of how important yet) are,

> => Grub2 [noparse](v1.97-1.98)[/noparse] is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub. Grub is in /dev/sda which is good. However this says it looks to partition 5, but /dev/sda has only the one partition according to the output above. Your Ubuntu install (and /boot/grub/core.img) is actually on /dev/sdc (partition 5). 
> sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
You also have Windows bootloaders in the MBR of /dev/sdb and /dev/sdc,  whereas the only one needed is the grub entry in /dev/sda. This all may cause issues on re-installing Win7 over the previous Vista install. I'm not sure if or how bad an issue these will cause, _*so I would ask you wait for further advice and results checking*_ by other helpers on this forum. Hopefully I'm only being overly cautious and you don't have any problems with reinstalling.

Happy New Year also and cheers for now. yetiman64

---

### Post by YannBuntu on 2012-01-06
Hello jrbrooks,

as said above, once you have reinstalled Windows, you will need to reinstall GRUB to recover access to Ubuntu. You can do this very easily via [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair").

JFYI, next time you need to uninstall a system, just use [OS-Uninstaller]("https://help.ubuntu.com/community/OS-Uninstaller") ;)

---

### Post by jrbrooks on 2012-01-09
Everything is now OK. I can now dual-boot as before Windows or Ubuntu
I did have a few problems
Before changing anything I tried to install Boot-repair by issuing the commands
#
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update[FONT=monospace]
[/FONT]sudo apt-get install -y boot-repair && boot-repair
#
However, something went wrong because the terminal got stuck on "checking system files" - something like that I forget what exactly and I closed the terminal. So, although "Boot-Repair" now appears in the Administration menu i am not sure if it works properly.

The Windows 7 went surprisingly easily. After you start the Upgrade procedure you get the message that it is likely to take several hours - which it does.

However, I had lost the dual-boot option. I had to boot using the Boot repair CD. At the options I chose 64 bit Safe mode and then update the PPA(?). However the procedure did not complete and just hung at the same sort of place as above. I seemed to be unable to do anything so powered down. On Restart the computer would not boot up. Booting with Repair disk I selected the 64 bit "normal" option and did not update. Everything worked fine.
Two reports were automatically created (paste.ubuntu.com) 797771 and 79774 if they are of any interest


btw is it normal to have about 10 options for starting Ubuntu?
Ubuntu, with Linux 2.6.32-37-generic
Ubuntu, with Linux 2.6.32-37-generic (recovery mode)
to
Ubuntu, with Linux 2.6.32-24-generic (recovery mode) 
Thanks for much for all the assistance.

---

### Post by YannBuntu on 2012-01-10
"checking system files": i guess this was filesystem check that you activated in the advanced options. This can be very long (several minutes/hours).

"the procedure did not complete": this is a [known bug]("http://ubuntuforums.org/showpost.php?p=11594705&postcount=230"), sorry for this.

"is it normal to have about 10 options for starting Ubuntu?" : yes, there are 2 entries (one normal, and one failsafe) for each of your kernels. I recommend you leave them.

Happy Ubuntuing :)

---

