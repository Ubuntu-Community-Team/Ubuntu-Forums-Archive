---
title: "Unable to boot into ubuntu.."
date: 2010-12-19
forum: General Help
---

### Post by karthick87 on 2010-12-19
On starting Ubuntu from the grub, I get the following message,
  ```
No init found

Busybox v1.15.3(ubuntu 1.1.15 3-ubuntu5) built in shell (ash)
Enter 'help' for a list of commands

(initramfs)_
```  I use a dualboot system, with Ubuntu 10.10, and Windows 7.

---

### Post by lmarmisa on 2010-12-19
Please, run the Boot Info Script and post the contents of output file RESULTS.txt:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by karthick87 on 2010-12-21
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for (,msdos8)/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,432,559    61,432,497   7 HPFS/NTFS
/dev/sda2          61,433,856    72,075,263    10,641,408   7 HPFS/NTFS
/dev/sda3          72,075,264   160,139,263    88,064,000   7 HPFS/NTFS
/dev/sda4         160,141,310   312,571,903   152,430,594   f W95 Ext d (LBA)
/dev/sda5         160,141,312   184,717,311    24,576,000  83 Linux
/dev/sda6         184,719,360   206,059,519    21,340,160  83 Linux
/dev/sda7         206,061,568   214,450,175     8,388,608  82 Linux swap / Solaris
/dev/sda8         214,452,224   214,554,623       102,400  83 Linux
/dev/sda9         214,556,672   312,571,903    98,015,232   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        75D0CC007BFAE2C7                       ntfs       Windows7                      
/dev/sda2        CEF808CEF808B72D                       ntfs       Swap                          
/dev/sda3        6AF43A80F43A4F17                       ntfs       Erste                         
/dev/sda4: PTTYPE="dos" 
/dev/sda5        5c042167-b1a6-4dd4-93d1-43a23144994b   ext4                                     
/dev/sda6        97636a60-ed48-4c03-97f2-8858f0868c60   ext4                                     
/dev/sda7        be90497c-7376-468c-ae9d-bc6c58c1d503   swap                                     
/dev/sda8        213146e4-7115-4529-80a9-7fc34ea949ee   ext4                                     
/dev/sda9        863C73093C72F411                       ntfs       Zweite                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=5c042167-b1a6-4dd4-93d1-43a23144994b    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda8 :
UUID=213146e4-7115-4529-80a9-7fc34ea949ee    /boot    ext4    defaults    0    2
#Entry for /dev/sda6 :
UUID=97636a60-ed48-4c03-97f2-8858f0868c60    /home    ext4    defaults    0    2
#Entry for /dev/sda3 :
UUID=6AF43A80F43A4F17    /media/Erste    ntfs-3g    defaults,locale=en_IN    0    0
#Entry for /dev/sda2 :
UUID=CEF808CEF808B72D    /media/Swap    ntfs-3g    defaults,nosuid,nodev,locale=en_IN    0    0
#Entry for /dev/sda1 :
UUID=75D0CC007BFAE2C7    /media/Windows7    ntfs-3g    defaults,nosuid,nodev,locale=en_IN    0    0
#Entry for /dev/sda9 :
UUID=863C73093C72F411    /media/Zweite    ntfs-3g    defaults,locale=en_IN    0    0
#Entry for /dev/sda7 :
UUID=be90497c-7376-468c-ae9d-bc6c58c1d503    none    swap    sw    0    0



============================= sda8/grub/grub.cfg: =============================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 5c042167-b1a6-4dd4-93d1-43a23144994b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 213146e4-7115-4529-80a9-7fc34ea949ee
set locale_dir=($root)/grub/locale
set lang=
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 213146e4-7115-4529-80a9-7fc34ea949ee
    linux    /vmlinuz-2.6.35-22-generic-pae root=UUID=5c042167-b1a6-4dd4-93d1-43a23144994b ro   quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
    initrd    /initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 213146e4-7115-4529-80a9-7fc34ea949ee
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /vmlinuz-2.6.35-22-generic-pae root=UUID=5c042167-b1a6-4dd4-93d1-43a23144994b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 213146e4-7115-4529-80a9-7fc34ea949ee
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 213146e4-7115-4529-80a9-7fc34ea949ee
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 75d0cc007bfae2c7
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

=================== sda8: Location of files loaded by Grub: ===================


 109.8GB: grub/core.img
 109.8GB: grub/grub.cfg
 109.8GB: initrd.img-2.6.35-22-generic-pae
 109.8GB: vmlinuz-2.6.35-22-generic-pae
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  0a 78 42 9f 5b 5e 5d 10  d2 68 a1 82 a3 9e eb b5  |.xB.[^]..h......|
00000010  f1 c9 e5 df df b1 89 4c  aa 7c 3c e4 e8 f1 df 47  |.......L.|<....G|
00000020  97 10 f3 5a 8f 4d b1 80  65 3f 54 37 0f 4d ad cb  |...Z.M..e?T7.M..|
00000030  2b 93 44 02 bc 6c bb 35  aa 7a 1d 11 2e 3f 1d 23  |+.D..l.5.z...?.#|
00000040  dc 22 50 01 75 fe af 72  4b 7c 78 e3 d1 36 e3 0e  |."P.u..rK|x..6..|
00000050  6f 38 26 6d 57 df 91 e1  43 ce b8 fb 82 c8 1c 93  |o8&mW...C.......|
00000060  c7 76 f8 0d 50 08 b2 d7  4b 1c 14 c1 16 f0 6f 8f  |.v..P...K.....o.|
00000070  81 80 34 03 c4 ac 85 f4  10 fc b9 90 0f 06 f8 32  |..4............2|
00000080  b0 84 10 c4 91 f5 b9 82  51 75 fd 89 ed 39 e3 20  |........Qu...9. |
00000090  f0 10 20 83 09 20 c3 e2  f1 2f 4b c4 8b 62 b6 64  |.. .. .../K..b.d|
000000a0  a6 c4 9a 24 ab a5 ca 0d  89 5e 1f 48 ad 4b 81 0c  |...$.....^.H.K..|
000000b0  50 58 2c 25 59 8b 0a 95  5b c1 5d 54 07 65 aa 62  |PX,%Y...[.]T.e.b|
000000c0  a7 2b 04 0f 04 01 fd 55  f0 0d 12 47 c2 41 76 cb  |.+.....U...G.Av.|
000000d0  55 7d 5e 7f e0 a8 8c d7  83 02 00 34 12 7e 25 0f  |U}^........4.~%.|
000000e0  81 08 03 01 81 01 57 c4  8c c1 e8 93 41 41 12 ea  |......W.....AA..|
000000f0  be a0 0c 94 74 90 0a 67  cc 5e e5 0f 87 a2 51 7c  |....t..g.^....Q||
00000100  53 ef ca ea 3e fc f6 17  cd d3 00 d0 03 87 e0 18  |S...>...........|
00000110  25 17 41 f2 b2 e1 22 97  b3 e1 22 fc be 2a 08 b5  |%.A..."..."..*..|
00000120  58 95 e8 06 d5 45 b3 f0  61 e3 ef 0a 50 ea f4 ee  |X....E..a...P...|
00000130  1c 38 46 f0 ae 78 2a aa  8a f4 49 12 fc b1 70 95  |.8F..x*...I...p.|
00000140  60 13 a2 58 30 b0 20 42  e1 fc 04 12 f1 2d 45 06  |`..X0. B.....-E.|
00000150  c2 f0 80 3e f2 96 07 a5  c5 e5 f7 10 0f dd c3 c7  |...>............|
00000160  93 50 ad 92 06 7e b6 9f  56 25 f1 f8 61 30 f6 e6  |.P...~..V%..a0..|
00000170  b8 4a a3 e8 e1 2d 54 d8  68 10 e5 7a 65 9c a8 7d  |.J...-T.h..ze..}|
00000180  61 90 6d 50 3c b2 56 e6  5e 1e 1f 0f 9e 5c 10 47  |a.mP<.V.^....\.G|
00000190  51 97 81 4d ba 5e db 47  d3 f0 19 4d f1 30 8a 79  |Q..M.^.G...M.0.y|
000001a0  5c 53 47 e3 df 4c b1 04  71 d2 63 e9 8f 06 fe ae  |\SG..L..q.c.....|
000001b0  13 48 5f 77 cb 44 6e fd  2f e5 c8 60 7d 35 00 fe  |.H_w.Dn./..`}5..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 00 77 01 00 fe  |............w...|
000001d0  ff ff 05 fe ff ff 02 00  77 01 00 a8 45 01 00 00  |........w...E...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by wojox on 2010-12-21
Boot a Live-CD, open a terminal and run 

```
sudo e2fsck -C0 -p -f -v /dev/sda5
```

---

### Post by oldfred on 2010-12-21
You have a separate /boot that makes it a bit more complex. Is there some reason for a separate /boot?

Normally the boot files are in a /boot folder within the boot partition, but yours are not? But both grub.cfg and the files locations seem to match, so it looks like it should work. Did you move anything around after installing grub2 to the MBR? I would think on a kernel update it may put them into /boot and cause confusion.

If you want to reinstall grub2 you also have to be sure to mount the /boot partition as part of the reinstall.

$sudo mount /dev/sda5 /mnt
$sudo mount /dev/sda8 /mnt/boot  
sudo grub-install --root-directory=/mnt/ /dev/sda
$sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

But you may have to do the full chroot method (also mount /boot)

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by karthick87 on 2010-12-21
I dont know,how it happened..I am really confused,what should i do now??

---

### Post by oldfred on 2010-12-21
Running e2fsck or reinstall grub will not conflict with each other. Ubuntu normally runs fsck every 30 boots. But I would run it on both sda8 & sda5. that is slightly easier to run

That could solve the problem which is not finding init. Reinstalling grub to the boot loader may or may not find it also. 

I think the full chroot reinstall of grub may be the best solution but both of the others are easy to do first and may work.

---

### Post by karthick87 on 2010-12-21
Running e2fsck din help.It is still the same..So how to reinstall grub..

---

### Post by sikander3786 on 2010-12-21
Try the chroot method **oldfred** already referred to.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

I have no experience with PAE-Kernels but I strongly feel that Grub is missing some files.

Here is the list of Grub files from my older output.

```
  96.2GB: boot/grub/core.img
  94.4GB: boot/grub/grub.cfg
  96.2GB: boot/initrd.img-2.6.32-21-generic
  96.2GB: boot/vmlinuz-2.6.32-21-generic
 [COLOR="Red"] 96.2GB: initrd.img
  96.2GB: vmlinuz[/COLOR]
```

PAE-Kernel doesn't need those generic images? I am not sure. I can't see those in your output.

However, the best practice for the moment is definitely chroot and purge/reinstall Grub. Lets see how that goes.

---

### Post by Rubi1200 on 2010-12-21
I agree with sikander3786 (and oldfred of course) and think that the best course of action is to purge and reinstall GRUB using the chroot method.

Good luck!

And, if you need more help, please ask.

---

### Post by karthick87 on 2010-12-21
What is chroot method??

---

### Post by amsterdamharu on 2010-12-21
> **karthick87 said:**
> What is chroot method??
The link has been posted twice (3 times now):
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

From a live cd run these command ([COLOR=Red]note to others sda8 and sda5 are specific for the OP do not use it if you found this while googling but run bootscript first and post the output[/COLOR])
```
sudo mkdir /mnt/boot
sudo mount /dev/sda8 /mnt/boot
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by karthick87 on 2010-12-21
Thanks a lot for all who helped me :)

---

### Post by threestripebrand on 2010-12-22
i apologize in advance if this is the wrong place for this post. i've been at this all day without success. i found an old tower in my garage so i decided to mess around with it a lil bit and add a dvd drive and another hdd etc. anyway it now has two 80gb hdd's i installed windows xp on one, and i would like to install 10.10 on half of the other and maybe osx on the remaining or whatever. anyway i've tried everything i've found in posts and nothing has worked. i left wonder if this due to it being on another drive. i would like the multi boot option. i've got 10.10 installed but now all i have is grub rescue. even when i use the supergrub2 it doesnt show linux there. and that seems to be the onlyway to get into windows now. when in terminal when working from live cd, using fdisk -l i see linux there. so basicly nothing works lol. any help would make this noob very happy. thanks for your time whoever reads this.

---

### Post by oldfred on 2010-12-22
threestripebrand - Welcome to the forums, but you problem is a lot different. Please start a new thread and post this.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

