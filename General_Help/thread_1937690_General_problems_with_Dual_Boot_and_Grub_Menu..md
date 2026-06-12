---
title: "General problems with Dual Boot and Grub Menu."
date: 2012-03-08
forum: General Help
---

### Post by BlinkinCat on 2012-03-08
Hello all,

As there is a Windows program that I very much wanted to gain access to I decided to dual boot with Windows 7. I am ashamed to admit that I probably made a botched up job of it as may be supported by the screen shot of Gparted and the Boot info script.

Both systems seem to work fine when I eventually get access to them however there is a problem with the Grub menu. Actually, ubuntu loads in a reasonable time but Win 7 scrolling on the menu "jams up" and regularly doesn't accept the key down positions at all for a period of several minutes. As a result, logging on to ubuntu is fine being the first item in the menu but trying to select Win 7 can take several attempts of logging in and out of ubuntu until it eventually "flukes" a down key command.

Anyway, I would very much appreciate any input regarding my problems.
I have the feeling there is quite a lot wrong with the installation.
  
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1          39,063,550   470,702,079   431,638,530   5 Extended
/dev/sda5          39,063,552    50,780,159    11,716,608  82 Linux swap / Solaris
/dev/sda6          50,782,208   265,623,551   214,841,344  83 Linux
/dev/sda7         265,625,600   470,702,079   205,076,480  83 Linux
/dev/sda2         470,702,080   470,906,879       204,800   7 NTFS / exFAT / HPFS
/dev/sda3    *    470,906,880 1,953,521,663 1,482,614,784   7 NTFS / exFAT / HPFS
/dev/sda4               2,048    39,061,503    39,059,456  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        62F867F3F867C3BF                       ntfs       System Reserved
/dev/sda3        DA5E70EF5E70C633                       ntfs       
/dev/sda4        4989c344-b613-4623-807b-c8617d026729   ext4       
/dev/sda5        c981f1c9-6363-44ce-ae47-9b99d159fe23   swap       
/dev/sda6        8b5e1fbc-cb8d-43a3-9acc-42c0b4591efc   ext4       
/dev/sda7        8f64977b-77df-4a69-8fdb-b594e5fa1d84   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda4        /tmp                     ext4       (rw,commit=0)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext4       (rw,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 8b5e1fbc-cb8d-43a3-9acc-42c0b4591efc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 8b5e1fbc-cb8d-43a3-9acc-42c0b4591efc
  set locale_dir=($root)/boot/grub/locale
  set lang=en_AU
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 8b5e1fbc-cb8d-43a3-9acc-42c0b4591efc
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=8b5e1fbc-cb8d-43a3-9acc-42c0b4591efc ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 8b5e1fbc-cb8d-43a3-9acc-42c0b4591efc
    echo    'Loading Linux 3.0.0-16-generic ...'
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=8b5e1fbc-cb8d-43a3-9acc-42c0b4591efc ro recovery nomodeset 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 8b5e1fbc-cb8d-43a3-9acc-42c0b4591efc
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=8b5e1fbc-cb8d-43a3-9acc-42c0b4591efc ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 8b5e1fbc-cb8d-43a3-9acc-42c0b4591efc
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=8b5e1fbc-cb8d-43a3-9acc-42c0b4591efc ro recovery nomodeset 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 8b5e1fbc-cb8d-43a3-9acc-42c0b4591efc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 8b5e1fbc-cb8d-43a3-9acc-42c0b4591efc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 62F867F3F867C3BF
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=8b5e1fbc-cb8d-43a3-9acc-42c0b4591efc /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=8f64977b-77df-4a69-8fdb-b594e5fa1d84 /home           ext4    defaults        0       2
# /tmp was on /dev/sda4 during installation
UUID=4989c344-b613-4623-807b-c8617d026729 /tmp            ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=c981f1c9-6363-44ce-ae47-9b99d159fe23 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-16-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-16-generic                  1
               =                initrd.img                                     2
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

```p.s. I had a screenshot of Gparted, but it wouldn't upload.

---

### Post by HappyJony on 2012-03-08
Did you install Ubuntu before installing Windows 7 then use the alternate CD to reinstall Grub?

---

### Post by BlinkinCat on 2012-03-08
Hi HappyJony,

No, I installed windows first and followed the dual boot directions to re-install Ubuntu which from memory automatically installed grub. I must say I am nervous about the installation but I have nowhere enough knowledge to interpret the Boot info script. The two systems seem to operate reasonably but I have the feeling something is not quite right. - :)

---

### Post by oldfred on 2012-03-08
I do not see anything in boot script that indicates an boot issue. I think boot script would only show something if it did not boot. You may want to move boot flag to sda2 as that is the Windows boot partition, but grub does not use a boot flag. Only if you have to repair booting in Windows from your Windows repairCD would you need the flag on sda2.

It seems like a grub issue, but grub uses the BIOS keyboard definition, where both Windows & Ubuntu seem to use their own drivers. Check that you have USB keyboard turned on in BIOS if that is the case. Not sure what else in grub would make menu slow.

Update - found in my notes some more possibly related BIOS issues.
Disable Quickboot in BIOS
BIOS setting, Keyboard response in grub really slow
Fast Boot setting prevents keyboard from working & other issues
Bios not loading no key works - disconnected power for about 10-15 minutes and the bios reset itself.

---

### Post by HappyJony on 2012-03-08
I don't know how to modify these files, TBH, but here's one thing that I'd try:

Update Grub menu to generate a new Grub.cfg:
```
sudo update-grub
```

If that doesn't work, you can always install "Start-up Manager". This will allow you to change which line the grub menu will start on. Its only a temporary work around though... You can also get rid of the timer in the grub menu with this program.

Hope this helps
Jony

---

### Post by BlinkinCat on 2012-03-08
Hi oldfred,

Thanks very much for your input - I will check bios settings.
One other thing you or anybody else may care to comment is that I seem to have a problem maintaining an adequate internet connection. For example logging onto the forum does not allow a good connection for a period of more than around ten minutes - I really don't know what is going on.
Any clues would be appreciated.

Cheers - :)

---

### Post by BlinkinCat on 2012-03-08
> **oldfred said:**
> I do not see anything in boot script that indicates an boot issue. I think boot script would only show something if it did not boot. You may want to move boot flag to sda2 as that is the Windows boot partition, but grub does not use a boot flag. Only if you have to repair booting in Windows from your Windows repairCD would you need the flag on sda2.

It seems like a grub issue, but grub uses the BIOS keyboard definition, where both Windows & Ubuntu seem to use their own drivers. Check that you have USB keyboard turned on in BIOS if that is the case. Not sure what else in grub would make menu slow.

Update - found in my notes some more possibly related BIOS issues.
Disable Quickboot in BIOS
BIOS setting, Keyboard response in grub really slow
Fast Boot setting prevents keyboard from working & other issues
Bios not loading no key works - disconnected power for about 10-15 minutes and the bios reset itself.

Thanks again oldfred - I will take note of your additional comments - thank you - :)

---

### Post by BlinkinCat on 2012-03-09
Hi again and hooray - Grub menu scrolling problem has been solved - all it took was a new $20 Keyboard. Now working like a dream. A few searches produced similar solutions in a number of threads that I checked.

I found that enabling Quick Boot produced an error. So I disabled again.

Both operating systems are generally working O.K. now other than a Networking problem with Ubuntu. I have started another thread for that.

Thanks very much to HappyJony and oldfred for your inputs - will mark as solved.

Cheers - :)

---

