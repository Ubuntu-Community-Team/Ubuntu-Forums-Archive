---
title: "grub 2 &quot;invalid signature&quot; chainloader CentOS 6"
date: 2012-01-05
forum: General Help
---

### Post by JDFire on 2012-01-05
Hello All,

I am trying to triple boot a system with Ubuntu 11.10, Windows 7, and CentOS 6.2. I am able to boot into each one using os_probe. What I am trying to do is chainload CentOS 6.2 so that I may update kernels and not have to boot into Ubuntu to run update-grub2. 

I was looking at the configuration for Windows 7 and it seems it is using chainloader to boot the Windows boot loader. I copied this config changing the drive location and insmod from ntfs to ext2 but when I try to load I get invalid signature error message. I have done some google searches and tried many thing which have not worked. Any ideas as to what I can do to resolve this issue.

Here is my configuration for CentOS entry.
```

menuentry "CentOS" {
        insmod part_msdos
        insmod ext2
        set root='(hd2,msdos1)'
        chainloader +1
}

```

Thank you for your time and have a great day!

Regards,
JD

---

### Post by oldfred on 2012-01-05
Drive number can depend on which drive from BIOS you set to boot from. The BIOS boot drive will always be hd0, even if it is sdc. Then hd numbers with grub are in drive order.

A new boot script is being tested, try this first:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

Current version of boot info script:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by JDFire on 2012-01-05
Hello oldfred,

I have checked the boot order in the BIOS and it seems to be correct. When I boot into CentOS 6.2 and look at its own grub config it shows the same drive that I am trying to boot.

Below you will find the results as requested.

```

                   Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Grub Legacy is installed in the MBR of /dev/sdc and looks at sector 
    226794808 on boot drive #3 for the stage2 file, but no stage2 files can be 
    found at this location..
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 48b87fd5-8f5c-42ef-91bc-9822a94c1085 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Windows is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:  Grub Legacy (v0.97) is installed in the boot sector 
                       of sda1 and looks at sector 25602 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #1 
                       for /grub/grub.conf.
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf

sda2: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdd2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdd3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sde5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

centos_vg-swap_lv': ____________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

centos_vg-root_lv': ____________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       411,647       409,600  83 Linux
/dev/sda2             411,648   145,225,727   144,814,080  8e Linux LVM


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   145,225,727   145,223,680  8e Linux LVM


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63 3,907,024,064 3,907,024,002   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 600.1 GB, 600127266816 bytes
255 heads, 63 sectors/track, 72961 cylinders, total 1172123568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdd2             206,848 1,167,925,247 1,167,718,400   7 NTFS / exFAT / HPFS
/dev/sdd3       1,167,925,248 1,172,119,551     4,194,304   7 NTFS / exFAT / HPFS


Drive: sde _____________________________________________________________________

Disk /dev/sde: 600.1 GB, 600127266816 bytes
255 heads, 63 sectors/track, 72961 cylinders, total 1172123568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1               2,048 1,168,123,903 1,168,121,856  83 Linux
/dev/sde2       1,168,125,950 1,172,121,599     3,995,650   5 Extended
/dev/sde5       1,168,125,952 1,172,121,599     3,995,648  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/centos_vg-root_lv 391ec1a3-b4c7-47f3-9a3d-8b63c3d632eb   ext4       
/dev/mapper/centos_vg-swap_lv e29a7700-2c82-4d30-b155-1c363fd86e73   swap       
/dev/sda1        58eda028-6311-43ab-a7c1-61013de52fa1   ext4       
/dev/sda2        t1zZtF-Fscb-4Yhm-07yo-hwWd-AOPV-iSF0VZ LVM2_member 
/dev/sdb1        9qXUyR-Asuj-PWqT-GvZp-5Ukt-EGq3-sG8fRa LVM2_member 
/dev/sdc1        32CEDED661DE0A1C                       ntfs       Data
/dev/sdd1        EC7AFD927AFD59B2                       ntfs       System Reserved
/dev/sdd2        C45CC1865CC173A8                       ntfs       
/dev/sdd3        1C848C60848C3DF0                       ntfs       SWAP
/dev/sde1        48b87fd5-8f5c-42ef-91bc-9822a94c1085   ext4       
/dev/sde5        63b735e8-044c-4d1c-9152-1436251d13de   swap       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
centos_vg-root_lv
centos_vg-swap_lv
control

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sde1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/CentOS            iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


============================= sda1/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd2,0)
#          kernel /vmlinuz-version ro root=/dev/mapper/centos_vg-root_lv
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda1
default=0
timeout=15
splashimage=(hd2,0)/grub/splash.xpm.gz
title CentOS (2.6.32-220.el6.x86_64)
	root (hd2,0)
	kernel /vmlinuz-2.6.32-220.el6.x86_64 ro root=/dev/mapper/centos_vg-root_lv rd_NO_LUKS LANG=en_US.UTF-8 rd_NO_MD quiet SYSFONT=latarcyrheb-sun16 rhgb rd_LVM_LV=centos_vg/root_lv  KEYBOARDTYPE=pc KEYTABLE=us rd_LVM_LV=centos_vg/swap_lv rd_NO_DM
	initrd /initramfs-2.6.32-220.el6.x86_64.img
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/grub.conf                                 1
               =                grub/menu.lst                                  1
               =                grub/stage2                                    1
               =                initramfs-2.6.32-220.el6.x86_64.img            2
               =                initrd-2.6.32-220.el6.x86_64kdump.img          1
               =                vmlinuz-2.6.32-220.el6.x86_64                  1

=========================== sde1/boot/grub/grub.cfg: ===========================

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
set default="6"
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
set root='(hd4,msdos1)'
search --no-floppy --fs-uuid --set=root 48b87fd5-8f5c-42ef-91bc-9822a94c1085
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd4,msdos1)'
  search --no-floppy --fs-uuid --set=root 48b87fd5-8f5c-42ef-91bc-9822a94c1085
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
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
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd4,msdos1)'
	search --no-floppy --fs-uuid --set=root 48b87fd5-8f5c-42ef-91bc-9822a94c1085
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=48b87fd5-8f5c-42ef-91bc-9822a94c1085 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd4,msdos1)'
	search --no-floppy --fs-uuid --set=root 48b87fd5-8f5c-42ef-91bc-9822a94c1085
	echo	'Loading Linux 3.0.0-14-generic ...'
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=48b87fd5-8f5c-42ef-91bc-9822a94c1085 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd4,msdos1)'
	search --no-floppy --fs-uuid --set=root 48b87fd5-8f5c-42ef-91bc-9822a94c1085
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=48b87fd5-8f5c-42ef-91bc-9822a94c1085 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd4,msdos1)'
	search --no-floppy --fs-uuid --set=root 48b87fd5-8f5c-42ef-91bc-9822a94c1085
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=48b87fd5-8f5c-42ef-91bc-9822a94c1085 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd4,msdos1)'
	search --no-floppy --fs-uuid --set=root 48b87fd5-8f5c-42ef-91bc-9822a94c1085
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=48b87fd5-8f5c-42ef-91bc-9822a94c1085 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd4,msdos1)'
	search --no-floppy --fs-uuid --set=root 48b87fd5-8f5c-42ef-91bc-9822a94c1085
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=48b87fd5-8f5c-42ef-91bc-9822a94c1085 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd4,msdos1)'
	search --no-floppy --fs-uuid --set=root 48b87fd5-8f5c-42ef-91bc-9822a94c1085
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd4,msdos1)'
	search --no-floppy --fs-uuid --set=root 48b87fd5-8f5c-42ef-91bc-9822a94c1085
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdd1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root EC7AFD927AFD59B2
	chainloader +1
}
menuentry "CentOS (2.6.32-220.el6.x86_64) (on /dev/mapper/centos_vg-root_lv)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 58eda028-6311-43ab-a7c1-61013de52fa1
	linux /vmlinuz-2.6.32-220.el6.x86_64 ro root=/dev/mapper/centos_vg-root_lv rd_NO_LUKS LANG=en_US.UTF-8 rd_NO_MD quiet SYSFONT=latarcyrheb-sun16 rhgb rd_LVM_LV=centos_vg/root_lv KEYBOARDTYPE=pc KEYTABLE=us rd_LVM_LV=centos_vg/swap_lv rd_NO_DM
	initrd /initramfs-2.6.32-220.el6.x86_64.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "CentOS Test " { 
        insmod part_msdos
        insmod ext2
        set root='(hd2,msdos1)'
        chainloader --force +1
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sde1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde1 during installation
UUID=48b87fd5-8f5c-42ef-91bc-9822a94c1085 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde5 during installation
UUID=63b735e8-044c-4d1c-9152-1436251d13de none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sde1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-11-generic              2
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-14-generic               2
               =                boot/vmlinuz-2.6.38-11-generic                 1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-14-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on centos_vg-swap_lv'


Unknown BootLoader on centos_vg-root_lv'



=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/centos_vg-swap_lv': No such file or directory
hexdump: /dev/mapper/centos_vg-swap_lv': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/centos_vg-root_lv': No such file or directory
hexdump: /dev/mapper/centos_vg-root_lv': No such file or directory

```

---

### Post by oldfred on 2012-01-06
If booting with grub2, you must be booting sdd. Then sda is hd1.

I prefer to keep each install on a separate drive which it looks like you have, but then also have each system's boot loader in that same drive. Then any drive failure lets me use BIOS to boot another drive. 

From Ubuntu you can reinstall grub to the MBR of any drive. If drives do not always mount in same order you need to confirm which is which before reinstalling.

sudo grub-install /dev/sde

Grub also remembers which drive to reinstall to on grub updates. So you should reset that also:
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

You have Windows in sdd, so I would also reinstall the Windows boot loader to the MBR of sdd.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I would also make sure you have a liveCD or repairCd/USB for the current version of every system you have installed.
Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by JDFire on 2012-01-06
Oldfred,

Thank you for your quick response!! I thought that I had each bootloader on its own drive and then use Ubuntus grub to chain load each one. Is there something in the config that is not showing this? Also on my Centos drive it's boot loader is pointing to the same config that I set grub 2 to chain boot. Are you seeing something different? Any other ideas as to what the problem is?

---

### Post by oldfred on 2012-01-06
When you have lots of drives it becomes difficult to keep track. And some systems do not always mount them in the same order which makes it even worse. Grub2 often works as it uses both the set root and then the search by UUID to find the boot partition.

Your centos grub.conf in sda1 shows it booting from root (hd2,0) or the fourth drive. Your manually added entry to 40_custom also shows hd2,0, So drive order must have changed. But if booting from sdd with grub2 then the entry for sda1 would be hd1,1. But you also have to pay attention to partition numbers. In grub legacy hdX,0 is the first, but in grub2 the first partition is hdX,1 or on first drive sda1 it would be hd0,1 for grub2.

I used to chainboot a lot (to partitions) with grub legacy but when Ubuntu changed to grub2, I mostly stopped using chainload entries. But I did some chainload with grub2 to other MBRs and found the boot drive is always hd0. So my chainload entries I might have in a 40_custom or a flash drive often had to be adjusted depending on which drive I selected in BIOS to boot. 

I found sometimes I just had to experiment with the entry by using e on the grub menu in grub2 and editing the entry until I found the correct drive or partition number.

---

### Post by JDFire on 2012-01-06
Thank you so much for your help!!!!  I was able to locate the issue and resolve it. It was actually two fold. First the hd setting in the CentOS grub configuration was wrong it should have been hd1,1 (Not sure how this happened as none of the drives changed and I just installed it last night). Second I had to change the grub2 to hd1,1 as you suggested. After changing the above everything is working as it should be. Thanks again for your help and have  a great day/weekend :)


Regards, 
JD

---

### Post by oldfred on 2012-01-07
Glad you got it working.:)

I find with multiple drives and/or multiple systems the bootinfoscript is invaluable for knowing what is where. I normally run it before & after changes to hard drive or new installs, just to document system in detail.

---

### Post by nardis_Miles1 on 2012-05-15
We are wrestling with a similar problem, although both Ubuntu (natty) and Centos are on RAID-1 file systems. Why have you abandoned chainloading in Grub 2?

---

