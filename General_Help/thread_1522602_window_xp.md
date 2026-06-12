---
title: "window xp"
date: 2010-07-02
forum: General Help
---

### Post by adling11 on 2010-07-02
hello every body
i reinstall ubuntu but when i restarted my pc is login directly into ubuntu i can't choose between xp and ubuntu ....what can i do??

---

### Post by artemyv on 2010-07-02
> **adling11 said:**
> hello every body
i reinstall ubuntu but when i restarted my pc is login directly into ubuntu i can't choose between xp and ubuntu ....what can i do??
you could try
```

sudo update-grub

```

to make grub search for other oses and add them to boot menu

---

### Post by Rubi1200 on 2010-07-02
> **adling11 said:**
> hello every body
i reinstall ubuntu but when i restarted my pc is login directly into ubuntu i can't choose between xp and ubuntu ....what can i do??

Did you install Ubuntu using Wubi?

---

### Post by adling11 on 2010-07-02
i installed ubuntu from a live cd

---

### Post by Megaptera on 2010-07-02
Are you sure you set up a dual boot and didn't erase XP?

---

### Post by sahabcse on 2010-07-02
Pls follow below url for fixing the grub[Grub Fix]("http://ubuntulinux.co.in/blog/ubuntu/fixing-the-grub-error-in-ubuntu/")

---

### Post by celldweller1591 on 2010-07-02
try > sudo update-grub

---

### Post by Rubi1200 on 2010-07-02
> **sahabcse said:**
> Pls follow below url for fixing the grub[Grub Fix]("http://ubuntulinux.co.in/blog/ubuntu/fixing-the-grub-error-in-ubuntu/")

@ sahabcse: With all due respect, since we do not have enough information I think it is premature to offer solutions without knowing more.

@ adling11: Click on the link at the bottom of my post and follow the instructions there.

You need to do this from an Ubuntu CD, choosing to try the live version.

Post the results back here and we will try and help you resolve this.

---

### Post by adling11 on 2010-07-02
i didn't erase xp

---

### Post by adling11 on 2010-07-02
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000436d6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,432,559    61,432,497   7 HPFS/NTFS
/dev/sda2          61,432,560   321,669,494   260,236,935   f W95 Ext d (LBA)
/dev/sda5          61,432,623   122,865,119    61,432,497   7 HPFS/NTFS
/dev/sda6         122,865,183   184,297,679    61,432,497   b W95 FAT32
/dev/sda7         184,297,743   315,982,484   131,684,742  83 Linux
/dev/sda8         315,982,548   321,669,494     5,686,947  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A830031F3002F3DA                       ntfs                                     
/dev/sda5        E69859069858D721                       ntfs                                     
/dev/sda6        BC4F-6312                              vfat                                     
/dev/sda7        713a2a26-b473-494f-95b3-ceebf15d2d9b   ext4                                     
/dev/sda8        06571886-e2ce-46fb-9be0-cc595e398c1f   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)


=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set 713a2a26-b473-494f-95b3-ceebf15d2d9b
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 713a2a26-b473-494f-95b3-ceebf15d2d9b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=713a2a26-b473-494f-95b3-ceebf15d2d9b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 713a2a26-b473-494f-95b3-ceebf15d2d9b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=713a2a26-b473-494f-95b3-ceebf15d2d9b ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=713a2a26-b473-494f-95b3-ceebf15d2d9b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=06571886-e2ce-46fb-9be0-cc595e398c1f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  94.7GB: boot/grub/core.img
  94.7GB: boot/grub/grub.cfg
  94.7GB: boot/initrd.img-2.6.31-14-generic
  94.7GB: boot/vmlinuz-2.6.31-14-generic
  94.7GB: initrd.img
  94.7GB: vmlinuz

---

### Post by Rubi1200 on 2010-07-02
Under normal circumstances, most booting problems are/can be solved by re-installing GRUB to the MBR.

But, there is something here that makes me unsure whether that would be the right thing to do here:

```
sda5: __________________________________________________  _______________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: __________________________________________________  _______________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   
```

Hang in there a bit longer until we see if someone else has some ideas for this.

---

### Post by adling11 on 2010-07-02
thank u anyway i decided and i reinstalled xp and ubuntu
thanks a lot

---

### Post by Rubi1200 on 2010-07-02
> **adling11 said:**
> thank u anyway i decided and i reinstalled xp and ubuntu
thanks a lot

I am glad you got it sorted out; and sometimes re-installing is the best thing to do as well as being a good learning experience.

:)

---

