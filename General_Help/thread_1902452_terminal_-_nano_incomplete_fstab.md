---
title: "terminal - nano incomplete fstab"
date: 2011-12-30
forum: General Help
---

### Post by toyoracer on 2011-12-30
Good day. I have my partitions setup and aligned, but I cannot edit the /etc/fstab as it's incomplete in nano. Tring to auto mount my partitions. I have been following the ubuntu guides to no avail. Thanks for any advice. Checked if already posted nothing.

---

### Post by drs305 on 2011-12-30
Are you sure it's nano and not the fstab file itself? It doesn't sound right that nano isn't loading the entire fstab file unless it's corrupt. Are you trying to edit is as root:  *sudo nano /etc/fstab* 

Have you tried "cat /etc/fstab" just to compare the results with what nano shows as the entire file?

---

### Post by toyoracer on 2011-12-30
Thank you, yes I tried nano, gedit, cat all in root. They only show 2 partitions. I am tring to mount a couple of more. Tried mounted and unmounted all the same result

craig@craig-GA-990FXA-UD5:~$ sudo cat /etc/fstab
[sudo] password for craig: 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a9758cc4-cc4a-46a9-bca5-ffd4821d4d28 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=0bd1adda-7755-480c-b53a-0b85e839b82a none            swap    sw              0       0
craig@craig-GA-990FXA-UD5:~$

---

### Post by drs305 on 2011-12-30
OK - you want to add additional partitions to fstab...

Here is a good guide written by forum member *bodhi.zazen* on how to construct fstab entries:
[How to fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by toyoracer on 2011-12-30
I have tried those guides. The UUID will not show up in the editor so I can edit fstab, so HDD's auto mount.

---

### Post by drs305 on 2011-12-30
You should be able to get the UUID by running "sudo blkid" in a terminal.

If you need help with creating an fstab entry one way would be to download and run the boot info script. It was designed to report information needed to fix boot issues, but it would provide all the information a helper would need to create an fstab entry for any partition the script finds.

You would download the script from the following site. Run it, post the contents of RESULTS.txt and tell us which partitions you would like to mount and the mountpoint you would like them mounted on.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by toyoracer on 2011-12-30
```
/home/craig/Desktop/RESULTS.txt
```I would like sdb1 to be /media or correctly /media on sdb1 

I would also like to move /var and any thing else off the SSD - sda1

                  Boot Info Script 0.60    from 17 May 2011

                  Boot Info Script 0.60    from 17 May 2011
[HTML]                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    17777152 of the same hard drive for core.img. core.img is at this location 
    and looks for  on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.
 => No boot loader is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

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

sdc2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdd2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdd3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdd4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sde2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sde3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sde4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   117,231,407   117,231,407  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048    57,956,351    57,954,304 EFI System partition
/dev/sda2      57,956,352   114,542,591    56,586,240 Data partition (Windows/Linux)
/dev/sda3     114,542,592   117,229,567     2,686,976 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048   975,177,727   975,175,680 Data partition (Windows/Linux)
/dev/sdb2     975,177,728 1,950,353,407   975,175,680 Data partition (Windows/Linux)
/dev/sdb3   1,950,353,408 2,925,529,087   975,175,680 Data partition (Windows/Linux)
/dev/sdb4   2,925,529,088 3,907,028,991   981,499,904 Logical Volume Manager (LVM) partition (Linux)

Drive: sdc _____________________________________________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdc1           2,048   975,177,727   975,175,680 Logical Volume Manager (LVM) partition (Linux)
/dev/sdc2     975,177,728 1,950,353,407   975,175,680 Logical Volume Manager (LVM) partition (Linux)
/dev/sdc3   1,950,353,408 2,925,529,087   975,175,680 Logical Volume Manager (LVM) partition (Linux)
/dev/sdc4   2,925,529,088 3,892,316,159   966,787,072 Logical Volume Manager (LVM) partition (Linux)
/dev/sdc5   3,892,316,160 3,907,024,064    14,707,905 Swap partition (Linux)

Drive: sdd _____________________________________________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdd1           2,048   975,177,727   975,175,680 Data partition (Windows/Linux)
/dev/sdd2     975,177,728 1,950,353,407   975,175,680 Data partition (Windows/Linux)
/dev/sdd3   1,950,353,408 2,925,529,087   975,175,680 Data partition (Windows/Linux)
/dev/sdd4   2,925,529,088 3,907,028,991   981,499,904 Data partition (Windows/Linux)

Drive: sde _____________________________________________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sde1           2,048   975,177,727   975,175,680 Data partition (Windows/Linux)
/dev/sde2     975,177,728 1,950,353,407   975,175,680 Data partition (Windows/Linux)
/dev/sde3   1,950,353,408 2,925,529,087   975,175,680 Data partition (Windows/Linux)
/dev/sde4   2,925,529,088 3,907,028,991   981,499,904 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        a9758cc4-cc4a-46a9-bca5-ffd4821d4d28   ext4       
/dev/sda2        c6743b58-e0f7-4051-839c-069526f48983   ext4       
/dev/sdb1        607585fc-75f8-4577-8330-58e68b41da5f   ext4       
/dev/sdb2        73ef247d-0d53-467f-bea1-3874513f5dcc   ext4       
/dev/sdb3        ac0c8606-1f0e-4dea-bcdb-491752679124   ext4       
/dev/sdb4        b8b2282e-53df-4eab-b80a-ad31818e18f4   ext4       
/dev/sdc1        e7274f35-1b95-4adb-be64-c265c9d2a478   ext4       
/dev/sdc2        e92f3b6a-4f23-42ce-90ec-4195212dc12f   ext4       
/dev/sdc3        a14d2da8-26cc-4a31-8edc-82fd78079b96   ext4       
/dev/sdc4        56dcf873-6df7-43ea-ac26-63ad17b4c36a   ext4       
/dev/sdc5        776f08ae-2396-45e1-a8e4-0636a58ade2a   swap       swap
/dev/sdd1        355c7a0a-9704-4de8-81e9-ea89cd22801f   ext4       
/dev/sdd2        4d93215b-96ad-42a0-98f4-7daf9d95b1c2   ext4       
/dev/sdd3        50e0409e-c3f3-4c7f-9790-c75149857039   ext4       
/dev/sdd4        67869a5e-2ac9-4608-9720-b80ea8558434   ext4       
/dev/sde1        80dd0d9b-438f-4162-ad42-3b0518e9489f   ext4       
/dev/sde2        35dc8fa0-9188-4481-afb2-f1277d343c45   ext4       
/dev/sde3        7111af24-abcb-427c-a7a1-663b153c583a   ext4       
/dev/sde4        5fd25766-e32f-4ee5-a9f5-0a54a07c59ef   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,gpt1)'
search --no-floppy --fs-uuid --set=root a9758cc4-cc4a-46a9-bca5-ffd4821d4d28
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt1)'
  search --no-floppy --fs-uuid --set=root a9758cc4-cc4a-46a9-bca5-ffd4821d4d28
  set locale_dir=($root)/boot/grub/locale
  set lang=en_CA
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
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt1)'
    search --no-floppy --fs-uuid --set=root a9758cc4-cc4a-46a9-bca5-ffd4821d4d28
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=a9758cc4-cc4a-46a9-bca5-ffd4821d4d28 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt1)'
    search --no-floppy --fs-uuid --set=root a9758cc4-cc4a-46a9-bca5-ffd4821d4d28
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=a9758cc4-cc4a-46a9-bca5-ffd4821d4d28 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt1)'
    search --no-floppy --fs-uuid --set=root a9758cc4-cc4a-46a9-bca5-ffd4821d4d28
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=a9758cc4-cc4a-46a9-bca5-ffd4821d4d28 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt1)'
    search --no-floppy --fs-uuid --set=root a9758cc4-cc4a-46a9-bca5-ffd4821d4d28
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=a9758cc4-cc4a-46a9-bca5-ffd4821d4d28 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt1)'
    search --no-floppy --fs-uuid --set=root a9758cc4-cc4a-46a9-bca5-ffd4821d4d28
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt1)'
    search --no-floppy --fs-uuid --set=root a9758cc4-cc4a-46a9-bca5-ffd4821d4d28
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 0d04ec4f-0fa4-44d0-a6e0-85db50123968
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=0d04ec4f-0fa4-44d0-a6e0-85db50123968 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 0d04ec4f-0fa4-44d0-a6e0-85db50123968
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=0d04ec4f-0fa4-44d0-a6e0-85db50123968 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-12-generic
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a9758cc4-cc4a-46a9-bca5-ffd4821d4d28 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=0bd1adda-7755-480c-b53a-0b85e839b82a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-14-generic               1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-14-generic                  1
               =                initrd.img                                     1
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
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
 [/HTML]

---

### Post by drs305 on 2011-12-30
Please copy the contents of RESULTS.txt, then start a new post and click the # icon in the post's menu. This will generate 'code' tags. Paste the contents between the code tags. This will allow us to see the contents in a format that doesn't take up too much space.

---

### Post by toyoracer on 2011-12-30
Sorry tried # left it full page.:confused:

---

### Post by drs305 on 2011-12-31
For your sdb4, the entry would be something like the following. The "users,auto" will mount the the partition on boot. 

You will want to mount the partition on a folder in /media, not on /media directly. So first, create the mountpoint and make yourself the owner. I'll use *data* as the mountpoint name, but use whatever you would like. Since you mentioned /media, that's where I put it although I prefer /mnt so it doesn't appear on the Desktop:

$USER is the current user, the colon ( : ) makes the group owner the same.

```

sudo blkid # To get the UUID numbers
sudo mkdir /media/*data*
sudo chown -R $USER: /media/*data*
gksu gedit /etc/fstab &

```

> 
UUID=b8b2282e-53df-4eab-b80a-ad31818e18f4    /media/*data* ext4   defaults,users 0 2

For the /var folder, again create the mountpoint (/media/var), or "/mnt/var" if you don't want it displayed on the desktop, copy the /var file to the partition you want to use, and then add the fstab entry.

Create the new /var folder on the correct partition.
```
sudo mkdir /mnt/var
sudo mount /dev/sd**[COLOR="DarkRed"]b2[/COLOR]** /mnt/var
sudo cp -p -R /var/* /mnt/var/
sudo umount /dev/sd**[COLOR="DarkRed"]b2[/COLOR]**
```

Add this to fstab, using the correct UUID:
> UUID=**[COLOR="DarkRed"]73ef247d-0d53-467f-bea1-3874513f5dcc[/COLOR]** /var ext4 defaults 0 1
In this case, do not 'chown' the contents - you want them to belong to root. The "-p" switch in the copy command will preserve the 'root' ownership during the copy process.

You should 'test'  your fstab entries before rebooting to make sure they are correct. Close all apps and then:
```
sudo umount -a # You will get busy messages for partitions in use.
sudo mount -a # You should not get any error messages as the system tries to mount all fstab entries.
```

---

### Post by toyoracer on 2011-12-31
Thank you so much. Started with /var on sdb2. Have an error.

```
sudo umount -a
[sudo] password for craig: 
umount: /run/shm: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /run: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
craig@craig-GA-990FXA-UD5:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

craig@craig-GA-990FXA-UD5:~$ dmesg | tail
[    9.269298] [fglrx] Gart cacheable size:508 M.
[    9.269303] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[    9.269305] [fglrx] Reserved FB block: Unshared offset:f8fd000, size:403000 
[    9.269306] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[   10.178213] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   10.548811] r8169 0000:05:00.0: eth0: link up
[   10.549553] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.240016] eth0: no IPv6 routers present
[ 1811.740522] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[ 3772.288536] EXT4-fs (sdb2): Unrecognized mount option "0" or missing value
craig@craig-GA-990FXA-UD5:~$ 
```

---

### Post by drs305 on 2011-12-31
I modified the instructions in my previous post regarding the copying of the 'var' folder and I've updated the instructions specifically for your sdb2 partition. The previous instructions may have created a /mnt/var/var folder and copied your system files there.

Assuming you haven't been able to mount /var to the new partition, mount sdb2 and remove what you copied there - specifically the /mnt/var/var folder, if it exists.  Be sure it's not your 'real' var folder.

Then follow the instructions in the previous post and see if it works now.

---

### Post by toyoracer on 2011-12-31
Okay did that, files are all in "root" so no user access and did not auto mount.

Maybe I should try it with the first method?

---

### Post by drs305 on 2011-12-31
I'm not sure of the status of your system. If you correctly copied the /var folder to your new partition, this is what you should be seeing after you mount the new partition to /mnt/var:

```
ls /mnt/var # All the same things you see if you run 'ls /var'.
```

Unmount /dev/sdb2, then when you run 'sudo mount -a' you should get no messages about sdb2 and /var should be using your new partition. You can check by creating a file in /var. It should show if you use the "ls /var" command and disappear if you unmount /dev/sdb2:

```
sudo mount -a # This should mount your new var partition according to your fstab entry *
sudo touch /var/testfile
ls /var # You should see 'testfile' listed
sudo umount /mnt/var
ls /var # You should not see 'testfile' as it is reporting your original 'var' folder contents
```

* If it doesn't mount, you may be able to more clearly see the reason why by trying to mount the specific partition:
```
sudo mount /dev/sdb2 /mnt/var
```

Note: I've never used an SSD before. It's possible that the system may have problems because the files it calls from the /var folder aren't yet mounted. I would think this might happen on a cold boot, but not when testing it on a running system. You might search to make sure you can do what you desire when splitting system files between SSD and conventional drives.

---

### Post by toyoracer on 2011-12-31
Okay tried that the test file is in the original /var file the /mnt/var file is empty. I cannot copy files since every file is in root permission.

I will try doing what you had for the media file.


Just thinking, how do I change file system to "user" then make the changes then put back to "root" might be the problem.

---

### Post by drs305 on 2011-12-31
> **toyoracer said:**
> Okay tried that the test file is in the original /var file the /mnt/var file is empty. I cannot copy files since every file is in root permission.

I will try doing what you had for the media file.

Just thinking, how do I change file system to "user" then make the changes 
then put back to "root" might be the problem.

I strongly recommend NOT trying to change permissions on your system folders. If it gets messed up, it's hard to get all the permissions back the way they should be. Ownership is a bit easier, but I'd still shy away from it. 

Using the "sudo cp -p -R" command should allow you to copy any system file to any location. You say you can't copy them because they are owned by root but this command should allow you to accomplish it. You can also try opening Nautilus as root (gksu nautilus /var) and copy the files that way. Just make sure the new partition is mounted before copying to /mnt/var. Otherwise you will be copying the files to the /mnt/var folder on your real system partition.

---

### Post by toyoracer on 2011-12-31
I have tried everything, Nothing all access root, it worked in nautilus with user permissions.

I also have a lock-up on reboot. have to hard reboot. 

I also made a /docs at /mnt/docs using the /media example same issue. Also none auto-mount.

---

### Post by drs305 on 2011-12-31
You might run the boot info script and repost the results. Perhaps it's time I step aside and let others take a fresh look at this.

Added: You could add "auto" to the options to see if that makes a difference, although 'defaults' is supposed to include the 'auto' option.

---

### Post by toyoracer on 2011-12-31
I thank you very much for taking all of this time. :D

I added the "auto" into /etc/fstab . I got this warning.

```
(gedit:5361): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
craig@craig-GA-990FXA-UD5:~$ sudo mount -a
craig@craig-GA-990FXA-UD5:~$ 
  
``````

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    17777152 of the same hard drive for core.img. core.img is at this location 
    and looks for  on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.
 => No boot loader is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

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

sdc2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdd2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdd3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdd4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sde2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sde3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sde4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   117,231,407   117,231,407  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048    57,956,351    57,954,304 EFI System partition
/dev/sda2      57,956,352   114,542,591    56,586,240 Data partition (Windows/Linux)
/dev/sda3     114,542,592   117,229,567     2,686,976 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048   975,177,727   975,175,680 Data partition (Windows/Linux)
/dev/sdb2     975,177,728 1,950,353,407   975,175,680 Data partition (Windows/Linux)
/dev/sdb3   1,950,353,408 2,925,529,087   975,175,680 Data partition (Windows/Linux)
/dev/sdb4   2,925,529,088 3,907,028,991   981,499,904 Logical Volume Manager (LVM) partition (Linux)

Drive: sdc _____________________________________________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdc1           2,048   975,177,727   975,175,680 Logical Volume Manager (LVM) partition (Linux)
/dev/sdc2     975,177,728 1,950,353,407   975,175,680 Logical Volume Manager (LVM) partition (Linux)
/dev/sdc3   1,950,353,408 2,925,529,087   975,175,680 Logical Volume Manager (LVM) partition (Linux)
/dev/sdc4   2,925,529,088 3,892,316,159   966,787,072 Logical Volume Manager (LVM) partition (Linux)
/dev/sdc5   3,892,316,160 3,907,024,064    14,707,905 Swap partition (Linux)

Drive: sdd _____________________________________________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdd1           2,048   975,177,727   975,175,680 Data partition (Windows/Linux)
/dev/sdd2     975,177,728 1,950,353,407   975,175,680 Data partition (Windows/Linux)
/dev/sdd3   1,950,353,408 2,925,529,087   975,175,680 Data partition (Windows/Linux)
/dev/sdd4   2,925,529,088 3,907,028,991   981,499,904 Data partition (Windows/Linux)

Drive: sde _____________________________________________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sde1           2,048   975,177,727   975,175,680 Data partition (Windows/Linux)
/dev/sde2     975,177,728 1,950,353,407   975,175,680 Data partition (Windows/Linux)
/dev/sde3   1,950,353,408 2,925,529,087   975,175,680 Data partition (Windows/Linux)
/dev/sde4   2,925,529,088 3,907,028,991   981,499,904 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        a9758cc4-cc4a-46a9-bca5-ffd4821d4d28   ext4       
/dev/sda2        c6743b58-e0f7-4051-839c-069526f48983   ext4       
/dev/sdb1        1c2849b4-c581-4331-b9b5-e660d89ac557   ext4       
/dev/sdb2        38354160-25db-4e8e-92f3-7a2dc8cbede0   ext4       var
/dev/sdb3        4b0309b6-af04-4850-814e-60e37976c5b8   ext4       
/dev/sdb4        65bfa0ff-e848-4b21-890c-2190542ecf22   ext4       
/dev/sdc1        e7274f35-1b95-4adb-be64-c265c9d2a478   ext4       
/dev/sdc2        e92f3b6a-4f23-42ce-90ec-4195212dc12f   ext4       
/dev/sdc3        a14d2da8-26cc-4a31-8edc-82fd78079b96   ext4       
/dev/sdc4        56dcf873-6df7-43ea-ac26-63ad17b4c36a   ext4       
/dev/sdc5        776f08ae-2396-45e1-a8e4-0636a58ade2a   swap       swap
/dev/sdd1        355c7a0a-9704-4de8-81e9-ea89cd22801f   ext4       
/dev/sdd2        4d93215b-96ad-42a0-98f4-7daf9d95b1c2   ext4       
/dev/sdd3        50e0409e-c3f3-4c7f-9790-c75149857039   ext4       
/dev/sdd4        67869a5e-2ac9-4608-9720-b80ea8558434   ext4       
/dev/sde1        80dd0d9b-438f-4162-ad42-3b0518e9489f   ext4       
/dev/sde2        35dc8fa0-9188-4481-afb2-f1277d343c45   ext4       
/dev/sde3        7111af24-abcb-427c-a7a1-663b153c583a   ext4       
/dev/sde4        5fd25766-e32f-4ee5-a9f5-0a54a07c59ef   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /mnt/docs                ext4       (rw,noexec,nosuid,nodev,commit=0)
/dev/sdb2        /var                     ext4       (rw,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,gpt1)'
search --no-floppy --fs-uuid --set=root a9758cc4-cc4a-46a9-bca5-ffd4821d4d28
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt1)'
  search --no-floppy --fs-uuid --set=root a9758cc4-cc4a-46a9-bca5-ffd4821d4d28
  set locale_dir=($root)/boot/grub/locale
  set lang=en_CA
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
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt1)'
    search --no-floppy --fs-uuid --set=root a9758cc4-cc4a-46a9-bca5-ffd4821d4d28
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=a9758cc4-cc4a-46a9-bca5-ffd4821d4d28 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt1)'
    search --no-floppy --fs-uuid --set=root a9758cc4-cc4a-46a9-bca5-ffd4821d4d28
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=a9758cc4-cc4a-46a9-bca5-ffd4821d4d28 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt1)'
    search --no-floppy --fs-uuid --set=root a9758cc4-cc4a-46a9-bca5-ffd4821d4d28
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=a9758cc4-cc4a-46a9-bca5-ffd4821d4d28 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt1)'
    search --no-floppy --fs-uuid --set=root a9758cc4-cc4a-46a9-bca5-ffd4821d4d28
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=a9758cc4-cc4a-46a9-bca5-ffd4821d4d28 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt1)'
    search --no-floppy --fs-uuid --set=root a9758cc4-cc4a-46a9-bca5-ffd4821d4d28
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt1)'
    search --no-floppy --fs-uuid --set=root a9758cc4-cc4a-46a9-bca5-ffd4821d4d28
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 0d04ec4f-0fa4-44d0-a6e0-85db50123968
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=0d04ec4f-0fa4-44d0-a6e0-85db50123968 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sdc1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 0d04ec4f-0fa4-44d0-a6e0-85db50123968
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=0d04ec4f-0fa4-44d0-a6e0-85db50123968 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-12-generic
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a9758cc4-cc4a-46a9-bca5-ffd4821d4d28 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=0bd1adda-7755-480c-b53a-0b85e839b82a none            swap    sw              0       0
UUID=38354160-25db-4e8e-92f3-7a2dc8cbede0 /var ext4 defaults 0 1 
UUID=1c2849b4-c581-4331-b9b5-e660d89ac557 /mnt/docs ext4 defaults,users 0 2 

--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-14-generic               1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-14-generic                  1
               =                initrd.img                                     1
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
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
I love ubuntu -9.10- and built this computer to play in it, but I need help. Please.

---

### Post by drs305 on 2011-12-31
By the way, here is an extract from an old development thread (the forum is now closed) addressing the GTK error message:

> 
drs305
November 28th, 2010, 03:17 PM
I've read this thread and as a frequent user of "gksu gedit" I wanted to see what was happening.

I installed the daily build of Natty, ran 'gksu gedit' and got the same errors as Quackers. Even with the messages, the root-owned file saved and reopened correctly despite the terminal messages.

I could not create the recently-used.xbel file using "sudo touch...".

I then installed nautilus-gksu. (Edit: You may need to reboot or logout/login before this option will be displayed). I opened the /etc/grub.d folder as administrator by right clicking the folder and choosing that option, edited 10_linux by clicking on it and opening with 'text editor' and saved the file. This being a completely GUI operation, I never saw any warning messages.

Next I inspected /root/.local/share and there was recently-used.xbel.

At some point I rebooted, then ran the "gksu gedit" command again. Voila, no error messages in the terminal of any sort.

I'm posting for several reasons, among them one way to create the recently-used.xbel file and rid the error messages, and also so someone would confirm the same happens for them.

---

