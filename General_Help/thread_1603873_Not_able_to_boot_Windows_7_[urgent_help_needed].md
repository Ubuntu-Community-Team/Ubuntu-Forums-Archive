---
title: "Not able to boot Windows 7 [urgent help needed]"
date: 2010-10-23
forum: General Help
---

### Post by sumtata on 2010-10-23
I was using windows 7. Today I installed ubuntu 10.10. After installing the normal boot option is now replaced with grub boot menu.
I am able to boot ubuntu successfully using that but I am not able to go to windows 7.

In the menu it's showing:
windows 7(loader) /dev/sda1 whereas my windows is installed in /dev/sdb1.
Also it's showing another entry for windows xp whereas I don't have windows xp at all.

Please help me. It's urgent. My CD drive is also not working therefore I am not able to run the windows 7 rescue utility. Also not sure whether it'll work or not...:(:(:(:(

---

### Post by searchfgold6789 on 2010-10-23
Welcome to the forums.
(My recommendations start here)

Boot into Ubuntu and run ```
sudo update-grub
```from the terminal (under Accessories). If that don't work post back and we'll help you.

---

### Post by compiz addict on 2010-10-23
Another thing you can try is installing Ubuntu within Windows. If you can find a way to repair the Windows loader and get rid of Linux, than boot to Windows 7 and put in the CD and install it that way.

Why does this happen? Well, Windows likes to be on top, and Linux isn't letting it. It's a known issue.

---

### Post by compiz addict on 2010-10-23
Oh, didn't read the thing about the broken CD drive. Can you boot to a USB?

---

### Post by sumtata on 2010-10-23
Already done.
Below is the output:
------------------
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Microsoft Windows XP Professional on /dev/sdb1
done
-----------------

The problem is that my windows 7 is in /dev/sdb1 and there is no Windows XP professional

---

### Post by Quackers on 2010-10-23
What happens when you try to boot from Windows 7 (loader) or Windows XP Professional?

---

### Post by sumtata on 2010-10-23
> **compiz addict said:**
> Oh, didn't read the thing about the broken CD drive. Can you boot to a USB?


I don't have the iso image for windows 7 to write into USB.
I found a windows recovery iso file but couldn't write it to USB so as to make it bootable.

The startupdisk creator utility couldn't recognize the windows recovery iso file.

---

### Post by sumtata on 2010-10-23
> **Quackers said:**
> What happens when you try to boot from Windows 7 (loader) or Windows XP Professional?

When I click on Windows 7, it goes to a black screen and then in 1 sec comes back to the grub menu...

When I click on WIndows XP, it goes to a black screen and remains there forever till I hard restart the PC.

---

### Post by compiz addict on 2010-10-23
Startup disk creator? Use K3B (you'll need to install it from the Ubuntu Software Center)

---

### Post by Quackers on 2010-10-23
Please go to the site below and download the script to your desktop. Then run the script using the command given on that site. This will produce a Results.txt file on your desktop. Copy the contents of that file and paste it between CODE tags in your next post. (For code tags click on New Reply then on the # symbol in the toolbar then paste in between them).

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by perspectoff on 2010-10-23
> **compiz addict said:**
> Another thing you can try is installing Ubuntu within Windows. If you can find a way to repair the Windows loader and get rid of Linux, than boot to Windows 7 and put in the CD and install it that way.

Why does this happen? Well, Windows likes to be on top, and Linux isn't letting it. It's a known issue.

That's not very accurate. 

Nothing has happened to the Windows bootloader. All that has happened is that the Master Boot Record was overwritten by Ubuntu to refer to Grub 2 as the Master bootloader (whereas when windows was the only OS, the Windows bootloader was the Master bootloader). There can only be one Master bootloader per computer. The Master bootloader then chainloads any secondary bootloaders. So when Grub2 is the Master bootloader, it chainloads the Windows bootloader. 

(In fact, getting rid of Ubuntu and trying to "repair" the Windows bootloader is a long way round. What that statement really means is to reset the Master Boot Record so that it refers to the Windows bootloader as the Master bootloader, again. In the long run, however, that is not the solution for someone who wants a dual-boot or multi-boot system.)

All that has happened for this user is that the chainloading from Grub2 to the Windows bootloader is not working, for some reason. 

It is easier to fix the Grub2 bootloader, and the first step is, indeed update-grub, which scans the OS's on the hard drive(s) again and tries to recognize the Windows bootloader again (so that it can be chainloaded properly).

For me, Grub2 has been odd, however, about not recognizing OS's on sdb, as well, (especially when I add a second hard drive after everything has been set up, even after update-grub).

I think there is a way of manually tweaking the Grub2 settings for chainloading (but I'm not sure what it is).

It's one of the reasons I still use Grub Legacy in a boot partition as the Master Bootloader (and use it to chainload the secondary bootloaders, such as the Windows bootloader and the Grub2 bootloader).

---

### Post by sumtata on 2010-10-23
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 201760216 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 469. But according to the info from fdisk, 
                       sda5 starts at sector 81915904.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /Windows/System32/winload.exe /ntldr 
                       /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 32.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,902   312,560,639   230,644,738   f W95 Ext d (LBA)
/dev/sda5          81,915,904   184,315,903   102,400,000   7 HPFS/NTFS
/dev/sda6         245,746,368   312,560,639    66,814,272   7 HPFS/NTFS
/dev/sda7         184,317,952   213,612,543    29,294,592  83 Linux
/dev/sda8         213,614,592   240,955,391    27,340,800  83 Linux
/dev/sda9         240,957,440   245,743,615     4,786,176  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,140,159    78,140,097   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 515 MB, 515899392 bytes
16 heads, 32 sectors/track, 1968 cylinders, total 1007616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     1,007,615     1,007,584   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DA18B77518B74EEF                       ntfs       MUSIC                         
/dev/sda2: PTTYPE="dos" 
/dev/sda5        9EAAC60AAAC5DEC1                       ntfs       MOVIES                        
/dev/sda6        2CB08FF5B08FC434                       ntfs       DATA2                         
/dev/sda7        5ce96b4e-8d7b-445e-a9cc-b68fb97cc139   ext4                                     
/dev/sda8        b5cc2ba5-1228-4f54-b008-55ebc5b875d0   ext4                                     
/dev/sda9        6524a156-58b3-4e81-9666-f1bd38a822fe   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        EA44767D44764BF7                       ntfs       WINDOWS                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        83D0-8C1C                              vfat       New Volume                    
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda8        /home                    ext4       (rw,commit=0)
/dev/sda5        /media/MOVIES            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/New Volume        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 5ce96b4e-8d7b-445e-a9cc-b68fb97cc139
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 5ce96b4e-8d7b-445e-a9cc-b68fb97cc139
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 5ce96b4e-8d7b-445e-a9cc-b68fb97cc139
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5ce96b4e-8d7b-445e-a9cc-b68fb97cc139 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 5ce96b4e-8d7b-445e-a9cc-b68fb97cc139
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5ce96b4e-8d7b-445e-a9cc-b68fb97cc139 ro single 
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 5ce96b4e-8d7b-445e-a9cc-b68fb97cc139
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 5ce96b4e-8d7b-445e-a9cc-b68fb97cc139
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set da18b77518b74eef
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set ea44767d44764bf7
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
UUID=5ce96b4e-8d7b-445e-a9cc-b68fb97cc139 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=b5cc2ba5-1228-4f54-b008-55ebc5b875d0 /home           ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=6524a156-58b3-4e81-9666-f1bd38a822fe none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 103.3GB: boot/grub/core.img
  97.3GB: boot/grub/grub.cfg
  97.1GB: boot/initrd.img-2.6.35-22-generic
 103.2GB: boot/vmlinuz-2.6.35-22-generic
  97.1GB: initrd.img
 103.2GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  54 4c 4f 53 53 20 65 72  72 6f 72 0d 0a 00 00 00  |TLOSS error.....|
00000010  53 49 4e 47 20 65 72 72  6f 72 0d 0a 00 00 00 00  |SING error......|
00000020  44 4f 4d 41 49 4e 20 65  72 72 6f 72 0d 0a 00 00  |DOMAIN error....|
00000030  52 36 30 32 38 0d 0a 2d  20 75 6e 61 62 6c 65 20  |R6028..- unable |
00000040  74 6f 20 69 6e 69 74 69  61 6c 69 7a 65 20 68 65  |to initialize he|
00000050  61 70 0d 0a 00 00 00 00  52 36 30 32 37 0d 0a 2d  |ap......R6027..-|
00000060  20 6e 6f 74 20 65 6e 6f  75 67 68 20 73 70 61 63  | not enough spac|
00000070  65 20 66 6f 72 20 6c 6f  77 69 6f 20 69 6e 69 74  |e for lowio init|
00000080  69 61 6c 69 7a 61 74 69  6f 6e 0d 0a 00 00 00 00  |ialization......|
00000090  52 36 30 32 36 0d 0a 2d  20 6e 6f 74 20 65 6e 6f  |R6026..- not eno|
000000a0  75 67 68 20 73 70 61 63  65 20 66 6f 72 20 73 74  |ugh space for st|
000000b0  64 69 6f 20 69 6e 69 74  69 61 6c 69 7a 61 74 69  |dio initializati|
000000c0  6f 6e 0d 0a 00 00 00 00  52 36 30 32 35 0d 0a 2d  |on......R6025..-|
000000d0  20 70 75 72 65 20 76 69  72 74 75 61 6c 20 66 75  | pure virtual fu|
000000e0  6e 63 74 69 6f 6e 20 63  61 6c 6c 0d 0a 00 00 00  |nction call.....|
000000f0  52 36 30 32 34 0d 0a 2d  20 6e 6f 74 20 65 6e 6f  |R6024..- not eno|
00000100  75 67 68 20 73 70 61 63  65 20 66 6f 72 20 5f 6f  |ugh space for _o|
00000110  6e 65 78 69 74 2f 61 74  65 78 69 74 20 74 61 62  |nexit/atexit tab|
00000120  6c 65 0d 0a 00 00 00 00  52 36 30 31 39 0d 0a 2d  |le......R6019..-|
00000130  20 75 6e 61 62 6c 65 20  74 6f 20 6f 70 65 6e 20  | unable to open |
00000140  63 6f 6e 73 6f 6c 65 20  64 65 76 69 63 65 0d 0a  |console device..|
00000150  00 00 00 00 52 36 30 31  38 0d 0a 2d 20 75 6e 65  |....R6018..- une|
00000160  78 70 65 63 74 65 64 20  68 65 61 70 20 65 72 72  |xpected heap err|
00000170  6f 72 0d 0a 00 00 00 00  52 36 30 31 37 0d 0a 2d  |or......R6017..-|
00000180  20 75 6e 65 78 70 65 63  74 65 64 20 6d 75 6c 74  | unexpected mult|
00000190  69 74 68 72 65 61 64 20  6c 6f 63 6b 20 65 72 72  |ithread lock err|
000001a0  6f 72 0d 0a 00 00 00 00  52 36 30 31 36 0d 0a 2d  |or......R6016..-|
000001b0  20 6e 6f 74 20 65 6e 6f  75 67 68 20 73 70 00 fe  | not enough sp..|
000001c0  ff ff 07 fe ff ff 02 00  00 00 00 80 1a 06 00 fe  |................|
000001d0  ff ff 05 fe ff ff 83 da  c3 09 7f 81 fb 03 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by sumtata on 2010-10-23
> **perspectoff said:**
> That's not very accurate. 

Nothing has happened to the Windows bootloader. All that has happened is that the Master Boot Record was overwritten by Ubuntu to refer to Grub 2 as the Master bootloader (whereas when windows was the only OS, the Windows bootloader was the Master bootloader). There can only be one Master bootloader per computer. The Master bootloader then chainloads any secondary bootloaders. So when Grub2 is the Master bootloader, it chainloads the Windows bootloader. 

(In fact, getting rid of Ubuntu and trying to "repair" the Windows bootloader is a long way round. What that statement really means is to reset the Master Boot Record so that it refers to the Windows bootloader as the Master bootloader, again. In the long run, however, that is not the solution for someone who wants a dual-boot or multi-boot system.)

All that has happened for this user is that the chainloading from Grub2 to the Windows bootloader is not working, for some reason. 

It is easier to fix the Grub2 bootloader, and the first step is, indeed update-grub, which scans the OS's on the hard drive(s) again and tries to recognize the Windows bootloader again (so that it can be chainloaded properly).

For me, Grub2 has been odd, however, about not recognizing OS's on sdb, as well, (especially when I add a second hard drive after everything has been set up, even after update-grub).

I think there is a way of manually tweaking the Grub2 settings for chainloading (but I'm not sure what it is).

It's one of the reasons I still use Grub Legacy in a boot partition as the Master Bootloader (and use it to chainload the secondary bootloaders, such as the Windows bootloader and the Grub2 bootloader).

Was any solution suggested above?

---

### Post by perspectoff on 2010-10-23
> **sumtata said:**
> 
windows 7(loader) /dev/sda1 whereas my windows is installed in /dev/sdb1.
Also it's showing another entry for windows xp whereas I don't have windows xp at all.


The second entry (Windows XP) is usually a Recovery partition and generally will load a Recovery setup for windows.

Clearly there was a problem recognizing your Windows partition.

[http://grub.enbug.org/ChainLoadWindows?highlight=%28chainload%29](http://grub.enbug.org/ChainLoadWindows?highlight=%28chainload%29)

gives a solution that can be used.

It involves finding the UUID of the Windows partition 

 sudo blkid

and then specifying that in Grub 2.

If you think Grub2 is easy to use and configure, just look at the loooong help page at

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Quackers on 2010-10-23
At a guess I would suspect that you have installed grub to sda1 instead of sda.
In the guide you were following, it says you need to mount your Ubuntu system (while running the live cd environment) which appears to be sda7 and then install grub to sda (not sda1 or sda7). As Ubuntu will not now boot you will need to follow the chroot method detailed in the same guide. This should get Ubuntu booting again. We can have a go at Windows later.

---

### Post by perspectoff on 2010-10-23
> **Quackers said:**
> At a guess I would suspect that you have installed grub to sda1 instead of sda.
In the guide you were following, it says you need to mount your Ubuntu system (while running the live cd environment) which appears to be sda7 and then install grub to sda (not sda1 or sda7). As Ubuntu will not now boot you will need to follow the chroot method detailed in the same guide. This should get Ubuntu booting again. We can have a go at Windows later.

Correct. Installing to /dev/sda is equivalent to installing Grub 2 to the Master Boot Record on sda.

This ought to fix all problems.

---

### Post by sumtata on 2010-10-23
For me, the file [I]/etc/grub.d/40_custom doesn't contain any windows entries.

Below are the contents-

File: 40_custom
[/I]```

[I]#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
[/I]
```

File:41_custom
```

#!/bin/sh
cat <<EOF
if [ -f  \$prefix/custom.cfg ]; then
  source \$prefix/custom.cfg;
fi
EOF

```

Also I am not able to edit those files either. Tried chmod...

---

### Post by Quackers on 2010-10-23
We need to get things booting up before worrying about the menu.
Once Ubuntu is booting we can concern ourselves with Windows (which does look a bit messed up at the moment). But to fix Windows it is likely that you will need a bootable Windows cd or usb.

---

### Post by sumtata on 2010-10-23
First of all to clear things....

UBUNTU is booting fine...

---

### Post by Quackers on 2010-10-23
Right then, just do what you did before (re-installing grub) but to sda this time (if you didn't last time).

---

### Post by sumtata on 2010-10-23
> **Quackers said:**
> Right then, just do what you did before (re-installing grub) but to sda this time (if you didn't last time).

Do you want me to reinstall ubuntu and select sda this time.

But how is it gonna restore the Windows 7 MBR? As I understand ubuntu has already messed it up.

Correct if I am wrong.

---

### Post by Quackers on 2010-10-23
You don't need to re-install Ubuntu - just grub to sda.
The Windows 7 mbr is over-written by grub. That is fixed by using a Windows repair disc (or usb). At the moment you have somehow got Windows XP boot files in Windows 7's system. Maybe some repair you have run, perhaps? This is why sdb1 reports Windows XP and not Windows 7.

---

### Post by oldfred on 2010-10-23
Windows combines boot loaders into one. It also likes to install a separate boot partition that is hidden, but then most users do not know it exists and install some else there and corrupt it.

Your win7 boots thru sda1 as the boot partition as it has the win7 bootmgr & BCD. But you have installed grub2 to its boot sector corrupting the win install. You just need to fix that.

    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector[/COLOR] of sda1 and 
                       looks at sector 201760216 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Did you install win7 over XP as you win7 main partition sdb1 has boot XP boot files (red) and the win7 file (Blue)
    Boot files/dirs:   [COLOR=Red]/boot.ini[/COLOR] [COLOR=SeaGreen][COLOR=Blue]/Windows/System32/winload.exe[/COLOR] [/COLOR][COLOR=Red]/ntldr 
                       /NTDETECT.COM[/COLOR]

---

### Post by sumtata on 2010-10-23
Now I am a bit confused.

First:
I checked in Synaptic, grub or grub2 are not installed. Instead grub-pc is installed. I marked it for reinstall and applied. But it didn't ask me where I would like to install it.

How to reinstall grub in sda.

Next is my priority now is to recover and boot Windows when there is no CD/DVD drive.

If someone can guide me through the process of using a USB to achieve the same, it would be a gr8 help..

---

### Post by sumtata on 2010-10-23
> **oldfred said:**
> Windows combines boot loaders into one. It also likes to install a separate boot partition that is hidden, but then most users do not know it exists and install some else there and corrupt it.

Your win7 boots thru sda1 as the boot partition as it has the win7 bootmgr & BCD. But you have installed grub2 to its boot sector corrupting the win install. You just need to fix that.

    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector[/COLOR] of sda1 and 
                       looks at sector 201760216 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Did you install win7 over XP as you win7 main partition sdb1 has boot XP boot files (red) and the win7 file (Blue)
    Boot files/dirs:   [COLOR=Red]/boot.ini[/COLOR] [COLOR=SeaGreen][COLOR=Blue]/Windows/System32/winload.exe[/COLOR] [/COLOR][COLOR=Red]/ntldr 
                       /NTDETECT.COM[/COLOR]


I already checked "testdisk".
It shows that my bootsector and backup boot sector are identical. So the BackupBS option doesn't come at all..

---

### Post by Quackers on 2010-10-23
Lots of info/methods in this thread

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Try googling for bootable usb - I am not familiar with the process.

---

### Post by perspectoff on 2010-10-23
grub-pc is GRUB2.

Grub doesn't combine bootloaders into one. Grub merely chainloads the Windows bootloader (which resides in either the main Windows partition or in a special windows boot partition.) 

There is only one MBR per computer (well, technically, per hard drive).

There isn't a separate MBR for Windows and Ubuntu.

You merely need to allow Grub 2 (grub-pc) to be "installed into" /dev/sda from the Ubuntu installation.

What this really does is to adjust the Master Boot Record registers on the hard drive to recognize Grub2 as the Master Boot Loader.

Grub2 is actually stored in the Ubuntu partition. The Master boot Record registers just store information about where to find Grub2 and some basic information about Grub 2.

What is confusing about the Ubuntu installer is that when you choose to install Grub2 into /dev/sda, it actually installs Grub2 (grub-pc) into the Ubuntu partition (which is often /dev/sda4 or /dev/sda6, for example) and then changes the MBR to refer to Grub2 there. 

It is actually the terminology of the Ubuntu installer that is misleading.

While it is possible to reset the MBR (using the Windows Recovery options on the windows LiveCD) so that the registers then record the location of the Windows bootloader (stored either in the Windows partition or a special windows boot partition, depending on the version of Windows you are using) as the Master Boot loader, it shouldn't be necessary.

However, if you accidentally wrote Grub2 into /dev/sda1 and /dev/sda1 is where the Windows bootloader was located, then, yes, you have corrupted the Windows ability to boot. You will indeed need to repair that with the Windows Recovery disk. Grub should never be written into a Windows NTFS partition.

You probably should do a full repair using the Windows Recovery disk. Once Windows is booting again, you can revisit the Ubuntu installation and this time install Grub to /dev/sda instead of /dev/sda1.

---

### Post by Sef on 2010-10-23
> In the menu it's showing:
windows 7(loader) /dev/sda1 whereas my windows is installed in /dev/sdb1.

Windows needs to be on the first primary partition (sda1.) That is why it is looking for it there.

---

### Post by oldfred on 2010-10-23
Testdisk also has a function to rebuild boot sector.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)


I tried installing the Win7 repair from neosmart to a USB flash drive, but could not get it to work directly from Ubuntu. And the issue was the boot sector. I may try again. I was able to write it to a CD and use it to create a bootable USB. I then converted that CD to boot with grub2 and it saw the boot sector and booted the repair CD from the USB.

---

