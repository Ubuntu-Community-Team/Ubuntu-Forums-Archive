---
title: "Ubuntu no booting"
date: 2010-08-25
forum: General Help
---

### Post by PortaleMedia on 2010-08-25
Hi,

I have windows 7 + Ubuntu 10.04 in dual boot, I noticed that sometimes the ubuntu was not booting.

Right after I select the os in grub (ubuntu) the screen goes black with the blink cursor and nothing happens, that's all no messages it's stuck there forever.

Today, it does this every time I try to enter Ubuntu, it's just stuck there.

What can I do? I'm on windows right now.

---

### Post by PortaleMedia on 2010-08-25
Nobody can help me? srry for double post.

---

### Post by Quackers on 2010-08-25
Can you boot into recovery mode (hold the shift key down while booting)

---

### Post by Rubi1200 on 2010-08-25
What graphics card do you have?

Have you recently installed/upgraded anything?

How did you install Ubuntu?

The more you can tell us that you think might be relevant, the better we can help you.

Thanks.

---

### Post by PortaleMedia on 2010-08-25
Recovery mode stucks at the same point, black screen with blink cursor forever.

I have a EVGA GTX 260 core 216 with the drivers installed (P6X58D-E + i7 930) and I always install all the updates but the problem has been there since the first boot, sometimes it boots right and sometimes it don't.

I installed Win7, then installed ubuntu with the 10.04 live DVD without errors.

I've tried "sudo update-grub" but still the same problem.

I have 2 Samsung Spinpoint F3 500Gb each, one is the OS drive and the other one is only for data backup and other things I need, but both OSs are installed in the first drive.

Thank you very much !

---

### Post by PortaleMedia on 2010-08-25
This is the RESULT.txt I get from executing the "boot info script".

---

### Post by Rubi1200 on 2010-08-25
Hi,
let's try something:

boot the computer and after selecting Ubuntu in the GRUB menu press "e" to edit.

Find the line, using the cursor, that ends with```
 ro quiet splash
```
Remove quiet splash and type nomodeset instead so that it looks like this ```
ro nomodeset
``` Then "Ctrl" + "x" to boot.

If you get in, we can try and find a more permanent solution.

Hope this helps.

---

### Post by Rubi1200 on 2010-08-25
For those concerned:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   859,197,022   858,990,175   7 HPFS/NTFS
/dev/sda3         859,197,438   976,773,119   117,575,682   5 Extended
/dev/sda5         859,197,440   971,878,399   112,680,960  83 Linux
/dev/sda6         971,880,448   976,773,119     4,892,672  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   976,769,023   976,766,976   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        147843227843024A                       ntfs       System Reserved               
/dev/sda2        AE2245DF2245AD61                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        1dfc8260-3021-4093-b9e6-c580a0b69a5e   ext4                                     
/dev/sda6        6b323f01-fe3c-47c5-acd5-56984a006cba   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8A92F4C292F4B3B3                       ntfs       Backup                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
set default="${saved_entry}"
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
search --no-floppy --fs-uuid --set 1dfc8260-3021-4093-b9e6-c580a0b69a5e
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
search --no-floppy --fs-uuid --set 1dfc8260-3021-4093-b9e6-c580a0b69a5e
set locale_dir=($root)/boot/grub/locale
set lang=es
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, con Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1dfc8260-3021-4093-b9e6-c580a0b69a5e
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1dfc8260-3021-4093-b9e6-c580a0b69a5e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    savedefault
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 147843227843024a
    chainloader +1
}
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
UUID=1dfc8260-3021-4093-b9e6-c580a0b69a5e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6b323f01-fe3c-47c5-acd5-56984a006cba none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 476.5GB: boot/grub/core.img
 487.3GB: boot/grub/grub.cfg
 476.6GB: boot/initrd.img-2.6.32-24-generic
 476.5GB: boot/vmlinuz-2.6.32-24-generic
 476.6GB: initrd.img
 476.5GB: vmlinuz
```

---

### Post by PortaleMedia on 2010-08-25
> **Rubi1200 said:**
> 
Find the line, using the cursor, that ends with```
 ro quiet splash
```
Remove quiet splash and type nomodeset instead so that it looks like this ```
ro nomodeset
``` Then "Ctrl" + "x" to boot.


I tried this, and now the boot process shows a lot of text but it still stucks at some point:
```

[   3.495582] 12241 pages shared
[   3.495639] 456 pages shared
[   3.495695] 214824 pages shared
_

```

And nothing more, stuck at the blinking cursor...

Thanks for the help.

---

### Post by Rubi1200 on 2010-08-25
Well, as far as I can tell there are no issues with the bootscript. I still think this might be a graphics issue, but it might also be a memory issue.

How much RAM do you have installed?

---

### Post by PortaleMedia on 2010-08-25
I have 6Gb DDR3 1600 (3x2Gb) Corsair XMS3, the memtest tells everything is ok.

I've noticed that the stuck is always ALWAYYYYYSSSS !!! right before the "plymouth process killed by KILL signal" (aprox.). When it boots succesfuly I see that message, not when boot fails.

I have a problem with that "process" named "plymouth", imho.

:'(

EDIT: some links:
[ [1]("http://www.idontlikethisgame.com/ubuntu/problems-with-plymouth-process-in-ubuntu-10-04-alpha-3/") ] [ [2]("http://ubuntuforums.org/showthread.php?t=1495401&page=3") ] [ [3]("http://ubuntuforums.org/showthread.php?t=1521652") ]

---

### Post by Rubi1200 on 2010-08-25
> **PortaleMedia said:**
> I have 6Gb DDR3 1600 (3x2Gb) Corsair XMS3, the memtest tells everything is ok.

I've noticed that the stuck is always ALWAYYYYYSSSS !!! right before the "plymouth process killed by KILL signal" (aprox.). When it boots succesfuly I see that message, not when boot fails.

I have a problem with that "process" named "plymouth", imho.

:'(

EDIT: some links:
[ [1]("http://www.idontlikethisgame.com/ubuntu/problems-with-plymouth-process-in-ubuntu-10-04-alpha-3/") ] [ [2]("http://ubuntuforums.org/showthread.php?t=1495401&page=3") ] [ [3]("http://ubuntuforums.org/showthread.php?t=1521652") ]
You might be right. So, let's test something else. Can you download and burn another Ubuntu CD, but this time 9.10?
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)
Karmic does not use Plymouth; so you should not experience the same issues.
If the LiveCD works, you may have to consider using Karmic until a solution is found for the issue with Plymouth (if that is the problem).

---

### Post by PortaleMedia on 2010-08-25
> **Rubi1200 said:**
> You might be right. So, let's test something else. Can you download and burn another Ubuntu CD, but this time 9.10?
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)
Karmic does not use Plymouth; so you should not experience the same issues.
If the LiveCD works, you may have to consider using Karmic until a solution is found for the issue with Plymouth (if that is the problem).

I guess that'll be the only solution, I like the new Ubuntu 10, the theme and all the improvements but well, I had problems with the wireless card too so let's go back to 9.10 :'(

Thank you very much for the help !!!

---

