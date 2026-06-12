---
title: "Dual boot does not work"
date: 2011-09-11
forum: General Help
---

### Post by Rodayo on 2011-09-11
So I dualbooted a 64-bit windows machine with 64-bit natty. The installation seemed to have gone without a hitch. However when I turn on my computer the grub menu doesn't show up and goes straight into windows. I tried to manual boot from the partition but my bios didn't give me the option.

The only thing that went wrong during the install was when I did the initial restart(where it tells you to remove the media and hit Enter) it just stayed at the black screen with a whole bunch of writing. I didn't bother reading it.

Also the windows partition has shrunk so the ubuntu ext partition is definitely there.

Any ideas?

---

### Post by raja.genupula on 2011-09-11
while booting press shift key to get grub menu . if you're done with this , then we can go for next step to set some time delay for grub. 

all the best

---

### Post by Quackers on 2011-09-11
Where was grub installed to?

---

### Post by Rodayo on 2011-09-11
> **raja.genupula said:**
> while booting press shift key to get grub menu . if you're done with this , then we can go for next step to set some time delay for grub. 

all the best

Doesn't work unfortunately. =/

---

### Post by Rodayo on 2011-09-11
> **Quackers said:**
> Where was grub installed to?

I don't know. How would I check?

I was thinking about using the live usb to play around with grub. Maybe the time delay is too short or something...

---

### Post by Quackers on 2011-09-11
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
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

### Post by Rodayo on 2011-09-11
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdf.

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>..........V...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1445104 of /dev/sdf1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdf1 starts at sector 
                       0. But according to the info from fdisk, sdf1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,303,034,650 1,302,827,803   7 NTFS / exFAT / HPFS
/dev/sda3       1,928,501,248 1,953,521,663    25,020,416   7 NTFS / exFAT / HPFS
/dev/sda4       1,303,035,902 1,928,501,247   625,465,346   5 Extended
/dev/sda5       1,920,307,200 1,928,501,247     8,194,048  82 Linux swap / Solaris
/dev/sda6       1,303,035,904 1,912,111,103   609,075,200  83 Linux
/dev/sda7       1,912,113,152 1,920,296,959     8,183,808  82 Linux swap / Solaris


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 4007 MB, 4007624704 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7827392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *             62     7,826,383     7,826,322   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        B878F7CB78F78702                       ntfs       SYSTEM
/dev/sda2        6C605C85605C57C2                       ntfs       OS
/dev/sda3        0E1448F81448E3F5                       ntfs       HP_RECOVERY
/dev/sda5        31d79c82-3776-4947-a680-d8b0e1e8df29   swap       
/dev/sda6        f8e75531-0c30-4c09-a2bc-0e07d0ac2fa5   ext4       
/dev/sda7        e58dae55-41d5-44a7-931c-0b82edc9aab3   swap       
/dev/sdf1        9032-ED9B                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdf1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root f8e75531-0c30-4c09-a2bc-0e07d0ac2fa5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root f8e75531-0c30-4c09-a2bc-0e07d0ac2fa5
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root f8e75531-0c30-4c09-a2bc-0e07d0ac2fa5
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=f8e75531-0c30-4c09-a2bc-0e07d0ac2fa5 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root f8e75531-0c30-4c09-a2bc-0e07d0ac2fa5
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=f8e75531-0c30-4c09-a2bc-0e07d0ac2fa5 ro single 
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root f8e75531-0c30-4c09-a2bc-0e07d0ac2fa5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root f8e75531-0c30-4c09-a2bc-0e07d0ac2fa5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root B878F7CB78F78702
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 0E1448F81448E3F5
    drivemap -s (hd0) ${root}
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=e58dae55-41d5-44a7-931c-0b82edc9aab3 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 815.519935608 = 875.657863168  boot/grub/grub.cfg                             1
 621.844772339 = 667.700740096  boot/initrd.img-2.6.38-8-generic               2
 861.468753815 = 924.995031040  boot/vmlinuz-2.6.38-8-generic                  1
 621.844772339 = 667.700740096  initrd.img                                     2
 861.468753815 = 924.995031040  vmlinuz                                        1

=========================== sdf1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdf1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdf1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdf1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdf1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```
E:are you sure you don't want me to run this from the ubuntu partition that I installed?
E: nevermind that won't even work

---

### Post by Quackers on 2011-09-11
It seems that grub is not installed fully. I'm not sure but it may be the case that Ubuntu is not fully installed. It may be that purging and re-installing grub will fix it, but I would suggest that you start again and re-install Ubuntu to the same partition as last time. 
You also have 2 swap partitions. You only need one (if that) so can delete one of them and add that space to your Ubuntu partition if you wish.
Alternatively you can delete /dev/sda5, sda6 and sda7 and start again if you wish.
Grub should be installed to /dev/sda which is the default location.

---

### Post by Rodayo on 2011-09-11
> **Quackers said:**
> It seems that grub is not installed fully. I'm not sure but it may be the case that Ubuntu is not fully installed. It may be that purging and re-installing grub will fix it, but I would suggest that you start again and re-install Ubuntu to the same partition as last time. 
You also have 2 swap partitions. You only need one (if that) so can delete one of them and add that space to your Ubuntu partition if you wish.
Alternatively you can delete /dev/sda5, sda6 and sda7 and start again if you wish.
Grub should be installed to /dev/sda which is the default location.

This is actually the second time I've done an install. I reinstalled this morning in the hopes of making it work but the same problem persisted...

---

### Post by Quackers on 2011-09-11
That might explain the 2 swap partitions.
Have you checked the md6sum of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out you should check the integrity of the cd/usb that you are using by pressing any key at the first purple screen when booting from it. Then choose your language and on the next screen choose to check the cd (or usb) for errors.

---

### Post by Rodayo on 2011-09-11
> **Quackers said:**
> That might explain the 2 swap partitions.
Have you checked the md6sum of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out you should check the integrity of the cd/usb that you are using by pressing any key at the first purple screen when booting from it. Then choose your language and on the next screen choose to check the cd (or usb) for errors.

The md5 checks out. 

What did you mean by purple screen? The one with the ubuntu logo?

---

### Post by sum1nil on 2011-09-11
In the between time, you could use another bootloader like iBoot which should show all bootable partitions.

Just boot from it at startup from cd.

---

### Post by YesWeCan on 2011-09-11
From bootinfoscript it looks to me like the Grub boot program has not been installed to the MBR area of the disk but the Grub files are present in the root partition.

So from live CD:
```
[COLOR="DarkSlateBlue"]sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]
```

---

### Post by Rodayo on 2011-09-11
> **YesWeCan said:**
> From bootinfoscript it looks to me like the Grub boot program has not been installed to the MBR area of the disk but the Grub files are present in the root partition.

So from live CD:
```
[COLOR=DarkSlateBlue]sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]
```

Worked like a charm! Thanks a lot mate :D

---

### Post by YesWeCan on 2011-09-11
Great. Don't forget to mark this as solved in [COLOR="Red"]Thread Tools[/COLOR].

---

### Post by Quackers on 2011-09-11
Nice one :-)
That's interesting because no core.img was showing in the boot script. I suspected that grub or Ubuntu was not fully installed. Two installs too!
You learn something new every day :-)

---

### Post by YesWeCan on 2011-09-11
> **Quackers said:**
> Nice one :-)
That's interesting because no core.img was showing in the boot script. I suspected that grub or Ubuntu was not fully installed. Two installs too!
You learn something new every day :-)
It so happens that grub-install regenerates core.img before stuffing it into the MBR area. :)

I keep coming across 11.04 installs where Grub was not installed properly or at all. I wonder why? There are no obvious (to me) reasons why it shouldn't have worked the first time.

---

### Post by Quackers on 2011-09-11
Something seems to be going wrong sometimes. Strange!

---

