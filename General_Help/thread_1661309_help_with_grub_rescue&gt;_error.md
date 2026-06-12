---
title: "help with grub rescue&gt; error"
date: 2011-01-06
forum: General Help
---

### Post by munnster on 2011-01-06
[SIZE=3]I tried booting into my ubuntu 10.4 this morning and got 
error: unknown file system[/SIZE]
[SIZE=3]grub rescue>[/SIZE]

[SIZE=3]I ran boot info script and got this:
```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => HP/Gateway is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

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
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   151,150,591   151,148,544  83 Linux
/dev/sda2         151,152,638   156,301,311     5,148,674   5 Extended
/dev/sda5         151,152,640   156,301,311     5,148,672  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *      9,317,700   312,560,639   303,242,940   7 HPFS/NTFS
/dev/sdb2                  63     9,317,699     9,317,637   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

```How do I go about getting Grub up and running? Do I follow instructions here [http://ubuntuforums.org/showthread.php?t=1634902&highlight=grub-install+--reinstall](http://ubuntuforums.org/showthread.php?t=1634902&highlight=grub-install+--reinstall)
I am using the live cd right now, but I do not understand what "mount ubuntus partition" means--I mean how do I do that?  If I am going in the wrong direction, please let me know. I don't want to lose all the information I have on my Ubuntu drive. (Many apologies if this has all been covered a million times, I just don't want to do the wrong thing.)

Thank you so much for any help.[/SIZE]

---

### Post by Rubi1200 on 2011-01-06
You have a problem with your Ubuntu install which is on, I assume, sda1:
[SIZE=3]> [/SIZE]Mounting failed:
mount: unknown filesystem type ''

Please try and describe the events that led up to the current situation.

Updates, power failures, anything you think might be relevant.

Right now, reinstalling GRUB will not help so please do not do that.

---

### Post by munnster on 2011-01-06
I can't think of anything out of the ordinary. The only issue I have been having is when I shut down, Ubuntu restarts. This however has been an off and on problem depending on what updates install (or at least it seems to be linked to that). So to shut down I have been holding the power button down which I believe I found as a setting somewhere--that holding it would turn it off (as no other solution has worked for me in the past).

I had been searching on the forum and someone said something about checking disk utility and it says the disk itself is supposedly healthy, so I thought my grub got screwed up. (And yes, Ubuntu is supposed to be on sda1.) 

Is my disk actually toast?

---

### Post by drs305 on 2011-01-06
From the LiveCd, try to run a disk check on the sda1 partition. I'm not talking about checking the health, but running the e2fsck or fsck check to repair any problems. You can do this in either Gparted (highlight sda1, Partition, Check) or Disk Utilitiy (System, Administration, Disk Utility: highlight sda1, then Check Filesystem.

---

### Post by munnster on 2011-01-06
[SIZE=3]on GParted (by way of system, administration,GParted), I highlighted sda1, but when I go up to partition, "check" is not able to be clicked on.

In Disk Utility, I have a list on the left that says Local Storage and my drive is not listed as sda1, it is only listed as "80GB Hard Disk" but I do not see anything labeled "check file system". On the right side of the window (Drive; Model; Serial Number etc) and the only things I can click are "benchmark" "smart data". When I click Smart Data, it gives me a list "Read Error Rate, Spinup Time, Start/Stop count, Reallocated sector count, seek error rate, etc. are you looking for something in there or am I missing something?[/SIZE]

---

### Post by Rubi1200 on 2011-01-06
Again from the LiveCD, try these commands in the terminal (Applications > Accessories >Terminal)

```
sudo e2fsck -C0 -p -f -v /dev/sda1
```

if the first command reports errors, run this:

```
sudo e2fsck -f -y -v /dev/sda1
```

Reboot, taking out the CD, and see if you can get in again.

---

### Post by munnster on 2011-01-06
[SIZE=3]The first code gave me an error of some kind (sorry I did not write it down) and the second seemed to work. I think it said "sda1 was modified" after it ran through it's thing. But when I rebooted (without the disk) although I DID get the grub menu back, when it was supposed to load my OS, I got a black screen with this message:

/sbin/init: error while loading shared libraries: /lib/libnih.so.1: cannot read file data: Error 21
[       3.569176] Kernel panic-not syncing: attempted to kill init![/SIZE]

[SIZE=3]And when I tried again to start it up, I got another number (I don't know what the numbers mean) [     3.587689][/SIZE]

---

### Post by Rubi1200 on 2011-01-07
Okay, so here is what we need you to do please.

Use the LiveCD again and run the boot info script as before and post the results.

I want to see if the file-system is now being recognized again so we can try some other things.

---

### Post by munnster on 2011-01-07
```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => HP/Gateway is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

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
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   151,150,591   151,148,544  83 Linux
/dev/sda2         151,152,638   156,301,311     5,148,674   5 Extended
/dev/sda5         151,152,640   156,301,311     5,148,672  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *      9,317,700   312,560,639   303,242,940   7 HPFS/NTFS
/dev/sdb2                  63     9,317,699     9,317,637   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5e1398c8-0285-4675-bbe4-066efad602d2   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        5fc3c2fd-9b5c-473d-9309-94cac27db222   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        06FC6325FC630DED                       ntfs                                     
/dev/sdb2        423B-2BDF                              vfat       RECOVERY                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 5e1398c8-0285-4675-bbe4-066efad602d2
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 5e1398c8-0285-4675-bbe4-066efad602d2
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 5e1398c8-0285-4675-bbe4-066efad602d2
insmod tga
if background_image /boot/grub/Lake_mapourika_NZ.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5e1398c8-0285-4675-bbe4-066efad602d2
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=5e1398c8-0285-4675-bbe4-066efad602d2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5e1398c8-0285-4675-bbe4-066efad602d2
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=5e1398c8-0285-4675-bbe4-066efad602d2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5e1398c8-0285-4675-bbe4-066efad602d2
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=5e1398c8-0285-4675-bbe4-066efad602d2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5e1398c8-0285-4675-bbe4-066efad602d2
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=5e1398c8-0285-4675-bbe4-066efad602d2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5e1398c8-0285-4675-bbe4-066efad602d2
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=5e1398c8-0285-4675-bbe4-066efad602d2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5e1398c8-0285-4675-bbe4-066efad602d2
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=5e1398c8-0285-4675-bbe4-066efad602d2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5e1398c8-0285-4675-bbe4-066efad602d2
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5e1398c8-0285-4675-bbe4-066efad602d2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 06fc6325fc630ded
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


  41.2GB: boot/grub/grub.cfg
  60.2GB: boot/initrd.img-2.6.32-21-generic
  60.3GB: boot/initrd.img-2.6.32-23-generic
  60.5GB: boot/initrd.img-2.6.32-24-generic
  63.2GB: boot/initrd.img-2.6.32-25-generic
  37.6GB: boot/initrd.img-2.6.32-26-generic
  63.3GB: boot/initrd.img-2.6.32-27-generic
  60.2GB: boot/vmlinuz-2.6.32-21-generic
  60.4GB: boot/vmlinuz-2.6.32-22-generic
  60.4GB: boot/vmlinuz-2.6.32-24-generic
  60.4GB: boot/vmlinuz-2.6.32-25-generic
  63.2GB: boot/vmlinuz-2.6.32-26-generic
  63.3GB: boot/vmlinuz-2.6.32-27-generic
  63.3GB: initrd.img
  37.6GB: initrd.img.old
  63.3GB: vmlinuz
  63.2GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  00 00 c0 00 10 00 c0 00  20 00 c0 00 fe 17 b1 18  |........ .......|
00000010  b7 00 04 00 00 00 00 00  00 00 00 00 78 18 f8 cf  |............x...|
00000020  01 00 c0 00 11 00 c0 00  20 02 c0 00 3d 00 00 20  |........ ...=.. |
00000030  00 00 05 00 00 00 00 00  00 00 00 00 00 20 b5 73  |............. .s|
00000040  02 00 c0 00 12 00 c0 00  20 04 c0 00 42 00 00 20  |........ ...B.. |
00000050  00 00 05 00 00 00 00 00  00 00 00 00 00 20 f2 1e  |............. ..|
00000060  03 00 c0 00 13 00 c0 00  20 06 c0 00 00 00 00 20  |........ ...... |
00000070  00 00 05 00 00 00 00 00  00 00 00 00 00 20 9d d2  |............. ..|
00000080  05 00 c0 00 15 00 c0 00  20 0a c0 00 00 00 00 20  |........ ...... |
00000090  00 00 05 00 00 00 00 00  00 00 00 00 00 20 42 d0  |............. B.|
000000a0  04 00 c0 00 14 00 c0 00  20 08 c0 00 00 00 00 20  |........ ...... |
000000b0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 99 70  |............. .p|
000000c0  06 00 c0 00 16 00 c0 00  20 0c c0 00 00 00 00 20  |........ ...... |
000000d0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 2c 71  |............. ,q|
000000e0  07 00 c0 00 17 00 c0 00  20 0e c0 00 00 00 00 20  |........ ...... |
000000f0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 f7 d1  |............. ..|
00000100  09 00 c0 00 19 00 c0 00  20 12 c0 00 00 00 00 20  |........ ...... |
00000110  00 00 05 00 00 00 00 00  00 00 00 00 00 20 fc d5  |............. ..|
00000120  08 00 c0 00 18 00 c0 00  20 10 c0 00 00 00 00 20  |........ ...... |
00000130  00 00 05 00 00 00 00 00  00 00 00 00 00 20 27 75  |............. 'u|
00000140  0a 00 c0 00 1a 00 c0 00  20 14 c0 00 a5 03 00 20  |........ ...... |
00000150  00 00 05 00 00 00 00 00  00 00 00 00 00 20 50 6b  |............. Pk|
00000160  0b 00 c0 00 1b 00 c0 00  20 16 c0 00 7a 30 00 20  |........ ...z0. |
00000170  00 00 05 00 00 00 00 00  00 00 00 00 00 20 64 da  |............. d.|
00000180  0c 00 c0 00 1c 00 c0 00  20 18 c0 00 f4 13 00 20  |........ ...... |
00000190  00 00 05 00 00 00 00 00  00 00 00 00 00 20 c2 41  |............. .A|
000001a0  0d 00 c0 00 1d 00 c0 00  20 1a c0 00 2e 19 00 20  |........ ...... |
000001b0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 24 60  |............. $`|
000001c0  0f 00 c0 00 1f 00 c0 00  20 1e c0 00 61 38 00 20  |........ ...a8. |
000001d0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 ff f8  |............. ..|
000001e0  0e 00 c0 00 1e 00 c0 00  20 1c c0 00 e9 36 00 20  |........ ....6. |
000001f0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 eb b1  |............. ..|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by drs305 on 2011-01-07
> **munnster said:**
> [       3.569176] Kernel panic-not syncing: attempted to kill init!

And when I tried again to start it up, I got another number (I don't know what the numbers mean) [     3.587689]

The number is just a timer noting the time of the message in seconds.

Try booting from the grub prompt without the CD. To get to the prompt, press "c" at the Grub menu. If you don't see the menu, hold down the SHIFT key during boot.

At the grub prompt:
```
set root=(hd0,1)
set prefix=(hd0,1)/boot/grub
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot

```

If it boots, run:
```
sudo grub-install --recheck /dev/sda
sudo update-grub
```
Reboot and see if G2 now works.

---

### Post by munnster on 2011-01-07
[SIZE=3]I got through the grub prompt part but it would not boot. I wrote down everything that was on the screen because I wasn't sure if you would want/need all of it or not.

(After what I BELIEVE is basic info on my computer) it said this:
Begin: Running/scripts/local-premount...
done
[3.220646] EXT4-fs(sda1): mounted filesystem with ordered data mode
Begin: running/scripts/local-bottom...
Done
Done
Begin: running/scripts/init-bottom...
Done
/sbin/init; error while loading shared libraries: /lib/libnih.so.1: cannot read file data: Error 21

(times in [ ] at the front of each line)

[ ] kernel panic-not syncing: attempted to kill init!
[ ] Pid:1, comm: init Not tainted 2.6.32-27-generic #49-Ubuntu
[ ] Call Trace:
[ ] [<c058b313>] ? print k+0x1d/0x22
[ ] [<c058b249>] panic+0x48/0xf5
[ ] [<c014efed>] forget_original_parent+0x2bd/0x2c0
[ ] [<c014f003>] exit_notify+0x13/0x170
[ ] [<c0150911>] do_exit+0x181/0x310
[ ] [<c00ade>] do_group_exit+0x3e/0xa0
[ ] [<c0150b58>] sys_exit_group+0x18/0x20
[ ] [<c01033ec>] syscall_call+0x7/0x6
[ ] [<c0590000>] ? do_page_fault+0x270/0x3o0
[/SIZE]

---

### Post by drs305 on 2011-01-07
munnster,

The kernel panic could be caused by files actually missing or Grub2 just looking in the wrong location. Since we can't be sure I would suggest is completely purging and removing Grub2. That will either allow you to boot or Grub as a problem.

You would boot from the LiveCD and then run the 'chroot' procedure from the following guide. The partition to mount would be sda1.
[HOWTO: Purge and Reinstall Grub 2 from the Live CD ]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by munnster on 2011-01-07
[SIZE=3]I must be doing something wrong. I got this:

cp: cannot create regular file `/mnt/temp/etc/resolv.conf': No such file or directory
[/SIZE]

---

### Post by drs305 on 2011-01-07
> **munnster said:**
> [SIZE=3]I must be doing something wrong. I got this:

cp: cannot create regular file `/mnt/temp/etc/resolv.conf': No such file or directory
[/SIZE]

Not every system has or needs that file. If you can connect to the Internet without it just proceed to the next command.

---

### Post by munnster on 2011-01-07
Sorry Drs305, the next command gives me this:

chroot: cannot change root directory to /mnt/temp: Operation not permitted

---

### Post by drs305 on 2011-01-07
> **munnster said:**
> Sorry Drs305, the next command gives me this:

chroot: cannot change root directory to /mnt/temp: Operation not permitted

Without seeing the preceding terminal output I can't be sure what happened. The most likely thing would be that you didn't use 'sudo' at the start of the command. The next would be that the partition wasn't mounted correctly.

If you want to try it again I would reboot (to clear anything that is currently mounted) and copy the commands from the guide (except changing 'sdXY' to 'sda1' ). To copy into the terminal, you should be able to highlight the command with your mouse, then click in the terminal to make it active and finally middle click to paste the command.

---

### Post by munnster on 2011-01-07
[SIZE=3]You were right of course, missed the sudo when I was cutting and pasting but now I get this:
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
/bin/bash: error while loading shared libraries: /lib/libncurses.so.5: invalid ELF header
[/SIZE]

---

### Post by psusi on 2011-01-07
You've made it past grub and now it appears that you have some hard disk corruption.  Fire up the disk utility on the livecd and check the SMART statistics.  Make sure there aren't any pending, reallocated, or offline_uncorrectable sectors.  Then check the filesystem:

```
sudo e2fsck -f /dev/sda1
```

---

### Post by munnster on 2011-01-07
[SIZE=3]I had restarted my system to clear the terminal and when I went to Disk Utility, SMART Status says "Not Supported" I have looked at this status previously (during this issue) so I know it was working[/SIZE]. [SIZE=3]What exactly does this message mean? Do I have to do something to make it start up?

Never mind, I ran a benchmark and it now says it's healthy. How would I know if something is pending? I don't see anything like that on the list at the bottom of that screen.
[/SIZE]

---

### Post by munnster on 2011-01-07
Sorry!
Pending sector count(?) says N/A
Reallocated sector count says "Good"
Uncorrectable sector count says N/A

Do I have to run the self-test to see if those things are "Good" or should it already be registered as good or bad?

---

### Post by munnster on 2011-01-07
ubuntu@ubuntu:~$ sudo e2fsck -f /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 360115/4726784 files (0.3% non-contiguous), 6997239/18893568 blocks

---

### Post by psusi on 2011-01-07
Look at the actual value of those fields rather than just the assessment.  Also running the long test would be a good idea too.

If there still are no bad sectors found after the long self test, and e2fsck found no problems, then you just seem to have some files that are corrupt and need reinstalled.

You got an error with /lib/libncurses.so.5, so if you run dpkg -S /lib/libncurses.so.5, it will tell you that file belongs to libncurses5, so you need to reinstall it.  If you are running from the livecd and have your hd mounted in /mnt, then cd to /var/cache/apt/archives.  Once there, run apt-get install libncurses5 -d --reinstall to force apt to download the package, then you can reinstall it on your hd with sudo dpkg -i libncurses5*.deb --root=/mnt.

---

### Post by munnster on 2011-01-12
Thank you everyone for your help and advice. I had some  help from drs305 and it ends up my home folder (and then some) had been deleted by my 4 year old. Taught me to maker her her own account! So I had to do an entire reinstall.

---

### Post by psusi on 2011-01-12
How did your 4 year old manage to use sudo?  Assuming you even gave her an admin account?

I wouldn't be so quick to blame the kiddo ;)

---

