---
title: "Please help! Booting issue"
date: 2011-04-08
forum: General Help
---

### Post by willthong on 2011-04-08
Dear all,

I upgraded from Maverick to the Natty beta a little while ago. It all  worked fine for a couple of weeks. Then, this morning, I was unable to boot. I got to GRUB,  picked the first option and it went to the Ubuntu 11.04 with the dots,  then returned this:

```
fsck from util-linux-ng 2.17.2
/dev/sdb2: clean, 330122/2170880 files, 7302496/8683520 blocks
init: udevtrigger main process (367) terminated with status 1
init: udevtrigger post-stop process (372) terminated with status 1
init: udevmonitor main process (366) killed by TERM signal
init: ureadahead-other main process (428) terminated with status 4
init: udev-fallback-graphics main process (373) terminated with status 1
init: ureadahead-other main process (453) terminated with status 4
init:ureadahead-other main process (459) terminated with status 4
 * Starting mDNS/DNS-SD daemon [ OK ]
 * Starting network connection manager [ OK ]
 * Starting CUPS printing spooler/server [ OK ]

```

Then it doesn't load into GUI.
 
 
PLEASE HELP ME!

Other info:
* I'm dual-booting with Vista
* I'm running it all on a Sony VAIO laptop (model number VGN-AR51M)
* I've tried recovery mode, but it basically does a similar thing
 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]   		 		 		 		 		  	 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=10652029")

---

### Post by willthong on 2011-04-08
Update: I ran a LiveCD of Maverick and ran the Boot Information Script. The output was as follows:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for Pi.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for +e.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,004,863    20,002,816  27 Hidden HPFS/NTFS
/dev/sda2    *     20,004,864   312,579,759   292,574,896   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,126   243,111,935   243,095,810   f W95 Ext d (LBA)
/dev/sdb5              16,128   174,498,029   174,481,902   7 HPFS/NTFS
/dev/sdb6         174,498,093   243,111,644    68,613,552  82 Linux swap / Solaris
/dev/sdb2         243,111,936   312,580,095    69,468,160  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5AF2BA8AF2BA6A41                       ntfs       Recovery                      
/dev/sda2        78B6BD5DB6BD1C96                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        ffd7a20d-1476-4c55-a2f1-b8c5e838906c   ext4                                     
/dev/sdb5        DCC89FF7C89FCE60                       ntfs                                     
/dev/sdb6        349b76d7-7d73-466f-b90c-5ef8dc2ec238   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos2)'
search --no-floppy --fs-uuid --set=root ffd7a20d-1476-4c55-a2f1-b8c5e838906c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos2)'
search --no-floppy --fs-uuid --set=root ffd7a20d-1476-4c55-a2f1-b8c5e838906c
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root ffd7a20d-1476-4c55-a2f1-b8c5e838906c
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=ffd7a20d-1476-4c55-a2f1-b8c5e838906c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root ffd7a20d-1476-4c55-a2f1-b8c5e838906c
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=ffd7a20d-1476-4c55-a2f1-b8c5e838906c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root ffd7a20d-1476-4c55-a2f1-b8c5e838906c
    linux    /boot/vmlinuz-2.6.38-7-generic root=UUID=ffd7a20d-1476-4c55-a2f1-b8c5e838906c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root ffd7a20d-1476-4c55-a2f1-b8c5e838906c
    echo    'Loading Linux 2.6.38-7-generic ...'
    linux    /boot/vmlinuz-2.6.38-7-generic root=UUID=ffd7a20d-1476-4c55-a2f1-b8c5e838906c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root ffd7a20d-1476-4c55-a2f1-b8c5e838906c
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=ffd7a20d-1476-4c55-a2f1-b8c5e838906c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root ffd7a20d-1476-4c55-a2f1-b8c5e838906c
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=ffd7a20d-1476-4c55-a2f1-b8c5e838906c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root ffd7a20d-1476-4c55-a2f1-b8c5e838906c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root ffd7a20d-1476-4c55-a2f1-b8c5e838906c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 5AF2BA8AF2BA6A41
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 78B6BD5DB6BD1C96
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

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdb2 :
UUID=ffd7a20d-1476-4c55-a2f1-b8c5e838906c    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda2 :
UUID=78B6BD5DB6BD1C96    /media/78B6BD5DB6BD1C96    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.utf8    0    0
#Entry for /dev/sdb5 :
UUID=DCC89FF7C89FCE60    /media/DCC89FF7C89FCE60    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.utf8    0    0
#Entry for /dev/sda1 :
UUID=5AF2BA8AF2BA6A41    /media/Recovery    ntfs-3g    defaults,locale=en_GB.utf8    0    0
#Entry for /dev/sdb6 :
UUID=349b76d7-7d73-466f-b90c-5ef8dc2ec238    none    swap    sw    0    0



=================== sdb2: Location of files loaded by Grub: ===================


 148.2GB: boot/grub/core.img
 156.9GB: boot/grub/grub.cfg
 147.3GB: boot/initrd.img-2.6.35-25-generic
 134.9GB: boot/initrd.img-2.6.38-7-generic
 127.5GB: boot/initrd.img-2.6.38-8-generic
 148.7GB: boot/vmlinuz-2.6.35-25-generic
 150.4GB: boot/vmlinuz-2.6.38-7-generic
 139.0GB: boot/vmlinuz-2.6.38-8-generic
 127.5GB: initrd.img
 134.9GB: initrd.img.old
 139.0GB: vmlinuz
 150.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 00 00  00 00 00 80 08 a0 41 11  |..............A.|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  80 27 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |.'.t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  00 00 00 00 00 00 24 12  |...<.u........$.|
000001c0  0f 09 00 be bd 7d 31 c0  cd 13 46 8a 0c 80 f9 00  |.....}1...F.....|
000001d0  75 0f be da 7d e8 da ff  eb a4 46 6c 6f 70 70 79  |u...}.....Floppy|
000001e0  00 bb 00 70 8e c3 31 db  b8 01 02 b5 00 b6 00 cd  |...p..1.........|
000001f0  13 72 d3 b6 01 b5 4f e9  ff fe 00 00 00 00 55 aa  |.r....O.......U.|
00000200


```

Can somebody help me? :confused:

---

### Post by willthong on 2011-04-08
I hate to BUMP but I need to be able to access my computer!

---

### Post by THGIC on 2011-04-08
I was just reading over this and something came to mind -- mind you, I am no Linux expert like the support staff are, but I am an expert when it comes to computer hardware. Just reading through the coding that 'Terminal' was outputting sounded like maybe your HDD is nearing the end of it's life. 

You upgraded from 10.10 to 11.04 -- 11.04 has much a much later and better kernel; which means, it has better driver support -- and then you said it would not boot into 11.04, it instead goes to a 'Terminal' view.  

My two questions for you are:
1) Can you boot into Windows Vista properly, without getting any BSOD or errors stating that you have boot files missing? 
2) Will it boot successfully from the LiveCD -- meaning, do you see a GUI as the end result?

---

### Post by willthong on 2011-04-08
Thanks a lot for the swift response!

2) I'm in Maverick LiveCD now with no problems.

1) I've now booted into Vista, and it's fine except I can't get the theme away from Windows Standard, i.e. it will not give me Aero whatever I do.

The computer dates from around 2007...is it normal for the hard drives to have failed at this stage?

---

### Post by THGIC on 2011-04-08
Not a problem -- I want to make sure that your Windows OS is still intact. If you can boot into Windows, that means the HDD still is in a good condition. 

My thoughts on the Linux partition:
I think your partition may have become corrupted somewhere down the line -- For example, a bad shutdown can cause boot issues. 

You are running 11.04 on one partition, so my fear is that perhaps the Linux partition has become corrupted or maybe another thing -- you mentioned that you "upgraded" from 10.10 to 11.04. Did you literally choose the "upgrade" option or did you wipe your drive and then clean install? 

I figure that if you had inter-mitten issues (unknown to you) in 10.10, then you upgrade to 11.04; by doing the upgrade, you may have carried over certain issues. As far as upgrading Operating Systems go, you use the current OS and simply build from what you have (IE: patches, Service Packs, Windows Anytime Upgrade, etc). If you build off of an unstable OS, you may incur random issues, such as what you are experiencing. 

As I have stated before; I am not a Linux Expert, but I do know a bit about Hardware. I have worked with Operating Systems and Windows issues for a good bit. I am simply applying common sense, troubleshooting, and what little knowledge of Linux I have to help. 

Just thought I would let you know.  :)

---

### Post by willthong on 2011-04-08
Alright, so would it be a good idea to wipe that partition and reinstall Ubuntu?

Cheers!

---

### Post by THGIC on 2011-04-08
If you have backed up what is important to you, then I would go for it. A clean installation of any OS is always the best route.

Please post with results of your installation.

Also, did you boot into Windows Vista successfully? 

Thanks,

---

### Post by willthong on 2011-04-08
Yeah, it's fine, except that the theme is stuck onto Windows Standard...no Aero.

I'll post as soon as the installation is done.

---

### Post by THGIC on 2011-04-08
How is the installation process coming along? 

Note: Make sure you know which platform you have to install -- 32-Bit vs 64-Bit. 

I was using the 11.04 32-Bit version on my 64-Bit rig. To be honest, it seemed more glitchy than it should have, so I am now going to install 64-Bit. 

Best of Luck!

---

### Post by willthong on 2011-04-09
Just reinstalled and it's all good! (32-bit)

---

