---
title: "Can not boot since updating to 12.04"
date: 2012-05-09
forum: General Help
---

### Post by Kaheil on 2012-05-09
Hello,

I do not often ask for help, as RTFM and Google are usually my preferred methods. However, this time I am stuck and have no idea what the solution could be.

Since updating to 12.04 via the update manager, I have encountered several issues. Some more annoying than others. After hours of fixing them one after another, I gave up and decided to do a fresh install.

The install went fine, however when booting I was greeted by the grub rescue prompt and the following error "could not find device: hdd-were-Ubuntu-is-installed". Note: it was not written sdc but rather a long stream of seemingly random numbers.

After rebooting and facing the same issue, I booted a live CD, checked than the HDD was fine and that grub was correctly installed in it. I then used Boot-Repair (default settings) and rebooted: same issue.

I then decided to install grub manually: "error: could not find sdc, verify that device is fine etc...". I tried running boot-repair again, this time making sure to erase the previous installation: boot repair froze. Rebooted, retested boot repair, same issue.

Finally I reinstalled 12.04, setting up partitions manually and installing grub to sdc (same drive as OS) but faced the same error.


I am currently stranded and do not know what else I could do, any help is greatly appreciated.

Config:

Desktop PC working fine, with enough power and no compatibility issues.
HHD: 4x500Gb drives, sda & sdb are made into one hardware RAID0, with an old and unused Windows install on it, currently used for storage, sdc is the OS drive and sdd is additional storage.


TL;DR: can't boot, error with grub, tried fixing grub and reinstalling: same issue.

---

### Post by Kaheil on 2012-05-09
Update:

Tried running Boot-Repair again, this time it did not froze, but same issue after reboot.

Tried using the grub rescue prompt.
```

>ls
(hd0) (hd0,msdos1) (hd1) (hd1,msdos5) (hd1, msdos2) (hd2) (fd0)
> ls (hd2) /boot/grub
error: unkown filesystem
(tried the same with every partition, got the same error, except for fd0 sending back read error and hd1,msdos2 sending back bad filename)
```

Note: I have no floppy installed, but every OS on the machine always detects one, never understood why.

Update 2:

Tried reseting BIOS to default (thus deactivating the RAID) and choose as first device to boot the HHD where ubuntu is: same issue.

---

### Post by wilee-nilee on 2012-05-09
Since you have run the bootrepair app it generates a results.txt from a  script called the bootscript, please post the last one run. Or just down  load the script from this link and extract it to your desktop and run the posted  command. We need to see how it looks right now.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

When posting open the new reply or quote and click the # in the top of the reply  panel you will see code tags copy and paste all the text from the  results.txt in between.

---

### Post by Kaheil on 2012-05-10
I ran the script (as boot repair would not work again) and got this result:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 1b9f739c-39fc-40c3-bbd0-8c54ac3d0f6f root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdd and looks at sector 
    193988096 of the same hard drive for core.img, but core.img can not be 
    found at this location.
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/isw_cicedciaeh_Raid0 
    and looks at sector 1 of the same hard drive for core.img. core.img is at 
    this location and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 1b9f739c-39fc-40c3-bbd0-8c54ac3d0f6f root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

isw_cicedciaeh_Raid01: _________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048 1,953,533,951 1,953,531,904   7 NTFS / exFAT / HPFS

/dev/sda1 ends after the last sector of /dev/sda

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   968,388,607   968,386,560  83 Linux
/dev/sdc2         968,390,654   976,771,071     8,380,418   5 Extended
/dev/sdc5         968,390,656   976,771,071     8,380,416  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdd1              34   976,773,134   976,773,101 Data partition (Windows/Linux)

Drive: isw_cicedciaeh_Raid0 _____________________________________________________________________

Disk /dev/mapper/isw_cicedciaeh_Raid0: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953536512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_cicedciaeh_Raid01              2,048 1,953,533,951 1,953,531,904   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_cicedciaeh_Raid0p1 20768741768716A6                       ntfs       Master's Brain
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 
/dev/sdc1        13e6f612-9824-4313-ac79-bf6526438512   ext4       
/dev/sdd1        c9c69c7a-4b16-4d74-8cd1-c77805df2175   ext4       Videos
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS amd64

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_cicedciaeh_Raid0
isw_cicedciaeh_Raid0p1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mapper/isw_cicedciaeh_Raid0p1 /media/Master's Brain    fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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

insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set=root 13e6f612-9824-4313-ac79-bf6526438512
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd2,msdos1)'
  search --no-floppy --fs-uuid --set=root 13e6f612-9824-4313-ac79-bf6526438512
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
function gfxmode {
    set gfxpayload="$1"
    if [ "$1" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 13e6f612-9824-4313-ac79-bf6526438512
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=13e6f612-9824-4313-ac79-bf6526438512 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 13e6f612-9824-4313-ac79-bf6526438512
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=13e6f612-9824-4313-ac79-bf6526438512 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 13e6f612-9824-4313-ac79-bf6526438512
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 13e6f612-9824-4313-ac79-bf6526438512
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=13e6f612-9824-4313-ac79-bf6526438512 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
#UUID=f83f8a9d-6b65-414c-aebb-def1f2a0fb8e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on isw_cicedciaeh_Raid01



=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
hexdump: /dev/mapper/isw_cicedciaeh_Raid01: No such file or directory
hexdump: /dev/mapper/isw_cicedciaeh_Raid01: No such file or directory

```

---

### Post by Kaheil on 2012-05-11
Update:

Tried physically removing both the sdc and sdd drives (corresponding to ubuntu) and booting, got the same error. Tried repairing Windows Vista with the CD, no issue was detected by windows: tried rebooting, same issue.

---

### Post by Ridgerunrbunny on 2012-05-13
Have you tried holding the "shift" key down while loading the kernel? That worked once for me.

Bunny

---

### Post by turbos4 on 2012-05-14
You have dual boot with windows 7?

Try to fix mbr windows from ubuntu live with ms-sys, windows will just create the same issu.

#sudo su

#ms-sys -m /dev/sda

and install grub manual after then grub can write to mbr boot sect. windows.

MS-SYS
[http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)

---

### Post by Kaheil on 2012-06-05
Hello,

I found the solution one week ago. The issue was obvious and, yet, not so. The motherboard was programmed to go look for an OS to boot first on the RAID and then on the other disks. This happened after she reseted herself to default settings after a failed overclock and I forgot to switch back. As to why it kept working until the upgrade, I have no idea.

Anyway, thank you for your help and for proving, once again, that 99% of the issues are in between the chair and the keyboard :)

---

