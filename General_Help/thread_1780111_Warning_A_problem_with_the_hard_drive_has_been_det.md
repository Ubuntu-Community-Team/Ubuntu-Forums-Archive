---
title: "Warning: A problem with the hard drive has been detected."
date: 2011-06-11
forum: General Help
---

### Post by wrobertshd1 on 2011-06-11
I just installed Ubuntu 11.04 and during boot up, after POST message the following error message is displayed:

[FONT=Courier New]The following are warnings that were detected during this boot.
These can be viewed in setup on the event log page.
Warning: A problem with the hard drive has been detected.
[/FONT]
I don't know how to view setup on the event log page.

This was a clean install on a computer that was running WXP.

I'm not dual booting - I wanted to learn Ubuntu.

The computer does boot, but I'd like to diagnose what the hard drive problem is.

Cheers,
Biill

---

### Post by Rubi1200 on 2011-06-11
Hi and welcome to the forums :-)

How old is the computer?

Have you had problems with the hard-drive before?

On 11.04 you need to search applications for the Disk Utility application.

Open it and look at the SMART status regarding the health of the drive.

Report back with what it finds.

Thanks.

---

### Post by wrobertshd1 on 2011-06-11
The machine is home built - about 3 years old.

The hard drive in question was part of a 2 drive striped raid array.

The boot drive shows SMART status not supported; the second drive shows all green on SMART status.

---

### Post by Rubi1200 on 2011-06-11
Okay, it could be that the fact that the drive was part of a RAID array is the cause of the error.

Do you still use a RAID setup in the current configuration?

To help us get a better overview of what is where, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by wrobertshd1 on 2011-06-11
I am not using RAID.

When I ran the boot_info_script there was a warning that gawk could not be found - I presume this is not important.[INDENT][FONT=Courier New]ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script.sh[/FONT]

[FONT=Courier New]boot_info_script version: 0.60        [17 May 2011][/FONT]


[FONT=Courier New]"gawk" could not be found, using "busybox awk" instead.[/FONT]
[FONT=Courier New]This may lead to unreliable results.[/FONT]

[FONT=Courier New]Identifying MBRs...[/FONT]
[FONT=Courier New]Computing Partition Table of /dev/sda...[/FONT]
[FONT=Courier New]Computing Partition Table of /dev/sdb...[/FONT]
[FONT=Courier New]Searching sda1 for information... [/FONT]
[FONT=Courier New]Searching sda2 for information... [/FONT]
[FONT=Courier New]Searching sda5 for information... [/FONT]
[FONT=Courier New]Searching sdb1 for information... [/FONT]

[FONT=Courier New]Finished. The results are in the file "RESULTS.txt"[/FONT]
[FONT=Courier New]located in "/home/ubuntu/Desktop/".[/FONT]
[/INDENT]RESULTS.TXT content:

```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   226,062,335   226,060,288  83 Linux
/dev/sda2         226,064,382   234,440,703     8,376,322   5 Extended
/dev/sda5         226,064,384   234,440,703     8,376,320  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
81 heads, 63 sectors/track, 45941 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   234,441,647   234,439,600  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        95adff7d-a784-4168-906d-22e42a11fc60   ext4       
/dev/sda5        d48bf9b1-29e9-4e4a-a346-785e64a3242e   swap       
/dev/sdb1        5074ded6-e20a-4728-afce-8b650c2bffe7   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 95adff7d-a784-4168-906d-22e42a11fc60
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 95adff7d-a784-4168-906d-22e42a11fc60
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 95adff7d-a784-4168-906d-22e42a11fc60
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=95adff7d-a784-4168-906d-22e42a11fc60 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 95adff7d-a784-4168-906d-22e42a11fc60
    echo    'Loading Linux 2.6.38-8-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=95adff7d-a784-4168-906d-22e42a11fc60 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 95adff7d-a784-4168-906d-22e42a11fc60
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 95adff7d-a784-4168-906d-22e42a11fc60
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=95adff7d-a784-4168-906d-22e42a11fc60 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d48bf9b1-29e9-4e4a-a346-785e64a3242e none            swap    sw              0       0
/dev/sdb1 /mnt/sdb1 ext4 defaults 0 0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  62.135009766 = 66.716958720   boot/grub/core.img                             1
  48.245845795 = 51.803582464   boot/grub/grub.cfg                             1
   1.696289062 = 1.821376512    boot/initrd.img-2.6.38-8-generic-pae           2
   0.708435059 = 0.760676352    boot/vmlinuz-2.6.38-8-generic-pae              1
   1.696289062 = 1.821376512    initrd.img                                     2
   0.708435059 = 0.760676352    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d0 7f 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by Rubi1200 on 2011-06-12
The script results look okay to me. I still think you should investigate the hard disk integrity angle. 

Look in BIOS and see if anything looks out of place, check the website of the disk manufacturer and see if there are any diagnostic tools available for download that can check the health of the drive.

You could also boot the computer with a LiveCD and run the following command to check if there is any residual RAID metadata:


```
sudo dmraid -E -r /dev/sda

```

If it tells you there is metadata and you are sure that the drive won't be used for such, then you can probably go ahead and remove it.

Then check with the Disk Utility again regarding the health status.

If I find other relevant information, I will post again.

---

### Post by wrobertshd1 on 2011-06-12
Thank you for your help Rubi1200.

I have concluded that the hard drive in question had hardware problems.

I replaced it with an identical hard drive, reinstalled Ubuntu 11.04 and all is well.

Please close this thread, and thanks again for your help.

Best regards,

Bill Roberts

---

### Post by Rubi1200 on 2011-06-13
Okay, I am glad you found a solution and are able to use Ubuntu as you wanted.

Please mark this Solved using the Thread Tools near the top of the page.

Thanks.

---

