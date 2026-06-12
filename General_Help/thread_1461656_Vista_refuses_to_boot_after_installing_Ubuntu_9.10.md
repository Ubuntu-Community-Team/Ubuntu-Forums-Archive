---
title: "Vista refuses to boot after installing Ubuntu 9.10"
date: 2010-04-24
forum: General Help
---

### Post by CookieMonster. on 2010-04-24
Right so here's how it is... I've used Windows Vista and Windows XP for quite a while before I decided to swap XP for Ubuntu (mainly for the performance). After formatting the drive, where XP was, and installing Ubuntu 9.10 I've discovered that I can't boot into my Vista any more. I used to use a Windows 7 boot loader to switch between Vista and XP (I had Windows 7 installed before Windows Vista) and now it's gone.

I've tried to boot using the GRUB2 that Ubuntu 9.10 uses but I failed. At first it gave me a "no such partition" error whenever I tried to boot it, but after some changes I managed to get it to go in to some sort of a black screen. But it's as far as it goes. :(

I have also tried to repair the Windows boot with a recovery disc. Unfortunately I get a "The volume does not contain a recognised file system." error whenever I try to import the bcd.temp file using bcdedit.exe

I really need Vista back up since it has PhotoShop on it and all other things that I need in order to continue working on my schoolwork, which has to be done in a couple of days.

Please note that I'm completely new to all this Ubuntu/Linux thing so please try to make your replies as simple as possible.

---

### Post by oldfred on 2010-04-24
The XP partition had the Vista boot files and you have to repair the Vista. You may need to set the boot flag on the Vista partition. Boot flag has to be on a primary partition.

If your Vista partition is in an extended/logical partition it is a big problem. Somewhere I did see someone to get it to work but officially windows only boots from a primary partition. Only second installs of windows can be on a logical but have to boot thru the first install on a primary.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by CookieMonster. on 2010-04-24
Thanks for the reply, oldfred.
Looks like I'm in for quite a bit of reading.

---

### Post by oldfred on 2010-04-24
You may want to post this so we can see where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by CookieMonster. on 2010-04-24
I'm back on my old Vista.
I reinstalled a fresh copy of Windows Vista booted from there and installed EasyBCD. Used it to repair my old Vista boot and it works! :)
Now if I delete the newly installed Vista OS will I still be able to boot to the old one? Or will everything disappear along with the new version?

---

### Post by oldfred on 2010-04-24
It depends on what partitions are where. Windows combines boot usually into the first, but it should be the one with the boot flag.The boot script should tell.

---

### Post by CookieMonster. on 2010-04-26
I can't execute the script because it doesn't let me get into my Ubuntu anymore. I add an OS using EasyBCD but it doesen't load. And when I add neogrub it gets me into a grub console. Any ideas?

---

### Post by oldfred on 2010-04-26
I do not know easyBCD, a few here seemed to have used it, but had to use the very newest or beta version of it to get it to work. 

I like grub2 as for most it works. Only a few that have issues give up too quick and go back to old grub or try other boot loaders.

You can run the script from a liveCD, instructions are on the linked page.

---

### Post by CookieMonster. on 2010-04-26
I'll do that whenever I have the time to. I'll post what I get here and we'll see how it goes from there.

---

### Post by Mark Phelps on 2010-04-26
> **CookieMonster. said:**
> I can't execute the script because it doesn't let me get into my Ubuntu anymore. I add an OS using EasyBCD but it doesen't load. And when I add neogrub it gets me into a grub console. Any ideas?

Yes -- since you're having problems with EasyBCD, why not just go to their support forums with your questions?  They have forums and FAQs that will help you.

Check out the NeoSmart Technology forums.

---

### Post by CookieMonster. on 2010-04-30
I reinstalled GRUB2 to get Ubuntu and Vista to dualboot. So the problem remains. Do I need to have that extra operating system in a primary partition ir order for everything to work?

My RESULTS.txt from the boot info script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file 
                       /NST/nst_grub-F2BDB2C988ED414542ACD8DA3E093A3B.mbr is 
                       trying to chain load sector #63 on boot drive #1 
                       BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #63 on boot drive #1
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Boot file info:     BootPart in the file 
                       /NST/nst_grub-6753161B5B0788B63EAEFA208E41DA2D.mbr is 
                       trying to chain load sector #63 on boot drive #1 
                       BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #63 on boot drive #1
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Windows/System32/winload.exe /grldr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   166,690,439   166,690,377  83 Linux
/dev/sda2    *    166,690,816   208,891,903    42,201,088   7 HPFS/NTFS
/dev/sda3         208,893,195   625,121,279   416,228,085   f W95 Ext d (LBA)
/dev/sda5         208,893,258   417,786,389   208,893,132   7 HPFS/NTFS
/dev/sda6         417,786,453   625,121,279   207,334,827   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        f1acda23-d4b7-4c91-ae63-078de9611e7b   ext2                                     
/dev/sda2        4098E99198E9862E                       ntfs                                     
/dev/sda5        22508D2B508D06AF                       ntfs       Local Disk                    
/dev/sda6        00C8511AC8510F72                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext2       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set f1acda23-d4b7-4c91-ae63-078de9611e7b
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
  set timeout=30
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
    search --no-floppy --fs-uuid --set f1acda23-d4b7-4c91-ae63-078de9611e7b
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=f1acda23-d4b7-4c91-ae63-078de9611e7b ro  vga=792 splash  quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f1acda23-d4b7-4c91-ae63-078de9611e7b
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=f1acda23-d4b7-4c91-ae63-078de9611e7b ro single  vga=792 splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f1acda23-d4b7-4c91-ae63-078de9611e7b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f1acda23-d4b7-4c91-ae63-078de9611e7b ro  vga=792 splash  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f1acda23-d4b7-4c91-ae63-078de9611e7b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f1acda23-d4b7-4c91-ae63-078de9611e7b ro single  vga=792 splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows VISTA" {
set root=(hd0,2)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
UUID=f1acda23-d4b7-4c91-ae63-078de9611e7b /               ext2    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  10.4GB: boot/grub/core.img
  10.5GB: boot/grub/grub.cfg
  10.5GB: boot/grub/stage2
  10.4GB: boot/initrd.img-2.6.31-14-generic
  10.4GB: boot/initrd.img-2.6.31-20-generic
  10.3GB: boot/vmlinuz-2.6.31-14-generic
  10.3GB: boot/vmlinuz-2.6.31-20-generic
  10.4GB: initrd.img
  10.4GB: initrd.img.old
  10.3GB: vmlinuz
  10.3GB: vmlinuz.old
```

---

### Post by oldfred on 2010-04-30
You need to reinstall the windows boot loader to the windows boot sector:

    Boot file info:     [COLOR=Blue]BootPart in the file 
                       /NST/nst_grub-F2BDB2C988ED414542ACD8DA3E093A3B.mbr is 
                       trying to chain load sector #63 on boot drive #1 
                       BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #63 on boot drive #1[/COLOR]
    Operating System:  Windows Vista
    Boot files/dirs:   [COLOR=Black][COLOR=Black]/bootmgr[/COLOR] /Boot/BCD[/COLOR] /Windows/System32/winload.exe [COLOR=DarkRed]/grldr[/COLOR]

Instructions here using testdisk to repair:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You can also use windows repairs fixboot command.

The red parts are not standard. Are they from your other boot loader?

---

