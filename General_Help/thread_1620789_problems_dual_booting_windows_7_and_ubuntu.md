---
title: "problems dual booting windows 7 and ubuntu"
date: 2010-11-13
forum: General Help
---

### Post by shresthanator on 2010-11-13
For a while i had my computer set up so it would dual boot vista and ubuntu. I think i installed windows first then ubuntu and grub was automatically set up so I was allowed to dual boot into either  one of the OS just fine. However, now that I got windows 7, setting up a dual boot is giving me a lot of problems.

I first tried to just partition another drive on my HD and install windows 7, but that got rid of grub and set up a windows boot loader. Naturally, it no longer recoginzed linux, and I was only able to boot either into vista or windows 7. I looked on online forms and fiddled around with trying to get grub back for hours, but it just didn't work out. So I formatted my whole hard drive. 

First I installed window7 then i installed ubuntu. I got Grub back, and it lists windows7, but I cannot boot into it. Can someone please help me?

---

### Post by Rubi1200 on 2010-11-13
Hi,
please boot into Ubuntu and then follow the instructions in the link at the bottom of my post.

Post the results back here and we will try and help you find a solution.

Thanks.

---

### Post by arpanaut on 2010-11-13
Try this to get an idea of what is going on with your system

Posted by oldfred in another thread:

> Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's  menu and then paste the contents between the generated [ code][ /code]  tags.

Boy, Am I slow or what?

---

### Post by shresthanator on 2010-11-13
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 208118424 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1   321,672,959   321,672,959  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              34   195,079,084   195,079,051 Linux or Data
/dev/sda2     195,079,085   321,672,926   126,593,842 Linux or Data

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   165,879,895   165,673,048   7 HPFS/NTFS
/dev/sdb3         307,210,995   488,392,064   181,181,070  83 Linux
/dev/sdb4         165,881,854   307,210,239   141,328,386   5 Extended
/dev/sdb5         165,881,856   301,359,103   135,477,248  83 Linux
/dev/sdb6         301,361,152   307,210,239     5,849,088  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3E7430B6580C4834                       ntfs       100_gig_windows_extra         
/dev/sda2        ba66235a-1cad-4a3e-8533-9f09762b1c30   ext4       linux_extra                   
/dev/sda: PTTYPE="gpt" 
/dev/sdb1        0EFE0CB7FE0C98DB                       ntfs       System Reserved               
/dev/sdb2        442838022837F212                       ntfs                                     
/dev/sdb3        00c43f32-c051-4940-a943-5da7718d3b46   ext4       New Volume                    
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        b89af7dc-2afe-4ff4-bc0e-27e16acf65ac   ext4                                     
/dev/sdb6        1064409a-3be6-4f72-a169-12ec85fd69d5   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb2        /media/442838022837F212  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set b89af7dc-2afe-4ff4-bc0e-27e16acf65ac
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set b89af7dc-2afe-4ff4-bc0e-27e16acf65ac
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=16
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set b89af7dc-2afe-4ff4-bc0e-27e16acf65ac
insmod png
if background_image /usr/share/images/desktop-base/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set b89af7dc-2afe-4ff4-bc0e-27e16acf65ac
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=b89af7dc-2afe-4ff4-bc0e-27e16acf65ac ro  vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set b89af7dc-2afe-4ff4-bc0e-27e16acf65ac
	echo	'Loading Linux 2.6.35-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=b89af7dc-2afe-4ff4-bc0e-27e16acf65ac ro single  vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set b89af7dc-2afe-4ff4-bc0e-27e16acf65ac
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set b89af7dc-2afe-4ff4-bc0e-27e16acf65ac
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 0efe0cb7fe0c98db
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=b89af7dc-2afe-4ff4-bc0e-27e16acf65ac /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=1064409a-3be6-4f72-a169-12ec85fd69d5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 106.5GB: boot/grub/core.img
 106.5GB: boot/grub/grub.cfg
  98.3GB: boot/initrd.img-2.6.35-22-generic-pae
 106.5GB: boot/vmlinuz-2.6.35-22-generic-pae
  98.3GB: initrd.img
 106.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb4

00000000  69 6e 67 3a 20 27 24 24  24 61 76 4c 61 6e 67 53  |ing: '$$$avLangS|
00000010  70 61 6e 69 73 68 27 29  2c 0d 0a 09 7a 73 74 72  |panish'),...zstr|
00000020  69 6e 67 5f 77 69 64 74  68 28 7a 73 74 72 69 6e  |ing_width(zstrin|
00000030  67 3a 20 27 24 24 24 61  76 4c 61 6e 67 53 77 65  |g: '$$$avLangSwe|
00000040  64 69 73 68 27 29 29 3b  0d 0a 0d 0a 0d 0a 67 54  |dish'));......gT|
00000050  72 61 70 70 65 64 59 65  73 20 3d 20 7a 73 74 72  |rappedYes = zstr|
00000060  69 6e 67 5f 77 69 64 74  68 28 7a 73 74 72 69 6e  |ing_width(zstrin|
00000070  67 3a 20 27 24 24 24 61  76 59 65 73 27 29 3b 0d  |g: '$$$avYes');.|
00000080  0a 67 54 72 61 70 70 65  64 4e 6f 20 3d 20 7a 73  |.gTrappedNo = zs|
00000090  74 72 69 6e 67 5f 77 69  64 74 68 28 7a 73 74 72  |tring_width(zstr|
000000a0  69 6e 67 3a 20 27 24 24  24 61 76 4e 6f 27 29 3b  |ing: '$$$avNo');|
000000b0  0d 0a 67 54 72 61 70 70  65 64 55 6e 6b 6e 6f 77  |..gTrappedUnknow|
000000c0  6e 20 3d 20 7a 73 74 72  69 6e 67 5f 77 69 64 74  |n = zstring_widt|
000000d0  68 28 7a 73 74 72 69 6e  67 3a 20 27 24 24 24 61  |h(zstring: '$$$a|
000000e0  76 55 6e 6b 6e 6f 77 6e  27 29 3b 0d 0a 0d 0a 67  |vUnknown');....g|
000000f0  50 6f 70 75 70 57 69 64  74 68 20 3d 20 6d 61 78  |PopupWidth = max|
00000100  28 0d 0a 09 67 54 72 61  70 70 65 64 54 72 75 65  |(...gTrappedTrue|
00000110  2c 0d 0a 09 67 54 72 61  70 70 65 64 46 61 6c 73  |,...gTrappedFals|
00000120  65 2c 0d 0a 09 67 54 72  61 70 70 65 64 55 6e 6b  |e,...gTrappedUnk|
00000130  6e 6f 77 6e 29 20 2b 20  6d 61 78 5f 63 68 61 72  |nown) + max_char|
00000140  5f 77 69 64 74 68 28 29  3b 0d 0a 0d 0a 67 4e 75  |_width();....gNu|
00000150  6d 43 6f 70 69 65 73 57  69 64 74 68 20 3d 20 7a  |mCopiesWidth = z|
00000160  73 74 72 69 6e 67 5f 77  69 64 74 68 28 7a 73 74  |string_width(zst|
00000170  72 69 6e 67 3a 20 27 24  24 24 61 76 44 65 66 61  |ring: '$$$avDefa|
00000180  75 6c 74 27 29 20 2b 20  33 3b 0d 0a 0d 0a 64 69  |ult') + 3;....di|
00000190  61 6c 6f 67 28 6e 61 6d  65 3a 20 27 24 24 24 2f  |alog(name: '$$$/|
000001a0  44 69 61 6c 6f 67 73 2f  50 44 46 49 6e 66 6f 27  |Dialogs/PDFInfo'|
000001b0  2c 20 6d 61 72 67 69 6e  5f 68 65 69 67 68 00 fe  |, margin_heigh..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 38 13 08 00 fe  |...........8....|
000001d0  ff ff 05 fe ff ff 02 38  13 08 00 48 59 00 00 00  |.......8...HY...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```
Code tags added by The Cog.

---

### Post by shresthanator on 2010-11-13
> **Rubi1200 said:**
> Hi,
please boot into Ubuntu and then follow the instructions in the link at the bottom of my post.

Post the results back here and we will try and help you find a solution.

Thanks.


I did what you said, I really would appreciate your help :)

---

### Post by kristine12 on 2010-11-13
> **shresthanator said:**
> For a while i had my computer set up so it would dual boot vista and ubuntu. I think i installed windows first then ubuntu and grub was automatically set up so I was allowed to dual boot into either  one of the OS just fine. However, now that I got windows 7, setting up a dual boot is giving me a lot of problems.

I first tried to just partition another drive on my HD and install windows 7, but that got rid of grub and set up a windows boot loader. Naturally, it no longer recoginzed linux, and I was only able to boot either into vista or windows 7. I looked on online forms and fiddled around with trying to get grub back for hours, but it just didn't work out. So I formatted my whole hard drive. 

First I installed window7 then i installed ubuntu. I got Grub back, and it lists windows7, but I cannot boot into it. Can someone please help me?

I've experienced that problem before. Here's what I do:
[LIST=1]
[*]Open your terminal
[*]Edit your grub
   ```
sudo gedit /boot/grub/menu.lst
```
[*]Add Windows 7 on your partition
   ```

title Windows 7
root (hd0,1)
makeactive
chainloader +1
   
```
[*]Save your modification and reboot. When the GRUB loader launches hit ESC for the boot menu.
[*]If you want to make the GRUB menu always available, boot back into Ubuntu and edit the MENU.LST file. Find the hiddenmenu text string and change it to #hiddenmenu.
[/LIST]

---

### Post by Rubi1200 on 2010-11-13
With all due respect, kristine12, this will not work for 2 reasons:

1. your advice is for using legacy-GRUB which the OP does not have

2. there is a problem in the Windows boot sector that needs to be fixed before anything else

@shresthanator:

This is what you need to do:
If you look at sdb1, you will see that GRUB files got onto your Windows boot sector; we need to correct this.

Using this guide, restore the Windows bootloader:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Once Windows is booting again normally, post back here and we will get Ubuntu up and running again for you.

If you have any questions, please ask.

---

### Post by oldfred on 2010-11-13
Rubi1200's link to repair the windows uses windows tools - fixBoot or bootrec /fixBoot depending on which version of windows you have. 

But if you do not immediately have a windows repair CD ( which you should have) you can use the Ubuntu liveCD and download testdisk.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)


Win7 repair Cd.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

