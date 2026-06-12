---
title: "Grub2 doesn't boot either OS"
date: 2010-06-14
forum: General Help
---

### Post by Quikj on 2010-06-14
Hello everyone,

I'm new to Ubuntu and recently installed it alongside Win7 a few weeks ago. For awhile it was working fine, with no problems at all. I was extremely impressed with the OS. However, a couple of days ago, I turned my computer on and the grub2 wouldn't load at all. I'm able to boot into Linux using Super Grub Disc, but I can only repair grub temporarily, using various commands found on the web. When I shut down or restart windows and attempt to reboot, the startup screen cycles continuously, without a hint of the Grub interface at all. 

Any help on the matter is much appreciated, I'd love to keep using ubuntu, but these problems are worrying to say the least.

---

### Post by john newbuntu on 2010-06-14
Just for the forum members including me to get a complete picture, follow the directions on this site, run the boot_info_script.sh and post the output file RESULTS.TXT withing code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Quikj on 2010-06-14
> **john newbuntu said:**
> Just for the forum members including me to get a complete picture, follow the directions on this site, run the boot_info_script.sh and post the output file RESULTS.TXT withing code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Thanks for the quick reply! Here you go:
```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   429,819,413   399,017,494   7 HPFS/NTFS
/dev/sda4         429,819,902   488,396,799    58,576,898   5 Extended
/dev/sda5         429,819,904   485,887,999    56,068,096  83 Linux
/dev/sda6         485,890,048   488,396,799     2,506,752  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        AE7CFBCD7CFB8E79                       ntfs       RECOVERY                      
/dev/sda3        4C14EEA414EE8FEE                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        54784ab3-a652-4951-afe9-87dac117c292   ext4                                     
/dev/sda6        aa7d57f4-e154-45ba-bc7e-9dbf8b9e1e46   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/CDROM             iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 54784ab3-a652-4951-afe9-87dac117c292
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 54784ab3-a652-4951-afe9-87dac117c292
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54784ab3-a652-4951-afe9-87dac117c292
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=54784ab3-a652-4951-afe9-87dac117c292 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54784ab3-a652-4951-afe9-87dac117c292
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=54784ab3-a652-4951-afe9-87dac117c292 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54784ab3-a652-4951-afe9-87dac117c292
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=54784ab3-a652-4951-afe9-87dac117c292 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54784ab3-a652-4951-afe9-87dac117c292
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=54784ab3-a652-4951-afe9-87dac117c292 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54784ab3-a652-4951-afe9-87dac117c292
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54784ab3-a652-4951-afe9-87dac117c292
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set ae7cfbcd7cfb8e79
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=54784ab3-a652-4951-afe9-87dac117c292 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=aa7d57f4-e154-45ba-bc7e-9dbf8b9e1e46 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 245.9GB: boot/grub/core.img
 229.7GB: boot/grub/grub.cfg
 246.1GB: boot/initrd.img-2.6.32-21-generic
 246.1GB: boot/initrd.img-2.6.32-22-generic
 245.9GB: boot/vmlinuz-2.6.32-21-generic
 231.6GB: boot/vmlinuz-2.6.32-22-generic
 246.1GB: initrd.img
 246.1GB: initrd.img.old
 231.6GB: vmlinuz
 245.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  90 eb 07 c0 01 0a 0a 00  80 00 fa 33 c0 8e d0 bc  |...........3....|
00000010  00 7c fb 50 53 51 52 1e  06 cd 12 eb 07 88 16 00  |.|.PSQR.........|
00000020  08 b4 08 62 c1 e0 06 8b  d0 2e c5 1e bc 00 81 7f  |...b............|
00000030  03 52 50 75 0b 80 7f 05  4c 75 05 b8 06 4a cd 2f  |.RPu....Lu...J./|
00000040  8b ca 0e 1f 55 56 57 8b  f1 4e 2b 36 03 7c 83 e6  |....UVW..N+6.|..|
00000050  c0 89 36 4b 7d 2b ce c1  e1 03 8e c6 33 ff 33 c0  |..6K}+......3.3.|
00000060  fc f3 ab 06 8e c0 b4 08  8b 16 08 7c 52 cd 13 83  |...........|R...|
00000070  e1 3f 8a c1 f6 e6 03 c1  8b f8 bb 00 7e 88 0e 4d  |.?..........~..M|
00000080  7d 8b 0e 06 7c 5a e8 4b  00 33 c0 07 8a 07 68 00  |}...|Z.K.3....h.|
00000090  08 07 8d 77 08 50 5b 4b  53 52 c1 e3 02 8b 00 8b  |...w.P[KSR......|
000000a0  50 02 3b d7 73 3e f7 f7  92 8b ca f6 36 4d 7d c0  |P.;.s>......6M}.|
000000b0  e5 06 fe c4 0a ec 86 cd  5a 8a f0 c1 e3 07 74 64  |........Z.....td|
000000c0  8a 26 05 7c fe cc d0 e4  38 e7 75 05 ff 36 4b 7d  |.&.|....8.u..6K}|
000000d0  07 68 96 7c b0 05 50 b8  01 02 cd 13 58 72 01 c3  |.h.|..P.....Xr..|
000000e0  fe c8 75 f2 0e 07 0e 1f  fc be 00 7c 0e 58 c1 e0  |..u........|.X..|
000000f0  04 2b f0 56 8b de 8b fe  81 c7 00 02 b9 ae 01 f3  |.+.V............|
00000100  a4 e9 00 02 83 c6 10 8b  14 0a d2 74 f7 79 05 8b  |...........t.y..|
00000110  4c 02 eb c0 be 63 7f ac  0a c0 74 fe 32 ff b4 0e  |L....c....t.2...|
00000120  cd 10 eb f3 58 a1 03 7c  8b 36 06 7c 8b 3e 08 7c  |....X..|.6.|.>.||
00000130  8c c5 83 c5 20 8e dd 66  81 3f fe fd ce ef 75 a4  |.... ..f.?....u.|
00000140  89 6f 08 ff 5f 06 72 9c  ea 04 02 49 6e 76 61 6c  |.o.._.r....Inval|
00000150  69 64 20 70 61 72 74 69  74 69 6f 6e 20 74 61 62  |id partition tab|
00000160  6c 65 00 45 72 72 6f 72  20 6c 6f 61 64 69 6e 67  |le.Error loading|
00000170  20 6f 70 65 72 61 74 69  6e 67 20 73 79 73 74 65  | operating syste|
00000180  6d 00 4d 69 73 73 69 6e  67 20 6f 70 65 72 61 74  |m.Missing operat|
00000190  69 6e 67 20 73 79 73 74  65 6d 00 00 00 52 65 61  |ing system...Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  b5 32 30 40 00 00 80 01  |...<.u...20@....|
000001c0  01 00 de fe 3f 04 3f 00  00 00 86 39 01 00 00 19  |....?.?....9....|
000001d0  15 05 07 fe ff ff 00 40  01 00 00 c0 d4 01 00 fe  |.......@........|
000001e0  ff ff 07 fe ff ff 00 00  d6 01 16 86 c8 17 00 fe  |................|
000001f0  ff ff 05 fe ff ff fe 87  9e 19 02 d0 7d 03 55 aa  |............}.U.|
00000200

```

---

### Post by garvinrick4 on 2010-06-14
Put ubuntu cd in tray and boot. Pick try ubuntu. Go to gparted in System/Admin and open gparted. Right click on sda5 and go to label and name it lucid. Check green arrow up on top to apply the label of lucid. Close gparted got to Applications/accessories to teriminal open a terminal and do these one at a time, copy and paste is easiest.

```
sudo mkdir /media/lucid
``````
sudo mount /dev/sda5 /media/lucid
```                          ```
sudo grub-install --recheck --root-directory=/media/lucid [/dev/sda]("file:///media/dev/sda") 
``````
sudo umount /media/lucid
``` (not a typo)

Now take out the Cd and reboot into Ubuntu. When it boots.
do these.
```
sudo update-grub
``````
sudo grub-mkconfig
```That will put your grub back and make a new config file, yours now has know Grub installed to boot from.

---

### Post by xsandz on 2010-06-14
It seems to me that u hv installed both the OSs i.e. Windows & and Ubuntu in a sinngle HDD. Please let me know is there any other HDD attached with your system or not.

---

### Post by Quikj on 2010-06-14
Yes, I do have both OS's installed on a single hard drive

I'm currently trying the fix listed above. Will report back with results.

---

### Post by Quikj on 2010-06-14
I tried the fix listed above, but i get an error message after startup:

Error: File not found
grub rescue>

Or something like that...

---

### Post by john newbuntu on 2010-06-14
From the grub rescue prompt, type these commands one by one:

```
set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro quiet splash
initrd /initrd.img
boot
```

See if you can boot into ubuntu. If so, immediately run "sudo update-grub";

---

### Post by Quikj on 2010-06-15
The last three commands returned an unknown command message.

---

### Post by confused57 on 2010-06-15
Sounds like it may be related to this problem:
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

### Post by Quikj on 2010-06-15
Thanks, that may actually apply to me as well. Can't I just delete the Dell Utility partition?

---

### Post by wilee-nilee on 2010-06-15
> **Quikj said:**
> Thanks, that may actually apply to me as well. Can't I just delete the Dell Utility partition?

Can you boot into windows? if you can find the dell data save and delete it then we will reinstall grub with this link from a live Ubuntu cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[B]
Do not delete the dell partition!!!!![/B]

---

### Post by Quikj on 2010-06-15
I cannot boot into Windows at all. I won't delete the Dell Partition. Thanks for clearing that up. I reformatted my hard drive after Windows wouldn't boot about a month ago and didn't install Dell Data Safe, because it was one of their updates that crashed my system in the first place. Would it still be on my system?

---

### Post by wilee-nilee on 2010-06-15
> **Quikj said:**
> I cannot boot into Windows at all. I won't delete the Dell Partition. Thanks for clearing that up. I reformatted my hard drive after Windows wouldn't boot about a month ago and didn't install Dell Data Safe, because it was one of their updates that crashed my system in the first place. Would it still be on my system?

If you installed a backup of the original OEM probably we wont know without looking. You have no bootloader in the script for sda have you done any fixes since running the script? If so so run the script again so we can see exactly whats going on.

But if you can get windows to boot with supergrub look for that dell program in add remove. I'm not sure if supergrub will boot W7 without any bootloader in the MBR=sda.

Do you have a regular install or recovery dvd for W7?

---

### Post by john newbuntu on 2010-06-15
Just before you give up on booting from grub rescue prompt, do you want to give this a try.  This is directly from drs305's post (section #15)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Hopefully the first command below should list your /boot directory. If so, try these, if not, alter (hd0,5) to another partition and try it.
```
ls (hd0,5)/
search -f /vmlinuz
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
ls /boot
insmod (hd0,5)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot
```If you boot in, run "sudo update-grub"

Edit: The second command will give you the location where vmlinuz is located, which I am guessing is (hd0,5).  If not change the commands appropriately.

---

### Post by Quikj on 2010-06-15
I just downloaded and burned a Win7 Repair CD. 

Here are the results from running the script:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /media/lucid/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   429,819,413   399,017,494   7 HPFS/NTFS
/dev/sda4         429,819,902   488,396,799    58,576,898   5 Extended
/dev/sda5         429,819,904   485,887,999    56,068,096  83 Linux
/dev/sda6         485,890,048   488,396,799     2,506,752  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        AE7CFBCD7CFB8E79                       ntfs       RECOVERY                      
/dev/sda3        4C14EEA414EE8FEE                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        54784ab3-a652-4951-afe9-87dac117c292   ext4       lucid                         
/dev/sda6        aa7d57f4-e154-45ba-bc7e-9dbf8b9e1e46   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 54784ab3-a652-4951-afe9-87dac117c292
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 54784ab3-a652-4951-afe9-87dac117c292
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54784ab3-a652-4951-afe9-87dac117c292
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=54784ab3-a652-4951-afe9-87dac117c292 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54784ab3-a652-4951-afe9-87dac117c292
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=54784ab3-a652-4951-afe9-87dac117c292 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54784ab3-a652-4951-afe9-87dac117c292
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=54784ab3-a652-4951-afe9-87dac117c292 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54784ab3-a652-4951-afe9-87dac117c292
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=54784ab3-a652-4951-afe9-87dac117c292 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54784ab3-a652-4951-afe9-87dac117c292
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54784ab3-a652-4951-afe9-87dac117c292
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set ae7cfbcd7cfb8e79
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=54784ab3-a652-4951-afe9-87dac117c292 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=aa7d57f4-e154-45ba-bc7e-9dbf8b9e1e46 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 245.9GB: boot/grub/core.img
 230.2GB: boot/grub/grub.cfg
 246.1GB: boot/initrd.img-2.6.32-21-generic
 246.1GB: boot/initrd.img-2.6.32-22-generic
 245.9GB: boot/vmlinuz-2.6.32-21-generic
 231.6GB: boot/vmlinuz-2.6.32-22-generic
 246.1GB: initrd.img
 246.1GB: initrd.img.old
 231.6GB: vmlinuz
 245.9GB: vmlinuz.old
```

I'm also going to continue to try and boot using the grub rescue commands

---

### Post by Quikj on 2010-06-15
What is vmlinuz? I just entered most of the commands, with the sole exception of the second command. I got an error saying "unknown command". 

After the 'boot' command, it started to load the OS, but stopped abruptly and now I have blinking caps and scroll lights, as well as some script on the screen that I don't understand.

---

### Post by wilee-nilee on 2010-06-15
Never mind for now I need to see the script posted two posts back.

---

### Post by wilee-nilee on 2010-06-15
I think we are missing the missing ntldr part of the boot, I don't see it in the MS partitions.

Hello jon newbuntu.

---

### Post by Quikj on 2010-06-15
So how do I install the ntldr part?

---

### Post by john newbuntu on 2010-06-15
vmlinuz is a link to the current kernel.  Do you see a file called "vmlinuz" when you type this from the recovery console:
```
ls (hd0,5)/
```If not, can you find anything that starts with vmlinuz (such as vmlinuz-2.6.32-22-generic) when you run:
```
ls (hd0,5)/boot/
```If you do, then replace the lines:
```
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img

```with
```
linux /boot/vmlinuz-2.6.32-22.generic root=/dev/sda5 ro
initrd /boot/initrd.img-2.6.32-22-generic

```Replace the vmlinuz-.... and initrd..... files appropriately.

---

### Post by wilee-nilee on 2010-06-15
The only thing more I will say here is that even if you get Ubuntu to boot and run update grub, I don't think W7 is going to boot without the ntldr. I might be wrong I hope I am, but a regular comes on line within a couple of hours usually and this looks like a job for him.

---

### Post by john newbuntu on 2010-06-15
@wilee: Sorry. Feels like I am trying to ignore you.  Don't get me wrong pal.  I feel /dev/sda2 has a boot loader but the partition is missing a boot flag.  I was suggesting on marking that as the active partition (gparted or other means).  Then, once we fix grub2, a simple sudo update-grub would pick it up automatically.

Alternatively,  he could use the win7 repair cd to fix the boot sector and the MBR and then we could take care of Ubuntu.

I also noticed that the boot info script says that grub is installed on /media/lucid/boot/grub which is a bit odd.  Your thoughts?

---

### Post by wilee-nilee on 2010-06-15
> **john newbuntu said:**
> @wilee: Sorry. Feels like I am trying to ignore you.  Don't get me wrong pal.  I feel /dev/sda2 has a boot loader but the partition is missing a boot flag.  I was suggesting on marking that as the active partition (gparted or other means).  Then, once we fix grub2, a simple sudo update-grub would pick it up automatically.

Alternatively,  he could use the win7 repair cd to fix the boot sector and the MBR and then we could take care of Ubuntu.

I also noticed that the boot info script says that grub is installed on /media/lucid/boot/grub which is a bit odd.  Your thoughts?

Hold on, I am also wrong about the ntldr. You are probably correct it makes sense that the boot would be there, in sda2, sda1 I think is the dell firmware or dell extra junk. 

I just obsessed with the ntldr but after looking at another thread oldfred had looked at with W7 he said it looked okay and the boot files are the same as this one, carry on.

Edit: yeah the media /lucid/boot/grub might be a grub in the partition other then the regular grub.cfg...etc files but shouldn't theoretically cause a problem, but you never know.

---

### Post by Quikj on 2010-06-15
Thanks guys for all of your help. It's sincerely appreciated. Will report back with results once again.

---

### Post by Quikj on 2010-06-15
I see a file called initr.img vmlinuz cdrom/ and vmlinuz.old

---

### Post by Quikj on 2010-06-15
I just booted into ubuntu for the first time, using the changes as described by John newbuntu. 

First time doing this without Super grub disk in awhile.

Now running:

```
 sudo update-grub 
```

So do I reboot as usual?

---

### Post by Quikj on 2010-06-15
> **wilee-nilee said:**
> Hold on, I am also wrong about the ntldr. You are probably correct it makes sense that the boot would be there, in sda2, sda1 I think is the dell firmware or dell extra junk. 

I just obsessed with the ntldr but after looking at another thread oldfred had looked at with W7 he said it looked okay and the boot files are the same as this one, carry on.

Edit: yeah the media /lucid/boot/grub might be a grub in the partition other then the regular grub.cfg...etc files but shouldn't theoretically cause a problem, but you never know.

the media /lucid/boot/grub is the result of me trying this fix from another [site.]("http://tolearnfree.blogspot.com/2009/12/how-to-fix-grub2-on-ubuntu-910.html")

---

### Post by wilee-nilee on 2010-06-15
Yay so far;)

---

### Post by Quikj on 2010-06-15
I'm doing my happy dance in front of my machine, but I'm scared to reboot.

grub.cfg shows all of my OS's.

---

### Post by wilee-nilee on 2010-06-15
> **Quikj said:**
> the media /lucid/boot/grub is the result of me trying this fix from another [site.]("http://tolearnfree.blogspot.com/2009/12/how-to-fix-grub2-on-ubuntu-910.html")

Kind of a long way around, you can do the same thing with a live cd and two commands, can you boot into windows now?

Here is the link to those two commands.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by wilee-nilee on 2010-06-15
> **Quikj said:**
> I'm doing my happy dance in front of my machine, but I'm scared to reboot.

grub.cfg shows all of my OS's.

Boot in and look for that dell data safe, if it is there in add remove delete it and if you can't boot back into ubuntu, run the commands in the link just remember that sda2 is the boot and sda is the MBR. I'm assuming it was that, sda2 as john newbuntu suggested was the boot partition.

---

### Post by john newbuntu on 2010-06-15
I was just gonna add: Please set the active boot flag to /dev/sda2 before you try to boot windoze.

---

### Post by gwpryz on 2010-06-15
> **garvinrick4 said:**
> Put ubuntu cd in tray and boot. Pick try ubuntu. Go to gparted in System/Admin and open gparted. Right click on sda5 and go to label and name it lucid. Check green arrow up on top to apply the label of lucid. Close gparted got to Applications/accessories to teriminal open a terminal and do these one at a time, copy and paste is easiest.

```
sudo mkdir /media/lucid
``````
sudo mount /dev/sda5 /media/lucid
```                          ```
sudo grub-install --recheck --root-directory=/media/lucid [/dev/sda]("file:///media/dev/sda") 
``````
sudo umount /media/lucid
``` (not a typo)

Now take out the Cd and reboot into Ubuntu. When it boots.
do these.
```
sudo update-grub
``````
sudo grub-mkconfig
```That will put your grub back and make a new config file, yours now has know 
Grub installed to boot from.


Grub was in disarray after having swapped dual boot partitions. I have spent hours on a fix, now here it is, in the above quote. Many thanks!

---

### Post by Quikj on 2010-06-15
So I still get the grub recovery console instead of seeing the grub2 interface. It still says: "error:file not found". Obviously I can't boot into Windows. 

Oh and dev/sda2 is marked as bootable.

---

### Post by john newbuntu on 2010-06-15
My guess is that the changes that we did last time was not permanent as we did not write it to the DOS compat region.  I'd suggest continuing with the exercise using command line in the rescue mode to boot back into Ubuntu as you did before.  This time, after you boot in, run:
sudo update-grub
and
sudo grub-install /dev/sda
and
sudo grub-install --recheck /dev/sda

Also verify your grub install using the following command:
```
grub-probe -t device /boot/grub
```This should indicate /dev/sda5.

---

### Post by Quikj on 2010-06-16
I tried to run the code above and it couldn't find any grub files. It asked me if I wanted to reinstall grub and I ran:

```
sudo apt-get install grub
```

And it worked!!! I'm now typing on this forums via Windows 7. Now to delete all of the Dell crap...

---

### Post by Quikj on 2010-06-17
So, I think that windows is still erasing grub because I have to continually reinstall grub from a terminal after booting from super grub disk. 

Basically, I'm back to where I started at the beginning of this thread.

---

### Post by wilee-nilee on 2010-06-17
> **Quikj said:**
> So, I think that windows is still erasing grub because I have to continually reinstall grub from a terminal after booting from super grub disk. 

Basically, I'm back to where I started at the beginning of this thread.

First did you remove dell data safe in Windows from add remove?
Second use the grub install here.
[grub2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

From a live Ubuntu cd.

This is a good un-installer that will get the dependencies and extras as well, the pro has an 30 day free but there is a free version.
[revo](http://www.revouninstaller.com/)

---

### Post by Quikj on 2010-06-17
I didn't see any traces of the dell data safe programs, but maybe I wasn't thorough enough.

---

### Post by wilee-nilee on 2010-06-17
> **Quikj said:**
> I didn't see any traces of the dell data safe programs, but maybe I wasn't thorough enough.

I'm not sure what you mean, after removing and how you removed it, if you did, or no trace at all.

---

### Post by Quikj on 2010-06-17
I didn't see the program at all. I was thinking that maybe there are some hidden files or traces of the Dell Data Safe Utility, similar to files left on a computer after uninstalling some virus protection software.

---

### Post by wilee-nilee on 2010-06-17
> **Quikj said:**
> I didn't see the program at all. I was thinking that maybe there are some hidden files or traces of the Dell Data Safe Utility, similar to files left on a computer after uninstalling some virus protection software.

Hmm, it may be under another name or mixed in with stuff, here is a google link for your search.
[http://www.google.com/#hl=en&source=hp&q=dell+datasafe+uninstall&aq=9&aqi=g10&aql=&oq=dell+data&gs_rfai=ChlbR0ckZTKSuHoi6Men86d8KAAAAqgQFT9BKFV0&fp=f6f642595e92e50c](http://www.google.com/#hl=en&source=hp&q=dell+datasafe+uninstall&aq=9&aqi=g10&aql=&oq=dell+data&gs_rfai=ChlbR0ckZTKSuHoi6Men86d8KAAAAqgQFT9BKFV0&fp=f6f642595e92e50c)

I also wonder if all the tweaking done to get things up and running hasn't caused a problem, I would at least install grub to the boot loader=mbr with the live cd as the grub2 link I supplied suggests. You don't need to use super grub to get in, and I wonder if that method is flawed.

---

### Post by john newbuntu on 2010-06-17
Unless you figure out what program is writing/erasing the MBR, your options are:
1. Keep repeating what you have done before - (absolute nightmare).
2. Boot from an external drive such as a USB flash drive with grub installed in its MBR (painful.  but will work)
3. Create a separate boot partition for Ubuntu and install grub there.  Then you would chainload from windows on to that partition using say, bcdedit or easy BCD. (a better solution)

---

