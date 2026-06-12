---
title: "Windows 7 not booting after Ubuntu Update"
date: 2012-02-17
forum: General Help
---

### Post by omid429 on 2012-02-17
So I installed 11.10 a few weeks ago and everything worked great...until today. I installed some updates and then my system had to restart. So I went about my work and then came home and a few hours later when I started my computer I went into Windows 7. It hung at the splash screen. I restarted and tried safe mode, no dice. I installed my Win7 cd and again, hung at the splash screen. I scoured the forums and tried everything I could find. Updated grub, boot repair, and even Hiren's boot cd. While in Hirens boot cd, it said that my partition table had errors and the partition table doctor said the repairs were made successfully. However, I still have the problem. I attempted the ms-sys fix but it did not work. I am now at a loss. I don't know what to do. My grub sees the windows partition and even lists the OS and will attempt to boot into it, but again, it just hangs. Safe mode not an option, last known configuration that worked not working, and the cd also hangs. I have a lot of work related documents and emails that I cannot afford to lose so re-installing is not an option. I am afraid of removing Ubuntu because then I may lose access to the hdd altogether. If anyone has an idea of what I could do I would be more than greatful. Thanks in advance and I hope that someone has a solution for me.

---

### Post by Rubi1200 on 2012-02-18
Hi,

please post the results of the boot info script so we can get a better overview of the state of the system.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by omid429 on 2012-02-18
Thank you for your response. i have done as you asked and the results are below.
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
    Boot files:        /Windows/System32/winload.exe /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       401,624       399,577  17 Hidden NTFS / HPFS
/dev/sda2    *        401,625   510,240,305   509,838,681   7 NTFS / exFAT / HPFS
/dev/sda3         510,240,766   593,778,464    83,537,699   f W95 Extended (LBA)
/dev/sda5         556,015,616   572,651,519    16,635,904  82 Linux swap / Solaris
/dev/sda6         572,653,053   593,778,464    21,125,412   7 NTFS / exFAT / HPFS
/dev/sda7         510,240,768   539,375,615    29,134,848  83 Linux
/dev/sda8         539,377,664   556,009,471    16,631,808  82 Linux swap / Solaris
/dev/sda4         593,778,465   625,137,344    31,358,880  12 Compaq diagnostics


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        01CB4D14177688C0                       ntfs       
/dev/sda2        01CB4D2D128208D0                       ntfs       one
/dev/sda4        01CB4D16248F2010                       ntfs       LENOVO_PART
/dev/sda5        dd9d12a3-4421-4e58-94df-6a8820518d6c   swap       
/dev/sda6        01CC7E42F6629960                       ntfs       two
/dev/sda7        3886b955-c5fa-4cc7-bde4-bbc278d529b3   ext4       
/dev/sda8        ab758a7b-5797-4d8a-bb6d-e05275a988fd   swap       
/dev/zram0       2a4c9be2-986c-45e3-b480-b5da9f60f6a3   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root 3886b955-c5fa-4cc7-bde4-bbc278d529b3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root 3886b955-c5fa-4cc7-bde4-bbc278d529b3
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
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
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 3886b955-c5fa-4cc7-bde4-bbc278d529b3
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=3886b955-c5fa-4cc7-bde4-bbc278d529b3 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 3886b955-c5fa-4cc7-bde4-bbc278d529b3
    echo    'Loading Linux 3.0.0-16-generic ...'
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=3886b955-c5fa-4cc7-bde4-bbc278d529b3 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 3886b955-c5fa-4cc7-bde4-bbc278d529b3
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=3886b955-c5fa-4cc7-bde4-bbc278d529b3 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 3886b955-c5fa-4cc7-bde4-bbc278d529b3
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=3886b955-c5fa-4cc7-bde4-bbc278d529b3 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 3886b955-c5fa-4cc7-bde4-bbc278d529b3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 3886b955-c5fa-4cc7-bde4-bbc278d529b3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 01CB4D14177688C0
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 01CB4D16248F2010
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=3886b955-c5fa-4cc7-bde4-bbc278d529b3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=dd9d12a3-4421-4e58-94df-6a8820518d6c none            swap    sw              0       0
# swap was on /dev/sda8 during installation
UUID=ab758a7b-5797-4d8a-bb6d-e05275a988fd none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-16-generic               3
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-16-generic                  1
               =                initrd.img                                     3
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by oldfred on 2012-02-19
The boot partition is the (hidden in Windows) sda1 and Windows auto  repairs default to the active or boot flagged partition. If the other  repairs resized any of the Windows partitions then chkdsk & fixBoot  would be required. Both fixBoot & chkdsk seem to update the Windows PBR or partition boot sector and they seem to depend on each other, or you may need to run each more than once.

If repairs are directly run on sda2, it may also  work, but it will add bootmgr & BCD (Or you may copy & repair BCD) to sda2 and in effect obsolete  the sda1 boot partition.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
chkdsk c: /r
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

If you run the auto repair or the fixMBR command you will be able to confirm that Windows directly boots, but then will have to reinstall the grub2 boot loader to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by omid429 on 2012-02-20
Can't boot into recovery environment or with cd

---

### Post by pqwoerituytrueiwoq on 2012-02-20
you should be able to mount the windows partition from Ubuntu look under places
you may see something like System or 40gb partition anyway that is your windows install
click it open the windows folder then the users folder then the folder with your account name you should be able to figure out where your own files are from this point

what email client are you using? if it is Thunderbird you could copy it's app data to ubuntu and access it

edit: have you tried scanning windows for viruses you can use clamav for that (don't forget to install the definitions) google is your friend here

---

### Post by Mark Phelps on 2012-02-20
> **omid429 said:**
> Can't boot into recovery environment or with cd

OUCH!!!

OK, if you (1) can't boot into any CD, and (2) can't boot into the HDD -- then the only option you will have is to boot using USB, hook an external drive to your PC, and use Ubuntu to copy the files and stuff you want to save to that external drive.

If you go to PendriveLinux.com, you will find they have a Universal USB Installer you can use (together with an Ubuntu image) to create an Ubuntu BOOT USB.

---

### Post by oldfred on 2012-02-20
Someone reported that systems may save bad data and reuse it on a warm boot or reboot. But a total cold boot/ full power down resets everything so then you can boot from a bootable CD.

---

### Post by omid429 on 2012-02-21
Ok so here is what I did to solve the issue. Before committing murder on my hdd, I went and got an external hdd with a nice hdd in it. I opened it up and placed it in my system and started from scratch. Reinstalled everything. Then I put the old hdd in the case and used it to retrieve my important documents. End result. New hdd in my pc, new external hdd since I formatted it, and my computer is running smooth and happy. Thank you all for your help and in the end I suspect that the PBR became corrupted somehow. I am sure there was another way to fix it, but since this is my only computer and I didn't have access to another one to create a bootable usb, this seemed to be the best option.

---

### Post by Rubi1200 on 2012-02-24
Glad you got things sorted out with the help of everyone :-)

---

