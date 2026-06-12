---
title: "GRUB 2 error delays startup, doesn't show menu"
date: 2010-10-12
forum: General Help
---

### Post by searchfgold6789 on 2010-10-12
Hi, I'm encountering an unusual problem with GRUB 2.
Whenever I start up my system, my BIOS'es load and do their thing, and then hand the show over to GRUB, which is supposed to not appear or do anything because my GRUB countdown is set to 0, but instead I get two errors like this that appear for about 5 or 10 seconds (greatly delaying startup) and then Xubuntu, the first entry on my Grub menu, loads: (I set GRUB to automatically boot my first entry):
```
error: no suitable mode found
error: unknown command 'terminal'

```
I'm gonna keep googling; if I find a solution I'll post back, otherwise any suggestions would be helpful.
Thank you in advance!
 - search

P.S.
Is there any way to downgrade to Grub Legacy?

---

### Post by Rubi1200 on 2010-10-12
Could you post the output of /etc/default/grub please?

Thanks.

---

### Post by drs305 on 2010-10-12
Please download and run the boot info script and post the content's of the RESULTS.txt it generates. Most likely there is an error in one of the script file parameters.

[_http://bootinfoscript.sourceforge.net/_]("http://bootinfoscript.sourceforge.net/")

---

### Post by searchfgold6789 on 2010-10-12
Here you go. (this is grub.cfg)
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi=force"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
And here's the results from BIS:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2               2,046   219,944,959   219,942,914   5 Extended
/dev/sda5               2,048   218,486,783   218,484,736  83 Linux
/dev/sda6         218,488,832   219,944,959     1,456,128  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 30.0 GB, 30003240960 bytes
255 heads, 63 sectors/track, 3647 cylinders, total 58600080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    42,957,809    42,957,747  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2: PTTYPE="dos" 
/dev/sda5        855ee1d4-73cb-403f-99e3-292348e41b52   ext4                                     
/dev/sda6        fbc356df-4bd5-4af9-8838-3bc65e5d98a8   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c41b529d-77ee-427c-82b3-dff16f2123a2   ext4       Sheet Music                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/sheetmusic        ext4       (rw,noexec,nosuid,nodev)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 855ee1d4-73cb-403f-99e3-292348e41b52
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 855ee1d4-73cb-403f-99e3-292348e41b52
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 855ee1d4-73cb-403f-99e3-292348e41b52
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=855ee1d4-73cb-403f-99e3-292348e41b52 ro acpi=force  quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 855ee1d4-73cb-403f-99e3-292348e41b52
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=855ee1d4-73cb-403f-99e3-292348e41b52 ro single acpi=force
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 855ee1d4-73cb-403f-99e3-292348e41b52
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=855ee1d4-73cb-403f-99e3-292348e41b52 ro acpi=force  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 855ee1d4-73cb-403f-99e3-292348e41b52
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=855ee1d4-73cb-403f-99e3-292348e41b52 ro single acpi=force
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 855ee1d4-73cb-403f-99e3-292348e41b52
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=855ee1d4-73cb-403f-99e3-292348e41b52 ro acpi=force  quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 855ee1d4-73cb-403f-99e3-292348e41b52
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=855ee1d4-73cb-403f-99e3-292348e41b52 ro single acpi=force
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 855ee1d4-73cb-403f-99e3-292348e41b52
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 855ee1d4-73cb-403f-99e3-292348e41b52
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
UUID=855ee1d4-73cb-403f-99e3-292348e41b52 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=fbc356df-4bd5-4af9-8838-3bc65e5d98a8 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=c41b529d-77ee-427c-82b3-dff16f2123a2 /media/sheetmusic ext4 auto,rw,user,noexec 0 2

=================== sda5: Location of files loaded by Grub: ===================


 109.6GB: boot/grub/core.img
  24.2GB: boot/grub/grub.cfg
 109.6GB: boot/initrd.img-2.6.32-21-generic
  17.0GB: boot/initrd.img-2.6.32-24-generic
 110.0GB: boot/initrd.img-2.6.32-25-generic
 109.6GB: boot/vmlinuz-2.6.32-21-generic
 109.8GB: boot/vmlinuz-2.6.32-24-generic
 109.7GB: boot/vmlinuz-2.6.32-25-generic
 110.0GB: initrd.img
  17.0GB: initrd.img.old
 109.7GB: vmlinuz
 109.8GB: vmlinuz.old

```

---

### Post by Rubi1200 on 2010-10-12
Thanks searchfgold6789; much appreciated. Looks normal to me. I suggest you follow the advice posted by drs305 and post the results of the boot-script.

Thanks.

---

### Post by searchfgold6789 on 2010-10-12
I edited it into my previous post <.<

---

### Post by searchfgold6789 on 2010-10-12
Someone must know this....

---

### Post by drs305 on 2010-10-12
I see something in your grub.cfg file that may be the problem:
> 
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
[COLOR="Red"]**    terminal gfxterm**[/COLOR]
  fi


In my grub.cfg, this is 
> terminal_output gfxterm
This is generated from the /etc/grub.d/00_header script. It's possible our Grub2 versions are different but I don't know if the format has changed. My guess is that is the line providing the "terminal" error.


I see 4 paths here:

1. Manually edit /boot/grub/grub.cfg and make the line:
> 
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
[COLOR="Red"]**    terminal_output gfxterm**[/COLOR]
  fi

Don't update-grub or it will overwrite the change. See if the error message goes away and, once confirmed, pin down what is causing it.

2. Purge/reinstall Grub2 to remove all the Grub files and thereby most likely replace the script causing the error. 

3. Post your 00_header file and we can try to find out why it is generating the output the way it is.

4. The terminology in your version of G2 is correct, and it's something completely different.  ;-)

---

### Post by searchfgold6789 on 2010-10-12
Okay i'll try those and post back if any of them work. Thanks so much!

---

### Post by searchfgold6789 on 2010-10-12
Okay!
I tried path number zero and that led me into a tree.
So I tried path number One, and that got rid of the second error message. I think the second message appeared after doing some early-morning repairs trying to get rid of the first one. Now it only says 'error: no suitable mode found'.
Should I try purging, or is there a way to solve the other error as well??????
Eagerly awaiting replies,
 - search

---

### Post by searchfgold6789 on 2010-10-12
I've solved this problem by fixing the grub.cfg lines (which another person trying to fix this problem will probably not have to do) according to drs' instructions, and uncommenting the line in my /etc/default/grub that looks like this:
```
# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
```to this:
```
# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console
```
Thanks for the help!

---

### Post by drs305 on 2010-10-12
I was away and didn't see the intermediate posts. Now that you know how to manually overwrite the grub.cfg file, did you run update-grub after making the second change?

You probably should at some point because eventually the system is going to run "update-grub" for you (new kernel, a new update to grub, etc) - it's better to do it at the time of your choosing.

Just so you know if you haven't seen it yet: When you do run the update or it's run for you, your grub menu will be more like a terminal - no backgrounds, images, etc. You could also try commenting it and seeing if the troublesome line reappears or if it was a one-time error.

In any case, I'm glad you solved it.

---

