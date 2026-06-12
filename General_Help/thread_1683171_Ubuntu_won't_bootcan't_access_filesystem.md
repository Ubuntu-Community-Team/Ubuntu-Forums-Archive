---
title: "Ubuntu won't boot/can't access filesystem"
date: 2011-02-07
forum: General Help
---

### Post by TheCommissar on 2011-02-07
Hi folks, got a bit of a mysterious problem. I'm running Ubuntu 10.10 at the moment. I set it to hibernate and left, when I came back there was a mess of code on the screen and I couldn't get it to reboot into Ubuntu. The only LiveCD I have was Sabayon 5.4, which I intended to install dual-boot, so I did that, but now when I try to access my Ubuntu filesystem I get a dialog box with this in it:

> Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
I am incredibly confused and mystified. Any help would be invaluable. Thanks guys.

---

### Post by Rubi1200 on 2011-02-07
Hi,

please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

If you only have the Sabayon LiveCD, it should also work. You could also try running this from within the Sabayon install. 

By the way, if sudo does not work on Sabayon use su instead.

---

### Post by TheCommissar on 2011-02-07
Thankyou very much for your swift response. This is the contents of the RESULTS file.

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /boot/grub/grub.cfg /grub/core.img 
                       /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

vg_hal9001-lv_root: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files/dirs:   /etc/fstab

vg_hal9001-lv_swap: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,799,999   204,799,937  83 Linux
/dev/sda2         299,805,030   312,576,704    12,771,675   5 Extended
/dev/sda5         299,805,093   312,576,704    12,771,612  82 Linux swap / Solaris
/dev/sda3         204,800,000   205,823,999     1,024,000  83 Linux
/dev/sda4         205,824,000   299,804,671    93,980,672  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/vg_hal9001-lv_root c24a5a2d-bc1f-412d-9522-4e1d38cbb667   ext4                                     
/dev/mapper/vg_hal9001-lv_swap 136c2c6d-df3c-49f0-85c8-744ef91129c5   swap                                     
/dev/sda1        a1eb101c-8d0a-4a6f-aac6-dbaee5c85389   ext4                                     
/dev/sda2: PTTYPE="dos" PART_ENTRY_SCHEME="dos" PART_ENTRY_TYPE="0x5" PART_ENTRY_NUMBER="2" 
/dev/sda3        5e654c0f-64ed-40c8-bcff-c01039fc6a2e   ext4                                     
/dev/sda4        v9W9kq-bX3w-olAK-pCaI-aIMy-9at5-0rhZY9 LVM2_member                               
/dev/sda5        c3fd8add-bbcb-45ad-976d-a08172887f8d   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
vg_hal9001-lv_root
vg_hal9001-lv_swap

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/mapper/vg_hal9001-lv_root /                        ext4       (rw,commit=0)
/dev/sda3        /boot                    ext4       (rw,commit=0)


============================= sda3/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_fonts ###
### END /etc/grub.d/00_fonts ###

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="${saved_entry}"
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
insmod lvm
insmod ext2
set root='(vg_hal9001-lv_root)'
search --no-floppy --fs-uuid --set c24a5a2d-bc1f-412d-9522-4e1d38cbb667
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  # vga= is deprecated, grub2 handles this just fine
  # making grub2 res == linux fb res
  set gfxpayload=keep
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if sleep --interruptible 0 ; then
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_distro_theme ###
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 5e654c0f-64ed-40c8-bcff-c01039fc6a2e
insmod png
if background_image /grub/default-splash.png ; then
  set color_normal=white/black
  set color_highlight=magenta/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_distro_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Sabayon GNU/Linux, with Linux x86-2.6.35-sabayon" --class sabayon --class gnu-linux --class gnu --class os {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 5e654c0f-64ed-40c8-bcff-c01039fc6a2e
    echo    Loading Linux x86-2.6.35-sabayon ...
    linux    /kernel-genkernel-x86-2.6.35-sabayon ro  init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet dokeymap keymap=uk doslowusb scandelay=10 resume=swap:/dev/mapper/vg_hal9001-lv_swap real_resume=/dev/mapper/vg_hal9001-lv_swap dolvm root=/dev/mapper/vg_hal9001-lv_root docrypt 
    echo    Loading initial ramdisk ...
    initrd    /initramfs-genkernel-x86-2.6.35-sabayon
}
menuentry "Sabayon GNU/Linux, with Linux x86-2.6.35-sabayon (recovery mode)" --class sabayon --class gnu-linux --class gnu --class os {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 5e654c0f-64ed-40c8-bcff-c01039fc6a2e
    echo    Loading Linux x86-2.6.35-sabayon ...
    linux    /kernel-genkernel-x86-2.6.35-sabayon ro single init_opts=single  init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet dokeymap keymap=uk doslowusb scandelay=10 resume=swap:/dev/mapper/vg_hal9001-lv_swap real_resume=/dev/mapper/vg_hal9001-lv_swap dolvm root=/dev/mapper/vg_hal9001-lv_root docrypt
    echo    Loading initial ramdisk ...
    initrd    /initramfs-genkernel-x86-2.6.35-sabayon
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_fonts ###
### END /etc/grub.d/00_fonts ###

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="${saved_entry}"
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
insmod lvm
insmod ext2
set root='(vg_hal9001-lv_root)'
search --no-floppy --fs-uuid --set c24a5a2d-bc1f-412d-9522-4e1d38cbb667
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  # vga= is deprecated, grub2 handles this just fine
  # making grub2 res == linux fb res
  set gfxpayload=keep
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if sleep --interruptible 0 ; then
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_distro_theme ###
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 5e654c0f-64ed-40c8-bcff-c01039fc6a2e
insmod png
if background_image /grub/default-splash.png ; then
  set color_normal=white/black
  set color_highlight=magenta/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_distro_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Sabayon GNU/Linux, with Linux x86-2.6.35-sabayon" --class sabayon --class gnu-linux --class gnu --class os {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 5e654c0f-64ed-40c8-bcff-c01039fc6a2e
    echo    Loading Linux x86-2.6.35-sabayon ...
    linux    /kernel-genkernel-x86-2.6.35-sabayon ro  init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet dokeymap keymap=uk doslowusb scandelay=10 resume=swap:/dev/mapper/vg_hal9001-lv_swap real_resume=/dev/mapper/vg_hal9001-lv_swap dolvm root=/dev/mapper/vg_hal9001-lv_root docrypt 
    echo    Loading initial ramdisk ...
    initrd    /initramfs-genkernel-x86-2.6.35-sabayon
}
menuentry "Sabayon GNU/Linux, with Linux x86-2.6.35-sabayon (recovery mode)" --class sabayon --class gnu-linux --class gnu --class os {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 5e654c0f-64ed-40c8-bcff-c01039fc6a2e
    echo    Loading Linux x86-2.6.35-sabayon ...
    linux    /kernel-genkernel-x86-2.6.35-sabayon ro single init_opts=single  init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet dokeymap keymap=uk doslowusb scandelay=10 resume=swap:/dev/mapper/vg_hal9001-lv_swap real_resume=/dev/mapper/vg_hal9001-lv_swap dolvm root=/dev/mapper/vg_hal9001-lv_root docrypt
    echo    Loading initial ramdisk ...
    initrd    /initramfs-genkernel-x86-2.6.35-sabayon
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda3: Location of files loaded by Grub: ===================


 105.1GB: boot/grub/core.img
 105.1GB: boot/grub/grub.cfg
 105.1GB: boot/grub/stage2
 104.8GB: boot/initramfs-genkernel-x86-2.6.35-sabayon
 105.1GB: grub/core.img
 105.1GB: grub/grub.cfg
 105.1GB: grub/stage2
 104.8GB: initramfs-genkernel-x86-2.6.35-sabayon

======================== vg_hal9001-lv_root/etc/fstab: ========================


#
# /etc/fstab
# Created by anaconda on Mon Feb  7 10:14:43 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
/dev/mapper/vg_hal9001-lv_root /                       ext4    defaults        1 1
UUID=5e654c0f-64ed-40c8-bcff-c01039fc6a2e /boot                   ext4    defaults        1 2
/dev/mapper/vg_hal9001-lv_swap swap                    swap    defaults        0 0
UUID=c3fd8add-bbcb-45ad-976d-a08172887f8d swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically
```

---

### Post by Rubi1200 on 2011-02-07
Thanks for the results.

Okay, so something went wrong as you know. I assume you can boot normally into Sabayon?

Here is what you need to try:

boot from a LiveCD and run a file-system check on sda1:

```
sudo e2fsck -C0 -p -f -v /dev/sda1
```

If this returns errors, most likely, then run this command:

```
sudo e2fsck -f -y -v /dev/sda1
```

Reboot into Sabayon and run ```
sudo update-grub
```

You should see it add Ubuntu to the grub.cfg and if so then you should be able to boot back into Ubuntu as well.

Let me know how it goes.

---

### Post by TheCommissar on 2011-02-07
Just to be absolutely clear:

Yes, I can boot into Sabayon. Sabayon is installed on a partition, which I created after the problem with Ubuntu started (I have a research proposal to get done :P). 

Can I run those checks from the installed Sabayon partition rather than a LiveCD boot?

Cheers.

---

### Post by Rubi1200 on 2011-02-07
In other words, just to be clear, you started having problems with Ubuntu, created space for and then installed Sabayon correct?

What exactly caused this problem in the first place?

Those commands need to be run when the partition is unmounted and the safest way to do this is from the LiveCD. 

If there is important data on there, I strongly suggest you do it like this otherwise I cannot guarantee that you won't make the situation worse.

You should also consider downloading Testdisk in the event this does not work:
[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by TheCommissar on 2011-02-07
Unfortunately, when I run ```
sudo update-grub
``` in Sabayon I get this:
```

sudo: update-grub: command not found
```You suggested testdisk. There are lots of them at the link, I tried ```
emerge testdisk
``` but that didn't work. Is there a particular CD that would be best, or would any of them work?

---

### Post by Rubi1200 on 2011-02-07
Did you run the fsck? What were the results?

Run the boot script again please so we can see the changes (this can be done from within Sabayon).

System Rescue CD is supposed to be really good from what I have read.

Also, I have never used Sabayon; does it use sudo or su to elevate privileges?

If su, then run the update-grub command and preface it with that instead.

---

### Post by bilkay on 2011-02-07
Did you try selecting an earlier version from the grub menu?

---

### Post by TheCommissar on 2011-02-07
These were the results of the fsck:

```
e2fsck 1.41.12 (17-May-2010)
The filesystem size (according to the superblock) is 25600000 blocks
The physical size of the device is 25599992 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort? yes

```
and I repeated the boot script and got this: 

                     pre { font-family: "Times New Roman"; }p { margin-bottom: 0.08in; }```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /boot/grub/grub.cfg /grub/core.img 
                       /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

vg_hal9001-lv_root: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files/dirs:   /etc/fstab

vg_hal9001-lv_swap: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,799,999   204,799,937  83 Linux
/dev/sda2         299,805,030   312,576,704    12,771,675   5 Extended
/dev/sda5         299,805,093   312,576,704    12,771,612  82 Linux swap / Solaris
/dev/sda3         204,800,000   205,823,999     1,024,000  83 Linux
/dev/sda4         205,824,000   299,804,671    93,980,672  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/vg_hal9001-lv_root c24a5a2d-bc1f-412d-9522-4e1d38cbb667   ext4                                     
/dev/mapper/vg_hal9001-lv_swap 136c2c6d-df3c-49f0-85c8-744ef91129c5   swap                                     
/dev/sda1        a1eb101c-8d0a-4a6f-aac6-dbaee5c85389   ext4                                     
/dev/sda2: PTTYPE="dos" PART_ENTRY_SCHEME="dos" PART_ENTRY_TYPE="0x5" PART_ENTRY_NUMBER="2" 
/dev/sda3        5e654c0f-64ed-40c8-bcff-c01039fc6a2e   ext4                                     
/dev/sda4        v9W9kq-bX3w-olAK-pCaI-aIMy-9at5-0rhZY9 LVM2_member                               
/dev/sda5        c3fd8add-bbcb-45ad-976d-a08172887f8d   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
vg_hal9001-lv_root
vg_hal9001-lv_swap

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/mapper/vg_hal9001-lv_root /                        ext4       (rw,commit=0)
/dev/sda3        /boot                    ext4       (rw,commit=0)


============================= sda3/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_fonts ###
### END /etc/grub.d/00_fonts ###

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="${saved_entry}"
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
insmod lvm
insmod ext2
set root='(vg_hal9001-lv_root)'
search --no-floppy --fs-uuid --set c24a5a2d-bc1f-412d-9522-4e1d38cbb667
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  # vga= is deprecated, grub2 handles this just fine
  # making grub2 res == linux fb res
  set gfxpayload=keep
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if sleep --interruptible 0 ; then
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_distro_theme ###
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 5e654c0f-64ed-40c8-bcff-c01039fc6a2e
insmod png
if background_image /grub/default-splash.png ; then
  set color_normal=white/black
  set color_highlight=magenta/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_distro_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Sabayon GNU/Linux, with Linux x86-2.6.35-sabayon" --class sabayon --class gnu-linux --class gnu --class os {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 5e654c0f-64ed-40c8-bcff-c01039fc6a2e
    echo    Loading Linux x86-2.6.35-sabayon ...
    linux    /kernel-genkernel-x86-2.6.35-sabayon ro  init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet dokeymap keymap=uk doslowusb scandelay=10 resume=swap:/dev/mapper/vg_hal9001-lv_swap real_resume=/dev/mapper/vg_hal9001-lv_swap dolvm root=/dev/mapper/vg_hal9001-lv_root docrypt 
    echo    Loading initial ramdisk ...
    initrd    /initramfs-genkernel-x86-2.6.35-sabayon
}
menuentry "Sabayon GNU/Linux, with Linux x86-2.6.35-sabayon (recovery mode)" --class sabayon --class gnu-linux --class gnu --class os {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 5e654c0f-64ed-40c8-bcff-c01039fc6a2e
    echo    Loading Linux x86-2.6.35-sabayon ...
    linux    /kernel-genkernel-x86-2.6.35-sabayon ro single init_opts=single  init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet dokeymap keymap=uk doslowusb scandelay=10 resume=swap:/dev/mapper/vg_hal9001-lv_swap real_resume=/dev/mapper/vg_hal9001-lv_swap dolvm root=/dev/mapper/vg_hal9001-lv_root docrypt
    echo    Loading initial ramdisk ...
    initrd    /initramfs-genkernel-x86-2.6.35-sabayon
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_fonts ###
### END /etc/grub.d/00_fonts ###

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="${saved_entry}"
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
insmod lvm
insmod ext2
set root='(vg_hal9001-lv_root)'
search --no-floppy --fs-uuid --set c24a5a2d-bc1f-412d-9522-4e1d38cbb667
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  # vga= is deprecated, grub2 handles this just fine
  # making grub2 res == linux fb res
  set gfxpayload=keep
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if sleep --interruptible 0 ; then
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_distro_theme ###
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 5e654c0f-64ed-40c8-bcff-c01039fc6a2e
insmod png
if background_image /grub/default-splash.png ; then
  set color_normal=white/black
  set color_highlight=magenta/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_distro_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Sabayon GNU/Linux, with Linux x86-2.6.35-sabayon" --class sabayon --class gnu-linux --class gnu --class os {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 5e654c0f-64ed-40c8-bcff-c01039fc6a2e
    echo    Loading Linux x86-2.6.35-sabayon ...
    linux    /kernel-genkernel-x86-2.6.35-sabayon ro  init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet dokeymap keymap=uk doslowusb scandelay=10 resume=swap:/dev/mapper/vg_hal9001-lv_swap real_resume=/dev/mapper/vg_hal9001-lv_swap dolvm root=/dev/mapper/vg_hal9001-lv_root docrypt 
    echo    Loading initial ramdisk ...
    initrd    /initramfs-genkernel-x86-2.6.35-sabayon
}
menuentry "Sabayon GNU/Linux, with Linux x86-2.6.35-sabayon (recovery mode)" --class sabayon --class gnu-linux --class gnu --class os {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 5e654c0f-64ed-40c8-bcff-c01039fc6a2e
    echo    Loading Linux x86-2.6.35-sabayon ...
    linux    /kernel-genkernel-x86-2.6.35-sabayon ro single init_opts=single  init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet dokeymap keymap=uk doslowusb scandelay=10 resume=swap:/dev/mapper/vg_hal9001-lv_swap real_resume=/dev/mapper/vg_hal9001-lv_swap dolvm root=/dev/mapper/vg_hal9001-lv_root docrypt
    echo    Loading initial ramdisk ...
    initrd    /initramfs-genkernel-x86-2.6.35-sabayon
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda3: Location of files loaded by Grub: ===================


 105.1GB: boot/grub/core.img
 105.1GB: boot/grub/grub.cfg
 105.1GB: boot/grub/stage2
 104.8GB: boot/initramfs-genkernel-x86-2.6.35-sabayon
 105.1GB: grub/core.img
 105.1GB: grub/grub.cfg
 105.1GB: grub/stage2
 104.8GB: initramfs-genkernel-x86-2.6.35-sabayon

======================== vg_hal9001-lv_root/etc/fstab: ========================


#
# /etc/fstab
# Created by anaconda on Mon Feb  7 10:14:43 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
/dev/mapper/vg_hal9001-lv_root /                       ext4    defaults        1 1
UUID=5e654c0f-64ed-40c8-bcff-c01039fc6a2e /boot                   ext4    defaults        1 2
/dev/mapper/vg_hal9001-lv_swap swap                    swap    defaults        0 0
UUID=c3fd8add-bbcb-45ad-976d-a08172887f8d swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically 


```I tried both sudo and su, no joy with either. I'm going to download the System Rescue CD just now.

---

### Post by TheCommissar on 2011-02-14
Okay, thanks to this link:

[http://forum.sabayon.org/viewtopic.php?t=22500](http://forum.sabayon.org/viewtopic.php?t=22500)

I found out that the update-grub command doesn't exist on Sabayon, there's this instead:

```

#!/bin/sh -e exec grub-mkconfig -o /boot/grub/grub.cfg "$@"
```

I've run that instead, about to try booting into ubuntu.

---

### Post by TheCommissar on 2011-02-14
I gave up, the problem was too confusing to deal with. I asked around my techie mates and none of them could come up with anything. Thanks a lot for your help, I appreciate it. I have wiped the system and am starting again with a new install, the data was sacrificed.

Again, many thanks.

---

### Post by Rubi1200 on 2011-02-14
> **TheCommissar said:**
> I gave up, the problem was too confusing to deal with. I asked around my techie mates and none of them could come up with anything. Thanks a lot for your help, I appreciate it. I have wiped the system and am starting again with a new install, the data was sacrificed.

Again, many thanks.
Well, first of all, you are welcome for the help. Sorry I wasn't able to assist you further and that you lost the data.

Going forward, make sure to backup on a regular basis and always make sure to have some LiveCDs available for these types of situations.

Good luck!

---

### Post by TheCommissar on 2011-02-14
I went and bought an external hard drive and everything! :3

Rest assured I learned a lesson...

---

