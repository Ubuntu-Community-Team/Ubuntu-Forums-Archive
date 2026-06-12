---
title: "HELP!!! can't find/mount my two hard drives 19 hours in and still no luck"
date: 2011-04-29
forum: General Help
---

### Post by Chaos1986 on 2011-04-29
OK I've tried everything and so far had no luck, Now I could get the 60 or so screenshots of all the thousands of cryptic error messages and problems I've encountered but I won't bother with that.

Basically I've installed.. can't even remember the cryptic name of it but it shows up as "Storage Device Manager" in the control panel

When I open it I can see my 2 hard drives + the mounted (working) one which was already mounted when I installed Ubuntu.

I can see 

sda (already mounted on install)
sdb
sdc

where sdb and c are my other 2 hard drives, unfortunately clicking on either does nothing, where as clicking on sda offers a configuration window, the built in drive utility it useless as it only offers me the option to format the drives.

I've tried hundres of various commands and had an equil number of stupid errors, the most common is "mount: unknown filesystem type 'promise_fasttrack_raid_member'"

This appears when ever I try to use the commands often shown in online tutorials, I tried putting the same command over and over and over but it just gave the same error over and over

PLEASE PLEASE someone help, i tried on the irc but got ignored repeatedly then muted for asking the question twice, very helpful lol

---

### Post by Hedgehog1 on 2011-04-29
This will give us enough information (I hope) to help you:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

p.s. The '**promise_fasttrack_raid_member**' error is a key to your issue, but we need script output to help make things right.  This will be a group effort!

---

### Post by Chaos1986 on 2011-04-29
> **Hedgehog1 said:**
> This will give us enough information (I hope) to help you:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

p.s. The '**promise_fasttrack_raid_member**' error is a key to your issue, but we need script output to help make things right.  This will be a group effort!

OK here


                > Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.
 => Testdisk is installed in the MBR of /dev/mapper/pdc_biicdjcdgj

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

pdc_biicdjcdgj1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   342,212,312   342,005,465   7 HPFS/NTFS
/dev/sda3         342,212,606   500,117,503   157,904,898   5 Extended
/dev/sda5         342,212,608   458,192,895   115,980,288  83 Linux
/dev/sda6         458,194,944   500,117,503    41,922,560  82 Linux swap / Solaris


Drive: pdc_biicdjcdgj ___________________ _____________________________________________________

Disk /dev/mapper/pdc_biicdjcdgj: 1000.0 GB, 999999995904 bytes
255 heads, 63 sectors/track, 121576 cylinders, total 1953124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_biicdjcdgj1   *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS

/dev/mapper/pdc_biicdjcdgj1 ends after the last sector of /dev/mapper/pdc_biicdjcdgj

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/pdc_biicdjcdgj: PTTYPE="dos" 
/dev/sda1        6898551E9854EBD6                       ntfs       System Reserved               
/dev/sda2        C23C749F3C749061                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        6411b903-093c-4c75-a26d-6bc21fbe2f46   ext4                                     
/dev/sda6        e2e3bd88-55a6-4baf-912c-1747de8cbda9   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb                                                promise_fasttrack_raid_member                               
/dev/sdc                                                promise_fasttrack_raid_member                               
error: /dev/mapper/pdc_biicdjcdgj1: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
pdc_biicdjcdgj

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /media/C23C749F3C749061  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /mnt/sdb1                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda5/boot/grub/grub.cfg: ===========================

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

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 6411b903-093c-4c75-a26d-6bc21fbe2f46
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 6411b903-093c-4c75-a26d-6bc21fbe2f46
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 6411b903-093c-4c75-a26d-6bc21fbe2f46
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6411b903-093c-4c75-a26d-6bc21fbe2f46 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 6411b903-093c-4c75-a26d-6bc21fbe2f46
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6411b903-093c-4c75-a26d-6bc21fbe2f46 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 6411b903-093c-4c75-a26d-6bc21fbe2f46
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 6411b903-093c-4c75-a26d-6bc21fbe2f46
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 6898551E9854EBD6
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc  proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda5 during installation
UUID=6411b903-093c-4c75-a26d-6bc21fbe2f46  /      ext4  errors=remount-ro    0  1  
# swap was on /dev/sda6 during installation
UUID=e2e3bd88-55a6-4baf-912c-1747de8cbda9  none   swap  sw                   0  0  

=================== sda5: Location of files loaded by Grub: ===================


 196.8GB: boot/grub/core.img
 209.7GB: boot/grub/grub.cfg
 176.9GB: boot/initrd.img-2.6.38-8-generic
 196.8GB: boot/vmlinuz-2.6.38-8-generic
 176.9GB: initrd.img
 196.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on pdc_biicdjcdgj1



=============================== StdErr Messages: ===============================

hexdump: /dev/mapper/pdc_biicdjcdgj1: No such file or directory
hexdump: /dev/mapper/pdc_biicdjcdgj1: No such file or directory

---

### Post by Chaos1986 on 2011-04-29
I've tried the sudo commands, but i get errors when the tutorials say it should work, I don't understand, also sorry for my bad english it isn't my first language. Maybe there is no comparability?

---

### Post by imigueldiaz on 2011-04-29
> **Chaos1986 said:**
> I've tried the sudo commands, but i get errors when the tutorials say it should work, I don't understand, also sorry for my bad english it isn't my first language. Maybe there is no comparability?

Hi!

Are sdb and sdc already containing partitions (sdb1, sdc1 and so)?.
Have they been used as RAID before?.

Best

---

### Post by Chaos1986 on 2011-04-29
> **imigueldiaz said:**
> Hi!

Are sdb and sdc already containing partitions (sdb1, sdc1 and so)?.
Have they been used as RAID before?.

Best

The drives themselves were in raid yes but they have since been formatted and are no longer in raid

---

### Post by dino99 on 2011-04-29
sudo dmraid -rE

---

### Post by grontsnuifer on 2011-05-22
Maybe it is unrelated but... dmraid pdc is bugged in 11.04

" [B]ppa : susi/ppa "

solved it for me.
[/B]

---

