---
title: "Grub problem"
date: 2011-03-16
forum: General Help
---

### Post by Palm&#279; on 2011-03-16
Hello. Well, few days ago I installed Ubuntu 10.10 (I am new in Linux). It worked propertly, but today I installed Win 7 and it ruined grub (I knew this would happen, but haven't thought it will make so many problems). I tried to use my Ubuntu live cd to restore it using this site: "http://www.lancelhoff.com/restore-grub2-after-installing-windows/". Well, it didn't worked. Then i rebooted PC logs into a GRUB window, can't choose neither linux nor windows. Well, used hiren's boot cd and was able to start windows. Although when I choose Ubuntu it leads to Grub window. :/

---

### Post by oldfred on 2011-03-16
Welcome to the forums.

Just to be sure what is installed where:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Palm&#279; on 2011-03-21
Hello again.
This is what I got: 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   159,999,999   159,997,952  83 Linux
/dev/sda2         160,002,046   567,998,463   407,996,418   5 Extended
/dev/sda5         160,002,048   459,999,231   299,997,184  83 Linux
/dev/sda6         460,001,280   467,998,719     7,997,440  82 Linux swap / Solaris
/dev/sda7         468,000,768   567,998,463    99,997,696  83 Linux
/dev/sda3    *    567,998,464   568,203,263       204,800   7 HPFS/NTFS
/dev/sda4         568,203,264   735,975,423   167,772,160   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4b3eaf4f-a1bb-4850-99ba-6d907f39ea3b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        7C109A2B1099ED00                       ntfs       System Reserved               
/dev/sda4        F0A8C39FA8C36328                       ntfs                                     
/dev/sda5        6c9f1099-25a1-44d3-88d6-8ccfa14a3952   ext4                                     
/dev/sda6        49a25c46-1931-4d79-a6fb-0b4440283aa1   swap                                     
/dev/sda7        9babc43d-f5d9-457c-a713-e9cbabd558be   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sda1/grub/grub.cfg: =============================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 9babc43d-f5d9-457c-a713-e9cbabd558be
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 4b3eaf4f-a1bb-4850-99ba-6d907f39ea3b
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4b3eaf4f-a1bb-4850-99ba-6d907f39ea3b
    linux    /vmlinuz-2.6.35-27-generic root=UUID=9babc43d-f5d9-457c-a713-e9cbabd558be ro   quiet splash
    initrd    /initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4b3eaf4f-a1bb-4850-99ba-6d907f39ea3b
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /vmlinuz-2.6.35-27-generic root=UUID=9babc43d-f5d9-457c-a713-e9cbabd558be ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4b3eaf4f-a1bb-4850-99ba-6d907f39ea3b
    linux    /vmlinuz-2.6.35-22-generic root=UUID=9babc43d-f5d9-457c-a713-e9cbabd558be ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4b3eaf4f-a1bb-4850-99ba-6d907f39ea3b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=9babc43d-f5d9-457c-a713-e9cbabd558be ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4b3eaf4f-a1bb-4850-99ba-6d907f39ea3b
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4b3eaf4f-a1bb-4850-99ba-6d907f39ea3b
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=================== sda1: Location of files loaded by Grub: ===================


  15.1GB: boot/grub/core.img
  62.4GB: grub/core.img
  62.4GB: grub/grub.cfg
    .2GB: initrd.img-2.6.35-22-generic
    .2GB: initrd.img-2.6.35-27-generic
    .1GB: vmlinuz-2.6.35-22-generic
    .2GB: vmlinuz-2.6.35-27-generic

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=9babc43d-f5d9-457c-a713-e9cbabd558be /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext4    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=6c9f1099-25a1-44d3-88d6-8ccfa14a3952 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=49a25c46-1931-4d79-a6fb-0b4440283aa1 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 282.7GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  83 3e 00 00 00 00 ff ff  ff ff 00 00 00 00 00 03  |.>..............|
00000010  c1 3f 18 eb 1a 42 00 ac  c3 bf f9 66 07 3f 0a 27  |.?...B.....f.?.'|
00000020  31 3f 8c 8c fb 3e 14 54  06 3e e0 d2 d0 3e 68 55  |1?...>.T.>...>hU|
00000030  29 3f ac 68 15 3f 00 00  00 00 ff ff ff ff 00 00  |)?.h.?..........|
00000040  00 00 00 be 78 3f 80 8b  18 42 00 80 64 bf d5 f5  |....x?...B..d...|
00000050  11 3f dd 0e 36 3f a2 95  d2 3e e8 2d 17 3e 70 b0  |.?..6?...>.-.>p.|
00000060  d7 3e 42 54 28 3f 14 51  16 3f 00 00 00 00 ff ff  |.>BT(?.Q.?......|
00000070  ff ff 00 00 00 00 80 3a  1e 40 f0 b5 0f 42 00 70  |.......:.@...B.p|
00000080  c3 c0 84 b3 40 3f b1 bf  66 be 5b 59 1e bf 41 1c  |....@?..f.[Y..A.|
00000090  4d 3d a4 02 e1 3e 58 e5  ae 3e 91 cf 52 3f 00 00  |M=...>X..>..R?..|
000000a0  00 00 ff ff ff ff 00 00  00 00 80 7d 0d 40 b0 1c  |...........}.@..|
000000b0  0a 42 00 a3 9d c0 f6 04  54 3f 00 c5 d5 be e8 68  |.B......T?.....h|
000000c0  bf be 7e ec 71 3d 7e eb  f0 3e d0 4d ac 3e e2 d7  |..~.q=~..>.M.>..|
000000d0  54 3f 00 00 00 00 ff ff  ff ff 00 00 00 00 80 7d  |T?.............}|
000000e0  0d 40 b0 1c 0a 42 00 a3  9d c0 f6 04 54 3f 00 c5  |.@...B......T?..|
000000f0  d5 be e8 68 bf be 7e ec  71 3d 7e eb f0 3e cb 93  |...h..~.q=~..>..|
00000100  4e 3f 72 84 4f 3f 00 00  00 00 ff ff ff ff 00 00  |N?r.O?..........|
00000110  00 00 80 3a 1e 40 f0 b5  0f 42 00 70 c3 c0 84 b3  |...:.@...B.p....|
00000120  40 3f b1 bf 66 be 5b 59  1e bf 41 1c 4d 3d a4 02  |@?..f.[Y..A.M=..|
00000130  e1 3e 6a 74 4c 3f 0a c7  51 3f 00 00 00 00 ff ff  |.>jtL?..Q?......|
00000140  ff ff 00 00 00 00 80 18  0d 40 70 84 08 42 00 40  |.........@p..B.@|
00000150  5a c0 a5 ad 66 3f 84 06  dd be b7 28 28 bd c7 1e  |Z...f?.....((...|
00000160  a5 3d b4 e3 f9 3e 83 f3  4e 3f e0 e3 4c 3f 00 00  |.=...>..N?..L?..|
00000170  00 00 ff ff ff ff 00 00  00 00 00 13 e1 3f 48 cf  |.............?H.|
00000180  05 42 00 48 0c c0 b0 f2  66 3f 65 81 c5 be 8d dd  |.B.H....f?e.....|
00000190  45 3e df b4 ea 3d 60 35  01 3f e9 d9 4f 3f 8c b5  |E>...=`5.?..O?..|
000001a0  4a 3f 00 00 00 00 ff ff  ff ff 00 00 00 00 00 1f  |J?..............|
000001b0  a0 3f f0 13 06 42 00 78  a0 bf f8 f2 32 3f 00 fe  |.?...B.x....2?..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 98 e1 11 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 98  e1 11 00 10 7a 00 00 00  |............z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2011-03-21
Do you have two installs? Grub is trying to boot from sda7, but it does not look complete. But the install in sda1 looks complete. Try reinstalling grub to boot from sda1.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda1 and want grub2 in drive sda's MBR:
#Find linux partition, change sda1 if not correct:
sudo fdisk -l
#confirm that linux is sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

#More info here
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Palm&#279; on 2011-03-21
I am getting this: "Minimal BASH-Like line editing is supported.  For the first word, TAB  lists possible command completions.  Anywhere else TAB lists the  possible completions of a device/filename."

I did as you wrote, what is wrong? How to recover grub?

---

### Post by garvinrick4 on 2011-03-21
*Oldfred will be back to help you out Palme'

Does Windows boot partition being at end of drive
instead of at sda1 have any effect on booting nowadays?

Palme' did you copy and paste oldfreds code? Try again.

---

### Post by Mr. ViC on 2011-03-21
Take a look at my topic, I had a recent problem just like yours and was able to work it out.

```
http://ubuntuforums.org/showthread.php?t=1707472
```

:)

---

### Post by Palm&#279; on 2011-03-21
Well, I did exactly as oldfred wrote.



> 
 	Code:
 	[http://ubuntuforums.org/showthread.php?t=1707472](http://ubuntuforums.org/showthread.php?t=1707472) 


I don't know what to write in (hdx,x) part:
configfile (hd0,6)/boot/grub/grub.cfg

---

### Post by garvinrick4 on 2011-03-21
Being that sda1 is install you can chroot into install with live cd (install cd using Try ubuntu) and install grub2 in mbr. Copy and paste: (Lots of ways to do it this is just one I like when things are not going well.)

                          ```
sudo mount /dev/sda1 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
 

 
``````
grub-install /dev/sda
``````
update-grub
``````
exit
```                                 ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
``````
sudo shutdown -r now
```

---

### Post by Palm&#279; on 2011-03-22
> **garvinrick4 said:**
> Being that sda1 is install you can chroot into install with live cd (install cd using Try ubuntu) and install grub2 in mbr. Copy and paste: (Lots of ways to do it this is just one I like when things are not going well.)

                          ```
sudo mount /dev/sda1 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
 

 
```

First code does not work right, i am getting the error.
```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
mount: mount point /mnt/dev does not exist

```

---

### Post by garvinrick4 on 2011-03-22
sda1 does not have a file system then. Going by previous posts that sda1 is your install.
What does making the first line of code sda7 do for you.
                          ```
sudo mount /dev/sda7 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
 

 
```Now continue on with other lines of code.
Even though it does not look like you have a full install in sda1 or sda7.
We can go out and fetch a new grub2 from repo's and install in sda7 if you choose to try.

---

### Post by Palm&#279; on 2011-03-22
> **garvinrick4 said:**
> 

Everything worked, grub loads normaly except that I can't choose to log in Ubuntu, I can only load windows. Well, I played too much. :/ I will add boot info script later.

---

### Post by Palm&#279; on 2011-03-23
New boot info script results.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   159,999,999   159,997,952  83 Linux
/dev/sda2         160,002,046   567,998,463   407,996,418   5 Extended
/dev/sda5         160,002,048   459,999,231   299,997,184  83 Linux
/dev/sda6         460,001,280   467,998,719     7,997,440  82 Linux swap / Solaris
/dev/sda7         468,000,768   567,998,463    99,997,696  83 Linux
/dev/sda3    *    567,998,464   568,203,263       204,800   7 HPFS/NTFS
/dev/sda4         568,203,264   735,975,423   167,772,160   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4b3eaf4f-a1bb-4850-99ba-6d907f39ea3b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        7C109A2B1099ED00                       ntfs       System Reserved               
/dev/sda4        F0A8C39FA8C36328                       ntfs                                     
/dev/sda5        6c9f1099-25a1-44d3-88d6-8ccfa14a3952   ext4                                     
/dev/sda6        49a25c46-1931-4d79-a6fb-0b4440283aa1   swap                                     
/dev/sda7        9babc43d-f5d9-457c-a713-e9cbabd558be   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sda1/grub/grub.cfg: =============================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 9babc43d-f5d9-457c-a713-e9cbabd558be
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 4b3eaf4f-a1bb-4850-99ba-6d907f39ea3b
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4b3eaf4f-a1bb-4850-99ba-6d907f39ea3b
    linux    /vmlinuz-2.6.35-27-generic root=UUID=9babc43d-f5d9-457c-a713-e9cbabd558be ro   quiet splash
    initrd    /initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4b3eaf4f-a1bb-4850-99ba-6d907f39ea3b
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /vmlinuz-2.6.35-27-generic root=UUID=9babc43d-f5d9-457c-a713-e9cbabd558be ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4b3eaf4f-a1bb-4850-99ba-6d907f39ea3b
    linux    /vmlinuz-2.6.35-22-generic root=UUID=9babc43d-f5d9-457c-a713-e9cbabd558be ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4b3eaf4f-a1bb-4850-99ba-6d907f39ea3b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=9babc43d-f5d9-457c-a713-e9cbabd558be ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4b3eaf4f-a1bb-4850-99ba-6d907f39ea3b
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4b3eaf4f-a1bb-4850-99ba-6d907f39ea3b
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=================== sda1: Location of files loaded by Grub: ===================


  15.1GB: boot/grub/core.img
  62.4GB: grub/core.img
  62.4GB: grub/grub.cfg
    .2GB: initrd.img-2.6.35-22-generic
    .2GB: initrd.img-2.6.35-27-generic
    .1GB: vmlinuz-2.6.35-22-generic
    .2GB: vmlinuz-2.6.35-27-generic

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 9babc43d-f5d9-457c-a713-e9cbabd558be
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 9babc43d-f5d9-457c-a713-e9cbabd558be
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 7c109a2b1099ed00
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=9babc43d-f5d9-457c-a713-e9cbabd558be /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext4    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=6c9f1099-25a1-44d3-88d6-8ccfa14a3952 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=49a25c46-1931-4d79-a6fb-0b4440283aa1 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 282.8GB: boot/grub/core.img
 282.8GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  83 3e 00 00 00 00 ff ff  ff ff 00 00 00 00 00 03  |.>..............|
00000010  c1 3f 18 eb 1a 42 00 ac  c3 bf f9 66 07 3f 0a 27  |.?...B.....f.?.'|
00000020  31 3f 8c 8c fb 3e 14 54  06 3e e0 d2 d0 3e 68 55  |1?...>.T.>...>hU|
00000030  29 3f ac 68 15 3f 00 00  00 00 ff ff ff ff 00 00  |)?.h.?..........|
00000040  00 00 00 be 78 3f 80 8b  18 42 00 80 64 bf d5 f5  |....x?...B..d...|
00000050  11 3f dd 0e 36 3f a2 95  d2 3e e8 2d 17 3e 70 b0  |.?..6?...>.-.>p.|
00000060  d7 3e 42 54 28 3f 14 51  16 3f 00 00 00 00 ff ff  |.>BT(?.Q.?......|
00000070  ff ff 00 00 00 00 80 3a  1e 40 f0 b5 0f 42 00 70  |.......:.@...B.p|
00000080  c3 c0 84 b3 40 3f b1 bf  66 be 5b 59 1e bf 41 1c  |....@?..f.[Y..A.|
00000090  4d 3d a4 02 e1 3e 58 e5  ae 3e 91 cf 52 3f 00 00  |M=...>X..>..R?..|
000000a0  00 00 ff ff ff ff 00 00  00 00 80 7d 0d 40 b0 1c  |...........}.@..|
000000b0  0a 42 00 a3 9d c0 f6 04  54 3f 00 c5 d5 be e8 68  |.B......T?.....h|
000000c0  bf be 7e ec 71 3d 7e eb  f0 3e d0 4d ac 3e e2 d7  |..~.q=~..>.M.>..|
000000d0  54 3f 00 00 00 00 ff ff  ff ff 00 00 00 00 80 7d  |T?.............}|
000000e0  0d 40 b0 1c 0a 42 00 a3  9d c0 f6 04 54 3f 00 c5  |.@...B......T?..|
000000f0  d5 be e8 68 bf be 7e ec  71 3d 7e eb f0 3e cb 93  |...h..~.q=~..>..|
00000100  4e 3f 72 84 4f 3f 00 00  00 00 ff ff ff ff 00 00  |N?r.O?..........|
00000110  00 00 80 3a 1e 40 f0 b5  0f 42 00 70 c3 c0 84 b3  |...:.@...B.p....|
00000120  40 3f b1 bf 66 be 5b 59  1e bf 41 1c 4d 3d a4 02  |@?..f.[Y..A.M=..|
00000130  e1 3e 6a 74 4c 3f 0a c7  51 3f 00 00 00 00 ff ff  |.>jtL?..Q?......|
00000140  ff ff 00 00 00 00 80 18  0d 40 70 84 08 42 00 40  |.........@p..B.@|
00000150  5a c0 a5 ad 66 3f 84 06  dd be b7 28 28 bd c7 1e  |Z...f?.....((...|
00000160  a5 3d b4 e3 f9 3e 83 f3  4e 3f e0 e3 4c 3f 00 00  |.=...>..N?..L?..|
00000170  00 00 ff ff ff ff 00 00  00 00 00 13 e1 3f 48 cf  |.............?H.|
00000180  05 42 00 48 0c c0 b0 f2  66 3f 65 81 c5 be 8d dd  |.B.H....f?e.....|
00000190  45 3e df b4 ea 3d 60 35  01 3f e9 d9 4f 3f 8c b5  |E>...=`5.?..O?..|
000001a0  4a 3f 00 00 00 00 ff ff  ff ff 00 00 00 00 00 1f  |J?..............|
000001b0  a0 3f f0 13 06 42 00 78  a0 bf f8 f2 32 3f 00 fe  |.?...B.x....2?..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 98 e1 11 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 98  e1 11 00 10 7a 00 00 00  |............z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by oldfred on 2011-03-23
What happens when you try Ubuntu?  Have you tried recovery mode?

Often video issues or other system settings cause  problems.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

