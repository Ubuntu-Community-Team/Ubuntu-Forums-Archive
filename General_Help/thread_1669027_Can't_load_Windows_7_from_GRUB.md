---
title: "Can't load Windows 7 from GRUB"
date: 2011-01-17
forum: General Help
---

### Post by Voganaa on 2011-01-17
I was having problems with a video driver for ubuntu 10.10 64 bit so decided to try and down grade to 32 bit.
I kind of carelessly just deleted the ubuntu partition with Gparted thinking that worse case scenario I would still have access to windows 7, since I was running a dual boot. This was a terrible idea and I ran into a bunch of problems. I managed to reinstall ubuntu and it runs fine. However when I try to load windows 7 it justs loops back to the grub screen. Trying to avoid reinstalling everything to get a proper boot. Any help is greatly appreciated.

---

### Post by oldfred on 2011-01-17
Welcome to the forums:

Run this so we can see your exact configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Voganaa on 2011-01-17
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 651219000 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   396,982,465   396,982,403   7 HPFS/NTFS
/dev/sda2         716,804,235   716,836,364        32,130   7 HPFS/NTFS
/dev/sda3         396,984,318   716,802,047   319,817,730   5 Extended
/dev/sda5         396,984,320   703,737,855   306,753,536  83 Linux
/dev/sda6         703,739,904   716,802,047    13,062,144  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072932352 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142446 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   140,034,047   140,033,985   7 HPFS/NTFS
/dev/sdb2         140,034,048   625,141,759   485,107,712   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        70EC1AE0EC1AA100                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        61aec0ea-5b4a-4d34-a6ca-f4ab1752856b   ext4                                     
/dev/sda6        290ab3e3-9005-487a-a89c-88c577341cc9   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3C7C5D447C5CFA5A                       ntfs       FreeAgent Drive               
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/FreeAgent Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 61aec0ea-5b4a-4d34-a6ca-f4ab1752856b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 61aec0ea-5b4a-4d34-a6ca-f4ab1752856b
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 61aec0ea-5b4a-4d34-a6ca-f4ab1752856b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=61aec0ea-5b4a-4d34-a6ca-f4ab1752856b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 61aec0ea-5b4a-4d34-a6ca-f4ab1752856b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=61aec0ea-5b4a-4d34-a6ca-f4ab1752856b ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 61aec0ea-5b4a-4d34-a6ca-f4ab1752856b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 61aec0ea-5b4a-4d34-a6ca-f4ab1752856b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 70ec1ae0ec1aa100
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
UUID=61aec0ea-5b4a-4d34-a6ca-f4ab1752856b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=290ab3e3-9005-487a-a89c-88c577341cc9 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 295.7GB: boot/grub/core.img
 293.6GB: boot/grub/grub.cfg
 203.9GB: boot/initrd.img-2.6.35-22-generic
 295.7GB: boot/vmlinuz-2.6.35-22-generic
 203.9GB: initrd.img
 295.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 

```

Damn I've made a mess of my drive. I'll have to sort some things out if I ever get windows to boot properly.

Thanks for the help,

V

---

### Post by Bucky Ball on 2011-01-17
Open a terminal in Ubuntu (Applications >Accessories >Terminal) and input this:

```
sudo update-grub
```

That should fix it. ;)

---

### Post by Voganaa on 2011-01-17
Nope, that was the first thing I tried. Just tried it again for kicks, no luck.

---

### Post by Quackers on 2011-01-17
sda2 and sdb2 cannot be mounted for some reason. From the live cd desktop what does gparted show?

---

### Post by Voganaa on 2011-01-17
sdb isn't important, its just an external I forgot to eject. sda2 is read as an unknown file system by Gparted, it suggests that it is either damaged, unknown to Gparted or unformatted. I think its a small partition that windows created. When I originally installed ubuntu I used the advance partition options and made sure to leave it in place. On the reinstall I wasn't as careful. Now the linux OS and swap are between it and the windows OS. Source of problem? Fixes?

Thanks, 

V

---

### Post by Quackers on 2011-01-17
Can you post a screenshot of the gparted screen for sda please?

---

### Post by Voganaa on 2011-01-17
uhh... If you can tell me how to get the screenshot from Gparted to here, then yes.

---

### Post by Quackers on 2011-01-17
Presumably you have the screenshot on your desktop, or in pictures folder?
In the forum click on New Reply (not quick reply)  and type in what you want to type. Then further down the page click on "Manage Attachments". In the new window click on "Browse" and navigate to your screenshot.
Click on "upload" and after a few seconds (normally) close the window and click on "submit message". et voila! :-)

---

### Post by oldfred on 2011-01-17
We had a ton of this problem with 10.04 as it was installing grub too easily to the windows partition.

    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sda1[/COLOR] and 
                       looks at sector 651219000 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7

You have to have a windows boot in the windows partition.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I do not like that sda2 & sdb2 are not showing correctly. I would try running chkdsk from a windows CD first on those partitions.

---

### Post by Voganaa on 2011-01-17
Had been running Gparted off bootdisk, not through ubuntu. Much easier now that I have it installed.
Heres the screenshot.

---

### Post by Quackers on 2011-01-17
oldfred will sort you out :-) see one post up from yours.
Nice screenshot :-)

---

### Post by Voganaa on 2011-01-17
Not sure how to run a chkdsk from a windows CD, but did take a look at the drives with one. It recognizes sda2 as being primary type. Followed the link and the instructions. My issue wasn't quite the same. testdisk told me my boot and back up boot were not identical and gave me the option to copy over my backup boot to make it identical. This didn't fix the problem. Should I dump? rebuild? etc. move sda2 back beside sda1?

Thanks, 

V

---

### Post by Quackers on 2011-01-17
Sometimes it is better to start again, as the fix can take longer than re-installing everything. If you have good backups that may be a good option.
When installing grub always specify the drive but not a partition eg sda not sda1

---

### Post by Voganaa on 2011-01-17
Thanks for the help and advice. Everything is backed up, so the only thing i'll lose is more time.

V

---

### Post by Quackers on 2011-01-17
The advice is welcome. I'm sorry the outcome wasn't good.

---

