---
title: "Triple Boot system, Grub doesn't find XP"
date: 2011-06-25
forum: General Help
---

### Post by jruh64 on 2011-06-25
Hi

I just did clean installs of Windows 7, Windows XP and Ubuntu 11.04 (installed in that order). Each OS is installed on a separate HDD.

When I boot up, Grub only sees Ubuntu and Windows 7 (on sda and sdb respectively). It does not see my XP install (on sdc).

I've searched and found posts and tutorials for similar issues, but none that seem to fit my specific situation.

I would appreciate any help.

Thanks, John

---

### Post by jerrrys on 2011-06-26
have you tried
sudo update-grub

---

### Post by jruh64 on 2011-06-26
Thanks Jerrys but I did already try that.  Sorry I should have mentioned that in my original post.
 
John

---

### Post by oldfred on 2011-06-26
Even if it is a separate hard drive, if windows sees the second install, it will combine the boots as windows can only boot from one copy of windows. It literally moves the boot files to the first install. Then grub cannot see the boot files for the second install as they do not exist.

If XP was you second install, you can copy the boot files back to the XP install and edit boot.ini to the new drive/partition. Then the update-grub should find the XP install.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by jruh64 on 2011-06-27
Thanks Oldfred, I will read through those links more thoroughly when I get a chance.
Sounds like I would have been much better off if I had installed XP first, W7 second, and Ubuntu last.  I might still wipe the drives and do that next.
 
>  
If XP was you second install, you can copy the boot files back to the XP install and edit boot.ini to the new drive/partition.

This sounds like an option but I don't know which files to copy to where and wouldn't know what to edit in the boot.ini file.
 
Thanks again, John

---

### Post by oldfred on 2011-06-27
These are the boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Boot.ini has to refer to the correct drive & partition. It is a simple text file, but if edited in Ubuntu you have to be careful to make sure you resave as windows format not Linux as the line endings are different.

If editing windows files like boot.ini
(Using nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to choose windows format.


How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)

If you want specific instructions post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by jruh64 on 2011-06-27
OK I found a copy of boot.ini, ntldr, and NTDETECT.COM in the root of my Windows7 install.  I copied them to the root of my XP install, ran sudo update-grub and rebooted.
Grub does now see my XP installation but when I try to boot into it i get:

```
Missing or corrupt file
<windows root>\system32\hal.dll
please reinstall a copy of the above file
```I assume I will need to edit the boot.ini to fix this?

Here is the results of excellent Boot Info Script.

Thanks, John
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 6d6e550d-c564-4eb3-aab2-d95d43a799e1 root 
    set 
    prefix=($root)/grub--------------------------------------------------------
    ------------------------.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   204,802,047   204,800,000   7 NTFS / exFAT / HPFS
/dev/sda2         204,802,048   614,402,047   409,600,000   7 NTFS / exFAT / HPFS
/dev/sda3         614,402,048 1,953,523,711 1,339,121,664   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048       976,895       974,848  83 Linux
/dev/sdb2             976,896    16,601,087    15,624,192  82 Linux swap / Solaris
/dev/sdb3          16,601,088    75,194,367    58,593,280  83 Linux
/dev/sdb4          75,196,414 1,953,523,711 1,878,327,298   5 Extended
/dev/sdb5          75,196,416   563,476,479   488,280,064  83 Linux
/dev/sdb6         563,479,938   760,742,009   197,262,072   7 NTFS / exFAT / HPFS
/dev/sdb7         760,742,073 1,953,520,064 1,192,777,992   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   102,402,047   102,400,000   7 NTFS / exFAT / HPFS
/dev/sdc2         102,402,048 1,013,762,047   911,360,000   7 NTFS / exFAT / HPFS
/dev/sdc3       1,013,762,048 1,953,519,615   939,757,568   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        5AA398CC78A2F362                       ntfs       Seven
/dev/sda2        76A091C362C88A4E                       ntfs       Space
/dev/sda3        51D497284BD60E21                       ntfs       Video
/dev/sdb1        6d6e550d-c564-4eb3-aab2-d95d43a799e1   ext4       
/dev/sdb2        e6214996-9a36-48e0-9d6c-85ce4a0c6ecb   swap       
/dev/sdb3        7de5829a-1562-488d-b1da-1dad9098c73c   ext4       
/dev/sdb5        94d37247-7a71-46b1-9d68-491180742cdd   ext4       
/dev/sdb6        492D7A6424CABECD                       ntfs       Box
/dev/sdb7        32E9FDF875C355A3                       ntfs       Storage
/dev/sdc1        987C306E7C304970                       ntfs       XP
/dev/sdc2        ACBC8726BC86E9E2                       ntfs       Room
/dev/sdc3        2C6EC6DC6EC69DC8                       ntfs       Pile

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/Seven             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /boot                    ext4       (rw,commit=0)
/dev/sdb3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb5        /home                    ext4       (rw,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

============================= sdb1/grub/grub.cfg: ==============================

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
set root='(/dev/sdb,msdos3)'
search --no-floppy --fs-uuid --set=root 7de5829a-1562-488d-b1da-1dad9098c73c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 6d6e550d-c564-4eb3-aab2-d95d43a799e1
set locale_dir=($root)/grub/locale
set lang=en_US
insmod gettext
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 6d6e550d-c564-4eb3-aab2-d95d43a799e1
    linux    /vmlinuz-2.6.38-8-generic-pae root=UUID=7de5829a-1562-488d-b1da-1dad9098c73c ro  splash  quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 6d6e550d-c564-4eb3-aab2-d95d43a799e1
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 6d6e550d-c564-4eb3-aab2-d95d43a799e1
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 5AA398CC78A2F362
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 987C306E7C304970
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

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.261180878 = 0.280440832    grub/core.img                                  1
   0.261235237 = 0.280499200    grub/grub.cfg                                  1
   0.100783348 = 0.108215296    initrd.img-2.6.38-8-generic-pae                3
   0.020936012 = 0.022479872    vmlinuz-2.6.38-8-generic-pae                   1

=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos3)'
search --no-floppy --fs-uuid --set=root 7de5829a-1562-488d-b1da-1dad9098c73c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 6d6e550d-c564-4eb3-aab2-d95d43a799e1
set locale_dir=($root)/grub/locale
set lang=en_US
insmod gettext
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 6d6e550d-c564-4eb3-aab2-d95d43a799e1
    linux    /vmlinuz-2.6.38-8-generic-pae root=UUID=7de5829a-1562-488d-b1da-1dad9098c73c ro  splash  quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 6d6e550d-c564-4eb3-aab2-d95d43a799e1
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 6d6e550d-c564-4eb3-aab2-d95d43a799e1
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 5AA398CC78A2F362
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 987C306E7C304970
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

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=7de5829a-1562-488d-b1da-1dad9098c73c /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=6d6e550d-c564-4eb3-aab2-d95d43a799e1 /boot           ext4    defaults        0       2
# /home was on /dev/sdb5 during installation
UUID=94d37247-7a71-46b1-9d68-491180742cdd /home           ext4    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=e6214996-9a36-48e0-9d6c-85ce4a0c6ecb none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   8.176219940 = 8.779149312    boot/grub/core.img                             1
   8.176274300 = 8.779207680    boot/grub/grub.cfg                             1
   8.015822411 = 8.606923776    boot/initrd.img-2.6.38-8-generic-pae           3
   7.935975075 = 8.521188352    boot/vmlinuz-2.6.38-8-generic-pae              1
   8.015822411 = 8.606923776    initrd.img                                     3
   7.935975075 = 8.521188352    vmlinuz                                        1

================================ sdc1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb4

00000000  53 51 98 94 77 c5 83 eb  e3 6d 4f 3d f3 d2 97 c6  |SQ..w....mO=....|
00000010  63 26 bb e1 1d f0 77 80  1c 41 3e d6 90 8c c5 ef  |c&....w..A>.....|
00000020  94 5f cf 21 92 64 43 1b  00 89 a0 6b c9 e1 ce c8  |._.!.dC....k....|
00000030  30 8a 89 67 ec 2e 9b 02  0a a2 6f 3a f2 53 b5 6d  |0..g......o:.S.m|
00000040  88 71 47 c7 88 4f ec df  38 60 ad 34 6a 48 f5 30  |.qG..O..8`.4jH.0|
00000050  08 70 10 33 b2 d7 6f 6d  6b d9 99 cc 5d 03 41 cc  |.p.3..omk...].A.|
00000060  71 fa b0 a9 68 ad eb f0  8d 7f fc 80 a2 f5 96 0a  |q...h...........|
00000070  38 3f 11 04 39 b4 d1 dc  22 58 93 92 9b 96 40 09  |8?..9..."X....@.|
00000080  43 05 ed 4f a4 1c d5 ef  f6 ba f7 e1 f2 7d 7d cd  |C..O.........}}.|
00000090  0f aa 80 46 82 34 3d c6  6f 6c 07 c0 0f 8d 7f 43  |...F.4=.ol.....C|
000000a0  2f 18 7d f0 47 94 11 85  8f 57 1e a2 58 52 43 83  |/.}.G....W..XRC.|
000000b0  37 c7 53 de 17 ff 1b e4  23 3e bc fc 27 cc 0d 29  |7.S.....#>..'..)|
000000c0  2d ad b2 02 0b 6b 74 5e  a4 8c 0a 3c b3 eb d2 bd  |-....kt^...<....|
000000d0  7b 0c a4 b7 55 c0 1c ac  4d 4b db 4b 70 98 30 42  |{...U...MK.Kp.0B|
000000e0  22 39 45 88 9f ad a8 50  2d 4a c7 96 25 c8 c2 88  |"9E....P-J..%...|
000000f0  f5 66 58 c9 ce 93 d0 c0  7e e6 5f d3 6b 4b 3b 9a  |.fX.....~._.kK;.|
00000100  aa 30 4b c3 1a 2a 5b b2  0a 99 9f a2 c9 a5 d8 e0  |.0K..*[.........|
00000110  26 6f c5 a1 1c d3 3d e0  4d 0f 92 f5 16 ee 8b 03  |&o....=.M.......|
00000120  dd cb ae cf ac c6 08 fb  a1 25 db 52 f6 07 3f ca  |.........%.R..?.|
00000130  35 cc 29 83 38 5e fa 15  f8 44 b5 52 78 a9 2d 01  |5.).8^...D.Rx.-.|
00000140  a3 28 c2 80 a7 84 3d ac  3a be 6d 5e e7 6d 8f 27  |.(....=.:.m^.m.'|
00000150  03 6d 14 eb 39 94 ef f5  c3 0b dd e8 f6 81 af 37  |.m..9..........7|
00000160  62 d8 97 ee 12 e2 b4 a4  55 58 1c dc b5 cf cc f3  |b.......UX......|
00000170  fc 8f 0f fa db 16 96 7b  6d ca f3 15 6c b9 bd a7  |.......{m...l...|
00000180  ff ed 55 67 80 70 55 8e  bb a1 00 33 76 f2 8a 9b  |..Ug.pU....3v...|
00000190  fe 82 e9 ad 52 6d 6b b3  3e 5b 37 e2 31 e0 46 74  |....Rmk.>[7.1.Ft|
000001a0  39 d6 f7 2d 7e 8d c2 d2  41 2f c4 d0 7e 6a de 56  |9..-~...A/..~j.V|
000001b0  26 61 6d 8a 64 02 1b dd  7e 65 2b 60 71 c5 00 fe  |&am.d...~e+`q...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 90 1a 1d 00 fe  |................|
000001d0  ff ff 05 fe ff ff 45 9d  1a 1d 37 fb c1 0b 00 00  |......E...7.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by deserthowler on 2011-06-28
> **jruh64 said:**
> Hi

I just did clean installs of Windows 7, Windows XP and Ubuntu 11.04 (installed in that order). Each OS is installed on a separate HDD.

Back in the olden days ... I think Ubuntu 5.10, (Working from memory here :confused:)I found that I needed to install Win 98 and then Win 2K.  This gave me a dual boot.  Then I installed Ubuntu which gave me a grub menu of Ubuntu and Windows.  When I clicked the Windows Menu, I got a choice of 2K and 98.  I don't know if Windows still needs to be installed in chronological order but at one time it did, as I remember.

Earl

---

### Post by oldfred on 2011-06-28
The hal.dll error is usually a boot.ini error. I have not seen a lot of XP installs in second or third drives and am not 100% sure if multi or disk have to be edited also but rdisk(1), I think should be rdisk(3) for sdc1 install.

[boot loader] 
timeout=30 
default=multi(0)disk(0)[COLOR=Red]rdisk(1)[/COLOR]partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)[COLOR=Red]rdisk(1)[/COLOR]partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

If you want to repair from an XP disk, you will need to add a boot flag to sdc1 and from XP;'s repair console run this, not sure how to prevent it from seeing sda1 and it you unplug it then sdc will not have the correct drive number.

BOOTCFG  /rebuild  # rebuilds boot.ini

---

