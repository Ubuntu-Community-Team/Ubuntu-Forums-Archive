---
title: "Windows 7 does not load after repartitioning w/Ubuntu 11.10 during install"
date: 2011-10-29
forum: General Help
---

### Post by sublimestyle on 2011-10-29
after i repartitioned my disk to give more space to ubuntu when i  installed 11.10, i seemed to have lost some ciritcal files in windows 7.  Windows 7 (on /dev/sda1) loads with a black screen and blinking  underscore and Windows 7 (on /dev/sda2) boots Windows Error recovery,  then claims \Windows\system32\ntoskrnl.exe is in status 0xc000000f and  Windows failed to load because the kernel is missing, or corrupt.. 

When i booted the Windows 7 Repair disc, it detected Windows 7 on an unknown drive at 0mb and said the partition table is corrupt..

ive got a thinkpad l420 that came preloaded with windows 7 then installed earlier ubuntu versions with success, when i upgraded to 11.10 and repartitioned to give more space to ubuntu, this happened.

i can not recall if the power shut down or not during the install, and i hope nothing is lost because i have no installation CD for windows..

any ideas?

---

### Post by coffeecat on 2011-10-29
Let's get an overview of your system with the boot info script. Can you boot into Ubuntu? If you can, do so. If not, boot up with a live Ubuntu CD or USB and choose "try Ubuntu" to get to the live desktop. Go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the script (instructions are on that site) and post the contents of your RESULTS.txt file between [noparse]```
 and [/noparse]
``` tags.

---

### Post by sublimestyle on 2011-10-29
ubuntu works, heres the RESULTS.txt

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     2,459,647     2,457,600   7 NTFS / exFAT / HPFS
/dev/sda2           2,459,648   143,691,224   141,231,577   7 NTFS / exFAT / HPFS
/dev/sda3         467,914,752   488,394,751    20,480,000   7 NTFS / exFAT / HPFS
/dev/sda4         143,691,774   467,914,751   324,222,978   5 Extended
/dev/sda5         143,691,776   455,626,751   311,934,976  83 Linux
/dev/sda6         455,628,800   467,914,751    12,285,952  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        F60A5C000A5BBC75                       ntfs       SYSTEM_DRV
/dev/sda2        542C5DA52C5D8342                       ntfs       Windows7_OS
/dev/sda3        788260A782606C16                       ntfs       Lenovo_Recovery
/dev/sda5        037a3ed7-4bda-4ec9-8f31-77a5f107e5dd   ext4       
/dev/sda6        e4c6fc47-8f6c-44d3-9500-c580a903677d   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 037a3ed7-4bda-4ec9-8f31-77a5f107e5dd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 037a3ed7-4bda-4ec9-8f31-77a5f107e5dd
  set locale_dir=($root)/boot/grub/locale
  set lang=en_CA
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 037a3ed7-4bda-4ec9-8f31-77a5f107e5dd
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=037a3ed7-4bda-4ec9-8f31-77a5f107e5dd ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 037a3ed7-4bda-4ec9-8f31-77a5f107e5dd
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=037a3ed7-4bda-4ec9-8f31-77a5f107e5dd ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 037a3ed7-4bda-4ec9-8f31-77a5f107e5dd
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=037a3ed7-4bda-4ec9-8f31-77a5f107e5dd ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 037a3ed7-4bda-4ec9-8f31-77a5f107e5dd
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=037a3ed7-4bda-4ec9-8f31-77a5f107e5dd ro recovery nomodeset 
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
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 037a3ed7-4bda-4ec9-8f31-77a5f107e5dd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 037a3ed7-4bda-4ec9-8f31-77a5f107e5dd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root F60A5C000A5BBC75
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 542C5DA52C5D8342
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
# / was on /dev/sda5 during installation
UUID=037a3ed7-4bda-4ec9-8f31-77a5f107e5dd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e4c6fc47-8f6c-44d3-9500-c580a903677d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 188.662162781 = 202.574454784  boot/grub/core.img                             1
 188.662300110 = 202.574602240  boot/grub/grub.cfg                             1
 166.651996613 = 178.941218816  boot/grub/stage2                               1
  82.677738190 = 88.774545408   boot/initrd.img-2.6.38-11-generic              1
  72.558689117 = 77.909299200   boot/initrd.img-3.0.0-12-generic               3
 177.635074615 = 190.734209024  boot/vmlinuz-2.6.38-11-generic                 1
  82.299236298 = 88.368132096   boot/vmlinuz-3.0.0-12-generic                  1
  72.558689117 = 77.909299200   initrd.img                                     3
  82.677738190 = 88.774545408   initrd.img.old                                 1
  82.299236298 = 88.368132096   vmlinuz                                        1
 177.635074615 = 190.734209024  vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by coffeecat on 2011-10-29
I think there must be two problems. All your Windows boot files are there, the boot flag is set, so the errors you mention in the first paragraph probably mean that the Windows system is damaged.

The second problem, the "detected Windows 7 on an unknown drive at 0mb and said the partition table is corrupt" you get with the Windows 7 repair disc is less easily explained. I can see nothing wrong with your partition table as reported by the output of fdisk, and no reason why the Windows disc should not be able to see the boot partition on sda1 and C: partition on sda2.

Is this repair disc the CD you can create from within Windows 7, or a Lenovo disc?

In the meantime I'll get someone else to have a look as well.

---

### Post by sublimestyle on 2011-10-29
lenovo didnt send me any discs whatsoever,
its a repair disc i picked up on the internet, i cant find the link to it now.. i believe it is the same one as this [http://maximumpcguides.com/windows-7/create-a-windows-7-system-repair-disc/](http://maximumpcguides.com/windows-7/create-a-windows-7-system-repair-disc/) 
i created it with ubuntu

---

### Post by oldfred on 2011-10-29
Is repair disk same version 32bit or 64bit? 

I also do not see any issue as the files look like they are there. The boot sectors have correct start & ends but may have issues that a chkdsk or fixBoot may repair. Partition table & PBR partition boot sector have to match. Windows also repair partition with boot flag. You have boot files in both sda1 & sda2, so you might repair sda1 then move boot flag to sda2 & try to repair that.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  (have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Always best to make your own repair disk before modifying systems.

---

### Post by coffeecat on 2011-10-29
> **sublimestyle said:**
> i believe it is the same one as this [http://maximumpcguides.com/windows-7/create-a-windows-7-system-repair-disc/](http://maximumpcguides.com/windows-7/create-a-windows-7-system-repair-disc/) 
i created it with ubuntu

Interesting that they're still offering the ISO free. The usual link is this one:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

That used to be free, but now they make a charge and I *believe* that might be to do with copyright issues and Microsoft.

Whatever - I would have suggested running a chkdsk from the repair CD but since it's having difficulties, the ISO might be corrupt or you might have a bad burn. Do you have access to another Windows 7 system? If you do, you could create a fresh CD and see if you have any better luck. Having said that, I believe the recovery CD only has some basic recovery tools, such as repairing the filesystem with chkdsk and repairing the boot loader. 

I notice you still have the Lenovo recovery partition. Do you have instructions for booting into that? If the worst comes to the worst and you are able to boot into the recovery partition, you should be able to re-install Windows back to its factory condition.

---

### Post by sublimestyle on 2011-10-29
@oldfred : The repair disc is 64bit as it was a 64bit installation of W7. 
chkdsk returned no errors on /r or /f
/FixBoot completed successfully
/ScanOs identified 1 Windows installation at D:\A\Windows
/RebuildBcd identified the same installation and asked to add it to the boot list, i pressed Y. completed successfully

@coffeecat : That is the same one that i got, from that site, except i didnt pay for it..
No instructions given to access the Lenovo Recovery Partition, and it doesnt show up on the GRUB, (i believe it used to)

edit: And it boots /sda1 and /sda2 with the same results as before

---

### Post by oldfred on 2011-10-29
Sometimes reruning commands helps. Both chkdsk & fixboot do fixes to PBR and they seem to depend on each other. I run chkdsk from a Win7 repairUSB and it converted my PBR to a Win7 type NTFS which is different than a XP type. It still worked, but I converted it back to XP type.

Have you tried f8, immediately after grub entry on booting Windows? That sometimes gets you to the internal repair console, which also lets you make a repairCD.

Sometimes this will get you booting. 

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

