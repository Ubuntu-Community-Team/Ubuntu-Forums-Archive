---
title: "Re-installed grub2 but it wouldn't boot"
date: 2010-09-21
forum: General Help
---

### Post by Quackers on 2010-09-21
I have a 2 hard drive laptop. I have Mac OSX on /dev/sda and 64 bit Ubuntu on /dev/sdb. (I did have 32 bit Ubuntu on /dev/sda as well, but I have deleted that). So with the intention of deleting the 32 bit version and to make sure the 64 bit version on sdb still booted I re-installed grub2 to sdb before I deleted the 32 bit installation from sda. Sadly it wouldn't boot. It gave me the "no such partition - grub rescue" message. So I booted up the live cd and re-installed grub2 to sdb again, just to make sure. It ran ok but on reboot got the same message as before.
So I booted up the live cd again and installed grub2 to sda and now it boots fine.
I presume that the bios is looking at the first hard drive and if it finds nothing there it just gives up - not looking at the second drive at all. Is this normal on a 2 drive system? Unfortunately as it's a Sony Vaio the bios is almost completely locked so I suspect I cannot change it.

---

### Post by drs305 on 2010-09-21
I owned a Viao once and could change the BIOS settings, but it didn't have 2 drives. I assume you have tried to enter the BIOS and looked under the "Boot options" (or similar) section?

Is the Mac OS still bootable either via Grub2 or other means?

If you run the bootinfo script we can see if there's anything odd in your configuration. 
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by Quackers on 2010-09-21
Hi drs305,
The only options which I can change in the bios are raid or non-raid, that's it. It is currently set to non-raid.
I've run the boot script and enclose the output.
Mac OS X is bootable via grub2.
There is no device.map file

```
              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   293,844,914   293,844,852   7 HPFS/NTFS
/dev/sda3         293,844,915   488,392,064   194,547,150  af HFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,046     5,859,327     5,857,282   5 Extended
/dev/sdb5               2,048     5,859,327     5,857,280  82 Linux swap / Solaris
/dev/sdb2    *      5,859,328    30,273,535    24,414,208  83 Linux
/dev/sdb3          30,273,536   188,477,439   158,203,904  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        08D244CF35D707E8                       ntfs                                     
/dev/sda3        1a6aa2b2-6cb5-3c59-a3c7-79e612695c87   hfsplus    Snow Leopard                  
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        a0f9ca15-a968-4dd6-9cc8-087d4650f462   ext4                                     
/dev/sdb3        e4d4bb4e-7d8f-4400-ad94-8d89ef5898e2   ext4                                     
/dev/sdb5        add3dc6e-bcd4-4f6b-8282-280a16d2636f   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext4       (rw,errors=remount-ro)
/dev/sdb3        /home                    ext4       (rw)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set a0f9ca15-a968-4dd6-9cc8-087d4650f462
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set a0f9ca15-a968-4dd6-9cc8-087d4650f462
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=-1
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set a0f9ca15-a968-4dd6-9cc8-087d4650f462
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=a0f9ca15-a968-4dd6-9cc8-087d4650f462 ro   quiet splash nomodeset video=uvesafb:mode_option=1920x1200-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set a0f9ca15-a968-4dd6-9cc8-087d4650f462
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=a0f9ca15-a968-4dd6-9cc8-087d4650f462 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set a0f9ca15-a968-4dd6-9cc8-087d4650f462
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set a0f9ca15-a968-4dd6-9cc8-087d4650f462
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set fcd9dfad-cafb-45aa-a2ef-c604a194808a
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=fcd9dfad-cafb-45aa-a2ef-c604a194808a ro quiet splash nomodeset video=uvesafb:mode_option=1920x1200-24,mtrr=3,scroll=ywrap
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Mac OS X (32-bit) (on /dev/sda3)" {
    insmod hfsplus
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 4c38836e478ad4e1
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 4c38836e478ad4e1 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda3)" {
    insmod hfsplus
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 4c38836e478ad4e1
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 4c38836e478ad4e1 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=a0f9ca15-a968-4dd6-9cc8-087d4650f462 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=e4d4bb4e-7d8f-4400-ad94-8d89ef5898e2 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=a65962f1-18e9-4aeb-934e-fa2ecdeaad65 none            swap    sw              0       0
/dev/sdb5       none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


   3.2GB: boot/grub/core.img
  12.0GB: boot/grub/grub.cfg
   4.5GB: boot/initrd.img-2.6.32-24-generic
   4.4GB: boot/vmlinuz-2.6.32-24-generic
   4.5GB: initrd.img
   4.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e d8 8e c0 56 be 00  |.1...........V..|
00000010  7c bf 00 e0 fc b9 00 02  f3 a4 5e 68 1f e0 c3 66  ||.........^h...f|
00000020  8b 44 08 66 a3 00 e6 88  16 04 e6 c7 06 0a e6 00  |.D.f............|
00000030  10 66 31 c9 66 41 b0 02  66 ba 00 e2 00 00 e8 a3  |.f1.fA..f.......|
00000040  00 66 a1 28 e4 66 0f c8  66 c1 e8 09 66 a3 06 e6  |.f.(.f..f...f...|
00000050  a1 00 e4 3d 48 58 74 05  3d 48 2b 75 58 b0 04 8d  |...=HXt.=H+uX...|
00000060  36 ed e3 8d 3e 20 e5 e8  96 01 75 49 8d b6 1d 01  |6...> ....uI....|
00000070  8b 34 81 3c 00 02 75 3d  66 8b 5c 5c 66 0f cb 66  |.4.<..u=f.\\f..f|
00000080  81 c3 ff 01 00 00 66 c1  eb 09 81 fb ff 02 77 25  |......f.......w%|
00000090  66 8b 44 08 66 0f c8 66  31 c9 66 ba 00 02 02 00  |f.D.f..f1.f.....|
000000a0  8d 7c 68 e8 4e 02 bf f0  e1 e8 6d 00 8a 16 04 e6  |.|h.N.....m.....|
000000b0  ea 00 02 00 20 bf e7 e3  e8 5e 00 f4 eb fd 66 60  |.... ....^....f`|
000000c0  89 c3 66 31 c0 88 d8 81  fb 40 00 72 02 b0 40 e8  |..f1.....@.r..@.|
000000d0  12 00 29 c3 74 0b 66 01  c1 c1 e0 09 66 01 c2 eb  |..).t.f.....f...|
000000e0  e1 66 61 c3 66 60 06 89  e5 89 d3 80 e7 0f 66 c1  |.fa.f`........f.|
000000f0  ea 04 30 d2 8e c2 1e 1e  66 03 0e 00 e6 66 51 06  |..0.....f....fQ.|
00000100  53 30 e4 50 68 10 00 8a  16 04 e6 89 e6 b4 42 cd  |S0.Ph.........B.|
00000110  13 72 a2 89 ec 07 66 61  c3 66 60 57 be dd e3 e8  |.r....fa.f`W....|
00000120  07 00 5e e8 03 00 66 61  c3 bb 01 00 ac 3c 00 74  |..^...fa.....<.t|
00000130  06 b4 0e cd 10 eb f5 c3  66 60 ad 86 e0 ab 3c 00  |........f`....<.|
00000140  74 23 89 c1 ad 86 e0 80  3e 01 e4 58 74 14 09 c0  |t#......>..Xt...|
00000150  75 01 48 80 fc 00 77 0a  3c 41 72 06 3c 5a 77 02  |u.H...w.<Ar.<Zw.|
00000160  04 20 ab e2 df 66 61 c3  66 60 b2 00 66 8b 44 02  |. ...fa.f`..f.D.|
00000170  66 3b 45 02 75 0f 80 3c  00 75 0a 66 8b 44 06 66  |f;E.u..<.u.f.D.f|
00000180  3b 45 06 74 48 77 44 72  3d 66 60 31 d2 87 f7 66  |;E.tHwDr=f`1...f|
00000190  ad 66 89 c1 87 f7 66 ad  66 39 c8 77 2e 72 27 87  |.f....f.f9.w.r'.|
000001a0  f7 ad 89 c1 87 f7 ad 80  f9 00 74 1f 39 c8 74 0b  |..........t.9.t.|
000001b0  77 07 fe ce 89 c1 e9 02  00 fe c6 f3 a7 77 0c 72  |w............w.r|
000001c0  05 88 f2 e9 07 00 fe ca  e9 02 00 fe c2 88 96 14  |................|
000001d0  00 80 fa 00 66 61 c3 50  57 8b 3e 0a e6 57 47 47  |....fa.PW.>..WGG|
000001e0  49 49 b0 00 f3 aa 89 3e  0a e6 5d 89 2d 5f 58 c3  |II.....>..].-_X.|
000001f0  2f 62 6f 6f 74 00 00 00  00 00 00 00 00 00 55 aa  |/boot.........U.|
00000200


```

---

### Post by drs305 on 2010-09-21
Well, as you can see from the RESULTS.txt the bootinfo script thinks that Grub2 is booting from and using the files on sdb. The grub installed on sda points to a non-existent partition and wouldn't boot.

On a few occasions the script switches the sda and sdb designations. I haven't figured out why. Once booted, you could run "sudo blkid" and see if the partitions in the script match the results of *blkid*. It's possible they will be reversed. 

In this case, if everything is working it's probably best to just leave things the way they are until something *needs* changing.

---

### Post by Quackers on 2010-09-21
I understand what you are saying drs305. The strange thing is that Ubuntu wouldn't boot until I installed grub2 on sda - even though grub2 was installed on sdb. It's as if it needs grub2 on sda just to look any further.

---

### Post by Quackers on 2010-09-21
sudo blkid output lists the same details and UUID's

```
mike64@mike64-laptop:~$ sudo blkid
[sudo] password for mike64: 
/dev/sda1: UUID="08D244CF35D707E8" TYPE="ntfs" 
/dev/sda3: UUID="1a6aa2b2-6cb5-3c59-a3c7-79e612695c87" LABEL="Snow Leopard" TYPE="hfsplus" 
/dev/sdb2: UUID="a0f9ca15-a968-4dd6-9cc8-087d4650f462" TYPE="ext4" 
/dev/sdb3: UUID="e4d4bb4e-7d8f-4400-ad94-8d89ef5898e2" TYPE="ext4" 
/dev/sdb5: UUID="add3dc6e-bcd4-4f6b-8282-280a16d2636f" TYPE="swap" 

```

---

### Post by Darkness Des on 2010-09-21
I can tell you exactly why it isn't booting with GRUB2 only on sdb. It's because your BIOS is set to boot from sda.

---

### Post by Quackers on 2010-09-21
Darkness Des, that seems likely I must say, but if that were the case I should at least get an option to boot Mac OSX, which is on sda and detected by grub2.

---

