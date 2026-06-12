---
title: "PC Won't boot - GRUB related"
date: 2011-06-28
forum: General Help
---

### Post by breNTx22 on 2011-06-28
My PC will not boot past the GRUB selection screen. I'm not sure if that's what it's called but it's the screen that says I can boot Ubuntu, test memory, or boot Windows 7. The keyboard responds but I cannot hit the down arrow. When I select Ubuntu it says:

"
error: invalid extent.
error: symbol not found: 'grub_os_area_addr'.
error: symbol not found: 'grub_os_area_addr'.

"
Here's the chain of events:

1) Windows 7 Installed
2) Ubuntu 11 installed
3) Ubuntu 11 isn't working correctly (PC still boots into both OS's). Just a few minor issues.
4) Decide to go back to the tried and true Ubuntu 10.
5) Install Ubuntu 10, delete the Ubuntu 11 partition and replace it with Ubuntu 10.
6) Ubuntu 10 successfully installs, prompts me to restart
7) Upon restart I saw this:
"error:  symbol not found:   'grub_putchar'.
grub rescue >"

8 )After several attempts at fixing it (potential solutions found through google. Involved trying to reload Grub and/or Grub2). I'm finally at the problem I listed in the first paragraph.


I tried to keep it as brief as possible. If there's any information I can provide to make it easier to troubleshoot let me know. Thanks!

---

### Post by toor58 on 2011-06-28
I will make the suggestion that you fix the boot menu on your windows side following this guide: [http://ubuntuforums.org/showthread.php?t=508927]("http://ubuntuforums.org/showthread.php?t=508927")

Then I would advise you to use the windows disk manager to remove the linux partition. Delete it completely leaving only free space.

Then reinstall the distro you want.

Always follow this procedure when reinstalling. It removes any possibilty of errors. I use it, so I know it works.

---

### Post by Ozymandias_117 on 2011-06-28
Following this guide worked for another user with the same problem.  If you haven't tried it, you might want to. [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

I know you said you already reinstalled Grub, but there is definitely something wrong with it.  Did you merely install Grub back to the hard drive, or actually purge it and start over?

---

### Post by oldfred on 2011-06-28
Sometimes reinstall is quicker especially if you have no data to salvage. But post this so we can see if something is out of place that can be reset. We like to spend days fixing things when a reinstall only takes an hour:). (But fix may only take 5 minutes).

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by breNTx22 on 2011-06-28
> **toor58 said:**
> I will make the suggestion that you fix the boot menu on your windows side following this guide: [http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

Then I would advise you to use the windows disk manager to remove the linux partition. Delete it completely leaving only free space.

Then reinstall the distro you want.

Always follow this procedure when reinstalling. It removes any possibilty of errors. I use it, so I know it works.

Thank you for the response but I ran into a problem.

The instructions i'm following are:
 
"Re: HowTo: Remove Ubuntu (& Restore Windows) 

--------------------------------------------------------------------------------

If you delete the ubuntu partitions without running mbrfix then you can  use the ubuntu LiveCD to restore the master boot record by:

1. Booting from the ubuntu LiveCD
2. Enabling universe repositories - launch  System->Administation->Software Sources and check the "Community  maintained Open Source software (universe)"
3. Installing the "ms-sys" package - click  Applications->Accessories->Terminal and type "sudo apt-get update"  and then "sudo apt-get install ms-sys".
4. Finally restore the Windows master boot record by entering the  command "ms-sys -w /dev/[drive]", where [drive] is the hard disk whose  Windows master boot record you want to restore. You can find out which  this is by launching gparted (System->Administration->GNOME  Partition Editor) and cycling through the available drives until you  find your Windows partition"

I'm on Step 3. I type in "sudo apt-get install ms-sys" and it says:

"Reading package lists...Done
Building dependency tree
Reading state information...Done
e: Unable to locate package ms-sys"

I went back in and confirmed that "Community maintained Open Source software (universe)" has been checked.

---

### Post by breNTx22 on 2011-06-28
I have already tried to reinstall (Both Ubuntu 11 and 10) and I've had no luck. I will run that "boot info script" and post it shortly.

---

### Post by breNTx22 on 2011-06-28
results:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 433346616 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 5 for (,msdos5)/boot/grub. No 
                       errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   131,074,047   130,867,200   7 NTFS / exFAT / HPFS
/dev/sda3         131,076,094   625,141,759   494,065,666   5 Extended
/dev/sda5         131,076,096   605,612,031   474,535,936  83 Linux
/dev/sda6         605,614,080   625,141,759    19,527,680  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3EAC31D3AC318685                       ntfs       System Reserved
/dev/sda2        BA2C39DA2C39927D                       ntfs       Windows 7
/dev/sda5        0b12f3ef-d83c-497c-b0ec-1178371400c8   ext4       
/dev/sda6        ab35619b-4c3b-4405-8df1-8c9b17059b17   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/stage2                               1

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=========================== sda5/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd3,msdos5)'
search --no-floppy --fs-uuid --set 0b12f3ef-d83c-497c-b0ec-1178371400c8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd3,msdos5)'
search --no-floppy --fs-uuid --set 0b12f3ef-d83c-497c-b0ec-1178371400c8
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos5)'
    search --no-floppy --fs-uuid --set 0b12f3ef-d83c-497c-b0ec-1178371400c8
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0b12f3ef-d83c-497c-b0ec-1178371400c8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos5)'
    search --no-floppy --fs-uuid --set 0b12f3ef-d83c-497c-b0ec-1178371400c8
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0b12f3ef-d83c-497c-b0ec-1178371400c8 ro single 
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
    set root='(hd3,msdos5)'
    search --no-floppy --fs-uuid --set 0b12f3ef-d83c-497c-b0ec-1178371400c8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos5)'
    search --no-floppy --fs-uuid --set 0b12f3ef-d83c-497c-b0ec-1178371400c8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdd1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set 3eac31d3ac318685
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd5 during installation
UUID=0b12f3ef-d83c-497c-b0ec-1178371400c8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd6 during installation
UUID=ab35619b-4c3b-4405-8df1-8c9b17059b17 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 206.635791779 = 221.873491968  boot/grub/core.img                             1
 110.627113342 = 118.784958464  boot/grub/grub.cfg                             1
 111.017364502 = 119.203987456  boot/initrd.img-2.6.35-22-generic              2
 206.634262085 = 221.871849472  boot/vmlinuz-2.6.35-22-generic                 1
 111.017364502 = 119.203987456  initrd.img                                     2
 206.634262085 = 221.871849472  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  c0 4e dc 01 3a b6 0a 03  14 03 b2 c0 67 00 06 47  |.N..:.......g..G|
00000010  e3 0d e7 00 0a 00 00 00  00 00 00 0a 03 14 03 b2  |................|
00000020  af f6 60 09 b4 26 0a 03  14 03 b2 b5 a3 cf 0a e6  |..`..&..........|
00000030  f1 0a 03 14 03 b2 c0 90  52 06 19 79 0a 03 14 03  |........R..y....|
00000040  b2 c0 b2 93 04 fa c1 0a  03 14 03 b2 b5 a3 cf 0a  |................|
00000050  ea 09 0a 03 14 03 b2 aa  52 cf 0c 5c 9a 09 03 14  |........R..\....|
00000060  02 b2 c0 e8 af 76 01 0a  03 14 03 b2 b6 25 45 0c  |.....v.......%E.|
00000070  5f 0f 0a 03 14 03 b2 c4  cd 3b 0a f4 b3 0a 03 14  |_........;......|
00000080  03 b2 c4 cd 3b 0a f4 b2  0a 03 14 03 b2 c1 32 ef  |....;.........2.|
00000090  06 92 01 0a 03 14 03 b2  c1 3c 6f 02 4c a1 0a 03  |.........<o.L...|
000000a0  14 03 b2 c1 7e be 03 c3  20 0a 03 14 03 b2 c1 cb  |....~... .......|
000000b0  58 01 bc c1 0a 03 14 03  b2 c1 cd cf 06 69 bb 0a  |X............i..|
000000c0  03 14 03 b2 c2 1e 2c 06  49 2a 0a 03 14 03 b2 c2  |......,.I*......|
000000d0  2b e8 01 f5 97 0a 03 14  03 b2 c2 3a ce 08 18 c3  |+..........:....|
000000e0  0a 03 14 03 b2 c2 59 6e  06 0e f7 0a 03 14 03 b2  |......Yn........|
000000f0  c3 81 0d 0c a8 08 0a 03  14 03 b2 c2 b5 d3 04 ae  |................|
00000100  50 0a 03 14 03 b2 c2 e7  30 08 59 f5 0a 03 14 03  |P.......0.Y.....|
00000110  b2 c2 e8 3c 03 fd 79 0a  03 14 03 b2 c2 eb ab 07  |...<..y.........|
00000120  ff a1 0a 03 14 03 b2 c3  04 2b 03 72 16 0a 03 14  |.........+.r....|
00000130  03 b2 b8 b5 32 0a ff 1a  0a 03 14 03 b2 a9 37 0d  |....2.........7.|
00000140  0c a8 c1 0a 03 14 03 b2  b8 b5 32 0a ff 1b 0a 03  |..........2.....|
00000150  14 03 b2 c3 83 78 01 28  be 0a 03 14 03 b2 c3 8a  |.....x.(........|
00000160  ae 01 48 c1 0a 03 14 03  b2 c3 8d 1c 03 8b 58 0a  |..H...........X.|
00000170  03 14 03 b2 c3 8d 1c 03  b9 24 09 03 14 02 b2 c3  |.........$......|
00000180  8d 49 55 df 0a 03 14 03  b2 c3 d6 d4 03 6b 96 0a  |.IU..........k..|
00000190  03 14 03 b2 c4 28 10 01  34 62 0a 03 14 03 b2 c4  |.....(..4b......|
000001a0  35 cb 04 aa 4b 0a 03 14  03 b2 c4 48 53 08 3d 18  |5...K......HS.=.|
000001b0  0a 03 14 03 b2 c4 6e 34  03 c0 9e 0a 03 14 00 ef  |......n4........|
000001c0  ff ff 83 ef ff ff 02 00  00 00 00 d8 48 1c 00 ef  |............H...|
000001d0  ff ff 05 ef ff ff 02 d8  48 1c 00 00 2a 01 00 00  |........H...*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```



Update:

I am now able to boot into Ubuntu. I ran something to fix my boot menu:

[http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)


However, it does not display Windows 7 as an option to boot too. How can I add this in?

Thanks for the help so far!

---

### Post by oldfred on 2011-06-28
You installed grub2's boot loader into the windows partition which has to have window boot code.

> sda1: __________________________

    File system:       ntfs
    Boot sector type:  [COLOR=Red]Grub2 (v1.97-1.98)[/COLOR]
    Boot sector info:   [COLOR=Red]Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 433346616 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 5 for (,msdos5)/boot/grub. No 
                       errors found in the Boot Parameter Block.[/COLOR]
    Operating System:  
    Boot files:        /bootmgr /Boot/BCDFix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I do not know if it stops windows from booting like the above error but you have grub in sda2 also:

>     Boot files:        /Windows/System32/winload.exe [COLOR=Red]/boot/grub/core.img[/COLOR]
You should just delete the /boot folder in sda2.

Edit:
I also see this in the script in sda1:
> [FONT=monospace]boot/grub/stage2 [/FONT]

You cannot in windows have a /Boot and a /boot as windows is not case sensitive. Delete the /boot/grub folder, but be careful not to delete a /Boot/BCD folder as that is part of windows.

After those fixes this should then find your windows:

```
sudo update-grub
```

---

### Post by breNTx22 on 2011-06-29
> **oldfred said:**
> You installed grub2's boot loader into the windows partition which has to have window boot code.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I do not know if it stops windows from booting like the above error but you have grub in sda2 also:

You should just delete the /boot folder in sda2.

Edit:
I also see this in the script in sda1:


You cannot in windows have a /Boot and a /boot as windows is not case sensitive. Delete the /boot/grub folder, but be careful not to delete a /Boot/BCD folder as that is part of windows.

After those fixes this should then find your windows:

```
sudo update-grub
```


Thank you Fred. I followed this and it worked perfectly.

---

