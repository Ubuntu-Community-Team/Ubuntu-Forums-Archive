---
title: "No active partition; &quot;biosdisk&quot; already loaded"
date: 2011-03-05
forum: General Help
---

### Post by Syncakes on 2011-03-05
Hello. I've been using Ubuntu 10.04 relatively fine for some months now, until today. I ran into a strange problem on grub which read "no such device", which locked me out. After digging around for a while, I managed to fix it. 

Everything went fine, until later today. I restarted my computer, and I received a "biosdisk" already loaded message, and the same grub rescue prompt. I don't know what to do. I foolishly thought that by getting rid of grub completely and putting lilo on it would fix it, and that's what I did. Now it says "no active partition", "biosdisk" already loaded, and the same grub rescue prompt. 

Here's the bootinfo:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Lilo is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 316410397 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 316405045 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 316404789 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 316403893 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

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

/dev/sda1               2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sda2    *     20,973,568   104,962,047    83,988,480   7 HPFS/NTFS
/dev/sda3         104,962,048   216,626,183   111,664,136   7 HPFS/NTFS
/dev/sda4         216,627,200   312,578,047    95,950,848   f W95 Ext d (LBA)
/dev/sda5         216,629,248   312,578,047    95,948,800   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   316,127,069   316,127,007   c W95 FAT32 (LBA)
/dev/sdb2         316,127,070   625,137,344   309,010,275   5 Extended
/dev/sdb5         316,127,133   612,510,254   296,383,122  83 Linux
/dev/sdb6         612,510,318   625,137,344    12,627,027  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8844C25B44C24B9E                       ntfs       RECOVERY                      
/dev/sda2        A2C2C43CC2C41707                       ntfs                                     
/dev/sda3        B80481B004817264                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        F6300BCA300B90B3                       ntfs       New Volume                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1809-1A41                              vfat       FREECOM HDD                   
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        fd9a4caa-0f3a-42cd-a89c-1971ab411881   ext4                                     
/dev/sdb6        ffaa0233-f01f-49d3-b54b-6340f172860e   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/FREECOM HDD       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb5        /media/fd9a4caa-0f3a-42cd-a89c-1971ab411881 ext4       (rw,nosuid,nodev,uhelper=udisks)


=================== sdb1: Location of files loaded by Grub: ===================


    PCGB: boot/grub/core.img

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
search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
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
search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    echo    'Loading Linux 2.6.31-22-generic ...'
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8844c25b44c24b9e
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set a2c2c43cc2c41707
    drivemap -s (hd0) ${root}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=ffaa0233-f01f-49d3-b54b-6340f172860e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/mnt/4000Mb.swap  none  swap  sw  0 0

=================== sdb5: Location of files loaded by Grub: ===================


 162.0GB: boot/grub/core.img
 165.2GB: boot/grub/grub.cfg
 190.5GB: boot/initrd.img-2.6.31-21-generic
 163.4GB: boot/initrd.img-2.6.31-22-generic
 169.0GB: boot/initrd.img-2.6.32-22-generic
 169.4GB: boot/initrd.img-2.6.32-23-generic
 205.1GB: boot/initrd.img-2.6.32-24-generic
 206.1GB: boot/initrd.img-2.6.32-25-generic
 206.4GB: boot/initrd.img-2.6.32-26-generic
 207.8GB: boot/initrd.img-2.6.32-27-generic
 207.9GB: boot/initrd.img-2.6.32-28-generic
 189.5GB: boot/vmlinuz-2.6.31-21-generic
 190.6GB: boot/vmlinuz-2.6.31-22-generic
 163.4GB: boot/vmlinuz-2.6.32-22-generic
 163.3GB: boot/vmlinuz-2.6.32-23-generic
 191.0GB: boot/vmlinuz-2.6.32-24-generic
 193.3GB: boot/vmlinuz-2.6.32-25-generic
 204.0GB: boot/vmlinuz-2.6.32-26-generic
 193.8GB: boot/vmlinuz-2.6.32-27-generic
 204.1GB: boot/vmlinuz-2.6.32-28-generic
 207.9GB: initrd.img
 207.8GB: initrd.img.old
 204.1GB: vmlinuz
 193.8GB: vmlinuz.old

```What do I do? Any help will be greatly appreciated. Thanks. I'm a pretty new user to all this, so please try not to overwhelm me :)

---

### Post by Syncakes on 2011-03-05
Bump. Anyone? I'm very desperate.

---

### Post by psusi on 2011-03-05
You appear to have two hard disks.  The first looks like it has Windows on it, and Ubuntu is on the second.  The problem is that you have a broken installation of grub on the first drive, and lilo on the second ( weird ).

Boot from the livecd and run this:

```

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

---

### Post by Syncakes on 2011-03-05
Thanks for the reply psusi. I followed your instructions, but I still get a "No active partition" message, and now a grub> prompt. How can this be fixed?

---

### Post by Syncakes on 2011-03-06
Bump.

---

### Post by Syncakes on 2011-03-06
I managed to get rid of the "no active partition" problem. However, now I just get the grub prompt instead of the menu on startup. I've also noticed that everytime I boot up the live cd I can't just do "sudo grub" and do work from there. I have to install grub every time. Is this normal?

I ran the bootinfo script, and this is what I got:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 316410397 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 316405045 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 316404789 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 316403893 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

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

/dev/sda1               2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sda2    *     20,973,568   104,962,047    83,988,480   7 HPFS/NTFS
/dev/sda3         104,962,048   216,626,183   111,664,136   7 HPFS/NTFS
/dev/sda4         216,627,200   312,578,047    95,950,848   f W95 Ext d (LBA)
/dev/sda5         216,629,248   312,578,047    95,948,800   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   316,127,069   316,127,007   c W95 FAT32 (LBA)
/dev/sdb2         316,127,070   625,137,344   309,010,275   5 Extended
/dev/sdb5         316,127,133   612,510,254   296,383,122  83 Linux
/dev/sdb6         612,510,318   625,137,344    12,627,027  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8844C25B44C24B9E                       ntfs       RECOVERY                      
/dev/sda2        A2C2C43CC2C41707                       ntfs                                     
/dev/sda3        B80481B004817264                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        F6300BCA300B90B3                       ntfs       New Volume                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1809-1A41                              vfat       FREECOM HDD                   
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        fd9a4caa-0f3a-42cd-a89c-1971ab411881   ext4                                     
/dev/sdb6        ffaa0233-f01f-49d3-b54b-6340f172860e   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/FREECOM HDD       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb5        /media/fd9a4caa-0f3a-42cd-a89c-1971ab411881 ext4       (rw,nosuid,nodev,uhelper=udisks)


=================== sdb1: Location of files loaded by Grub: ===================


    PCGB: boot/grub/core.img

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
search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
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
search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    echo    'Loading Linux 2.6.31-22-generic ...'
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set fd9a4caa-0f3a-42cd-a89c-1971ab411881
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8844c25b44c24b9e
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set a2c2c43cc2c41707
    drivemap -s (hd0) ${root}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=fd9a4caa-0f3a-42cd-a89c-1971ab411881 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=ffaa0233-f01f-49d3-b54b-6340f172860e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/mnt/4000Mb.swap  none  swap  sw  0 0

=================== sdb5: Location of files loaded by Grub: ===================


 162.0GB: boot/grub/core.img
 165.2GB: boot/grub/grub.cfg
 162.1GB: boot/grub/stage2
 190.5GB: boot/initrd.img-2.6.31-21-generic
 163.4GB: boot/initrd.img-2.6.31-22-generic
 169.0GB: boot/initrd.img-2.6.32-22-generic
 169.4GB: boot/initrd.img-2.6.32-23-generic
 205.1GB: boot/initrd.img-2.6.32-24-generic
 206.1GB: boot/initrd.img-2.6.32-25-generic
 206.4GB: boot/initrd.img-2.6.32-26-generic
 207.8GB: boot/initrd.img-2.6.32-27-generic
 207.9GB: boot/initrd.img-2.6.32-28-generic
 189.5GB: boot/vmlinuz-2.6.31-21-generic
 190.6GB: boot/vmlinuz-2.6.31-22-generic
 163.4GB: boot/vmlinuz-2.6.32-22-generic
 163.3GB: boot/vmlinuz-2.6.32-23-generic
 191.0GB: boot/vmlinuz-2.6.32-24-generic
 193.3GB: boot/vmlinuz-2.6.32-25-generic
 204.0GB: boot/vmlinuz-2.6.32-26-generic
 193.8GB: boot/vmlinuz-2.6.32-27-generic
 204.1GB: boot/vmlinuz-2.6.32-28-generic
 207.9GB: initrd.img
 207.8GB: initrd.img.old
 204.1GB: vmlinuz
 193.8GB: vmlinuz.old

```When I set hd(1,4) as the root, I still can't boot up by typing "boot" afterwards. It says that the kernel isn't loaded. What's going on? I can't boot into anything, and I constantly have to use my LiveCD. Any help will be appreciated.

EDIT: I've also noticed I don't have a grub.cfg file in /boot/grub. Is this normal?

---

### Post by coldraven on 2011-03-06
I don't know how to fix it but I think I know what went wrong.
If you booted into the Windows "Recovery" by mistake then even if you do nothing and then select "Cancel" it will have overwritten grub. Sorry I can't be of more help.

---

### Post by Syncakes on 2011-03-06
I've never actually ran the Windows 'Recovery' thingy.

Interestingly enough, though, everytime I needed to boot into Windows, I would have to select Windows Recovery in the GRUB menu. It wouldn't do any of the recovery things, it would just boot into Windows normally.

---

### Post by Syncakes on 2011-03-06
Sorry to bump again, but I'm in dire need of help and I can't find anything.

---

### Post by Syncakes on 2011-03-06
Bump!

---

### Post by Syncakes on 2011-03-06
Bump...

---

