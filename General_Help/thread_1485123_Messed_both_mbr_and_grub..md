---
title: "Messed both mbr and grub."
date: 2010-05-16
forum: General Help
---

### Post by ciaastek on 2010-05-16
Hi.

Today I tried to boot up Win 7 but it appeared "BOOTMGR is missing" error. I boot from windows dvd, selected repair but it didn't found my windows install. I searched through some forums and found that I have to use rebuildbcd - didn't work, then mark my partition as active - I figured out that it was active and I marked it as inactive -.-''' and now grub is also broken and I'm using live cd. 

Please help me with both problems. Windows is important because of my dad who also use this computer -.-'

---

### Post by ciaastek on 2010-05-16
Bump.

Please it's important.

---

### Post by oldfred on 2010-05-16
You can reinstall grub from a liveCD:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

And to see your entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by ciaastek on 2010-05-16
Thanks for your answer!

I repaired grub, but about Windows. That's a bigger problem I think. When I use this bootrec commands I get "Element not found." So I use bootrec /rebuildbcd and there it is - it found Windows 7 on D partition, I hit "Y" and then it displays "Element not found" again...

And here is results.txt:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Windows/System32/winload.exe /grldr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7e86428a

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    30,716,279    30,716,217   7 HPFS/NTFS
/dev/sda2          30,716,342   234,438,325   203,721,984   f W95 Ext d (LBA)
/dev/sda5          30,716,343   128,054,114    97,337,772   7 HPFS/NTFS
/dev/sda6         128,054,178   130,977,944     2,923,767  82 Linux swap / Solaris
/dev/sda7         130,978,008   181,855,799    50,877,792  83 Linux
/dev/sda8         181,855,926   234,438,325    52,582,400   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4F1FD5A5721AEAA3                       ntfs       Downloads                     
/dev/sda5        9E2465262465029F                       ntfs       ciaastek                      
/dev/sda6        c31e6ff8-d6e4-4811-bf2a-89b10a1dd486   swap                                     
/dev/sda7        f801ddad-8dca-4723-8ad0-49d17f63dc2e   ext4                                     
/dev/sda8        368BA77205FBAE02                       ntfs       Windows 7                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda8        /media/Windows 7         fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda7        /media/sda7              ext4       (rw)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set default="4"
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
search --no-floppy --fs-uuid --set f801ddad-8dca-4723-8ad0-49d17f63dc2e
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
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
search --no-floppy --fs-uuid --set f801ddad-8dca-4723-8ad0-49d17f63dc2e
set locale_dir=($root)/boot/grub/locale
set lang=pl
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,8)'
search --no-floppy --fs-uuid --set f801ddad-8dca-4723-8ad0-49d17f63dc2e
insmod tga
if background_image /boot/grub/grub_lucid.tga ; then
  set color_normal=light-gray/black
  set color_highlight=white/magenta
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/red
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set f801ddad-8dca-4723-8ad0-49d17f63dc2e
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=f801ddad-8dca-4723-8ad0-49d17f63dc2e ro vga=792 splash  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.32-22-generic (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set f801ddad-8dca-4723-8ad0-49d17f63dc2e
    echo    'Wczytywanie systemu Linux 2.6.32-22-generic...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=f801ddad-8dca-4723-8ad0-49d17f63dc2e ro single vga=792 splash
    echo    'Wczytywanie pocz&#261;tkowego dysku RAM...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set f801ddad-8dca-4723-8ad0-49d17f63dc2e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set f801ddad-8dca-4723-8ad0-49d17f63dc2e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4f1fd5a5721aeaa3
    chainloader +1
}
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
# / was on /dev/sda8 during installation
UUID=f801ddad-8dca-4723-8ad0-49d17f63dc2e /               ext4    errors=remount-ro 0       1
# /media/Downloads was on /dev/sda1 during installation
UUID=4F1FD5A5721AEAA3 /media/Downloads ntfs    defaults,umask=007,gid=46 0       0
# /media/Windows7 was on /dev/sda6 during installation
UUID=368BA77205FBAE02 /media/Windows7 ntfs    defaults,umask=007,gid=46 0       0
# /media/ciaastek was on /dev/sda5 during installation
UUID=9E2465262465029F /media/ciaastek ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda7 during installation
UUID=c31e6ff8-d6e4-4811-bf2a-89b10a1dd486 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  67.9GB: boot/grub/core.img
  92.1GB: boot/grub/grub.cfg
  85.4GB: boot/initrd.img-2.6.32-22-generic
  88.2GB: boot/vmlinuz-2.6.32-22-generic
  85.4GB: initrd.img
  88.2GB: vmlinuz
```

And btw - don't really know why there is "Windows XP" fragment in that file.

---

### Post by ciaastek on 2010-05-16
Bump again.

---

### Post by oldfred on 2010-05-16
Did you have another copy of windows? Windows offically only boots from a primary partition sda1 thru sda4. Your install is on sda8 and windows will let you install to a logical but boots thru another windows install in the primary partition.

grub shows:
set root='(hd0,1)'

So was your boot loader in sda1 and your install in sda8?

If so try putting a boot flag on sda1 with gparted, or disk utility.

Then try to repair sda1, but I have seen others with separate boot partitions have issues with repairs.

---

### Post by ciaastek on 2010-05-16
You know what? You're freaking right. Some time ago (it was probably even in late 2009) I realised that, I have boot files on /dev/sda1 and it's my Downloads partition. Yesterday I just did Ctrl+A and Shift+Del. So I just deleted bootmgr. It's totally my fault. Damn you're go(o)d :)

But is there any way to install just clean bootmgr?

---

### Post by ciaastek on 2010-05-16
Geez, this is one super fast forum :)

---

### Post by oldfred on 2010-05-16
You have a copy of botmgr in sda8 but the boot partition also has both:
 /bootmgr /Boot/BCD

If you did not delete too long ago testdisk may be able to recover it. Windows may or may not repair it, I just do not know. Testdisk says something about rebuilding bcds?

You also have a pesty /grldr which I think is from grub4dos. I would delete it (or move it somewhere else incase you want to go back)

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
I do not know if the boot partition has a backup or not.
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.ex[COLOR=Red]e /RebuildBcd[/COLOR]

Some[COLOR=Red] advanced BCD rebuild[/COLOR], Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

---

