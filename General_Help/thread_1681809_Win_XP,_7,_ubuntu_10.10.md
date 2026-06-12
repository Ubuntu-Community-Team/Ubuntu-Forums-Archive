---
title: "Win XP, 7, ubuntu 10.10"
date: 2011-02-04
forum: General Help
---

### Post by penguin2O1O on 2011-02-04
Well hi everybody

I have windows xp, windows 7 and ubuntu 10.10, all of them are in different HDD&#347;, i can boot normally in ubuntu 10.10 and in windows 7 but not in win xp, when i try to boot in XP, all that i can get is a Blue Screen of Death, i tried to start Win XP in safe mode and configure it to stop reboot when the BSOD appears, but that didn work, the pc still reboot, and when i tried to put the HDD that has the XP OS as master in the MOBO, XP boot as normal, like nothing happens...

:confused::confused::confused:

So any guess of what is going on, would be aprecciated

Thanks and i am newbie in ubuntu...

---

### Post by penguin2O1O on 2011-02-05
I tried finding a solution in google, but no one seems to have similar issues...

---

### Post by techunit on 2011-02-05
If your system specs are good enough (at least dual core and 3 gigabytes ram) you might have more look with a virtual machine like virtualbox. Triple booting is highly impractical and hard on your machine. I would seriously recommend that you do this.

I know this doesn't answer your question but it is a better solution.

As for fixing your problem as you asked try this.
Make sure that the Ubuntu drive is the first in the boot order in your bios and in ubuntu run.
```
sudo update-grub
```

---

### Post by oldfred on 2011-02-05
Post this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by arsenic23 on 2011-02-05
Was XP the master drive when you installed it?  Depending on some of your setup, and if that was the case, it might have to be set in the master state to work.  Vista and win7 aren't picky like this, but XP can develop this kind of behavior.

You could always leave the XP drive attached in the manner that makes it work and then reinstall grub on that drive.

---

### Post by penguin2O1O on 2011-02-05
> **arsenic23]Post this:

Was XP the master drive when you installed it?  Depending on some of  your setup, and if that was the case, it might have to be set in the  master state to work.  Vista and win7 aren't picky like this, but XP can  develop this kind of behavior.

You could always leave the XP drive attached in the manner that makes it work and then reinstall grub on that drive.

[/QUOTE]

Yes it was master from a Gateway PC...

[QUOTE=oldfred said:**
> Post this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.


Well this is the results that show the Boot Info Script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => HP/Gateway is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 164.7 GB, 164696555520 bytes
255 cabezas, 63 sectores/pista, 20023 cilindros, 321672960 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   309,385,215   309,383,168  83 Linux
/dev/sda2         309,387,262   321,671,167    12,283,906   5 Extended
/dev/sda5         309,387,264   321,671,167    12,283,904  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 cabezas, 63 sectores/pista, 182401 cilindros, 2930277168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   880,651,169   880,651,107   7 HPFS/NTFS
/dev/sdb2         880,651,170 2,930,272,064 2,049,620,895   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disco /dev/sdc: 250.1 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros, 488397168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *      8,803,620   488,392,064   479,588,445   7 HPFS/NTFS
/dev/sdc2                  63     8,803,619     8,803,557   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        cefecbf7-4227-4eab-98e5-654dcc7976b8   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ad1ceec1-74d4-47d8-8f49-f1369104fb06   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D058B8EF58B8D606                       ntfs       Windows 7                     
/dev/sdb2        6CC001C8C001998A                       ntfs       WD15EADS                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        D4B4D524B4D50A3E                       ntfs       FAMILIA MORALES GARCIA        
/dev/sdc2        26C6-7A81                              vfat       RECOVERY                      
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set default="8"
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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set cefecbf7-4227-4eab-98e5-654dcc7976b8
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set cefecbf7-4227-4eab-98e5-654dcc7976b8
set locale_dir=($root)/boot/grub/locale
set lang=es
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=60
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set cefecbf7-4227-4eab-98e5-654dcc7976b8
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=cefecbf7-4227-4eab-98e5-654dcc7976b8 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set cefecbf7-4227-4eab-98e5-654dcc7976b8
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=cefecbf7-4227-4eab-98e5-654dcc7976b8 ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set cefecbf7-4227-4eab-98e5-654dcc7976b8
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=cefecbf7-4227-4eab-98e5-654dcc7976b8 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set cefecbf7-4227-4eab-98e5-654dcc7976b8
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=cefecbf7-4227-4eab-98e5-654dcc7976b8 ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set cefecbf7-4227-4eab-98e5-654dcc7976b8
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=cefecbf7-4227-4eab-98e5-654dcc7976b8 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set cefecbf7-4227-4eab-98e5-654dcc7976b8
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=cefecbf7-4227-4eab-98e5-654dcc7976b8 ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set cefecbf7-4227-4eab-98e5-654dcc7976b8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set cefecbf7-4227-4eab-98e5-654dcc7976b8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set d058b8ef58b8d606
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdc1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set d4b4d524b4d50a3e
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sdc2)" {
    insmod part_msdos
    insmod fat
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set 26c6-7a81
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=cefecbf7-4227-4eab-98e5-654dcc7976b8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ad1ceec1-74d4-47d8-8f49-f1369104fb06 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 107.5GB: boot/grub/core.img
  30.3GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-22-generic
   1.2GB: boot/initrd.img-2.6.35-24-generic
    .7GB: boot/initrd.img-2.6.35-25-generic
 107.5GB: boot/vmlinuz-2.6.35-22-generic
 107.5GB: boot/vmlinuz-2.6.35-24-generic
 107.5GB: boot/vmlinuz-2.6.35-25-generic
    .7GB: initrd.img
   1.2GB: initrd.img.old
 107.5GB: vmlinuz
 107.5GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader] 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

---

### Post by oldfred on 2011-02-05
Windows is thinking it is the master:
default=multi(0)disk(0[COLOR=Red])rdisk(0)[/COLOR]partition(1)\WINDOWS 

Whichever drive you boot in BIOS, that will be hd0 or in windows rdisk(0).

The drivemap command is supposed to renumber the drive order so windows will work, but I have seen several other cases where it does not.

The one solution I have seen work is to install grub to sdc and boot that so it is hd0 & drive 0.

Otherwise you may be able to edit boot.ini to change rdisk(0) or try various alternatives in the boot stanza. I would first just try removing the entire search line from the grub boot stanza for XP. To test you can use e for edit in grub menu and see if deleting search works.

---

### Post by penguin2O1O on 2011-02-05
> **oldfred said:**
> Windows is thinking it is the master:
default=multi(0)disk(0[COLOR=Red])rdisk(0)[/COLOR]partition(1)\WINDOWS 

Whichever drive you boot in BIOS, that will be hd0 or in windows rdisk(0).

The drivemap command is supposed to renumber the drive order so windows will work, but I have seen several other cases where it does not.

The one solution I have seen work is to install grub to sdc and boot that so it is hd0 & drive 0.

Otherwise you may be able to edit boot.ini to change rdisk(0) or try various alternatives in the boot stanza. I would first just try removing the entire search line from the grub boot stanza for XP. To test you can use e for edit in grub menu and see if deleting search works.

I can edit the boot.ini, the rdisk(0) sould be rdisk(1)?

---

### Post by oldfred on 2011-02-06
I consider editing boot.ini an experiment. It cannot hurt as long you save in windows mode not linux. Line endings are different. It used to be better to use nano, but gedit is updated. Be sure to select windows line endings.

---

### Post by penguin2O1O on 2011-02-07
> **oldfred said:**
> I consider editing boot.ini an experiment. It cannot hurt as long you save in windows mode not linux. Line endings are different. It used to be better to use nano, but gedit is updated. Be sure to select windows line endings.

Well i tried editing the boot.ini, but without succes, i tried grub, but the GUI has only 2 tabs and none of them allow me to change anything about the windows XP search line...

:(

---

### Post by oldfred on 2011-02-07
When the grub menu comes up, you can press e for edit on the windows line and delete the search line, then x to boot. You then also from there can experiment with different set root drives. If you find one that works then we can make it permanent in 40_custom.

---

### Post by penguin2O1O on 2011-02-07
Well im trying your solution, with no luck, but i have this, i managed to get the error of the BSOD it says:

IRQL_NOT_LESS_OR_EQUAL

STOP  0x0000000a (0xfffffffb 0x000000ff 0x00000000 0x80544d4f)

---

### Post by Bert987 on 2011-02-07
Have you tryed easyBCD in windows 7?
I have three hard drives (two on raid o) Win xp and a 250gb with win 7 Ultimate , Ultimate edition 2.8 (Ubuntu on sterods) 
 
Win 7 bootloader controls all the bootloading for (win 7 Ultimate Ed and win xp)

---

### Post by penguin2O1O on 2011-02-08
> **Bert987 said:**
> Have you tryed easyBCD in windows 7?
I have three hard drives (two on raid o) Win xp and a 250gb with win 7 Ultimate , Ultimate edition 2.8 (Ubuntu on sterods) 
 
Win 7 bootloader controls all the bootloading for (win 7 Ultimate Ed and win xp)

Looks interesting, i will give it a try...

Thanks my friend.. ;)

---

### Post by penguin2O1O on 2011-02-09
Well i managed to resolve this...

Win xp as stated in another post think it was the master...

Then i see in my BIOS the option that allow me boot from another hdd even if it is not the master...

So all i did was to put the xp hdd as master, but boot grub (ubuntu hdd), and then.... success, all of the OS run like a charm...

Sorry if i bothered any of you who helped in this thread,  but thanks for the advices, they get me to the solution....

Big thanks...):P):P):P

---

