---
title: "Ubuntu 11.10 Boot Issues..."
date: 2011-10-13
forum: General Help
---

### Post by Kduke on 2011-10-13
Hey everyone,

I just upgraded to Ubuntu 11.10 and everything is generally fine.  However, I do experience some weird startup issues.

I am currently forced to use kernel 2.6.38-10 under previous versions, as the new 3.0.0-12 will not boot up.

If I select the 3.0 option, I am presented with a blinking cursor and nothing more.  On a similar note, I also had problems with kernel 2.6.38-11.  I was unable to boot into that as well.

I don't mind using an older kernel, however, I am a bit dissapointed of being unable to use the new 3.0 kernel.

An additional note, regardless of which kernel I pick, I have no "splash screen".  It's just  black screen (my monitor actually goes into powersaving mode for a few moments when booting up 2.6.38-10)

Any thoughts on this issue, and how it may be resolved?

Is there any way to reconfigure boot options to their defaults?  I am not sure if it has to do with my grub settings.

Sorry if this post is a bit all over the place.  I look forward to your responses!

---

### Post by starNIX on 2011-10-15
Same issue here except this is a fresh install.  I cannot even get to the boot menu to choose a different kernel or anything.  HELP!!!!

---

### Post by Quackers on 2011-10-15
Kduke, what graphics card are you using?

starNIX, if you tap the Esc key or the shift key during boot does the grub menu show?
Also what graphics card are you using?

---

### Post by starNIX on 2011-10-15
Shift and Esc do nothing.  It is an Nvidia card.  I forget the model.  The live usb boots fine, can I boot with that and do something to fix this?

---

### Post by Quackers on 2011-10-15
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Or alternatively, have a look here

[http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980)

---

### Post by starNIX on 2011-10-15
Not sure if this means anything but I pressed ALT at startup and it is giving me "error: no such device: <long alpha-numeric string" 

I'm guessing it's because I am booting off of sdg instead of sda.  Will that fix above fix this issue?

---

### Post by Quackers on 2011-10-15
Where did you install Ubuntu to? Did you leave the default setting for grub installation (to /dev/sda)?
The boot script output will tell us.

---

### Post by Kduke on 2011-10-15
Sorry for the delay in my post, I've been quite busy.  Being busy, I was too lazy to try to figure out a way to fix it, so I downloaded the Ubuntu image and fixed it with that.

I personally believe that it was due to some of the settings I changed.  I was running a custom splash screen for awhile.  That may have been the issue.

I'll leave this thread unsolved for a bit to see if anyone else can get their solution fixed.

Thank you all for the replies.

---

### Post by tarunkumar on 2011-10-16
I am also facing similar issue after upgrading from 11.04 to 11.10, as while boot it says 
Can not read file
Please any key to continue...

and nothing happens after that, i have to use kernel 2.6.38-10 under previous versions, as the new 3.0.0-12 will not boot up.

How this can be resolved???

---

### Post by tarunkumar on 2011-10-16
Below is the contents of resuls.txt file after running boot_info_script.sh 

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    31,455,269    31,455,207   7 NTFS / exFAT / HPFS
/dev/sda2          31,464,781   136,321,919   104,857,139   5 Extended
/dev/sda5          31,464,783    73,407,599    41,942,817   7 NTFS / exFAT / HPFS
/dev/sda6          73,407,663   115,350,479    41,942,817   7 NTFS / exFAT / HPFS
/dev/sda7         115,350,543   136,321,919    20,971,377   7 NTFS / exFAT / HPFS
/dev/sda3         136,323,072   152,338,431    16,015,360  83 Linux
/dev/sda4         152,338,432   156,301,311     3,962,880  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        9CC4C68AC4C6665C                       ntfs       
/dev/sda3        65b82886-16cf-45d3-83da-82339071d15a   xfs        
/dev/sda4        1f3424b3-daa6-44d0-a23c-45ad957a2b4d   swap       
/dev/sda5        407C7E147C7E04C6                       ntfs       
/dev/sda6        62F4FFFCF4FFCFF1                       ntfs       
/dev/sda7        92C8EAB4C8EA95AF                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        xfs        (rw)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /noexecute=alwaysoff 
--------------------------------------------------------------------------------

=========================== sda3/boot/grub/grub.cfg: ===========================

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
insmod xfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 65b82886-16cf-45d3-83da-82339071d15a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod xfs
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 65b82886-16cf-45d3-83da-82339071d15a
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IN
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod xfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 65b82886-16cf-45d3-83da-82339071d15a
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=65b82886-16cf-45d3-83da-82339071d15a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod xfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 65b82886-16cf-45d3-83da-82339071d15a
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=65b82886-16cf-45d3-83da-82339071d15a ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod xfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 65b82886-16cf-45d3-83da-82339071d15a
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=65b82886-16cf-45d3-83da-82339071d15a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod xfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 65b82886-16cf-45d3-83da-82339071d15a
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=65b82886-16cf-45d3-83da-82339071d15a ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod xfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 65b82886-16cf-45d3-83da-82339071d15a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod xfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 65b82886-16cf-45d3-83da-82339071d15a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 9CC4C68AC4C6665C
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=65b82886-16cf-45d3-83da-82339071d15a /               xfs     defaults        0       1
# swap was on /dev/sda4 during installation
UUID=1f3424b3-daa6-44d0-a23c-45ad957a2b4d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  65.121315002 = 69.923479552   boot/grub/core.img                             1
  67.157878876 = 72.110223360   boot/grub/grub.cfg                             1
  72.553081512 = 77.903278080   boot/initrd.img-2.6.38-11-generic              6
  72.621353149 = 77.976584192   boot/initrd.img-3.0.0-12-generic              263
  72.291248322 = 77.622136832   boot/vmlinuz-2.6.38-11-generic                 1
  68.574131012 = 73.630912512   boot/vmlinuz-3.0.0-12-generic                  1
  72.621353149 = 77.976584192   initrd.img                                    263
  72.553081512 = 77.903278080   initrd.img.old                                 6
  68.574131012 = 73.630912512   vmlinuz                                        1
  72.291248322 = 77.622136832   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  2e 2f 2e 2e 2f 2e 2e 2f  2e 2e 2f 6a 61 76 61 2f  |./../../../java/|
00000010  6c 61 6e 67 2f 53 74 72  69 6e 67 2e 68 74 6d 6c  |lang/String.html|
00000020  22 20 74 69 74 6c 65 3d  22 63 6c 61 73 73 20 69  |" title="class i|
00000030  6e 20 6a 61 76 61 2e 6c  61 6e 67 22 3e 53 74 72  |n java.lang">Str|
00000040  69 6e 67 3c 2f 41 3e 26  6e 62 73 70 3b 6e 61 6d  |ing</A>&nbsp;nam|
00000050  65 73 70 61 63 65 55 52  49 2c 0a 20 20 20 20 20  |espaceURI,.     |
00000060  20 20 20 20 20 20 20 20  20 20 3c 41 20 48 52 45  |          <A HRE|
00000070  46 3d 22 2e 2e 2f 2e 2e  2f 2e 2e 2f 2e 2e 2f 6a  |F="../../../../j|
00000080  61 76 61 2f 6c 61 6e 67  2f 53 74 72 69 6e 67 2e  |ava/lang/String.|
00000090  68 74 6d 6c 22 20 74 69  74 6c 65 3d 22 63 6c 61  |html" title="cla|
000000a0  73 73 20 69 6e 20 6a 61  76 61 2e 6c 61 6e 67 22  |ss in java.lang"|
000000b0  3e 53 74 72 69 6e 67 3c  2f 41 3e 26 6e 62 73 70  |>String</A>&nbsp|
000000c0  3b 6c 6f 63 61 6c 4e 61  6d 65 29 3c 2f 43 4f 44  |;localName)</COD|
000000d0  45 3e 0a 0a 3c 42 52 3e  0a 26 6e 62 73 70 3b 26  |E>..<BR>.&nbsp;&|
000000e0  6e 62 73 70 3b 26 6e 62  73 70 3b 26 6e 62 73 70  |nbsp;&nbsp;&nbsp|
000000f0  3b 26 6e 62 73 70 3b 26  6e 62 73 70 3b 26 6e 62  |;&nbsp;&nbsp;&nb|
00000100  73 70 3b 26 6e 62 73 70  3b 26 6e 62 73 70 3b 26  |sp;&nbsp;&nbsp;&|
00000110  6e 62 73 70 3b 52 65 74  72 69 65 76 65 73 20 61  |nbsp;Retrieves a|
00000120  20 6e 6f 64 65 20 73 70  65 63 69 66 69 65 64 20  | node specified |
00000130  62 79 20 6c 6f 63 61 6c  20 6e 61 6d 65 20 61 6e  |by local name an|
00000140  64 20 6e 61 6d 65 73 70  61 63 65 20 55 52 49 2e  |d namespace URI.|
00000150  3c 2f 54 44 3e 0a 3c 2f  54 52 3e 0a 3c 54 52 20  |</TD>.</TR>.<TR |
00000160  42 47 43 4f 4c 4f 52 3d  22 77 68 69 74 65 22 20  |BGCOLOR="white" |
00000170  43 4c 41 53 53 3d 22 54  61 62 6c 65 52 6f 77 43  |CLASS="TableRowC|
00000180  6f 6c 6f 72 22 3e 0a 3c  54 44 20 41 4c 49 47 4e  |olor">.<TD ALIGN|
00000190  3d 22 72 69 67 68 74 22  20 56 41 4c 49 47 4e 3d  |="right" VALIGN=|
000001a0  22 74 6f 70 22 20 57 49  44 54 48 3d 22 31 25 22  |"top" WIDTH="1%"|
000001b0  3e 3c 46 4f 4e 54 20 53  49 5a 45 3d 22 2d 00 ef  |><FONT SIZE="-..|
000001c0  ff ff 07 ef ff ff 02 00  00 00 21 ff 7f 02 00 fe  |..........!.....|
000001d0  ff ff 05 fe ff ff 23 ff  7f 02 60 ff 7f 02 00 00  |......#...`.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by gsumaniitk on 2011-10-25
I have the same issue with 11.10. I upgraded from 11.04 to 11.10 and after that I can not boot with the latest kernel 3.0.0.12. During boot it stops at:

ACPI: Power Button [PWRF]

and nothing happens afterwards. I have tried to boot with the following boot options 

acpi=off
noapic
nolapic
apm=off

but none have worked.

However I can boot using the old kernel. One more piece of information that I would like to share is that during upgrading it asked whether I would like to keep the existing grub or wanted to replace it. I did not replace the grub rather I kept the existing one. I hope that this is not the issue in this case. 

Any help in this regard ?

[COLOR=Red]Update: I saw somewhere that if the USB in BIOS is disabled then with acpi=off booting is possible. I did that and it worked, but I have an USB mouse and hence mouse won't work if I disable USB in BIOS.[/COLOR]

---

