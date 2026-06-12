---
title: "Fedora's Grub Messed up my Ubuntu Login Splash Screen"
date: 2011-06-04
forum: General Help
---

### Post by UltraZone on 2011-06-04
Pretty much as the title says, I installed Fedora on a separate partition and during the install prompts forgot to uncheck the Grub installation.  So, Fedora installed with Grub 1 (imagine that) although I was able to find instructions to upgrade it to Grub 2 (plus it recognized all the OS on the computer).  So far so good, I don't have a preference whether Fedora's or Ubuntu's Grub is installed, however the Ubuntu Startup Splash screen is messed up, ie. a simple purple background with "Ubuntu" in system fonts.  Is there a way to fix this back to the graceful default splash screen?  Can I change back the Grub to be Ubuntu's?  Thanks.

---

### Post by garvinrick4 on 2011-06-04
Download this to Desktop then run the code in a terminal will put a RESULTS text file
on your Desktop, copy and paste it here. Will show us how your bootscript so we can
make sure all is right before giving you code to install Ubuntu's grub2 to mbr
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
  sudo bash ~/Desktop/boot_info_script.sh
```

---

### Post by UltraZone on 2011-06-04
Here's the contents of Results.txt after running the script:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 8 for /boot/grub2.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 15 (Lovelock) 
                       Kernel on an ()
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab 
                       /boot/grub2/core.img

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Recovery: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       385,559       385,497  de Dell Utility
/dev/sda2    *        385,560   164,225,023   163,839,464   7 NTFS / exFAT / HPFS
/dev/sda3         164,227,070   615,401,471   451,174,402   f W95 Extended (LBA)
/dev/sda5         299,756,961   446,241,335   146,484,375  83 Linux
/dev/sda6         446,242,816   579,368,159   133,125,344  83 Linux
/dev/sda7         602,492,928   615,401,471    12,908,544  82 Linux swap / Solaris
/dev/sda8         579,368,223   602,485,694    23,117,472  83 Linux
/dev/sda9         164,227,072   299,755,519   135,528,448  83 Linux
/dev/sda4         615,401,955   625,137,344     9,735,390  db CP/M / CTOS / ...


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D7-0111                              vfat       DellUtility
/dev/sda2        C0741899741893EE                       ntfs       
/dev/sda4                                               vfat       DellRestore
/dev/sda5        33a5a8e1-a51b-42a4-b144-d113b6345cfd   ext4       
/dev/sda6        69d1cf67-6585-4b72-9065-1b79bfcf98b8   ext4       
/dev/sda7        82a28739-4b4c-4165-a2fc-8d5179c7c1d4   swap       
/dev/sda8        f87d2650-ac0a-49c7-b968-372b100990d4   ext4       _Fedora-15-x86_6
/dev/sda9        f2282833-2648-4859-be92-a13945cf757c   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)
/dev/sda9        /usr                     ext4       (rw,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos9)'
search --no-floppy --fs-uuid --set=root f2282833-2648-4859-be92-a13945cf757c
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 33a5a8e1-a51b-42a4-b144-d113b6345cfd
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
    search --no-floppy --fs-uuid --set=root 33a5a8e1-a51b-42a4-b144-d113b6345cfd
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=33a5a8e1-a51b-42a4-b144-d113b6345cfd ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 33a5a8e1-a51b-42a4-b144-d113b6345cfd
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=33a5a8e1-a51b-42a4-b144-d113b6345cfd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 33a5a8e1-a51b-42a4-b144-d113b6345cfd
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=33a5a8e1-a51b-42a4-b144-d113b6345cfd ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 33a5a8e1-a51b-42a4-b144-d113b6345cfd
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=33a5a8e1-a51b-42a4-b144-d113b6345cfd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 33a5a8e1-a51b-42a4-b144-d113b6345cfd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 33a5a8e1-a51b-42a4-b144-d113b6345cfd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 07d7-0111
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root C0741899741893EE
    chainloader +1
}
menuentry "SUSE Linux Enterprise Desktop 10 (x86_64) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 60e27141-cb7a-4ca3-b410-f63caf64f4e4
    linux /boot/vmlinuz root=/dev/sda8
    initrd /boot/initrd
}
menuentry "SUSE Linux Enterprise Desktop 10 (x86_64) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 60e27141-cb7a-4ca3-b410-f63caf64f4e4
    linux /boot/vmlinuz root=/dev/sda8
    initrd /boot/initrd-2.6.16.60-0.54.5-smp
}
menuentry "SUSE Linux Enterprise Desktop 10 (x86_64) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 60e27141-cb7a-4ca3-b410-f63caf64f4e4
    linux /boot/vmlinuz root=/dev/sda8
    initrd /boot/initrd
}
menuentry "SUSE Linux Enterprise Desktop 10 (x86_64) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 60e27141-cb7a-4ca3-b410-f63caf64f4e4
    linux /boot/vmlinuz root=/dev/sda8
    initrd /boot/initrd-2.6.16.60-0.54.5-smp
}
menuentry "SUSE Linux Enterprise Desktop 10 (x86_64) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 60e27141-cb7a-4ca3-b410-f63caf64f4e4
    linux /boot/vmlinuz-2.6.16.60-0.54.5-smp root=/dev/sda8
    initrd /boot/initrd-2.6.16.60-0.54.5-smp
}
menuentry "SUSE Linux Enterprise Desktop 10 (x86_64) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 60e27141-cb7a-4ca3-b410-f63caf64f4e4
    linux /boot/vmlinux-2.6.16.60-0.54.5-smp.gz root=/dev/sda8
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=33a5a8e1-a51b-42a4-b144-d113b6345cfd /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=69d1cf67-6585-4b72-9065-1b79bfcf98b8 /home           ext4    defaults        0       2
# /usr was on /dev/sda9 during installation
UUID=f2282833-2648-4859-be92-a13945cf757c /usr            ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=82a28739-4b4c-4165-a2fc-8d5179c7c1d4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 165.065956593 = 177.238221312  boot/grub/core.img                             1
 152.412952900 = 163.652162048  boot/grub/grub.cfg                             1
 152.333500385 = 163.566850560  boot/initrd.img-2.6.35-28-generic              2
 151.997757435 = 163.206349312  boot/initrd.img-2.6.38-8-generic               2
 143.415726185 = 153.991463424  boot/vmlinuz-2.6.35-28-generic                 2
 143.759785175 = 154.360893952  boot/vmlinuz-2.6.38-8-generic                  1
 151.997757435 = 163.206349312  initrd.img                                     2
 152.333500385 = 163.566850560  initrd.img.old                                 2
 143.759785175 = 154.360893952  vmlinuz                                        1
 143.415726185 = 153.991463424  vmlinuz.old                                    2

========================== sda8/boot/grub/grub.conf: ===========================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,7)
#          kernel /boot/vmlinuz-version ro root=/dev/sda8
#          initrd /boot/initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,7)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.6-27.fc15.x86_64)
    root (hd0,7)
    kernel /boot/vmlinuz-2.6.38.6-27.fc15.x86_64 ro root=UUID=f87d2650-ac0a-49c7-b968-372b100990d4 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.38.6-27.fc15.x86_64.img
title GNU GRUB 2, (1.98)
    kernel /boot/grub2/core.img
title Fedora (2.6.38.6-26.rc1.fc15.x86_64)
    root (hd0,7)
    kernel /boot/vmlinuz-2.6.38.6-26.rc1.fc15.x86_64 ro root=UUID=f87d2650-ac0a-49c7-b968-372b100990d4 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.38.6-26.rc1.fc15.x86_64.img
title Other
    rootnoverify (hd0,1)
    chainloader +1
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Wed Jun  1 22:13:11 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=f87d2650-ac0a-49c7-b968-372b100990d4 /                       ext4    defaults        1 1
UUID=82a28739-4b4c-4165-a2fc-8d5179c7c1d4 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 276.393859386 = 296.775646720  boot/grub/grub.conf                            1
 276.393859386 = 296.775646720  boot/grub/menu.lst                             1
 276.404307842 = 296.786865664  boot/grub/stage2                               1
 278.519843578 = 299.058404864  boot/initramfs-2.6.38.6-26.rc1.fc15.x86_64.img  2
 279.019843578 = 299.595275776  boot/initramfs-2.6.38.6-27.fc15.x86_64.img     1
 277.409831524 = 297.866538496  boot/initrd-plymouth.img                       1
 277.418300152 = 297.875631616  boot/vmlinuz-2.6.38.6-26.rc1.fc15.x86_64       1
 278.930915356 = 299.499789824  boot/vmlinuz-2.6.38.6-27.fc15.x86_64           1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 4a 90 44 65 6c 6c 20  38 2e 30 00 02 08 01 00  |.J.Dell 8.0.....|
00000010  02 00 02 00 00 f8 bd 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  d3 e1 05 00 80 00 29 11  01 d7 07 44 65 6c 6c 55  |......)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 00 00  |tilityFAT16   ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 30 33 c0 8e d0  |...........03...|
00000050  bc 00 07 fc b9 80 00 8e  d8 be 00 7c b8 00 20 8e  |...........|.. .|
00000060  c0 33 ff f3 66 a5 ea 6b  00 00 20 8e d8 b8 01 02  |.3..f..k.. .....|
00000070  b9 01 00 b6 00 8a 16 24  00 bb 00 02 cd 13 0f 82  |.......$........|
00000080  e0 00 80 3e c2 03 06 74  0e c6 06 c2 03 06 b8 01  |...>...t........|
00000090  03 cd 13 0f 82 cb 00 66  0f b7 06 16 00 66 d1 e0  |.......f.....f..|
000000a0  66 40 66 03 06 1c 00 66  a3 3e 00 8b 2e 11 00 89  |f@f....f.>......|
000000b0  2e 44 00 c1 ed 04 e8 cb  00 4d 75 fa b9 0b 00 be  |.D.......Mu.....|
000000c0  ea 01 8b fd f3 a6 74 0f  83 c5 20 ff 0e 44 00 75  |......t... ..D.u|
000000d0  eb be e0 01 e9 8e 00 26  8b 46 1a a3 46 00 66 a1  |.......&.F..F.f.|
000000e0  1c 00 66 40 66 a3 3e 00  c7 06 48 00 00 00 8b 2e  |..f@f.>...H.....|
000000f0  16 00 e8 8f 00 4d 75 fa  c7 06 4a 00 70 00 c7 06  |.....Mu...J.p...|
00000100  48 00 00 00 66 0f b7 06  46 00 66 83 e8 02 66 0f  |H...f...F.f...f.|
00000110  b6 0e 0d 00 66 f7 e1 66  0f b7 0e 16 00 66 d1 e1  |....f..f.....f..|
00000120  66 41 66 03 0e 1c 00 66  03 c1 66 0f b7 0e 11 00  |fAf....f..f.....|
00000130  66 c1 e9 04 66 03 c1 66  a3 3e 00 0f b6 2e 0d 00  |f...f..f.>......|
00000140  e8 41 00 4d 75 fa 8b 36  46 00 b8 00 30 d1 e6 73  |.A.Mu..6F...0..s|
00000150  03 05 00 10 8e c0 26 ad  3d f8 ff 73 0d a3 46 00  |......&.=..s..F.|
00000160  eb a2 be d5 01 e8 0d 00  eb fe 8a 16 24 00 33 ed  |............$.3.|
00000170  ea 00 00 70 00 ac 3c 00  74 09 b4 0e bb 07 00 cd  |...p..<.t.......|
00000180  10 eb f2 c3 66 a1 3e 00  66 33 d2 66 0f b7 0e 18  |....f.>.f3.f....|
00000190  00 66 f7 f1 fe c2 88 16  25 00 32 d2 66 0f b7 0e  |.f......%.2.f...|
000001a0  1a 00 66 f7 f1 8a f2 8b  c8 b8 01 02 c0 e5 06 0a  |..f.............|
000001b0  2e 25 00 86 e9 8a 16 24  00 c4 1e 48 00 cd 13 72  |.%.....$...H...r|
000001c0  a1 66 ff 06 3e 00 81 06  48 00 00 02 75 06 81 06  |.f..>...H...u...|
000001d0  4a 00 00 10 c3 44 69 73  6b 20 65 72 72 6f 72 00  |J....Disk error.|
000001e0  4e 6f 20 6c 6f 61 64 65  72 00 44 45 4c 4c 42 49  |No loader.DELLBI|
000001f0  4f 20 42 49 4e 00 00 00  00 00 00 00 00 00 55 aa  |O BIN.........U.|
00000200

Unknown BootLoader on sda3

00000000  65 66 20 6e 61 6d 65 3d  22 44 49 45 5f 4c 6f 77  |ef name="DIE_Low|
00000010  65 72 50 6f 73 74 5f 44  6f 77 65 6c 48 6f 6c 65  |erPost_DowelHole|
00000020  43 72 65 61 74 65 50 61  64 22 20 74 79 70 65 3d  |CreatePad" type=|
00000030  22 69 6e 74 22 20 74 69  74 6c 65 3d 22 d0 a1 d0  |"int" title="...|
00000040  be d0 b7 d0 b4 d0 b0 d1  82 d1 8c 20 63 20 d0 b2  |........... c ..|
00000050  d1 8b d1 81 d1 82 d1 83  d0 bf d0 be d0 bc 22 20  |.............." |
00000060  76 61 6c 75 65 3d 22 32  22 20 76 65 72 3d 22 4e  |value="2" ver="N|
00000070  58 33 2e 30 2e 30 22 20  73 63 6f 70 65 3d 22 53  |X3.0.0" scope="S|
00000080  65 73 73 69 6f 6e 22 3e  0d 0a 20 20 20 20 20 20  |ession">..      |
00000090  20 20 20 20 20 20 20 20  20 20 20 20 20 20 3c 54  |              <T|
000000a0  6f 67 67 6c 65 20 6f 66  66 3d 22 32 22 2f 3e 0d  |oggle off="2"/>.|
000000b0  0a 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |.               |
000000c0  20 20 20 20 20 3c 44 61  74 61 20 74 79 70 65 3d  |     <Data type=|
000000d0  22 65 6e 75 6d 22 3e 0d  0a 20 20 20 20 20 20 20  |"enum">..       |
000000e0  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
000000f0  20 3c 45 6e 75 6d 45 6c  65 6d 20 6e 61 6d 65 3d  | <EnumElem name=|
00000100  22 d0 94 d0 b0 22 20 76  61 6c 75 65 3d 22 31 22  |"...." value="1"|
00000110  2f 3e 0d 0a 20 20 20 20  20 20 20 20 20 20 20 20  |/>..            |
00000120  20 20 20 20 20 20 20 20  20 20 20 20 3c 45 6e 75  |            <Enu|
00000130  6d 45 6c 65 6d 20 6e 61  6d 65 3d 22 d0 9d d0 b5  |mElem name="....|
00000140  d1 82 22 20 76 61 6c 75  65 3d 22 32 22 2f 3e 0d  |.." value="2"/>.|
00000150  0a 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |.               |
00000160  20 20 20 20 20 3c 2f 44  61 74 61 3e 0d 0a 20 20  |     </Data>..  |
00000170  20 20 20 20 20 20 20 20  20 20 20 20 20 20 3c 2f  |              </|
00000180  50 72 65 66 3e 0d 0a 20  20 20 20 20 20 20 20 20  |Pref>..         |
00000190  20 20 20 20 20 20 20 3c  50 72 65 66 20 6e 61 6d  |       <Pref nam|
000001a0  65 3d 22 44 49 45 5f 4c  6f 77 65 72 50 6f 73 74  |e="DIE_LowerPost|
000001b0  5f 44 6f 77 65 6c 48 6f  6c 65 50 61 64 44 00 fe  |_DowelHolePadD..|
000001c0  ff ff 83 fe ff ff a3 05  14 08 97 2c bb 08 00 fe  |...........,....|
000001d0  ff ff 05 fe ff ff 3a 32  cf 10 a8 5a ef 07 00 00  |......:2...Z....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by drs305 on 2011-06-04
If the GNU GRUB entry boots to Ubuntu, do that and then:
```
sudo grub-install /dev/sda

```
Since Fedora's grub wasn't kind enough to include Ubuntu in it's menu (specifically) you could restore Ubuntu's Grub 2 by booting the Natty LiveCD and running the following:```

sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

This will make the MBR use Grub2 and point to your grub installation on sda5. You may need to run "sudo update-grub" after booting into Ubuntu to include Fedora in Ubuntu's boot menu.

---

### Post by UltraZone on 2011-06-07
Thanks, a simple reinstall of grub as specified and a sudo update-grub later everything's back to normal, splash screen and everything.  Thanks!

---

