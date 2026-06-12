---
title: "Can not boot Windows XP"
date: 2010-05-09
forum: General Help
---

### Post by sajumuhamma on 2010-05-09
I upgraded Ubuntu 9.10 to Ubuntu 10.04. Grub menu showing 'Microsoft Windows XP Professional (on /dev/sda1)' But I can not boot Windows XP.

Output of  **sudo fdisk -l**

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00013e01

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        9729    67906755    f  W95 Ext'd (LBA)
/dev/sda5            1276        3569    18418522    b  W95 FAT32
/dev/sda6            3569        4462     7180992+   7  HPFS/NTFS
/dev/sda7            4463        6231    14209461    b  W95 FAT32
/dev/sda8            6232        9579    26892778+  83  Linux
/dev/sda9            9580        9729     1204843+  82  Linux swap / Solaris



Output of  **mount | tail -l**


none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/saju/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=saju)


**_grub.cfg _**

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 92c09fb1c09f99d5
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

---

### Post by unplugged23 on 2010-05-09
Exactly what happens when you try and boot into xp? it is visible from grub right?

---

### Post by sajumuhamma on 2010-05-09
Showing 'Microsoft Windows XP Professional (on /dev/sda1)' in grub menu. When select that after two or three seconds grub menu reloaded.

---

### Post by wilee-nilee on 2010-05-09
Post this boot script, when you paste it into the reply highlight the text and click on the # icon in the reply panel.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
If you can't post it in code tags let us know it is very hard to read otherwise.

---

### Post by unplugged23 on 2010-05-09
I havent messed around with grub outside of arch linux. Anyways, make a backup of the current grub configuration. My only guess would be to try this for the windows entry.
```
# Windows XP
title Windows XP
rootnoverify (hd0,0)
chainloader +1

```

I do not have much experience with grub, so if be some miniscule chance this works,awesome! Otherwise, we need to hope someone that knows about grub stumbles through here :)

---

### Post by wilee-nilee on 2010-05-09
> **unplugged23 said:**
> I havent messed around with grub outside of arch linux. Anyways, make a backup of the current grub configuration. My only guess would be to try this for the windows entry.
```
# Windows XP
title Windows XP
rootnoverify (hd0,0)
chainloader +1

```

I do not have much experience with grub, so if be some miniscule chance this works,awesome! Otherwise, we need to hope someone that knows about grub stumbles through here :)

Love arch, but it runs grub1 this is probably grub2, so we want the OP to post the script. There is a problem with upgrades and upgrades of grub that give people the choice of putting it in any partition and that if you aren't sure it is okay to do this>all partitions.

---

### Post by sajumuhamma on 2010-05-09
x

---

### Post by sajumuhamma on 2010-05-09
/fastdetect

---

### Post by sajumuhamma on 2010-05-09
.old

---

### Post by sajumuhamma on 2010-05-09
=====================

---

### Post by sajumuhamma on 2010-05-09
### end

---

### Post by unplugged23 on 2010-05-09
> **wilee-nilee said:**
> Love arch, but it runs grub1 this is probably grub2, so we want the OP to post the script. There is a problem with upgrades and upgrades of grub that give people the choice of putting it in any partition and that if you aren't sure it is okay to do this>all partitions.

My bad :D

I havent used ubuntu since intrepid :D

---

### Post by wilee-nilee on 2010-05-09
Post that script again with the instruction for the scrolling text, this is important if you want any answers in general, from anybody. It is even harder to read the way it is in the thread.

---

### Post by sajumuhamma on 2010-05-09
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 100382190 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 100384342 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 100382422 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda6 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda7 and 
                       looks at sector 100382486 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda7 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,482,874    20,482,812   7 HPFS/NTFS
/dev/sda2          20,482,875   156,296,384   135,813,510   f W95 Ext d (LBA)
/dev/sda5          20,482,938    57,319,981    36,837,044   b W95 FAT32
/dev/sda6          57,320,045    71,682,029    14,361,985   7 HPFS/NTFS
/dev/sda7          71,682,093   100,101,014    28,418,922   b W95 FAT32
/dev/sda8         100,101,078   153,886,634    53,785,557  83 Linux
/dev/sda9         153,886,698   156,296,384     2,409,687  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        92C09FB1C09F99D5                       ntfs       Preetha                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0C57-2894                              vfat       PRAVEENA                      
/dev/sda6        A060CB0760CAE2E0                       ntfs       New Volume                    
/dev/sda7        F46B-9784                              vfat       PRATHEEKSHA                   
/dev/sda8        5a79b4f6-4a62-4996-9677-f7175229e7e3   ext4                                     
/dev/sda9        551793c3-f50f-4caf-a80a-dbb1e1dafd4d   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
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
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 92c09fb1c09f99d5
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=551793c3-f50f-4caf-a80a-dbb1e1dafd4d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


  51.3GB: boot/grub/core.img
  54.5GB: boot/grub/grub.cfg
  62.0GB: boot/initrd.img-2.6.31-21-generic
  56.9GB: boot/initrd.img-2.6.32-21-generic
  61.4GB: boot/initrd.img-2.6.32-22-generic
  57.5GB: boot/vmlinuz-2.6.31-21-generic
  57.4GB: boot/vmlinuz-2.6.32-21-generic
  52.6GB: boot/vmlinuz-2.6.32-22-generic
  61.4GB: initrd.img
  56.9GB: initrd.img.old
  52.6GB: vmlinuz
  57.4GB: vmlinuz.old 
```

---

### Post by wilee-nilee on 2010-05-09
That is excellent. ;) The good news is that this can be fixed. The problem is that grub is installed all through various partitions, when it should only be in sda which is the MBR of the hard disk. There might be other problems but that is what I see right away. This will take somebody a little more knowledgeable then myself to get you up and running.

So if you get no response within the next 12 hours bump the thread as the people who are good at this are on line about that time, around 12 noon pacific time.

---

### Post by sajumuhamma on 2010-05-09
Thank you  for your advice

---

### Post by sajumuhamma on 2010-05-11
Problem solved by by  [http://sourceforge.net/apps/mediawik...ms:Boot_Sector](http://sourceforge.net/apps/mediawik...ms:Boot_Sector)


:guitar:

---

