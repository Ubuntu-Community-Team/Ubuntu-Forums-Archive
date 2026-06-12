---
title: "Cannot boot after fresh 11.04 install"
date: 2011-05-01
forum: General Help
---

### Post by Homeless2 on 2011-05-01
I just tried doing a fresh install of Ubuntu 11.04 on my laptop (inspiron 9300) and ran into a grub error of some sort

[img]http://www.roflsaurus.com/users/homeless/grub.png[/img]

Dual booting windows 7 if that makes a difference.  Reinstall grub2 doesn't seem to help either

---

### Post by Homeless2 on 2011-05-03
Anyone have any ideas?

---

### Post by oldfred on 2011-05-03
If you have reinstalled grub that is first choice. 

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

Post this to see if something looks out of place:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V56 has improved formating and requires code tags to make it legible. 

With Natty, a new versioin of boot script works better on parsing MBR, but it is not finalized yet:
Get last development version of Boot Info Script:
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

---

### Post by Homeless2 on 2011-05-05
The grub rescue prompt link got me back into ubuntu.  I then ran sudo update-grub and have the grub menu again.  However, I notice that just before the grub menu loads I get an error that says "error: out of disk"  It boots ok, but I assume that's not an error I want to have

 ```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

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

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   124,164,095   123,957,248   7 HPFS/NTFS
/dev/sda3         124,164,096   251,138,047   126,973,952   7 HPFS/NTFS
/dev/sda4         251,140,094   312,580,095    61,440,002   5 Extended
/dev/sda5         251,140,096   308,389,887    57,249,792  83 Linux
/dev/sda6         308,391,936   312,580,095     4,188,160  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        00609E1B609E178C                       ntfs       System Reserved               
/dev/sda2        4AB4AE00B4ADEF1F                       ntfs       Windows                       
/dev/sda3        F4583653583614B8                       ntfs       Files                         
/dev/sda4: PTTYPE="dos" 
/dev/sda5        0e4036df-5a0d-4a85-91ae-fd39e54a5859   ext4                                     
/dev/sda6        9c6b44c2-92a4-4010-95d9-8238dfd39f34   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=600)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 0e4036df-5a0d-4a85-91ae-fd39e54a5859
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 0e4036df-5a0d-4a85-91ae-fd39e54a5859
set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0e4036df-5a0d-4a85-91ae-fd39e54a5859
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=0e4036df-5a0d-4a85-91ae-fd39e54a5859 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0e4036df-5a0d-4a85-91ae-fd39e54a5859
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=0e4036df-5a0d-4a85-91ae-fd39e54a5859 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0e4036df-5a0d-4a85-91ae-fd39e54a5859
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0e4036df-5a0d-4a85-91ae-fd39e54a5859
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 00609E1B609E178C
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
UUID=0e4036df-5a0d-4a85-91ae-fd39e54a5859 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9c6b44c2-92a4-4010-95d9-8238dfd39f34 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 135.1GB: boot/grub/core.img
 137.3GB: boot/grub/grub.cfg
 129.6GB: boot/initrd.img-2.6.38-8-generic
 135.2GB: boot/vmlinuz-2.6.38-8-generic
 129.6GB: initrd.img
 135.2GB: vmlinuz

```

---

### Post by oldfred on 2011-05-05
Have you rebooted more than once? Grub2 does write an error flag and may just be reporting the error and needs a clean reboot to clear it.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

---

### Post by Homeless2 on 2011-05-05
Yep, I've rebooted a few times and the error is still there.  

My /etc/grub.d/10_linux doesn't have the "if  [ -n \${have_grubenv} ]; then save_env recordfail; fi" line anywhere in it

---

### Post by drs305 on 2011-05-05
> **Homeless2 said:**
> Yep, I've rebooted a few times and the error is still there.  

My /etc/grub.d/10_linux doesn't have the "if  [ -n \${have_grubenv} ]; then save_env recordfail; fi" line anywhere in it

The Grub files have changed, so the missing line isn't relevant. You have the replacement in the proper location of the grub.cfg file.

There are a few things that can cause the message. Two which are easy to to check when time permits:
a. Changing BIOS setting of the SATA controller mode from AHCI to compatibility mode.
b. Try adding 'rootdelay=90' (no quotes) to the end of the 'linux' line of your default menuentry. I'd only edit grub.cfg and add it so you can delete it the next time you run update-grub. If it removes the error message, you can continue to reduce the delay until the message reappears. Don't run 'update-grub' until you want to remove the change.

---

### Post by Homeless2 on 2011-05-07
My bios doesn't have the option of changing controller mode.  It's one of those old locked down dell bios'es.  Adding rootdelay=90 to the end of the grub.cfg didn't remove the error

---

### Post by drs305 on 2011-05-07
I am under the impression your system is booting properly now but that you get the 'out of disk' message just before the menu appears.

If you want to tinker to try to figure this out (i.e. have time to waste), you can try this to see if the message disappears. Further tinkering would probably be necessary to actually *fix* the issue, but if you want ...

The test will be done on /boot/grub/grub.cfg. This is non-persistent change which will be removed when update-grub is executed.

Open grub.cfg
```
gksu gedit +28 /boot/grub/grub.cfg
```
Comment the noted line, save the file, and see what happens the next time you boot.
> 
function recordfail {
  set recordfail=1
**[COLOR="DarkRed"]#[/COLOR]**  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}



---

### Post by Homeless2 on 2011-05-08
Yeah system boots like normal but I get the out of disk message just before the grub menu appears.  Commenting that line doesn't remove the message unfortunately

---

