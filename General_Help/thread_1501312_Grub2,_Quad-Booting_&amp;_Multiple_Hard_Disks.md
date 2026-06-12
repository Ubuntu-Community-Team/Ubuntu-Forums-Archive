---
title: "Grub2, Quad-Booting &amp; Multiple Hard Disks"
date: 2010-06-04
forum: General Help
---

### Post by Eat_the_Path on 2010-06-04
Hi all,

I'm having some trouble getting Grub2 just the way I want it.

At the moment, I have setup a computer that has two hard drives; one internal, one an external drive inside a swappable caddy. The internal drive has an installation of Win XP Pro while the external drive has installations of Win 7, Vista and Ubuntu 10.04 on seperate partitions. 

Currently, with both HDD connected, grub loads and provides options for Ubuntu, Memtest and then the Windows Boot Menu. The last option, obviously, takes you into the Windows boot menu allow you to select XP, Vista or Win 7. However, when you remove the caddy and the only drive connected has a Win XP Pro, Grub comes up with:

error: no such device: [32 character string].
grub rescue>

What can be done about this? Can Grub take the side line when only one drive is detected or can it be relocated to a location on the eternal drive and kick in automatically when the caddy is connected? I'm a Windows tech so Ubuntu and what it can do is completely new to me.

---

### Post by r_s on 2010-06-04
install grub in the MBR of the first disk and then chain it to the second hard disk.

---

### Post by philinux on 2010-06-04
What I think you need to do is to restore the windows bootloader to the internal drive and then using the livecd install grub2 to the external drive.

Then in the bios you set it up to boot from say cdrom first then the external drive then the internal drive. This way if the external is disconnected it with then find the internal drive.

Someone else may have a better idea.

Before you proceed it would be worth running the bootinfo script to see what bootloaders are currently installed.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Eat_the_Path on 2010-06-04
> What I think you need to do is to restore the windows bootloader to the  internal drive and then using the livecd install grub2 to the external  drive.

Then in the bios you set it up to boot from say cdrom first then the  external drive then the internal drive. This way if the external is  disconnected it with then find the internal drive.This is a logical way forward, my only concern being the possibility of having to enter the BIOS or One Time Boot Menu whenever a caddy is exchanged if the BIOS doesn't immediately recognize that the external HDD just inserted has priorty. This is being set up for a classroom of students that will remove and insert their personal caddies into whichever machine is free in the classroom. I don't really want them having to mess around with the BIOS because they're students and will do their very best to sabotage the computers they need to use to pass their course.

Anyway, the results of the script: 

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdg1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,560,639   312,560,577   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,046    97,656,831    97,654,786   5 Extended
/dev/sdb5               2,048    97,656,831    97,654,784  83 Linux
/dev/sdb2          97,656,832   200,056,831   102,400,000   7 HPFS/NTFS
/dev/sdb3         200,056,832   312,578,047   112,521,216   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 1028 MB, 1028653056 bytes
16 heads, 32 sectors/track, 3924 cylinders, total 2009088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1                  32     2,009,087     2,009,056   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        723CCFE93CCFA707                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        061CFCA61CFC91C3                       ntfs                                     
/dev/sdb3        68401E64401E3970                       ntfs                                     
/dev/sdb5        d4d003e9-749a-4332-8da4-1044ed900e32   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdg1        9CB2A278B2A25714                       ntfs                                     
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sdg1        /media/9CB2A278B2A25714  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/723CCFE93CCFA707  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set d4d003e9-749a-4332-8da4-1044ed900e32
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set d4d003e9-749a-4332-8da4-1044ed900e32
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set d4d003e9-749a-4332-8da4-1044ed900e32
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=d4d003e9-749a-4332-8da4-1044ed900e32 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set d4d003e9-749a-4332-8da4-1044ed900e32
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=d4d003e9-749a-4332-8da4-1044ed900e32 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
#menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
#    recordfail
#    insmod ext2
#    set root='(hd1,5)'
#    search --no-floppy --fs-uuid --set d4d003e9-749a-4332-8da4-1044ed900e32
#    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d4d003e9-749a-4332-8da4-1044ed900e32 ro   quiet splash
#    initrd    /boot/initrd.img-2.6.32-21-generic
#}
#menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
#    recordfail
#    insmod ext2
#    set root='(hd1,5)'
#    search --no-floppy --fs-uuid --set d4d003e9-749a-4332-8da4-1044ed900e32
#    echo    'Loading Linux 2.6.32-21-generic ...'
#    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d4d003e9-749a-4332-8da4-1044ed900e32 ro single 
#    echo    'Loading initial ramdisk ...'
#    initrd    /boot/initrd.img-2.6.32-21-generic
#}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set d4d003e9-749a-4332-8da4-1044ed900e32
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set d4d003e9-749a-4332-8da4-1044ed900e32
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Boot Menu" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 723ccfe93ccfa707
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=d4d003e9-749a-4332-8da4-1044ed900e32 /               ext4    errors=remount-ro 0       1

=================== sdb5: Location of files loaded by Grub: ===================


  21.8GB: boot/grub/core.img
  21.8GB: boot/grub/grub.cfg
  21.7GB: boot/initrd.img-2.6.32-21-generic
  21.8GB: boot/initrd.img-2.6.32-22-generic
    .1GB: boot/vmlinuz-2.6.32-21-generic
  21.7GB: boot/vmlinuz-2.6.32-22-generic
  21.8GB: initrd.img
  21.7GB: initrd.img.old
  21.7GB: vmlinuz
    .1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

---

### Post by philinux on 2010-06-04
@Eat the path,

I understand about the potential bios problem. But I think the problem is that grub2 got installed to the mbr of your internal drive. So with the external unplugged it has no config files to read. Hence the error message.


See the link in my sig for more info and this helpful post.
[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub)

---

### Post by philinux on 2010-06-04
> **r_s said:**
> install grub in the MBR of the first disk and then chain it to the second hard disk.

From the boot info script output it already is, but the is no config files to edit as it is an xp only install,

---

### Post by Eat_the_Path on 2010-06-04
> **[COLOR=DarkRed]External Drive Installs and MBR - Bug [/COLOR][bug/414996]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/414996")**
When installing Ubuntu to a USB drive, the potential exists for GRUB 2 to write to the hard drive's MBR or  split the installation between the hard drive and the USB drive (rather  than completely on the USB device). This can render the main drive  unbootable. 

Workaround: During the final stages of the install there is an  "Advanced" button which allows the user to select the install location. 
> **Restoring Windows MBR without a Windows CD**
If you want to boot directly to Windows but Grub  has overwritten the MBR, the  normal procdeure is to use the Windows CD  to restore things. If you do not have access to the Windows CD, the  following commands will rewrite the MBR, removing Grub and allowing the system to boot directly  into Windows. 

Boot the Ubuntu LiveCD, open a terminal (Applications, Accessories,  Terminal) and enter the following commands. Make sure you correctly  identify the Windows device (normally *sda*):
 	Code:
 	sudo apt-get install lilo
sudo lilo -M /dev/sd**[COLOR=DarkRed]a[/COLOR]** mbr 


I guess this is my solution. Cheers.

---

### Post by Mallikarjun Kalsure on 2010-06-04
> **Eat_the_Path said:**
> I guess this is my solution. Cheers.
thank u sir

---

