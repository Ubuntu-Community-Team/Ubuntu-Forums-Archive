---
title: "Can't find my FAT32 partition in Ubuntu"
date: 2010-06-24
forum: General Help
---

### Post by NeverHide on 2010-06-24
I've a new format in my HDD and put win7 and ubuntu 10.04.
I made a partition about 50GB so that i can get files from ubuntu to windows and the other way around.I can see that partition in windows but not in ubuntu....Any ideas?

P.S. i can see the windows partition in ubuntu

---

### Post by anglican on 2010-06-25
> **NeverHide said:**
> I've a new format in my HDD and put win7 and ubuntu 10.04.
I made a partition about 50GB so that i can get files from ubuntu to windows and the other way around.I can see that partition in windows but not in ubuntu....Any ideas?

P.S. i can see the windows partition in ubuntu
What does ```
sudo fdisk -l
``` show?

H

---

### Post by oldfred on 2010-06-25
Before you put a lot of data into it you may want to consider NTFS. FAT will not hold files over 4GB (less one byte) and does not have journeling, so repairs are difficult.

[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by NeverHide on 2010-06-26
> **anglican said:**
> What does ```
sudo fdisk -l
``` show?

H


```


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       10199    81817600    7  HPFS/NTFS
/dev/sda3           10199       30381   162107393    5  Extended
/dev/sda5           10199       11415     9764864   83  Linux
/dev/sda6           11415       23573    97654784   83  Linux
/dev/sda7           23573       23816     1951744   82  Linux swap / Solaris
/dev/sda8           23816       30381    52732928    b  W95 FAT32


```


I'm worried about the "Partition 1 does not end on cylinder bounadary"
Do you know what it means?

---

### Post by Rubi1200 on 2010-06-26
I cannot answer your question, but I suspect we may need more information.

Please go here and follow the instructions:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Good luck!

---

### Post by Dysport on 2010-06-26
> **NeverHide said:**
> ```

/dev/sda1   *           1          **13**      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              **13**       10199    81817600    7  HPFS/NTFS
```
I'm worried about the "Partition 1 does not end on cylinder bounadary"
Do you know what it means?

You should definitely consider re-partitioning your harddisk, as you can see sda1 and sda2 end/start on the same cylinder, this can lead to a corrupt file system if data is written into the wrong partition.
When repartitioning (with fdisk) set the size selection mode to 'cylinders' rather than 'megabytes', that way you'll get it done cleanly.

---

### Post by oldfred on 2010-06-26
It may show the same cylinder number because it does not end on cylinders. Formating does not use cylinder boundaries any more.

To see more detail by sectors:
sudo fdisk -lu 

If sectors do not overlap you are ok

---

### Post by Dysport on 2010-06-26
> **oldfred said:**
> It may show the same cylinder number because it does not end on cylinders. Formating does not use cylinder boundaries any more.

**If** sectors do not overlap you are ok

And if they do you're not :) at least examine the situation further and correct if necessary. It can easily cost you several hours to recover important data from a corrupted drive or partition.

---

### Post by NeverHide on 2010-06-27
> **Rubi1200 said:**
> I cannot answer your question, but I suspect we may need more information.

Please go here and follow the instructions:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Good luck!


I'll try it as soon as i get my liveCD back from a friend i gave it to install ubuntu.
I'm writting from my win7 partition cause my BT mouse won't work now and neither does my touchpad :P
I've been getting more and more weird bugs lately nad i guess i might have to format again

---

### Post by NeverHide on 2010-06-28
> **Rubi1200 said:**
> I cannot answer your question, but I suspect we may need more information.

Please go here and follow the instructions:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Good luck!



ok i've done that,sry it took me so long.....here are the results

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   163,842,047   163,635,200   7 HPFS/NTFS
/dev/sda3         163,844,094   488,058,879   324,214,786   5 Extended
/dev/sda5         163,844,096   183,373,823    19,529,728  83 Linux
/dev/sda6         183,375,872   378,685,439   195,309,568  83 Linux
/dev/sda7         378,687,488   382,590,975     3,903,488  82 Linux swap / Solaris
/dev/sda8         382,593,024   488,058,879   105,465,856   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9CD2F1EED2F1CD10                       ntfs       System Reserved               
/dev/sda2        4E8CFD918CFD73B5                       ntfs       Windows                       
/dev/sda3: PTTYPE="dos" 
/dev/sda5        cb88a9d3-e672-441d-9fd6-2ca09f6311a9   ext4                                     
/dev/sda6        d2e57e6e-c1d3-422a-9f5d-d0960e6c501d   ext4                                     
/dev/sda7        77a6e334-6ed5-492f-823a-8f1e4bc33784   swap                                     
/dev/sda8        1E49-9C24                              vfat                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set cb88a9d3-e672-441d-9fd6-2ca09f6311a9
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set cb88a9d3-e672-441d-9fd6-2ca09f6311a9
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb88a9d3-e672-441d-9fd6-2ca09f6311a9
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=cb88a9d3-e672-441d-9fd6-2ca09f6311a9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb88a9d3-e672-441d-9fd6-2ca09f6311a9
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=cb88a9d3-e672-441d-9fd6-2ca09f6311a9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb88a9d3-e672-441d-9fd6-2ca09f6311a9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb88a9d3-e672-441d-9fd6-2ca09f6311a9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9cd2f1eed2f1cd10
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=cb88a9d3-e672-441d-9fd6-2ca09f6311a9 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=d2e57e6e-c1d3-422a-9f5d-d0960e6c501d /home           ext4    defaults        0       2
# /windows was on /dev/sda8 during installation
UUID=1E49-9C24  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda7 during installation
UUID=77a6e334-6ed5-492f-823a-8f1e4bc33784 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  86.1GB: boot/grub/core.img
  88.7GB: boot/grub/grub.cfg
  86.5GB: boot/initrd.img-2.6.32-22-generic-pae
  86.3GB: boot/vmlinuz-2.6.32-22-generic-pae
  86.5GB: initrd.img
  86.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  41 00 4e 00 47 00 5c 00  4c 00 49 00 54 00 48 00  |A.N.G.\.L.I.T.H.|
00000010  55 00 41 00 4e 00 49 00  41 00 4e 00 2e 00 4c 00  |U.A.N.I.A.N...L.|
00000020  4e 00 47 00 00 00 5c 00  44 00 45 00 56 00 49 00  |N.G...\.D.E.V.I.|
00000030  43 00 45 00 5c 00 48 00  41 00 52 00 44 00 44 00  |C.E.\.H.A.R.D.D.|
00000040  49 00 53 00 4b 00 56 00  4f 00 4c 00 55 00 4d 00  |I.S.K.V.O.L.U.M.|
00000050  45 00 33 00 5c 00 50 00  4f 00 57 00 45 00 52 00  |E.3.\.P.O.W.E.R.|
00000060  49 00 53 00 4f 00 5c 00  4c 00 41 00 4e 00 47 00  |I.S.O.\.L.A.N.G.|
00000070  5c 00 4e 00 4f 00 52 00  53 00 4b 00 2e 00 4c 00  |\.N.O.R.S.K...L.|
00000080  4e 00 47 00 00 00 5c 00  44 00 45 00 56 00 49 00  |N.G...\.D.E.V.I.|
00000090  43 00 45 00 5c 00 48 00  41 00 52 00 44 00 44 00  |C.E.\.H.A.R.D.D.|
000000a0  49 00 53 00 4b 00 56 00  4f 00 4c 00 55 00 4d 00  |I.S.K.V.O.L.U.M.|
000000b0  45 00 33 00 5c 00 50 00  4f 00 57 00 45 00 52 00  |E.3.\.P.O.W.E.R.|
000000c0  49 00 53 00 4f 00 5c 00  4c 00 41 00 4e 00 47 00  |I.S.O.\.L.A.N.G.|
000000d0  5c 00 50 00 4f 00 4c 00  49 00 53 00 48 00 2e 00  |\.P.O.L.I.S.H...|
000000e0  4c 00 4e 00 47 00 00 00  5c 00 44 00 45 00 56 00  |L.N.G...\.D.E.V.|
000000f0  49 00 43 00 45 00 5c 00  48 00 41 00 52 00 44 00  |I.C.E.\.H.A.R.D.|
00000100  44 00 49 00 53 00 4b 00  56 00 4f 00 4c 00 55 00  |D.I.S.K.V.O.L.U.|
00000110  4d 00 45 00 33 00 5c 00  50 00 4f 00 57 00 45 00  |M.E.3.\.P.O.W.E.|
00000120  52 00 49 00 53 00 4f 00  5c 00 4c 00 41 00 4e 00  |R.I.S.O.\.L.A.N.|
00000130  47 00 5c 00 50 00 4f 00  52 00 54 00 55 00 47 00  |G.\.P.O.R.T.U.G.|
00000140  55 00 45 00 53 00 45 00  28 00 42 00 52 00 41 00  |U.E.S.E.(.B.R.A.|
00000150  5a 00 49 00 4c 00 29 00  2e 00 4c 00 4e 00 47 00  |Z.I.L.)...L.N.G.|
00000160  00 00 5c 00 44 00 45 00  56 00 49 00 43 00 45 00  |..\.D.E.V.I.C.E.|
00000170  5c 00 48 00 41 00 52 00  44 00 44 00 49 00 53 00  |\.H.A.R.D.D.I.S.|
00000180  4b 00 56 00 4f 00 4c 00  55 00 4d 00 45 00 33 00  |K.V.O.L.U.M.E.3.|
00000190  5c 00 50 00 4f 00 57 00  45 00 52 00 49 00 53 00  |\.P.O.W.E.R.I.S.|
000001a0  4f 00 5c 00 4c 00 41 00  4e 00 47 00 5c 00 52 00  |O.\.L.A.N.G.\.R.|
000001b0  55 00 53 00 53 00 49 00  41 00 4e 00 2e 00 00 fe  |U.S.S.I.A.N.....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 00 2a 01 00 fe  |............*...|
000001d0  ff ff 05 fe ff ff 02 00  2a 01 00 38 a4 0b 00 00  |........*..8....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




```I've also attached the actual RESULTS txt from the boot info script

At the "Drive/Partition Info" check sda3 starts,it at 163,844,094 and ends at 488,058,879
This is the end point of the last partition,all other partitions(expet for sda1 and 2 ) are within the boundaries of the sda3 partition

---

### Post by oldfred on 2010-06-28
I do not see anything wrong with your partition table.

When you open places do you not see your FAT partition on the left side. If you did not label it with gparted or disk utility it will just have a size like 50GB file system. I prefer to add labels.

If you want to permanently mount it you should add it to your fstab.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Once you have reviewed above and understand some of the settings you can use this to create the mount and add an entry to fstab. I find I still have to edit it so I usually just add manual entries.
But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)

Typical entry (with my UUID) for a vfat partition with slightly different settings:
# /windowsold was on /dev/sdc8 during installation
UUID=F6A6-705D  /windowsold     vfat    utf8,umask=007,gid=46 0       1
or
# Entry for /dev/sda4 :
UUID=46CD-C9B2                             /media/share   vfat         user,auto,fmask=0111,dmask=0000      0  0

These were just old partitions from old systems I saved, I only use NTFS for any new windows related data and now most of my data it in ext3 or ext4 partitions.

---

