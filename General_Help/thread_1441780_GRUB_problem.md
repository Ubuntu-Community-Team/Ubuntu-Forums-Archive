---
title: "GRUB problem"
date: 2010-03-29
forum: General Help
---

### Post by razor180 on 2010-03-29
I know this isn't exactly ubuntu, but I'm having a problem with GRUB

I use windows 7 for many things that I can't do in linux, but now I can't get into it through grub, it's running the chainloader, but when I tell it to run windows from sdb2, it doesn't work, it just restarts the computer. I don't know what the problem is, so therefor I can't fix it

---

### Post by razor180 on 2010-03-29
oh yes, forgot to mention, the option to boot into windows on GRUB bootloader says windows vista, and I recently replaced windows vista with windows 7 and have just reinstalled ubuntu as well as grub since the windows 7 installer deleted it all

---

### Post by Slonda828 on 2010-03-29
Your linux partition is still bootable, right? I would boot into linux, then open up a terminal and type:

grub-mkconfig (the absolute path is /usr/sbin/grub-mkconfig if you need it)

That should reconstruct your grub menu, which may be currently looking for vista when you now have 7 on there. Give that a shot and let us know if it does or does not work. If the box gives you the international greeting again, let us know how it does so ;)

---

### Post by razor180 on 2010-03-29
great, I know the problem, and this is ANNOYING

what I did when I installed windows 7 was install it into the existing partition for vista (I didn't upgrade because vista was 32 bit and I wanted x64) and it kept some of the files and didn't heavily edit the partition, and while I had to redo grub after installing it (and install linux, again) it's still reading the filesystem like it's windows vista, not quite sure why, but I have some ideas

it could be the label on the partition, it could be the windows 7 architecture is similar to windows vista, but the loader is different, but I'm going to try some things

and no, it didn't work (haven't tried grub, but) because in the terminal, when it got to reloading windows, it still says windows vista

I did have to do sudo grub-mkconfig because it needed to be root

EDIT: I know for a fact that it didn't work, I just tried it and it did the same thing, restarted

---

### Post by cbecker78 on 2010-03-29
I actually never had vista installed on my pc, but after installing win7 and then ubuntu, the grub bootscreen identified those partitions as "Vista".  Odd.

But to your question:  If this started happening right after installation of Ubuntu; my own similar problem was solved by inserting my windows 7 disk, booting from the cd, and selecting repair from the options that are available once the disk finishes it's initialization.  Then reboot and all was well.

Some thoughts:
there should be 2 partitions used when Win7 is properly installed.  one is the MBR which controls booting, the other is the OS. (a third sys recovery partition may be there too depending on whether or not you reformatted that as swap).  Pointing grub at the MBR partition (the smallest one) is what it takes for me to get Win7 to boot.

edit:  rereading your last post- are you saying it actually displays a "Vista" splashscreen when trying to boot into windows?

---

### Post by oldfred on 2010-03-29
IF you install from scratch win7 creates a boot partition and the install. If a NTFS partition exists it installs completely into that partition.

This will tell us more about your install:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by cbecker78 on 2010-03-29
> **oldfred said:**
> IF you install from scratch win7 creates a boot partition and the install. If a NTFS partition exists it installs completely into that partition.


Huh, didn't know that.  I may have to try reinstalling to free up a partition.

---

### Post by Slonda828 on 2010-03-29
Interesting. Well it shouldn't be your windows boot loader, because everything based on NT uses NTLDR and the boot.ini after windows 98SE. Your upgrade should not have changed anything as far as that is concerned.

---

### Post by razor180 on 2010-03-29
> **cbecker78 said:**
> edit:  rereading your last post- are you saying it actually displays a "Vista" splashscreen when trying to boot into windows?
I have no idea where you got that impression. like I said, all it does after I select windows vista on grub is restart the PC and go back to grub (after express gate) plus in order for there to be a vista splashscreen, there would have to be boot files from vista, but I'm trying to access windows 7

wouldn't repair get rid of grub, and when I tried to reinitialize it, I would go through the same exact problem?

Oldfred:
I know that, but what I did is just install it on that existing partition, I did not reformat it, and it kept all of the files on it in a folder called windows.old (of course it's not reading those files but...) but it may still be reading that partition as windows vista because I did not reformat

Slonda:
yes, I know it's not my windows bootloader, it was working fine until I installed ubuntu and GRUB, so I know for a fact that it's a GRUB problem, not a windows problem. it's just GRUB not being able to access the windows bootloader correctly, probably because it's trying something that's not there like you suggested earlier

---

### Post by Slonda828 on 2010-03-29
Can you view your grub.cfg and copy the windows entries and display them? Alternately, can you view them from inside the grub menu and just type out which one for your windows partition is giving you grief? Maybe we can hand jam it.

---

### Post by razor180 on 2010-03-29
I only have 2 windows partitions, a backup (which doesn't show up on grub) and windows boot (which does)

this is my full grub.cfg file
```
[I]#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="${saved_entry}"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 1f7980ab-2d0f-419a-b5b3-ca9d080f04a8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  #set gfxpayload=keep
  #set gfxpayload=1024x768x16
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 1f7980ab-2d0f-419a-b5b3-ca9d080f04a8
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=1f7980ab-2d0f-419a-b5b3-ca9d080f04a8 ro   
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 1f7980ab-2d0f-419a-b5b3-ca9d080f04a8
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=1f7980ab-2d0f-419a-b5b3-ca9d080f04a8 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 1f7980ab-2d0f-419a-b5b3-ca9d080f04a8
    linux    /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=1f7980ab-2d0f-419a-b5b3-ca9d080f04a8 ro   
    initrd    /boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 1f7980ab-2d0f-419a-b5b3-ca9d080f04a8
    linux    /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=1f7980ab-2d0f-419a-b5b3-ca9d080f04a8 ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-20-generic (on /dev/sda1)" {
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1f07e142-b93a-415a-b6f9-e64670f45d7f
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=1f07e142-b93a-415a-b6f9-e64670f45d7f ro quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode) (on /dev/sda1)" {
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1f07e142-b93a-415a-b6f9-e64670f45d7f
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=1f07e142-b93a-415a-b6f9-e64670f45d7f ro single
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda1)" {
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1f07e142-b93a-415a-b6f9-e64670f45d7f
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=1f07e142-b93a-415a-b6f9-e64670f45d7f ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda1)" {
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1f07e142-b93a-415a-b6f9-e64670f45d7f
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=1f07e142-b93a-415a-b6f9-e64670f45d7f ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Windows Vista (loader) (on /dev/sdb2)" {
    saved_entry=${chosen}
    save_env saved_entry
    insmod ntfs
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set e2bccd2fbcccfed3
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###[/I]
```

this is the windows part

[I]```
menuentry "Windows Vista (loader) (on /dev/sdb2)" {
    saved_entry=${chosen}
    save_env saved_entry
    insmod ntfs
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set e2bccd2fbcccfed3
    chainloader +1
```

[/I]**keep in mind that there are 2 different hard drives, one is solely for windows, the other one I dedicated for linux OS's. the hard drive for windows is SDB, and the other one is SDA, the windows partition I'm trying to boot into is known as SDB2**

---

### Post by razor180 on 2010-03-30
I tried that script

this is what I got
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007ad11

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    58,589,054    58,588,992  83 Linux
/dev/sda2          58,589,055   362,297,879   303,708,825   5 Extended
/dev/sda5          58,589,118    69,336,539    10,747,422  82 Linux swap / Solaris
/dev/sda6          69,336,603   362,297,879   292,961,277  83 Linux
/dev/sda4         362,297,880   370,892,654     8,594,775  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2527a2c7

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    20,482,874    20,482,812   7 HPFS/NTFS
/dev/sdb2    *     20,482,875   488,392,064   467,909,190   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        1f07e142-b93a-415a-b6f9-e64670f45d7f   ext3                                     
/dev/sda4        6563d67a-4c68-4802-b782-cd246273edcd   swap                                     
/dev/sda5        6385bd1c-05c7-4efb-b8af-5c8e398aafd9   swap                                     
/dev/sda6        1f7980ab-2d0f-419a-b5b3-ca9d080f04a8   ext3                                     
/dev/sdb1        592134601F58A36F                       ntfs       windows backup                
/dev/sdb2        E2BCCD2FBCCCFED3                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 1f07e142-b93a-415a-b6f9-e64670f45d7f
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1f07e142-b93a-415a-b6f9-e64670f45d7f
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=1f07e142-b93a-415a-b6f9-e64670f45d7f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1f07e142-b93a-415a-b6f9-e64670f45d7f
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=1f07e142-b93a-415a-b6f9-e64670f45d7f ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1f07e142-b93a-415a-b6f9-e64670f45d7f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=1f07e142-b93a-415a-b6f9-e64670f45d7f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1f07e142-b93a-415a-b6f9-e64670f45d7f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=1f07e142-b93a-415a-b6f9-e64670f45d7f ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set adc02f38-0da0-4920-acaf-e20998f61ef8
    linux /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=adc02f38-0da0-4920-acaf-e20998f61ef8 ro
    initrd /boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae (recovery mode) (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set adc02f38-0da0-4920-acaf-e20998f61ef8
    linux /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=adc02f38-0da0-4920-acaf-e20998f61ef8 ro single
    initrd /boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Windows Vista (loader) (on /dev/sdb2)" {
    insmod ntfs
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set e2bccd2fbcccfed3
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1f07e142-b93a-415a-b6f9-e64670f45d7f /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6385bd1c-05c7-4efb-b8af-5c8e398aafd9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  10.5GB: boot/grub/core.img
  10.4GB: boot/grub/grub.cfg
  10.5GB: boot/initrd.img-2.6.31-14-generic
  10.5GB: boot/initrd.img-2.6.31-20-generic
  10.4GB: boot/vmlinuz-2.6.31-14-generic
  10.4GB: boot/vmlinuz-2.6.31-20-generic
  10.5GB: initrd.img
  10.5GB: initrd.img.old
  10.4GB: vmlinuz
  10.4GB: vmlinuz.old

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="${saved_entry}"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 1f7980ab-2d0f-419a-b5b3-ca9d080f04a8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  #set gfxpayload=keep
  #set gfxpayload=1024x768x16
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 1f7980ab-2d0f-419a-b5b3-ca9d080f04a8
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=1f7980ab-2d0f-419a-b5b3-ca9d080f04a8 ro   
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 1f7980ab-2d0f-419a-b5b3-ca9d080f04a8
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=1f7980ab-2d0f-419a-b5b3-ca9d080f04a8 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 1f7980ab-2d0f-419a-b5b3-ca9d080f04a8
    linux    /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=1f7980ab-2d0f-419a-b5b3-ca9d080f04a8 ro   
    initrd    /boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 1f7980ab-2d0f-419a-b5b3-ca9d080f04a8
    linux    /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=1f7980ab-2d0f-419a-b5b3-ca9d080f04a8 ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-20-generic (on /dev/sda1)" {
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1f07e142-b93a-415a-b6f9-e64670f45d7f
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=1f07e142-b93a-415a-b6f9-e64670f45d7f ro quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode) (on /dev/sda1)" {
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1f07e142-b93a-415a-b6f9-e64670f45d7f
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=1f07e142-b93a-415a-b6f9-e64670f45d7f ro single
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda1)" {
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1f07e142-b93a-415a-b6f9-e64670f45d7f
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=1f07e142-b93a-415a-b6f9-e64670f45d7f ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda1)" {
    saved_entry=${chosen}
    save_env saved_entry
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1f07e142-b93a-415a-b6f9-e64670f45d7f
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=1f07e142-b93a-415a-b6f9-e64670f45d7f ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Windows Vista (loader) (on /dev/sdb2)" {
    saved_entry=${chosen}
    save_env saved_entry
    insmod ntfs
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set e2bccd2fbcccfed3
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=1f7980ab-2d0f-419a-b5b3-ca9d080f04a8 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=6563d67a-4c68-4802-b782-cd246273edcd none            swap    sw              0       0
# swap was on /dev/sda5 during installation
UUID=6385bd1c-05c7-4efb-b8af-5c8e398aafd9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 175.8GB: boot/grub/core.img
 175.7GB: boot/grub/grub.cfg
 175.8GB: boot/initrd.img-2.6.31-15-generic-pae
 175.8GB: boot/initrd.img-2.6.31-20-generic-pae
 175.8GB: boot/vmlinuz-2.6.31-15-generic-pae
 175.8GB: boot/vmlinuz-2.6.31-20-generic-pae
 175.8GB: initrd.img
 175.8GB: initrd.img.old
 175.8GB: vmlinuz
 175.8GB: vmlinuz.old
```there

the boot directory is correct, well, the 3rd one is, I checked

I doubt this is it, but my windows OS is 64 bit, could that affect anything (I doubt it would though)

---

### Post by oldfred on 2010-03-30
Just for future and to be sure windows is ok. I would in BIOS temporarily make sdb the first drive and use the win7 CD/DVD to repair windows including the fixmbr so sdb will boot windows as a stand alone drive. The old grub (0.97) you have in the MBR of sdb is not doing anything anyway.


Switch drives back and boot Ubuntu, after updating windows I would first try:
sudo update-grub

If that does not work then I would manually add a new entry to 40_custom and run the sudo update-grub. Windows has to be the first drive to work but is is the second so grub has to make it think it is first. The drivemap command switches drive order so windows then thinks it is first.

/etc/grub.d/40_custom
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
    insmod ntfs
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set E2BCCD2FBCCCFED3
    drivemap -s (hd1) ${root}
    chainloader +1
}

---

### Post by razor180 on 2010-03-30
I already made the other hard drive the primary drive, it didn't work. also, I don't have the disc with me, and I have no way of making a new one (I got it from the MSDN site, and I could get another one from there, if I was able to use internet explorer, I'll just have to wait till I get it back). The problem when I tried to boot the primary drive was the GRUB remnant, but for some odd reason, when I first installed windows 7, I was able to bypass that, as well as boot to my primary drive even though windows was on my secondary and still boot to windows automatically (no OS chooser)

and that old grub is a remnant I never figured out just how to destroy from an old ubuntu studio OS that I installed on that HDD before I got my 500GB HDD

It didn't work

however, I just found my windows 7 disc, I'll let you know how that works

okay, I just repaired startup, but what's strange is that in the startup repair, it listed my windows 7 professional OS as windows vista home premium, which is what I switched from and recycled the partition from

I just updated grub, I'll try booting into windows now

---

### Post by razor180 on 2010-03-30
IT WORKED!!!

thank you all

I'm not sure if it deleted that grub remnant but as long as I boot into my other hard drive and run grub (now) it should be fine

thank you

one odd thing though, it pulled up the vista splash screen, then loaded windows 7

but it's working now and I'm happy :D

thanks everyone

---

### Post by Slonda828 on 2010-03-30
Community man! Now find someone else and help them before you run along and never participate again ;)

---

