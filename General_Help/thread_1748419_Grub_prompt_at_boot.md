---
title: "Grub prompt at boot"
date: 2011-05-02
forum: General Help
---

### Post by TempusT on 2011-05-02
Hi there,

Not sure if this is exactly the right thread but here goes.

First, I am a more or less complete/total newb with ubuntu, I have it on a let's say third emergency computer but I do like the way it works.  Until today at least.

I get the same gnub prompt at boot up that I think this thread is dealing with.  I seems that most of this is somehow related to dual-booting though and I don't do that.
I upgraded to the newest version and when this started.  Some other threads have pointed to the computer gong into standby as maybe causing this (seems I have upgraded before and this wasn't a problem, maybe I was just lucky).

I found this in another thread and it gets me into the OS and everything is running just fine but can't get it to boot normally. 
< linus /vmlinuz root=/dev/sdal loop=/ubuntu/disks/root.disk ro quit splash initrd /initrd.img
boot >

Can someone tell me how to proceed from this point?  Can someone make it simple?  Well relatively, I mean I can follow directions most of the time even though I'm not sure what is always being talked about. 

Any help would be greatly appreciated.  If more info is required please just tell me.

Tempus

---

### Post by TempusT on 2011-05-02
@ bcbc  Real noob here, I will look back on the other posts and try to find out what that is.  Trying other "things" and now I'm locked at > Alert! /dev/sdal does not exist. Dropping to Shell!< Then BusyBox and so on and then a prompt with (initramfs) in front of it.  Thanks for looking

---

### Post by bcbc on 2011-05-02
> **TempusT said:**
> @ bcbc  Real noob here, I will look back on the other posts and try to find out what that is.  Trying other "things" and now I'm locked at > Alert! /dev/sdal does not exist. Dropping to Shell!< Then BusyBox and so on and then a prompt with (initramfs) in front of it.  Thanks for looking

Check this out: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If you get your current install booting you can run it from there, otherwise insert an ubuntu cd and select "Try without installing", then follow the instructions on that site.

---

### Post by TempusT on 2011-05-02
No still no luck getting back in, i have no idea wth I did.
Got a new cd, here you go.
```


                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 271095 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 11.04
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

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 274495 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb1 starts at sector 0. But according to the info 
                       from fdisk, sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   228,428,234   228,428,172  83 Linux
/dev/sda2         228,428,235   234,436,544     6,008,310   5 Extended
/dev/sda5         228,428,298   234,436,544     6,008,247  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,108,029    78,107,967   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        67f06a81-b526-4396-983d-14e88d11683a   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B3F5-8558                              vfat       New Volume                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=1e5a42e3-a5cf-4fa4-99dc-a0b3696a2a70 / ext4 errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=67f06a81-b526-4396-983d-14e88d11683a none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   2.8GB: boot/grub/grub.cfg
   1.4GB: boot/initrd.img-2.6.31-20-generic
   6.0GB: boot/initrd.img-2.6.32-25-generic
   7.2GB: boot/initrd.img-2.6.35-25-generic
   9.1GB: boot/initrd.img-2.6.38-8-generic
    .8GB: boot/vmlinuz-2.6.31-20-generic
   4.3GB: boot/vmlinuz-2.6.32-25-generic
   1.1GB: boot/vmlinuz-2.6.35-25-generic
   7.8GB: boot/vmlinuz-2.6.38-8-generic
   9.1GB: initrd.img
   7.2GB: initrd.img.old
   7.8GB: vmlinuz
   1.1GB: vmlinuz.old

```

 #  Hope this helps somehow!  Thank You!

---

### Post by bcbc on 2011-05-03
TempusT,

You do not have a wubi install. For any Wubi users, do NOT try this sort of fix.

Boot a live cd, drop to a terminal (CTRL+ALT+t):
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

If that doesn't fix it, please create a new thread with a new bootinfoscript results and post back here with a link to the new thread.

PS please also edit your last post and place a [CODE[SIZE="1"] [/SIZE]] before and a [/CODE] after the bootinfoscript. Thanks

---

### Post by TempusT on 2011-05-03
Not sure if I did the edit right, sorry.  About your suggestion...  Looked it up and;  "Wubi is an Ubuntu installer for Windows that lets you install and uninstall Ubuntu from a Windows desktop"  This is a stand alone install of ubuntu, no Widows involved.  Should I still try this?  Just being careful, that's why I'm asking.  I will check back tomorrow, it's late.  Thank you again!

---

### Post by bcbc on 2011-05-03
> **TempusT said:**
> Not sure if I did the edit right, sorry.  About your suggestion...  Looked it up and;  "Wubi is an Ubuntu installer for Windows that lets you install and uninstall Ubuntu from a Windows desktop"  This is a stand alone install of ubuntu, no Widows involved.  Should I still try this?  Just being careful, that's why I'm asking.  I will check back tomorrow, it's late.  Thank you again!

Yes that's what I said - if you read carefully what I wrote. Please create a new thread and include the bootinfoscript. Thanks

---

### Post by TempusT on 2011-05-03
bcbc

I was just checking before proceeding...

Those commands did whatever they were supposed to.

I wasn't sure what to pick but I went with the highest I guess "version" number to boot to and it booted up.

Powered down a number of times now and it appears to have cleared up the issue.

Boots up to the new version, and everything seems to work fine.

Wish I knew what actually went wrong, maybe the sleep mode thing during the upgrade had something to do with it.

THANK YOU for all the help!

---

### Post by bcbc on 2011-05-03
> **TempusT said:**
> bcbc

I was just checking before proceeding...

Those commands did whatever they were supposed to.

I wasn't sure what to pick but I went with the highest I guess "version" number to boot to and it booted up.

Powered down a number of times now and it appears to have cleared up the issue.

Boots up to the new version, and everything seems to work fine.

Wish I knew what actually went wrong, maybe the sleep mode thing during the upgrade had something to do with it.

THANK YOU for all the help!
Great! Always pick the highest (first entry) unless it is not working, in which case, try recovery to repair (second highest) - if that fails use a lower one (but in your case that will be a Maverick kernel). Grub2 changed **significantly** between 10.10 and 11.04 and if you somehow didn't get the bootloader updated (in the drive MBR) - which is what those commands I gave you did - then it most likely would not work (as you experienced).

Good luck!

PS for Wubi users - the instructions above do not apply. NEVER install Grub to the drive MBR.
PPS Rubi1200 - you might consider separating TempusT's posts and my responses to a separate thread to avoid confusion.

---

