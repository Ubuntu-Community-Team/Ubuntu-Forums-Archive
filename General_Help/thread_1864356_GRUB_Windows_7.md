---
title: "GRUB Windows 7"
date: 2011-10-18
forum: General Help
---

### Post by G00D_GUY on 2011-10-18
I installed Windows 7, inserted Ubuntu CD, tried to install GRUB(using terminal), but all I got was "sh:grub" when I rebooted. What do I do?

sba1 Windows7
sba2 Ubuntu 11.10
sba3 Swap

I guess should have followed the instructions and reinstalled Ubuntu, but I thought I could pull this off.

---

### Post by drs305 on 2011-10-18
I note you are using "sba" but assume this is meant to be "sda"...  If I'm incorrect, post back before running the commands following. You can run the boot info script.

If you have already installed 11.10 and merely need to install grub, try booting the 11.10 LiveCD and run the following:
```
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```
Don't include the partition number in the second command.

If a reboot doesn't display the Grub menu or boot to Ubuntu, please reboot the LiveCD and download/run the boot info script. Then post the contents of RESULTS.txt, which will show us the status of your boot files.

Get the script from the "BIS" link in my signature line.

---

### Post by G00D_GUY on 2011-10-18
```

Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM /grub/core.img

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa34aa34a

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   115,314,569   115,314,507   7 NTFS / exFAT / HPFS
/dev/sda2         115,314,570   152,424,719    37,110,150  83 Linux
/dev/sda3         152,424,720   156,296,384     3,871,665  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 41.2 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders, total 80418240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000f2156

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    77,449,364    77,449,302   7 NTFS / exFAT / HPFS
/dev/sdb2          77,449,365    80,405,324     2,955,960   5 Extended
/dev/sdb5          77,449,428    80,405,324     2,955,897  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2A44BBAF44BB7C5F                       ntfs       
/dev/sda2        5295cd03-8dbe-46c4-8245-5e777e0a33ef   ext3       
/dev/sda3        d890428a-c0fe-40db-a7d4-217bb40e482c   swap       
/dev/sdb1        406C25196C250AEC                       ntfs       
/dev/sdb5        9cab986b-013e-418b-81c3-a0a4cbb274c1   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (rw)
/dev/sr0         /cdrom                   iso9660    (rw)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             grub/core.img                                  2

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

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 5295cd03-8dbe-46c4-8245-5e777e0a33ef
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root 5295cd03-8dbe-46c4-8245-5e777e0a33ef
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5295cd03-8dbe-46c4-8245-5e777e0a33ef
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=5295cd03-8dbe-46c4-8245-5e777e0a33ef ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5295cd03-8dbe-46c4-8245-5e777e0a33ef
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=5295cd03-8dbe-46c4-8245-5e777e0a33ef ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5295cd03-8dbe-46c4-8245-5e777e0a33ef
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=5295cd03-8dbe-46c4-8245-5e777e0a33ef ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5295cd03-8dbe-46c4-8245-5e777e0a33ef
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=5295cd03-8dbe-46c4-8245-5e777e0a33ef ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5295cd03-8dbe-46c4-8245-5e777e0a33ef
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=5295cd03-8dbe-46c4-8245-5e777e0a33ef ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5295cd03-8dbe-46c4-8245-5e777e0a33ef
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=5295cd03-8dbe-46c4-8245-5e777e0a33ef ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5295cd03-8dbe-46c4-8245-5e777e0a33ef
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=5295cd03-8dbe-46c4-8245-5e777e0a33ef ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5295cd03-8dbe-46c4-8245-5e777e0a33ef
	echo	'Loading Linux 2.6.35-30-generic ...'
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=5295cd03-8dbe-46c4-8245-5e777e0a33ef ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-30-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5295cd03-8dbe-46c4-8245-5e777e0a33ef
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5295cd03-8dbe-46c4-8245-5e777e0a33ef
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 2A44BBAF44BB7C5F
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 406C25196C250AEC
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
# / was on /dev/sda2 during installation
UUID=5295cd03-8dbe-46c4-8245-5e777e0a33ef /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=d890428a-c0fe-40db-a7d4-217bb40e482c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             5
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.35-30-generic             10
               =                boot/initrd.img-2.6.38-10-generic              9
               =                boot/initrd.img-2.6.38-11-generic              8
               =                boot/initrd.img-3.0.0-12-generic              16
               =                boot/vmlinuz-2.6.35-30-generic                 4
               =                boot/vmlinuz-2.6.38-10-generic                 9
               =                boot/vmlinuz-2.6.38-11-generic                28
               =                boot/vmlinuz-3.0.0-12-generic                 146
               =                initrd.img.old                                 8
               =                vmlinuz                                       146
               =                vmlinuz.old                                   28

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

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

```
(Laughing like Tom Hanks in the Money Pit) HA! HAA HAAHAHAHHAHAH! HHAAAAAA HAHA  HA  HAAHAAAA!

Don't laugh at the size of my HARD DRIVES lol

---

### Post by G00D_GUY on 2011-10-19
If I screwed it up, just let me know. I am a big boy. I can handle it. The only that I care about is keep the Ubuntu OS in tact.

---

### Post by drs305 on 2011-10-19
Your files look okay other than the script isn't able to determine the physical location on the drive. That may be a result of the 'awk' error message. These may be eliminated if you install "gawk": 
```
sudo apt-get install gawk
```

Try booting from the grub prompt. First, let's try the really easy way:
```
configfile (hd0,2)/boot/grub/grub.cfg
```
If this works, you should see your Grub menu and be able to boot. If it boots, run the following:
```
sudo grub-install /dev/sda
sudo update-grub

```

If it doesn't display the menu, try to boot it manually from the grub prompt:
```
set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
linux (hd0,2)/vmlinuz root=/dev/sda2 ro
initrd (hd0,2)/initrd.img
boot

```
If it now boots, run the grub-install and update-grub commands above.

If you still can't boot, install *gawk* and then please rerun the boot info script.

---

### Post by oldfred on 2011-10-19
You also have some grub files in your Windows sda1 partition. Not sure if they will cause a problem or not. It does cause a problem with /Boot &  a /boot but just a /grub may not.

>     Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM [COLOR=Red]/grub/core.img[/COLOR]


---

### Post by G00D_GUY on 2011-10-19
I think I was perpetuating the problem by typing "sba2" instead of "sda2". In any case i want to thank you "DRS305". You saved my financial existence.

---

### Post by drs305 on 2011-10-19
Glad it's working. The next time you are in Windows you might consider moving/deleting the /grub/core.img file. Move it elsewhere and once you are assured everything works, delete it. It really has no purpose in your Windows OS with your current setup.

If you have no other issues in this thread, you can mark it SOLVED via the 'Thread Tools' link near the top right of the original post.

Happy Ubuntu-ing !

---

