---
title: "Problems with dual booting in Asus 53S"
date: 2011-11-13
forum: General Help
---

### Post by Peitra on 2011-11-13
Hi everybody... I'm a bit desperate... I've been trying to solve that the entire day and I don't know what to do else...

Somebody offer me a Asus with windows (no... is not an enemy) and if I  want to keep the warranty I need to keep the windows 7 installation  so... I decided to do a partition and install ubuntu (which I'm not an  expert but I've been using for 5 years) 

Sooo... the problem is that I can't boot the windows' partition. First I  only had one option that was recovery mode for windows (which doesn't  work with the cds that gave us in the shop ](*,)  so I can't recover the system from any cd) and now I sucess to create a  new one item in the grub list which is supposed to be the good one (the  windows' partition I think is there 8-[), but it says "BOOTMGR is missing" 

Thank you very much for your help....

---

### Post by oldfred on 2011-11-13
Post this so we can see exactly what is where. You can run it from Ubuntu or a Linux liveCD.


Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by West201 on 2011-11-13
Do you have an Ubuntu CD ? 

I follow this tutorial once on fixing my Windows MBR using an Ubuntu Live CD. 

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

---

### Post by Peitra on 2011-11-13
I downloaded the new ubuntu and installed booting from usb.

And there is the Boot info Script..... Thank you very much......

   ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    52,430,847    52,428,800  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     52,430,848   247,827,332   195,396,485  83 Linux
/dev/sda3         247,828,478   976,771,071   728,942,594   f W95 Extended (LBA)
/dev/sda5         443,142,144   976,771,071   533,628,928   7 NTFS / exFAT / HPFS
/dev/sda6         247,828,480   434,935,807   187,107,328  83 Linux
/dev/sda7         434,937,856   443,135,999     8,198,144  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 555b70e8-bae3-4392-a74b-19e75542bb34   swap       
/dev/sda1        B681-27DD                              vfat       RECOVERY
/dev/sda2        49ed782b-570f-4066-ba4f-519086c96749   ext4       
/dev/sda5        9E821AF0821ACCA1                       ntfs       DATA
/dev/sda6        6ff11251-d9b7-4e60-a427-3f0374c23a81   ext4       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /Windows                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


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
set default="${saved_entry}"
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
search --no-floppy --fs-uuid --set=root 6ff11251-d9b7-4e60-a427-3f0374c23a81
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 6ff11251-d9b7-4e60-a427-3f0374c23a81
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6ff11251-d9b7-4e60-a427-3f0374c23a81
    linux    /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=6ff11251-d9b7-4e60-a427-3f0374c23a81 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6ff11251-d9b7-4e60-a427-3f0374c23a81
    echo    'Loading Linux 3.0.0-12-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=6ff11251-d9b7-4e60-a427-3f0374c23a81 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6ff11251-d9b7-4e60-a427-3f0374c23a81
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=6ff11251-d9b7-4e60-a427-3f0374c23a81 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6ff11251-d9b7-4e60-a427-3f0374c23a81
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=6ff11251-d9b7-4e60-a427-3f0374c23a81 ro recovery nomodeset 
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
    search --no-floppy --fs-uuid --set=root 6ff11251-d9b7-4e60-a427-3f0374c23a81
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6ff11251-d9b7-4e60-a427-3f0374c23a81
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root b681-27dd
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows 7" {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 9E821AF0821ACCA1
chainloader +1
}

### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================
```

---

### Post by Peitra on 2011-11-13
Why is so difficult!! last time I mess up because I install first Ubuntu and after Windows... but now...:(

---

### Post by oldfred on 2011-11-13
Please use code tags (the # in the edit panel) to make script easier to read.

I do not see a Windows partition? It would normally be sda2 which is now linux? Was the sda5 the d: partition or a copy of something else as it shows it should start at sector 2048  which seems to say it is a copy or was moved somehow.

---

### Post by Peitra on 2011-11-13
Sorry I didn't know about code tags.

I think windows is in dev/sda5. 

I didn't have any other data in the pc and I only follow the recommendation for the partition that ubuntu give you when you make the installation.

Thank you again.

---

### Post by Peitra on 2011-11-14
Any idea? :(

---

### Post by Mark Phelps on 2011-11-14
While you're guessing that Win7 was in sda5, the label says DATA.

There are no Win7 boot files listed in the script output.  IF you have a Win7 Repair CD, you can replace those files.

But, a bigger concern, is that the script lists no Win7 OS files in sda5, either. That implies that Win7 is gone.

To confirm that, you need to open a file manager in Ubuntu and look into the sda5 partition to see what it there.  If there is still a directory there named Program Files, and one named Windows, then Win7 may be intact -- just missing the boot files.

---

### Post by Peitra on 2011-11-14
ufff... well I took two screen shot.. one is in /media and the other /Windows 

I don't know if it helps...

[ATTACH]207164[/ATTACH]

[ATTACH]207165[/ATTACH]

---

### Post by oldfred on 2011-11-14
Windows can use a logical as a system partition if you still boot from a primary. Your Windows boot files are in sda1, but it says it is a FAT type which is usually just the vendor system recovery partition. But it looks too large to be a vendor partition. 

You have the boot flag on sda2. Grub does not use boot flag so unless you manually moved it, that would normally say that was the Windows boot partition.

Partition sda5 says it is NTFS but also shows it starts at sector 2048 which does not work for Windows bootable partitions. Sector has to match the sector it starts in for NTFS to be a bootable partition. I think it may work as a NTFS partition even with the error but will not be bootable.

The script does not show this program which is always in the c: or working Windows partition. Sometimes script does not show it, can you find it in any of your NTFS partitions?
/Windows/System32/winload.exe

---

### Post by Peitra on 2011-11-14
I found that with the Gparted

[ATTACH]207168[/ATTACH]

What do you think?

---

### Post by oldfred on 2011-11-14
That just says you are mounting sda5 as /windows. It only shows 94MB of data which seems very small or just a few of your files?

You sda1 is labeled as the recovery partition, so that is your vendors image of the hard drive as you purchased it. Not a true Windows install, but a snapshot to restore. Did you make recovery DVDs from the recovery partition?

---

### Post by Peitra on 2011-11-14
They gave me some cds to recover the system but when you tried it said that were the wrong cds...

So, do you think I lose the Win7? do you think I need to download and install again?

---

### Post by Peitra on 2011-11-14
There is any way to change the boot to sda5? how can I know in the grub what is booting?

---

### Post by oldfred on 2011-11-14
You do not have enough data in sda5 to be a bootable system. Did you look at the files in sda5 to see if it looks like you have many files & folders that are a typical Windows install?

---

