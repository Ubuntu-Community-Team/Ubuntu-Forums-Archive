---
title: "Ubuntu 12.04 does not boot. Any suggestions appreciated"
date: 2012-06-22
forum: General Help
---

### Post by neela on 2012-06-22
I have a recently installed 12.04. I then installed Mosix 3 on top of it. After a proper orderly shutdown, my machine does not boot. The machine asks me to choose boot media and press the appropriate button.

If I try to login from a flash drive, I can. On the other hand, if I try to install afresh from the flash drive, it recognizes that there is an existing 12.04 install on the machine (I don't go through the full install of course). 

Would appreciate if someone could offer suggestions as to how I can get it to boot into my hard drive.

Thanks

---

### Post by idoitprone on 2012-06-22
> **neela said:**
> I have a recently installed 12.04. I then installed Mosix 3 on top of it. After a proper orderly shutdown, my machine does not boot. The machine asks me to choose boot media and press the appropriate button.

If I try to login from a flash drive, I can. On the other hand, if I try to install afresh from the flash drive, it recognizes that there is an existing 12.04 install on the machine (I don't go through the full install of course). 

Would appreciate if someone could offer suggestions as to how I can get it to boot into my hard drive.

Thanks

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
mosix 3 might of override the bootloader.

go to that link and run the bootscript

post it here so we can be sure

---

### Post by neela on 2012-06-22
I will go home, try it, and post the output here. But I have another machine that is setup identically, and I have no problem booting into that machine. Thanks for your response.

---

### Post by neela on 2012-06-23
Here is the RESULTS.txt file from running bootinfoscript.

Thanks for the help.

---

### Post by idoitprone on 2012-06-23
> **neela said:**
> Here is the RESULTS.txt file from running bootinfoscript.

Thanks for the help.

 Can you put it under code tags. some of us r lazy to download these things

this is your problem
```
   => No boot loader is installed in the MBR of /dev/sda. 
```make sure your live cd have the same grub version as install 

```
sudo mount /dev/sda3 /mnt

for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done

sudo chroot /mnt

sudo grub-install /dev/sda

sudo grub-install --recheck /dev/sda

sudo update-grub
# i just felt like typing these commands
#i wonder if you will fall for it
ctrl-d

sudo reboot
```these commands should do the trick unless you have a raid

[https://help.ubuntu.com/community/Grub2/Installing#Reinstall_from_the_LiveCD](https://help.ubuntu.com/community/Grub2/Installing#Reinstall_from_the_LiveCD)

i want to be lazy

---

### Post by neela on 2012-06-23
I am not sure what you mean by tags.

I tried what you suggested.

"sudo mount /dev/sda3 /mnt"    This command did not work, because the command needed me to provide file system type. And since sda3 is swap, that did not work.

I tried this with sda2 and specified ext4. This worked. Then the rest of the commands did not throw any errors. But when I reran
bootinforscript, in still got the above "=> No boot loader is installed in the MBR of /dev/sda."

I also tried this with sda1, which is vfat. In this case, the "for i .. " did not go through.

and

When I rebooted the machine, just to be sure, I got the message

"Reboot and select proper boot device or insert appropriate boot media in selected boot device"

Thanks for your help.

---

### Post by jmfal on 2012-06-23
When you reply, in the box you are typing your response are some icons (bold,italics , underline etc.) 
towards the right end of all that is  "#" which does this> [CODE][CODE]

if you highlight the terminal output right click and select copy you  can paste it between the code brackets, this will give you a scroll box which is easier for everybody to read.

same with quotes which is next to "#" on the left
I put the code tag where i want it using the cursor then place the cursor between the code brackets and use the space bar to spread them apart then go back and do your copy/paste.
After you  do it a few times it will become second nature.

---

### Post by idoitprone on 2012-06-23
> **neela said:**
> I am not sure what you mean by tags.

I tried what you suggested.

"sudo mount /dev/sda3 /mnt"    This command did not work, because the command needed me to provide file system type. And since sda3 is swap, that did not work.

I tried this with sda2 and specified ext4. This worked. Then the rest of the commands did not throw any errors. But when I reran
bootinforscript, in still got the above "=> No boot loader is installed in the MBR of /dev/sda."

I also tried this with sda1, which is vfat. In this case, the "for i .. " did not go through.

and

When I rebooted the machine, just to be sure, I got the message

"Reboot and select proper boot device or insert appropriate boot media in selected boot device"

Thanks for your help.

opps i made a mistake i accident put your swap file system
I kidda hate reading from a text file

```
sudo mount /dev/sda2 -t ext4 /mnt  for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done  sudo chroot /mnt  sudo grub-install /dev/sda  sudo grub-install --recheck /dev/sda  sudo update-grub
```

---

### Post by neela on 2012-06-23
Sorry about the text file.
I tried this:
```
sudo mount /dev/sda2 -t ext4 /mnt  for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done  sudo chroot /mnt  sudo grub-install /dev/sda  sudo grub-install --recheck /dev/sda  sudo update-grub

```

This did not throw any errors, and did not work on reboot.

Thanks.

---

### Post by neela on 2012-06-23
and this is the original text file ..

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20120131
    Boot sector info:  Syslinux looks at sector 1444576 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34       195,346       195,313 EFI System partition
/dev/sda2         195,347 1,920,005,893 1,919,810,547 Data partition (Windows/Linux)
/dev/sda3   1,920,005,894 1,953,525,118    33,519,225 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,826,383     7,826,322   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        8F73-D34A                              vfat       
/dev/sda2        f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0   ext4       
/dev/sda3        3bb4e83e-4bf9-49d9-9bd8-36aeb40f059b   swap       
/dev/sdb1        E8D7-3B7C                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt2)'
  search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
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
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.5' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
	linux	/boot/vmlinuz-3.2.5 root=UUID=f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.5
}
menuentry 'Ubuntu, with Linux 3.2.5 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
	echo	'Loading Linux 3.2.5 ...'
	linux	/boot/vmlinuz-3.2.5 root=UUID=f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.5
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
	linux	/boot/vmlinuz-3.2.0-25-generic root=UUID=f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-25-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
	echo	'Loading Linux 3.2.0-25-generic ...'
	linux	/boot/vmlinuz-3.2.0-25-generic root=UUID=f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-25-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
	echo	'Loading Linux 3.2.0-24-generic ...'
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=8F73-D34A  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=3bb4e83e-4bf9-49d9-9bd8-36aeb40f059b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/initrd.img-3.2.0-24-generic               1
               =                boot/initrd.img-3.2.0-25-generic               2
               =                boot/initrd.img-3.2.5                          3
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                boot/vmlinuz-3.2.0-24-generic                  1
               =                boot/vmlinuz-3.2.0-25-generic                  1
               =                boot/vmlinuz-3.2.5                             1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

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
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```

---

### Post by idoitprone on 2012-06-24
> **neela said:**
> and this is the original text file ..

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20120131
    Boot sector info:  Syslinux looks at sector 1444576 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34       195,346       195,313 EFI System partition
/dev/sda2         195,347 1,920,005,893 1,919,810,547 Data partition (Windows/Linux)
/dev/sda3   1,920,005,894 1,953,525,118    33,519,225 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,826,383     7,826,322   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        8F73-D34A                              vfat       
/dev/sda2        f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0   ext4       
/dev/sda3        3bb4e83e-4bf9-49d9-9bd8-36aeb40f059b   swap       
/dev/sdb1        E8D7-3B7C                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt2)'
  search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
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
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.5' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
    linux    /boot/vmlinuz-3.2.5 root=UUID=f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.5
}
menuentry 'Ubuntu, with Linux 3.2.5 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
    echo    'Loading Linux 3.2.5 ...'
    linux    /boot/vmlinuz-3.2.5 root=UUID=f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.5
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
    linux    /boot/vmlinuz-3.2.0-25-generic root=UUID=f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-25-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
    echo    'Loading Linux 3.2.0-25-generic ...'
    linux    /boot/vmlinuz-3.2.0-25-generic root=UUID=f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-25-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
    echo    'Loading Linux 3.2.0-24-generic ...'
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0
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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=f58e0212-d34e-4f0d-82b0-aecb1fb3a4b0 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=8F73-D34A  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=3bb4e83e-4bf9-49d9-9bd8-36aeb40f059b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/initrd.img-3.2.0-24-generic               1
               =                boot/initrd.img-3.2.0-25-generic               2
               =                boot/initrd.img-3.2.5                          3
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                boot/vmlinuz-3.2.0-24-generic                  1
               =                boot/vmlinuz-3.2.0-25-generic                  1
               =                boot/vmlinuz-3.2.5                             1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

=========================== sdb1/boot/grub/grub.cfg: ===========================

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

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

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
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```


argg 

it ruined the formatting this forums
```
sudo mount /dev/sda2 -t ext4 /mnt 
 for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
 sudo chroot /mnt
 sudo grub-install /dev/sda
 sudo grub-install --recheck /dev/sda
 sudo update-grub
```

---

### Post by neela on 2012-06-24
Ii am amenable to suggestion on the stylistic side. But I would also appreciate learning what I did wrong on the substantive side. What could I be missing?

---

### Post by idoitprone on 2012-06-24
> **neela said:**
> Ii am amenable to suggestion on the stylistic side. But I would also appreciate learning what I did wrong on the substantive side. What could I be missing?

in the command line. arguments are seperated by spaces and commands are seperate by semicolons or return character

This is important since commands have switch called arguments. You probably used one and didnt realized it

```
ls
```ls is the command that list the directory
 and ```
ls -l
```-l tells the command to run but behave a little differently 
according the man page ```
man ls
-l     use a long listing format

```If you remove the return character, then the command line will treat the whole like as one command

its not what i wanted since i want those commands to run with the proper switches

---

### Post by neela on 2012-06-24
I ran the commands one after the other, by manually typing them, and using a <Return> after each one.

> 
sudo mount /dev/sda2 -t ext4 /mnt <Return>
 for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done <Return>
 sudo chroot /mnt <Return>
 sudo grub-install /dev/sda <Return>
 sudo grub-install --recheck /dev/sda <Return>
 sudo update-grub <Return>


---

### Post by idoitprone on 2012-06-24
> **neela said:**
> I ran the commands one after the other, by manually typing them, and using a <Return> after each one.

did it work?

---

### Post by neela on 2012-06-24
It did not work. The commands did not throw an error, but behavior on reboot is unchanged.

---

### Post by neela on 2012-06-24
Here are some additional considerations:

When the live flash drive boots, I see this flash by very fast:   error "prefix" is not set.

The GNU GRUB Verison for the flash drive is 1.99-21ubuntu3

Separately, before the very first time it failed to boot, I saw a bunch of "Updating intel micro code" flash by very fast, with some errors thrown in there -- hasn't happened since in the following repeat attempts to boot. Looked like some mother board updating, although I am not sure how the mother board would try to update without a net connection at that point.

The system clock shows the wrong time and date now.

I am wondering if /dev/sda1 or /dev/sda3 was the place where the boot code ran from before, and whether the portion of the mother board that was pointing to these places somehow got corrupted. 

Incidentally, these are the actual commands I used and responses I got from your suggestions here:

> ubuntu@ubuntu:~$ sudo mount /dev/sda2 -t ext4 /mnt
ubuntu@ubuntu:~$  for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/#  sudo grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/#  sudo grub-install --recheck /dev/sda
Installation finished. No error reported.
root@ubuntu:/#  sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.5
Found initrd image: /boot/initrd.img-3.2.5
Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
done
root@ubuntu:/# exit
ubuntu@ubuntu:~$ 


I then run bootinfoscript on this machine, and still have 

> => No boot loader is installed in the MBR of /dev/sda.

More importantly, I have the same thing on another identical machine that is booting fine. The only difference in the bootinfoscipt output that I could find for the two machines is the following (not counting the entries for the flash drive)

For the non-booting machine:
> ================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev             /mnt/dev                 none       (rw,bind)
/dev/pts         /mnt/dev/pts             none       (rw,bind)
/dev/sda2        /mnt                     ext4       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


For the machine that is booting fine:
> 
Device           Mount_Point              Type       Options

/dev/sda1        /boot/efi                vfat       (rw)
/dev/sdb2        /                        ext4       (rw, error=remount-ro)



Can it be some strange motherboard problem?

Thanks

---

### Post by idoitprone on 2012-06-24
hmmm i just read your script again an i think you have the uefi or efi\

Is this a macbook by any chance?

or the newer motherboards

if so , i dont know if i know the commands to fix this problem. I never had uefi or efi

---

### Post by neela on 2012-06-24
It is not a macbook, but it is a newer motherboard -- about 9 months old. It is a asrock p67 extreme4 that takes in a intel i7 2600k chip.

---

### Post by idoitprone on 2012-06-24
> **neela said:**
> It is not a macbook, but it is a newer motherboard -- about 9 months old. It is a asrock p67 extreme4 that takes in a intel i7 2600k chip.

ok i never repaired a uefi before

i might give it a shot i guess

you need those efi binaries

```

sudo mount /dev/sda2 -t ext4 /mnt
sudo mount /dev/sda1 -t vfat /mnt/boot/efi
 for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
sudo cp /etc/resolv.conf /mnt/etc/
sudo chroot /mnt
sudo apt-get --reinstall  grub-efi-amd64
sudo update-grub

for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done
sudo umount /mnt/boot/efi
sudo umount /mnt

```

[https://help.ubuntu.com/community/UEFIBooting#Install_GRUB2_in_.28U.29EFI_systems](https://help.ubuntu.com/community/UEFIBooting#Install_GRUB2_in_.28U.29EFI_systems)

[http://superuser.com/questions/376470/how-to-reinstall-grub2-efi](http://superuser.com/questions/376470/how-to-reinstall-grub2-efi)

i hope this works

i heard efi is a pain. Please apple or perhaps intel do not make standards.

---

### Post by neela on 2012-06-24
Will try it. Thanks for all your time/help.

---

### Post by idoitprone on 2012-06-24
> **neela said:**
> Will try it. Thanks for all your time/help.

i can make no guarentee that it works.

[https://bbs.archlinux.org/viewtopic.php?id=140921](https://bbs.archlinux.org/viewtopic.php?id=140921)
i hope that link helps

i didnt put the proper grub instal /dev/sda

i havnt found the proper switches

it prob will not work unless

the reinstall grub2 install grub in the mbr

---

### Post by neela on 2012-06-24
I decided to reinstall from scratch as your earlier suggestion about efi did not work. Thanks again for everything.

---

### Post by nipunshakya on 2012-06-24
have you tried a graphical tool called boot-repair tool from below?? You can boot into live mode and run the tool from there... the recommended settings works most of the time,..
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by neela on 2012-06-24
I had already reinstalled, but thanks for the suggestion.

---

### Post by nipunshakya on 2012-06-24
ohh man.... missed to pour a suggestion by 36 minutes and u reinstalled... anyways, glad that your system is up and working...

Happy Linuxing

---

### Post by neela on 2012-07-01
As I mentioned earlier, I reinstalled 12.04.
2 days ago, I had a power outage for several minutes, and the problem re-occurred.

So I tried the suggestion by WinuxUser. This did not work. I then changed some of the settings of the Boot-Repair to install the MBR. Unfortunately, I did not remember all the settings -- but I just changed the MBR setting. This did not solve the problem, although the tool showed a setting where there is a 10 second wait before logging in.

then i tried the second method suggested by idoitprone -- uefi etc. this time it worked ( i think last time also the second method worked, but i did not realize it). but the feel of the login process is different now than before. for instance, now it takes 10 seconds.

i am puzzled about the process. more importantly, i am curious why loss of power reliably messes up my boot process.

---

### Post by nipunshakya on 2012-07-01
> **neela said:**
> i am puzzled about the process. more importantly, i am curious why loss of power reliably messes up my boot process.

There are answers to this question vague.... some calling it ubuntu's fault, while some saying hardware fault...
Maybe, at the hardware level, the MBR gets disturbed, which results in affecting the Bootloader. The MBR services and Bootloader are both BIOS services which results in Kernel initialization. Maybe at this point(Kernel Initialization), there is somewhere ubuntu's fault.... But who knows, thats just a maybe in pile of random answers...

---

### Post by neela on 2012-07-01
You are correct in that I may never know the definitive answer. By the way, I had to reinstall the nvidia driver, and a whole bunch of other stuff even though I didn't have reinstall 12.04 again after I followed the second suggestion by idoitProne. I am what I would call a dedicted but lay user of linux -- have been using it exclusively on 4 machines at home for 3 years, bvut I am not an expert user regarding grub, mbr etc.

---

### Post by idoitprone on 2012-07-02
> **neela said:**
> You are correct in that I may never know the definitive answer. By the way, I had to reinstall the nvidia driver, and a whole bunch of other stuff even though I didn't have reinstall 12.04 again after I followed the second suggestion by idoitProne. I am what I would call a dedicted but lay user of linux -- have been using it exclusively on 4 machines at home for 3 years, bvut I am not an expert user regarding grub, mbr etc.


uefi is the new replacement for bios. It is a complex beast. These days, classic os developers such as linus trovald hates uefi. Uefi represents the current trend of hardward; some new guy who does not understand the simplicity of hardware, decides to break everything that works and make a new one.

It is problematic because now you have problems because you have to deal with new standard in which everyone have to conform. Believe me, people hate those standards. It difficult to get right and of course, there will be more hardware bugs because of it

---

### Post by nipunshakya on 2012-07-02
> **idoitprone said:**
> 
It is problematic because now you have problems because you have to deal with new standard in which everyone have to conform. Believe me, people hate those standards. It difficult to get right and of course, there will be more hardware bugs because of it

Totally agreed to that... :D

---

### Post by idoitprone on 2012-07-02
> **WinuxUser said:**
> Totally agreed to that... :D

sighh. i kidda wish rob pike and ken thompson made standards again. If they made it, then nobody will complain

---

### Post by idoitprone on 2012-07-02
I hope amd make and push standards

[http://www.youtube.com/watch?v=X72LgcMpM9k](http://www.youtube.com/watch?v=X72LgcMpM9k)

Intel and apple should stop making standards

---

