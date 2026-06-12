---
title: "Boot freezed when external HDD turned on"
date: 2010-09-03
forum: General Help
---

### Post by izd on 2010-09-03
[FONT=Arial][SIZE=4]HI EVERYBODY,

I come from the French Ubuntu community (ubuntu-fr.org).
Nobody has any idea to solve my problem so I told myself that maybe our friends across the Atlantic could help me.

Here is my problem:

[/SIZE][/FONT][FONT=Arial][SIZE=4]When i start or reboot my computer, it crashes (freezes) after the grub menu if the external drive is connected **AND** turned on.[/SIZE][/FONT][FONT=Arial][SIZE=4][COLOR=#000000]

[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=4]Subsequently, I have no problem with the external hard drive.

The HDD is formated in NTFS, no boot loader, no OS installed on.

[/SIZE][/FONT][FONT=Arial Black][SIZE=3]Does anyone have a clue ?[/SIZE][/FONT]

[FONT=Comic Sans MS][SIZE=4]Thank you in advance.[/SIZE][/FONT]

---

### Post by izd on 2010-10-15
UUUuuppp !!!

---

### Post by sikander3786 on 2010-10-15
> When i start or reboot my computer, it crashes (freezes) after the grub menu if the external drive is connected AND turned on.

Hi.

I couldn't exactly understand the problem. Ubuntu is installed on the internal HDD or the external one?

What is the external driver intended for? Data storage?

Do you mean that you can boot without any problems when the external HDD is disconnected and can't boot when you plug it in?

---

### Post by izd on 2010-10-15
Thank you [sikander3786]("http://ubuntuforums.org/member.php?u=806649") to care about my problem.

Ubuntu is installed on internal HDD.

Boot freeze if EXTERNAL HDD pluged & connected.

---

### Post by VMC on 2010-10-15
> **izd said:**
> ...When i start or reboot my computer, it crashes (freezes) after the grub menu if the external drive is connected **AND** turned on. Subsequently, I have no problem with the external hard drive.

The HDD is formated in NTFS, no boot loader, no OS installed on.

...

With that external hard drive installed run [_Boot_info_script_]("http://sourceforge.net/projects/bootinfoscript/") and paste the RESULTS.txt file back here between CODES (#). Then we might be able to figure it all out.

---

### Post by izd on 2010-10-15
no RESULTS.txt file anywhere ?!?!!!
What is the syntax to launch the script ? (sudo sh **[[B][COLOR=Blue]boot_info_script[/COLOR]**]("http://sourceforge.net/projects/bootinfoscript/")[/B])

---

### Post by sikander3786 on 2010-10-15
```
sudo bash [path/to/the/download_folder]/boot_info_script*.sh
```

For details,

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by izd on 2010-10-15
Here's the result :

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disque /dev/sda: 40.0 Go, 40007761920 octets
255 têtes, 63 secteurs/piste, 4864 cylindres, total 78140160 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    74,840,063    74,838,016  83 Linux
/dev/sda2          74,842,110    78,139,391     3,297,282   5 Extended
/dev/sda5          74,842,112    78,139,391     3,297,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disque /dev/sdb: 250.1 Go, 250059350016 octets
255 têtes, 63 secteurs/piste, 30401 cylindres, total 488397168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disque /dev/sdc: 500.1 Go, 500107862016 octets
255 têtes, 63 secteurs/piste, 60801 cylindres, total 976773168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    67,103,504    67,103,442   7 HPFS/NTFS
/dev/sdc2          67,103,505   976,768,064   909,664,560   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e31b163f-2be8-4c9c-ab1d-7441162567b5   ext4       hd-main-pc27                  
/dev/sda2: PTTYPE="dos" 
/dev/sda5        6f85d270-eea0-44ae-bb17-28c8be1cd346   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2E9449BA944984F5                       ntfs       HD3_BACKUP                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        F21833CA18338D1B                       ntfs       HD2_BOOT                      
/dev/sdc2        30E86941E8690706                       ntfs       HD2_DATA                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/HD3_BACKUP        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/HD2_BOOT          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc2        /media/HD2_DATA          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set e31b163f-2be8-4c9c-ab1d-7441162567b5
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
search --no-floppy --fs-uuid --set e31b163f-2be8-4c9c-ab1d-7441162567b5
set locale_dir=($root)/boot/grub/locale
set lang=fr
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
menuentry 'Ubuntu, avec Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e31b163f-2be8-4c9c-ab1d-7441162567b5
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=e31b163f-2be8-4c9c-ab1d-7441162567b5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-25-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e31b163f-2be8-4c9c-ab1d-7441162567b5
    echo    'Chargement de Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=e31b163f-2be8-4c9c-ab1d-7441162567b5 ro single 
    echo    'Chargement du disque mémoire initial...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e31b163f-2be8-4c9c-ab1d-7441162567b5
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e31b163f-2be8-4c9c-ab1d-7441162567b5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-24-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e31b163f-2be8-4c9c-ab1d-7441162567b5
    echo    'Chargement de Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e31b163f-2be8-4c9c-ab1d-7441162567b5 ro single 
    echo    'Chargement du disque mémoire initial...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e31b163f-2be8-4c9c-ab1d-7441162567b5
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e31b163f-2be8-4c9c-ab1d-7441162567b5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-21-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e31b163f-2be8-4c9c-ab1d-7441162567b5
    echo    'Chargement de Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e31b163f-2be8-4c9c-ab1d-7441162567b5 ro single 
    echo    'Chargement du disque mémoire initial...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e31b163f-2be8-4c9c-ab1d-7441162567b5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e31b163f-2be8-4c9c-ab1d-7441162567b5
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/core.img
   9.0GB: boot/grub/grub.cfg
   2.3GB: boot/initrd.img-2.6.32-21-generic
   8.6GB: boot/initrd.img-2.6.32-24-generic
  10.1GB: boot/initrd.img-2.6.32-25-generic
   2.2GB: boot/vmlinuz-2.6.32-21-generic
   6.5GB: boot/vmlinuz-2.6.32-24-generic
   8.4GB: boot/vmlinuz-2.6.32-25-generic
  10.1GB: initrd.img
   8.6GB: initrd.img.old
   8.4GB: vmlinuz
   6.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  66 5a 7a 68 73 78 4b 7a  36 63 67 47 4c 76 6a 43  |fZzhsxKz6cgGLvjC|
00000010  79 34 0d 0a 30 51 71 70  53 79 4d 4c 41 55 58 46  |y4..0QqpSyMLAUXF|
00000020  69 4f 53 4d 65 30 70 73  6e 43 45 2b 4c 6a 52 55  |iOSMe0psnCE+LjRU|
00000030  71 4b 6f 6d 70 69 75 5a  43 51 36 53 6a 45 6f 32  |qKompiuZCQ6SjEo2|
00000040  66 54 52 6c 34 42 4b 78  58 45 35 6b 53 43 4a 42  |fTRl4BKxXE5kSCJB|
00000050  64 45 2f 72 42 4e 54 54  4e 70 41 48 0d 0a 38 59  |dE/rBNTTNpAH..8Y|
00000060  66 71 70 49 47 49 4a 6b  4b 65 39 75 56 49 35 77  |fqpIGIJkKe9uVI5w|
00000070  52 7a 77 67 34 46 6a 48  43 67 69 61 67 75 70 4b  |Rzwg4FjHCgiagupK|
00000080  34 6a 68 38 41 59 6d 38  61 4d 44 7a 45 34 33 78  |4jh8AYm8aMDzE43x|
00000090  47 52 69 6f 44 77 7a 2f  44 37 2f 65 7a 45 4a 71  |GRioDwz/D7/ezEJq|
000000a0  46 76 70 63 5a 6c 0d 0a  2b 75 56 55 79 58 39 79  |FvpcZl..+uVUyX9y|
000000b0  2b 76 45 41 39 6d 32 63  6c 49 76 69 2f 48 57 31  |+vEA9m2clIvi/HW1|
000000c0  43 4c 57 5a 73 47 65 72  58 74 4d 6c 47 6b 5a 73  |CLWZsGerXtMlGkZs|
000000d0  66 4f 54 63 2b 47 4d 57  4e 33 58 52 5a 61 63 48  |fOTc+GMWN3XRZacH|
000000e0  69 65 75 31 41 6f 48 4f  54 69 58 71 2f 44 6e 6c  |ieu1AoHOTiXq/Dnl|
000000f0  0d 0a 49 70 2b 58 46 4a  72 77 4f 2f 61 49 68 78  |..Ip+XFJrwO/aIhx|
00000100  71 33 33 56 69 76 45 78  4a 7a 64 7a 2f 59 46 59  |q33VivExJzdz/YFY|
00000110  64 48 65 37 64 43 46 65  76 33 6b 70 62 64 4d 4c  |dHe7dCFev3kpbdML|
00000120  4c 55 73 54 56 35 72 61  55 34 57 47 41 34 55 41  |LUsTV5raU4WGA4UA|
00000130  64 30 6f 74 6d 42 6d 70  31 78 0d 0a 67 69 43 35  |d0otmBmp1x..giC5|
00000140  46 6e 75 66 61 6d 70 47  47 72 39 49 71 51 67 65  |FnufampGGr9IqQge|
00000150  56 52 79 73 71 38 65 58  44 46 2f 4c 72 55 30 36  |VRysq8eXDF/LrU06|
00000160  79 4b 30 7a 65 58 38 54  42 32 53 4d 56 64 4e 76  |yK0zeX8TB2SMVdNv|
00000170  69 6e 7a 65 73 74 45 61  6b 33 66 47 69 56 44 4f  |inzestEak3fGiVDO|
00000180  2b 73 75 64 0d 0a 57 4b  4c 4b 35 73 49 74 43 50  |+sud..WKLK5sItCP|
00000190  53 52 54 54 31 6b 67 52  6f 53 50 4e 4e 2f 74 68  |SRTT1kgRoSPNN/th|
000001a0  70 70 74 47 4a 38 31 59  6b 69 72 76 62 6d 35 6f  |pptGJ81Ykirvbm5o|
000001b0  76 37 67 48 59 4a 33 49  43 31 6a 57 30 37 00 fe  |v7gHYJ3IC1jW07..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 50 32 00 00 00  |...........P2...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Forget about HD3_BACKUP disk. It is not concerned by my problem.

---

### Post by VMC on 2010-10-15
It looks ok at first glance. The only thing suspicious is the mount content. Why the media mounts?:


```
/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/HD3_BACKUP        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/HD2_BOOT          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc2        /media/HD2_DATA          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
```

Also, which is the external drive that causes the freeze problem?

---

### Post by izd on 2010-10-15
media/HD3_BACKUP is an external hdd mounted at this moment to...backup 

/media/HD2_BOOT & /media/HD2_DATA are the two partitions of the external HDD witch cause the freeze at boot time when the hard disk is plugged AND connected.
The meaning of my problem !

---

### Post by VMC on 2010-10-15
> **izd said:**
> media/HD3_BACKUP is an external hdd mounted at this moment to...backup 

/media/HD2_BOOT & /media/HD2_DATA are the two partitions of the external HDD witch cause the freeze at boot time when the hard disk is plugged AND connected.
The meaning of my problem !

I realized after I hung up that the media mounts were because they were plugged in.

Nothing else looks wrong. So if you have to have HD2 plugged in grub freezes? Is that correct.

---

### Post by izd on 2010-10-15
YES ! 
That is the situation. If HD2 plugged AND connected, GRUB freeze.
It is so strange because the boot starts well but crash...

---

### Post by VMC on 2010-10-15
> **izd said:**
> YES ! 
That is the situation. If HD2 plugged AND connected, GRUB freeze.
It is so strange because the boot starts well but crash...

With HD2 plugged in, can you type 'c' from the grub menu, then type 'ls', to list partitions or is it frozen?

When you say crash, do you mean its not frozen but you can start ubuntu, but it crashes.

---

### Post by izd on 2010-10-15
I just now reboot the pc.
GRUB menu appears, 
i choose my kernel,
black screen with blink cursor in upper left side

nothing else

no hdd led activity (pc or HD2)

no reaction when striking 'c' key or anyone

Ctrl+Alt+Del don't works

---

### Post by izd on 2010-10-15
Sorry...
I don't understand what you saids first time...(froggy tries to speak english)
I reboot and type 'c' IN grub menu...not after...

---

### Post by VMC on 2010-10-15
> **izd said:**
> I just now reboot the pc.
GRUB menu appears, 
i choose my kernel,
black screen with blink cursor in upper left side

nothing else

no hdd led activity (pc or HD2)

no reaction when striking 'c' key or anyone

Ctrl+Alt+Del don't works

I guess what I'm asking is, don't choose anything. When the grub menu appears, type 'c' by itself and see if that takes you to the grub> command prompt.

---

### Post by izd on 2010-10-15
You will be happy, i have new informations, strange but informations...
In fact, i reboot twice because the first time i typed 'c' key to enter grub command line, 'ls' seems to freeze the pc.
Because i'm working on another machine, i don't remember exactly if i do a ctrl+alt+del or not (it is 11 pm for me) but the pc reboot itself...
So, i reenter in grub command line, typed 'ls' and...system hang...
I wait with my eyes screw onto the screen and after 1 or 2 minutes, the return of 'ls' :
(hd0) (hd0,5) (hd0,1)
Next, i reboot to answer to you and try to let the HD2 plugged and connected until grub menu.
At this time, before selecting the kernel, i disconnected the HD2.
I had two ways, boot freeze as usual or not...and it didn't !
This means that the problem occurs after kernel selection. Something is done, checked that cause the failure if the HD2 is plugged and connected.

---

