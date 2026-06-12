---
title: "Dual Booting with Windows from different hdd's"
date: 2010-10-22
forum: General Help
---

### Post by Kewickviper on 2010-10-22
Hello,

I have been searching all day for an answer to this and cannot work it out myself.

I have Windows installed on one hdd and ubuntu linux installed on the other (which I am using now).
The last time I installed ubuntu onto the same hdd it automatically added a boot menu when I started up the computer but it is not doing it this time and just boots into ubuntu.

I would like to add a boot menu so when I turn the computer on I can choose to boot ubuntu off one hdd or windows off the other. 

I have searched for the last hour or two and the only guides I could find were for dual booting off one hdd.

Also I think I am now using grub2 and tried to update it and make scripts in the grub.d folder but it is still not adding grub when I start the computer.

If anyone can help I would be very grateful!

Thank you.

---

### Post by macem29 on 2010-10-22
hmmm, interesting question, by the time grub is started the machine will already have booted from one of the drives, whatever is set for first up in the bios...then you want to be able to start an OS from the other drive...sorry no solution to offer, but you gotta free bump anyway

---

### Post by Quackers on 2010-10-22
Presumably you are choosing which OS to boot via bios at the moment.
From a booted up Ubuntu try running
sudo update-grub
in a terminal. Watch as grub.cfg is run and see whether the Windows installation is picked up.
If Windows isn't picked up (and it may not be) please go to the site below and download the boot info script to your desktop. Then run the script with the command given on that site. This will produce a Results.txt on your desktop. Please copy the contents of that file and paste them into your next post inside CODE tags. (Select New Reply and then click on the # symbol in the toolbar).

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Kewickviper on 2010-10-22
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   599,740,415   599,738,368  83 Linux
/dev/sda2         599,742,462   625,141,759    25,399,298   5 Extended
/dev/sda5         599,742,464   625,141,759    25,399,296  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
240 heads, 63 sectors/track, 129201 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c19e6ea8-78b9-445d-913e-c295c0ad72bd   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        39c83f8d-c0f7-47d1-9edd-366a44e919e9   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8E8CD6808CD661EF                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c19e6ea8-78b9-445d-913e-c295c0ad72bd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c19e6ea8-78b9-445d-913e-c295c0ad72bd
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c19e6ea8-78b9-445d-913e-c295c0ad72bd
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c19e6ea8-78b9-445d-913e-c295c0ad72bd ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c19e6ea8-78b9-445d-913e-c295c0ad72bd
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c19e6ea8-78b9-445d-913e-c295c0ad72bd ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c19e6ea8-78b9-445d-913e-c295c0ad72bd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c19e6ea8-78b9-445d-913e-c295c0ad72bd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_Windows ###
menuentry "Windows 7" {
set root=(hd1,1)
chainloader +1
}
### END /etc/grub.d/40_Windows ###

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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=39c83f8d-c0f7-47d1-9edd-366a44e919e9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  71.0GB: boot/grub/core.img
 260.2GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-22-generic
  71.0GB: boot/vmlinuz-2.6.35-22-generic
   1.2GB: initrd.img
  71.0GB: vmlinuz
```

---

### Post by Quackers on 2010-10-22
If you change the boot device to the second drive in the bios does Windows still boot?
It appears to me that Windows has a couple of boot files missing. This is probably the reason for Grub not picking up the system.

---

### Post by Kewickviper on 2010-10-22
You are right it appears as though I am unable to boot into windows through the bios now. I am not sure what could have caused this since I have not touched my other hdd since I installed ubuntu earlier today, when Windows booted fine.

---

### Post by Quackers on 2010-10-22
I don't know what's happened but there are definitely boot files missing. Do you have a Windows repair disc or recovery disc? You will need to repair the Windows boot. If you don't have one there are sites from which you can download a repair disc, try Googling.
What you will need to do is change your bios back to the Windows drive but make the cd/dvd drive the first boot device and then save the changes and reboot with the repair disc in the drive.
It may ask you to press a key to boot from the cd and it may ask you to press the "R" key to enter the recovery/repair console. When you get there select repair your computer. It probably won't repair it but nevermind. Go to advanced option (I think it's called) and select the Command Prompt.
When there type in
bootrec.exe /fixmbr
and press enter. When it's run type in
bootrec.exe /fixboot              
and press enter.
###  Please note the space between the bootrec.exe and the /fixmbr and /fixboot  ###

When it's run reboot and hopefully Windows will boot. If it does change your bios back to the Ubuntu drive and boot up then run 
sudo update-grub
in the terminal. This time Windows should be picked up when grub.cfg is run.
Good luck and take care :-)

---

### Post by Kewickviper on 2010-10-23
Thank you for your help.
I tried what you said, but now both hard drives come up as "operating system missing" when I try to boot from them.
I am having to type this from a live ubuntu cd and am unsure of what to do next!
And to make matters worse my external hard drive is not working any more so I may have just lost all my backed up data.

Does anyone have any suggestions on what I should do next? The windows recovery cd doesn't recognise any windows installation on my hard drive.

---

### Post by Quackers on 2010-10-23
Did you change the boot device to the windows drive? Did you try bootrec.exe commands? It is normal for the repair function to not find Windows installations at this stage - you don't have the required boot files yet.

---

### Post by Kewickviper on 2010-10-23
Yes I changed the boot order in the bios to boot the windows hdd first. I have even tried unplugging the other hdd completely but to no avail. /fixmbr says that it works but /fixboot says something along the lines of no boot record.

I am going to reinstall ubuntu onto the other hard drive for now, but I am at a complete loss at how to get windows working again. If my external hard drive hadn't just died I would have backed everything up in ubuntu and just installed windows again but now I am completely stuck :(

---

### Post by Quackers on 2010-10-23
Last one I can think of for now is to go back into the Windows recovery environment and in the command prompt enter
bootrec.exe /rebuildbcd
If that runs ok it will offer you a Windows system to add to the boot record, answer y for yes.
That has worked for me in the past.
Good luck.

---

### Post by oldfred on 2010-10-23
Windows also need a boot flag (active partition) on the partition it is trying to repair. You only have a boot flag on sda1 but none on sdb1. Use gparted or disk utility to add a boot flag. 

If you are already in the win repair CD 

You can move the boot flag with the command prompt in the windows cd. If you have changed drive order it may be disk [COLOR=DarkRed]0[/COLOR]. 
Type this one line at a time and press enter
Diskpart
list disks
select disk [COLOR=DarkRed]1[/COLOR]
select partition 1
active
exit

---

### Post by Kewickviper on 2010-10-23
Finally managed to fix it. Had to pull out my harddrive with linux on and then run the windows recovery disc. I think it was getting confused with the hard drives and kept trying to patch the one with linux on even though I changed the order in the bios.

Also managed to fix grub2 on linux by installing it again with the live cd! Its been a long day haha!

Now though I want to return back to my original question, I have it set to boot the windows drive first and every time I want to use linux I go to my bios boot menu and boot that hard drive. I was wondering if there was any way to setup grub2 to let me choose windows or ubuntu.

---

### Post by oldfred on 2010-10-23
If both disks are plugged in running an update should find windows and let you boot it as a menu item.

```
sudo update-grub
```

---

### Post by Kewickviper on 2010-10-23
Wow I was not expecting it to be so simple! That worked perfectly thank you! Its a shame it couldn't have been that simple from the beginning I wonder how the hell my windows boot got so messed up :P

Thanks for your help everyone.

---

