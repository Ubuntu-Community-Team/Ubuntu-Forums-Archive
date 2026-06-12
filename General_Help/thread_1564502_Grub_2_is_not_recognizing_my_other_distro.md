---
title: "Grub 2 is not recognizing my other distro"
date: 2010-08-30
forum: General Help
---

### Post by hefaistos2001 on 2010-08-30
Hi! First of all I wish to thank everyone in this forum for your kind and valuable help, that's why I always find my answers without having to start a thread, but this time I'm a bit lost because I didn't find anything matching my particular problem. :confused: Here it goes:

On a new PC I installed Windows7, and after that I installed ubuntu-studio 10.04 x64 and Ubuntu 10.04 x64 using the alternate CD in order to setup different RAID's between 3 HD's (details below).

Now my grub shows up correctly windows7 and ubuntu 10.04 with the different kernel updates (and boots any of them) but _nothing about **ubuntu-studio** is listed there_. I can also mount the ubuntu-studio partition and I see at the /boot directory different files (like kernel images) with the suffix "-preemt".

I'm afraid I made some error while deciding where to install ubuntu-studio /boot but I'm not sure how exactly this works. I've been playing with many grub-related with no luck. Like:
```

sudo grub-install --recheck /dev/md0
sudo grub-install --recheck /dev/md1
sudo grub-install --root-directory=/mnt/ /dev/md0

```...among others...

How could I restore the access to my ubuntu-studio (without having to install everyting from the beginning or losing my other distros please!). Any clues? 
Remember that grub2 is apparently functioning properly and that I have RAID configuration.

Thanks in advance for your help! 

Here's my configuration:
```


**1TB HD:**
84 GB    NTFS Windows7
419 GB    NTFS (sharing purposes)
494 GB    same as above, but is free space at the momento


**3 x 1TB SATA HD's:**
RAID-5 24GB    /dev/md0    for ubuntu 10.04 /
RAID-5 40GB    /dev/md1    for ubuntu-studio /
RAID-0 2.8TB    /dev/md3    for /home
RAID-0 12GB    /dev/md7    for swap (yeah! I know 12 GB is a waste but it's ok xD)
RAID-5 50GB    /dev/md5    ext4 for backup and important things
RAID-5 14GB    /dev/md6    empty, I may use it to try another distros sometime
RAID-5 16GB    /dev/md2    same as above

```BTW. I've tried to be as brief as I could, so feel free to ask me for any information which could help.:)

---

### Post by oldfred on 2010-08-30
Not sure if the osprober searches RAID properly.

sudo update-grub

I am also not sure if boot info script parses RAID to see all the installs:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by hefaistos2001 on 2010-08-30
Hi, thanks for replying! 
Here's what RESULTS.txt outputs (very nice script! :))
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for (md0)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for (md0)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks for (md0)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdd and looks for (md0)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

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

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb8: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdc6: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc7: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc8: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdc4: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdd2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdd3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdd6: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdd7: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdd8: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdd4: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

md0: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

md6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

md7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

md5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

md3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

md1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

md2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   163,846,934   163,846,872   7 HPFS/NTFS
/dev/sda2         163,848,192   983,048,191   819,200,000   7 HPFS/NTFS
/dev/sda3       1,947,666,430 1,953,523,711     5,857,282   5 Extended
/dev/sda5       1,947,666,432 1,953,523,711     5,857,280  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    23,437,311    23,435,264  fd Linux raid autodetect
/dev/sdb2          23,437,312    62,498,815    39,061,504  fd Linux raid autodetect
/dev/sdb3          78,125,054 1,953,523,711 1,875,398,658   5 Extended
/dev/sdb5       1,947,666,432 1,953,523,711     5,857,280  fd Linux raid autodetect
/dev/sdb6          78,125,056    91,795,455    13,670,400  fd Linux raid autodetect
/dev/sdb7          91,797,504   141,015,039    49,217,536  fd Linux raid autodetect
/dev/sdb8         141,017,088 1,947,656,191 1,806,639,104  fd Linux raid autodetect
/dev/sdb4          62,498,816    78,123,007    15,624,192  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Disco /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048    23,437,311    23,435,264  fd Linux raid autodetect
/dev/sdc2          23,437,312    62,498,815    39,061,504  fd Linux raid autodetect
/dev/sdc3          78,125,054 1,953,523,711 1,875,398,658   5 Extended
/dev/sdc5       1,947,666,432 1,953,523,711     5,857,280  fd Linux raid autodetect
/dev/sdc6          78,125,056    91,795,455    13,670,400  fd Linux raid autodetect
/dev/sdc7          91,797,504   141,015,039    49,217,536  fd Linux raid autodetect
/dev/sdc8         141,017,088 1,947,656,191 1,806,639,104  fd Linux raid autodetect
/dev/sdc4          62,498,816    78,123,007    15,624,192  fd Linux raid autodetect


Drive: sdd ___________________ _____________________________________________________

Disco /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048    23,437,311    23,435,264  fd Linux raid autodetect
/dev/sdd2          23,437,312    62,498,815    39,061,504  fd Linux raid autodetect
/dev/sdd3          78,125,054 1,953,523,711 1,875,398,658   5 Extended
/dev/sdd5       1,947,666,432 1,953,523,711     5,857,280  fd Linux raid autodetect
/dev/sdd6          78,125,056    91,795,455    13,670,400  fd Linux raid autodetect
/dev/sdd7          91,797,504   141,015,039    49,217,536  fd Linux raid autodetect
/dev/sdd8         141,017,088 1,947,656,191 1,806,639,104  fd Linux raid autodetect
/dev/sdd4          62,498,816    78,123,007    15,624,192  fd Linux raid autodetect


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/md0         38731683-48a9-4b24-aecc-24c379a8502a   ext4       ubuntu                        
/dev/md1         a135badc-3a73-45fe-83cc-d1e2f54b1891   ext4       Ubuntu-Studio                 
/dev/md2         f892daa7-4a6b-4752-bf78-88bef7df4bea   ext4       linux3                        
/dev/md3         77bd9b3a-201e-4ffd-8768-33bf4203fe57   ext4       home                          
/dev/md5         abd4e6a6-2fc1-4af4-a9e5-8aa7443ee3ce   ext4       backup                        
/dev/md6         896e3960-caf9-4022-96f7-02fa23ebd2a9   ext4       linux4                        
/dev/md7         93393255-7131-4d23-9253-8f32e0dd1bf0   swap                                     
/dev/sda1        58C0352DC035132C                       ntfs                                     
/dev/sda2        206664906664690C                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        39903dbb-a226-289d-b23f-42629fa05ba2   linux_raid_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        774472bc-cda5-6bb6-042b-25b64030139a   linux_raid_member                               
/dev/sdb2        016e218e-e646-1909-50be-556ce12fe36d   linux_raid_member                               
/dev/sdb3: PTTYPE="dos" 
/dev/sdb4        b36b7dea-bebb-ff21-1465-05782bb9873e   linux_raid_member                               
/dev/sdb5        39903dbb-a226-289d-b23f-42629fa05ba2   linux_raid_member                               
/dev/sdb6        9fe7d158-b4ab-004d-f683-ab46db7f1bde   linux_raid_member                               
/dev/sdb7        9a979634-d196-cd1b-f47e-bf0c3c661659   linux_raid_member                               
/dev/sdb8        01548e13-8c33-b725-4548-52208d7bbdad   linux_raid_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        774472bc-cda5-6bb6-042b-25b64030139a   linux_raid_member                               
/dev/sdc2        016e218e-e646-1909-50be-556ce12fe36d   linux_raid_member                               
/dev/sdc3: PTTYPE="dos" 
/dev/sdc4        b36b7dea-bebb-ff21-1465-05782bb9873e   linux_raid_member                               
/dev/sdc5        39903dbb-a226-289d-b23f-42629fa05ba2   linux_raid_member                               
/dev/sdc6        9fe7d158-b4ab-004d-f683-ab46db7f1bde   linux_raid_member                               
/dev/sdc7        9a979634-d196-cd1b-f47e-bf0c3c661659   linux_raid_member                               
/dev/sdc8        01548e13-8c33-b725-4548-52208d7bbdad   linux_raid_member                               
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        774472bc-cda5-6bb6-042b-25b64030139a   linux_raid_member                               
/dev/sdd2        016e218e-e646-1909-50be-556ce12fe36d   linux_raid_member                               
/dev/sdd3: PTTYPE="dos" 
/dev/sdd4        b36b7dea-bebb-ff21-1465-05782bb9873e   linux_raid_member                               
/dev/sdd5        39903dbb-a226-289d-b23f-42629fa05ba2   linux_raid_member                               
/dev/sdd6        9fe7d158-b4ab-004d-f683-ab46db7f1bde   linux_raid_member                               
/dev/sdd7        9a979634-d196-cd1b-f47e-bf0c3c661659   linux_raid_member                               
/dev/sdd8        01548e13-8c33-b725-4548-52208d7bbdad   linux_raid_member                               
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/md0         /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /mnt/hefaistos/w7          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /mnt/hefaistos/wxp         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/md1         /mnt/hefaistos/studio      ext4       (rw)
/dev/md2         /mnt/hefaistos/linux3      ext4       (rw)
/dev/md5         /mnt/hefaistos/BACKUP      ext4       (rw)
/dev/md6         /mnt/hefaistos/linux4      ext4       (rw)
/dev/md3         /home                    ext4       (rw)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT /USEPMTIMER 

=========================== md0/boot/grub/grub.cfg: ===========================

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
set default="1"
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
insmod raid
insmod raid5rec
insmod mdraid
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set 38731683-48a9-4b24-aecc-24c379a8502a
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
insmod raid
insmod raid5rec
insmod mdraid
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set 38731683-48a9-4b24-aecc-24c379a8502a
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
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 38731683-48a9-4b24-aecc-24c379a8502a
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=38731683-48a9-4b24-aecc-24c379a8502a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-24-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 38731683-48a9-4b24-aecc-24c379a8502a
    echo    'Cargando Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=38731683-48a9-4b24-aecc-24c379a8502a ro single 
    echo    'Cargando el disco RAM inicial...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 38731683-48a9-4b24-aecc-24c379a8502a
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=38731683-48a9-4b24-aecc-24c379a8502a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-23-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 38731683-48a9-4b24-aecc-24c379a8502a
    echo    'Cargando Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=38731683-48a9-4b24-aecc-24c379a8502a ro single 
    echo    'Cargando el disco RAM inicial...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 38731683-48a9-4b24-aecc-24c379a8502a
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=38731683-48a9-4b24-aecc-24c379a8502a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-22-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 38731683-48a9-4b24-aecc-24c379a8502a
    echo    'Cargando Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=38731683-48a9-4b24-aecc-24c379a8502a ro single 
    echo    'Cargando el disco RAM inicial...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 38731683-48a9-4b24-aecc-24c379a8502a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=38731683-48a9-4b24-aecc-24c379a8502a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 38731683-48a9-4b24-aecc-24c379a8502a
    echo    'Cargando Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=38731683-48a9-4b24-aecc-24c379a8502a ro single 
    echo    'Cargando el disco RAM inicial...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 38731683-48a9-4b24-aecc-24c379a8502a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set 38731683-48a9-4b24-aecc-24c379a8502a
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

================================ md0/etc/fstab: ================================

proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=38731683-48a9-4b24-aecc-24c379a8502a /               ext4    errors=remount-ro 0       1
UUID=77bd9b3a-201e-4ffd-8768-33bf4203fe57 /home           ext4    defaults        0       2
UUID=abd4e6a6-2fc1-4af4-a9e5-8aa7443ee3ce /mnt/hefaistos/BACKUP ext4    defaults        0       2
UUID=f892daa7-4a6b-4752-bf78-88bef7df4bea /mnt/hefaistos/linux3 ext4    defaults        0       2
UUID=896e3960-caf9-4022-96f7-02fa23ebd2a9 /mnt/hefaistos/linux4 ext4    defaults        0       2
UUID=a135badc-3a73-45fe-83cc-d1e2f54b1891 /mnt/hefaistos/studio ext4    defaults        0       2
UUID=206664906664690C /mnt/hefaistos/w7 ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
UUID=58C0352DC035132C /mnt/hefaistos/wxp ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
UUID=93393255-7131-4d23-9253-8f32e0dd1bf0 none            swap    sw              0       0

==================== md0: Location of files loaded by Grub: ====================


  13.0GB: boot/grub/core.img
  22.0GB: boot/grub/grub.cfg
  13.0GB: boot/initrd.img-2.6.32-21-generic
  13.1GB: boot/initrd.img-2.6.32-22-generic
  13.1GB: boot/initrd.img-2.6.32-23-generic
   8.2GB: boot/initrd.img-2.6.32-24-generic
    .2GB: boot/vmlinuz-2.6.32-21-generic
   1.9GB: boot/vmlinuz-2.6.32-22-generic
   6.9GB: boot/vmlinuz-2.6.32-23-generic
  14.5GB: boot/vmlinuz-2.6.32-24-generic
   8.2GB: initrd.img
  13.1GB: initrd.img.old
  14.5GB: vmlinuz
   6.9GB: vmlinuz.old

=========================== md1/boot/grub/grub.cfg: ===========================

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
insmod raid
insmod raid5rec
insmod mdraid
insmod ext2
set root='(md1)'
search --no-floppy --fs-uuid --set a135badc-3a73-45fe-83cc-d1e2f54b1891
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
insmod raid
insmod raid5rec
insmod mdraid
insmod ext2
set root='(md1)'
search --no-floppy --fs-uuid --set a135badc-3a73-45fe-83cc-d1e2f54b1891
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
menuentry 'Ubuntu, with Linux 2.6.32-21-preempt' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod ext2
    set root='(md1)'
    search --no-floppy --fs-uuid --set a135badc-3a73-45fe-83cc-d1e2f54b1891
    linux    /boot/vmlinuz-2.6.32-21-preempt root=UUID=a135badc-3a73-45fe-83cc-d1e2f54b1891 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-preempt
}
menuentry 'Ubuntu, with Linux 2.6.32-21-preempt (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod ext2
    set root='(md1)'
    search --no-floppy --fs-uuid --set a135badc-3a73-45fe-83cc-d1e2f54b1891
    echo    'Loading Linux 2.6.32-21-preempt ...'
    linux    /boot/vmlinuz-2.6.32-21-preempt root=UUID=a135badc-3a73-45fe-83cc-d1e2f54b1891 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-preempt
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod ext2
    set root='(md1)'
    search --no-floppy --fs-uuid --set a135badc-3a73-45fe-83cc-d1e2f54b1891
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod ext2
    set root='(md1)'
    search --no-floppy --fs-uuid --set a135badc-3a73-45fe-83cc-d1e2f54b1891
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 58c0352dc035132c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

================================ md1/etc/fstab: ================================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md1 during installation
UUID=a135badc-3a73-45fe-83cc-d1e2f54b1891 /               ext4    errors=remount-ro 0       1
# /home was on /dev/md3 during installation
UUID=77bd9b3a-201e-4ffd-8768-33bf4203fe57 /home           ext4    defaults        0       2
# /mnt/hefaistos/w7 was on /dev/sda2 during installation
UUID=206664906664690C /mnt/hefaistos/w7 ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /mnt/hefaistos/xp was on /dev/sda1 during installation
UUID=58C0352DC035132C /mnt/hefaistos/xp ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/md7 during installation
UUID=93393255-7131-4d23-9253-8f32e0dd1bf0 none            swap    sw              0       0

==================== md1: Location of files loaded by Grub: ====================


   8.7GB: boot/grub/core.img
  25.9GB: boot/grub/grub.cfg
   8.7GB: boot/initrd.img-2.6.32-21-preempt
    .2GB: boot/vmlinuz-2.6.32-21-preempt
   8.7GB: initrd.img
    .2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb5

00000000  e0 51 ca 29 ff 7f 00 00  8a 54 7a cd f4 7f 00 00  |.Q.).....Tz.....|
00000010  d4 98 94 ce f4 7f 00 00  9c 78 7a cd f4 7f 00 00  |.........xz.....|
00000020  01 00 00 00 f4 7f 00 00  02 00 00 00 00 00 00 00  |................|
00000030  a0 50 ca 29 ff 7f 00 00  68 50 ca 29 ff 7f 00 00  |.P.)....hP.)....|
00000040  6c 50 ca 29 ff 7f 00 00  c0 50 ca 29 ff 7f 00 00  |lP.).....P.)....|
00000050  01 00 00 00 ff 7f 00 00  00 00 00 00 00 00 00 00  |................|
00000060  ff ff ff 7f ff 7f 00 00  20 eb 9c cd f4 7f 00 00  |........ .......|
00000070  00 00 00 00 00 00 00 00  04 00 00 00 00 00 00 00  |................|
00000080  78 91 97 ce f4 7f 00 00  14 00 00 00 00 00 00 00  |x...............|
00000090  14 00 00 00 00 00 00 00  eb 9a 7b cd f4 7f 00 00  |..........{.....|
000000a0  78 91 97 ce f4 7f 00 00  14 00 00 00 f4 7f 00 00  |x...............|
000000b0  6c 90 97 ce f4 7f 00 00  78 91 97 ce f4 7f 00 00  |l.......x.......|
000000c0  2c 51 ca 29 ff 7f 00 00  a1 9b 7b cd f4 7f 00 00  |,Q.)......{.....|
000000d0  78 91 97 ce f4 7f 00 00  04 00 00 00 00 00 00 00  |x...............|
000000e0  78 91 97 ce f4 7f 00 00  78 91 97 ce f4 7f 00 00  |x.......x.......|
000000f0  5c 51 ca 29 ff 7f 00 00  40 52 ca 29 ff 7f 00 00  |\Q.)....@R.)....|
00000100  1b 00 00 00 00 00 00 00  80 52 ca 29 ff 7f 00 00  |.........R.)....|
00000110  75 00 00 00 00 00 00 00  7c 9c 7b cd f4 7f 00 00  |u.......|.{.....|
00000120  13 00 00 00 00 00 00 00  04 00 00 00 14 00 00 00  |................|
00000130  20 52 ca 29 ff 7f 00 00  78 91 97 ce f4 7f 00 00  | R.)....x.......|
00000140  14 00 00 00 00 00 00 00  f4 81 7b cd f4 7f 00 00  |..........{.....|
00000150  d0 51 ca 29 ff 7f 00 00  b0 63 7a cd f4 7f 00 00  |.Q.).....cz.....|
00000160  10 00 00 00 00 00 00 00  78 91 97 ce f4 7f 00 00  |........x.......|
00000170  14 00 00 00 00 00 00 00  40 52 ca 29 ff 7f 00 00  |........@R.)....|
00000180  6c 00 00 00 00 00 00 00  1d 85 7b cd f4 7f 00 00  |l.........{.....|
00000190  76 00 00 00 00 00 00 00  80 52 ca 29 ff 7f 00 00  |v........R.)....|
000001a0  d0 51 ca 29 ff 7f 00 00  10 00 00 00 00 00 00 00  |.Q.)............|
000001b0  d0 51 ca 29 ff 7f 00 00  8a 54 7a cd f4 7f 00 00  |.Q.).....Tz.....|
000001c0  50 52 ca 29 ff 7f 00 00  78 63 7a cd f4 7f 00 00  |PR.)....xcz.....|
000001d0  6c 00 00 00 00 00 00 00  78 91 97 ce f4 7f 00 00  |l.......x.......|
000001e0  13 00 00 00 ff 7f 00 00  78 91 97 ce f4 7f 00 00  |........x.......|
000001f0  18 00 00 00 00 00 00 00  e0 ea 9c cd f4 7f 00 00  |................|
00000200

Unknown BootLoader  on sdc5

00000000  00 00 00 00 00 00 00 00  90 ff 93 ce f4 7f 00 00  |................|
00000010  40 00 00 00 00 00 00 00  a1 00 00 00 00 00 00 00  |@...............|
00000020  d0 00 94 ce f4 7f 00 00  d0 00 94 ce f4 7f 00 00  |................|
00000030  40 01 94 ce f4 7f 00 00  60 05 94 ce f4 7f 00 00  |@.......`.......|
00000040  34 63 be cd f4 7f 00 00  68 00 00 00 00 00 00 00  |4c......h.......|
00000050  05 00 00 00 00 00 00 00  00 05 94 ce f4 7f 00 00  |................|
00000060  30 01 94 ce f4 7f 00 00  e0 03 94 ce f4 7f 00 00  |0...............|
00000070  e0 03 94 ce f4 7f 00 00  00 00 00 00 00 00 00 00  |................|
00000080  18 5f 02 ce f4 7f 00 00  24 69 02 ce f4 7f 00 00  |._......$i......|
00000090  24 69 02 ce f4 7f 00 00  6f 60 02 ce f4 7f 00 00  |$i......o`......|
000000a0  b0 01 94 ce f4 7f 00 00  e0 f8 93 ce f4 7f 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  41 00 00 00 00 00 00 00  |........A.......|
000000c0  c0 f8 93 ce f4 7f 00 00  50 fa 93 ce f4 7f 00 00  |........P.......|
000000d0  20 00 94 ce f4 7f 00 00  20 00 94 ce f4 7f 00 00  | ....... .......|
000000e0  b0 f8 93 ce f4 7f 00 00  20 00 94 ce f4 7f 00 00  |........ .......|
000000f0  00 00 00 00 00 00 00 00  41 00 00 00 00 00 00 00  |........A.......|
00000100  50 01 94 ce f4 7f 00 00  50 01 94 ce f4 7f 00 00  |P.......P.......|
00000110  10 01 94 ce f4 7f 00 00  10 01 94 ce f4 7f 00 00  |................|
00000120  00 00 00 00 00 00 00 00  05 00 00 00 00 00 00 00  |................|
00000130  2f 65 74 63 00 00 00 00  41 00 00 00 00 00 00 00  |/etc....A.......|
00000140  e0 01 94 ce f4 7f 00 00  30 00 94 ce f4 7f 00 00  |........0.......|
00000150  00 01 94 ce f4 7f 00 00  00 01 94 ce f4 7f 00 00  |................|
00000160  20 00 94 ce f4 7f 00 00  00 01 94 ce f4 7f 00 00  | ...............|
00000170  00 00 00 00 00 00 00 00  61 00 00 00 00 00 00 00  |........a.......|
00000180  f0 01 94 ce f4 7f 00 00  f0 01 94 ce f4 7f 00 00  |................|
00000190  70 03 94 ce f4 7f 00 00  70 03 94 ce f4 7f 00 00  |p.......p.......|
000001a0  00 00 00 00 00 00 00 00  28 00 00 00 00 00 00 00  |........(.......|
000001b0  50 02 94 ce f4 7f 00 00  11 00 00 00 00 00 00 00  |P...............|
000001c0  f8 20 be cd f4 7f 00 00  a4 20 be cd f4 7f 00 00  |. ....... ......|
000001d0  05 22 be cd f4 7f 00 00  41 00 00 00 00 00 00 00  |."......A.......|
000001e0  10 04 94 ce f4 7f 00 00  40 01 94 ce f4 7f 00 00  |........@.......|
000001f0  80 01 94 ce f4 7f 00 00  80 01 94 ce f4 7f 00 00  |................|
00000200

Unknown BootLoader  on sdc8

00000000  00 00 c0 03 10 00 c0 03  20 00 c0 03 df 5f 00 20  |........ ...._. |
00000010  00 00 05 00 00 00 00 00  00 00 00 00 00 20 e4 d3  |............. ..|
00000020  01 00 c0 03 11 00 c0 03  20 02 c0 03 00 00 00 20  |........ ...... |
00000030  00 00 05 00 00 00 00 00  00 00 00 00 00 20 3d 7f  |............. =.|
00000040  02 00 c0 03 12 00 c0 03  20 04 c0 03 00 00 00 20  |........ ...... |
00000050  00 00 05 00 00 00 00 00  00 00 00 00 00 20 53 de  |............. S.|
00000060  03 00 c0 03 13 00 c0 03  20 06 c0 03 00 00 00 20  |........ ...... |
00000070  00 00 05 00 00 00 00 00  00 00 00 00 00 20 88 7e  |............. .~|
00000080  04 00 c0 03 14 00 c0 03  20 08 c0 03 ed 00 00 20  |........ ...... |
00000090  00 00 05 00 00 00 00 00  00 00 00 00 00 20 29 85  |............. ).|
000000a0  05 00 c0 03 15 00 c0 03  20 0a c0 03 00 00 00 20  |........ ...... |
000000b0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 57 7c  |............. W||
000000c0  06 00 c0 03 16 00 c0 03  20 0c c0 03 00 00 00 20  |........ ...... |
000000d0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 39 dd  |............. 9.|
000000e0  07 00 c0 03 17 00 c0 03  20 0e c0 03 00 00 00 20  |........ ...... |
000000f0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 e2 7d  |............. .}|
00000100  08 00 c0 03 18 00 c0 03  20 10 c0 03 00 00 00 20  |........ ...... |
00000110  00 00 05 00 00 00 00 00  00 00 00 00 00 20 32 d9  |............. 2.|
00000120  09 00 c0 03 19 00 c0 03  20 12 c0 03 00 00 00 20  |........ ...... |
00000130  00 00 05 00 00 00 00 00  00 00 00 00 00 20 e9 79  |............. .y|
00000140  0a 00 c0 03 1a 00 c0 03  20 14 c0 03 00 00 00 20  |........ ...... |
00000150  00 00 05 00 00 00 00 00  00 00 00 00 00 20 87 d8  |............. ..|
00000160  0b 00 c0 03 1b 00 c0 03  20 16 c0 03 a0 01 00 20  |........ ...... |
00000170  00 00 05 00 00 00 00 00  00 00 00 00 00 20 2f ca  |............. /.|
00000180  0c 00 c0 03 1c 00 c0 03  20 18 c0 03 5e 05 00 20  |........ ...^.. |
00000190  00 00 05 00 00 00 00 00  00 00 00 00 00 20 38 71  |............. 8q|
000001a0  0d 00 c0 03 1d 00 c0 03  20 1a c0 03 00 00 00 20  |........ ...... |
000001b0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 83 7a  |............. .z|
000001c0  0e 00 c0 03 1e 00 c0 03  20 1c c0 03 00 00 00 20  |........ ...... |
000001d0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 ed db  |............. ..|
000001e0  0f 00 c0 03 1f 00 c0 03  20 1e c0 03 00 00 00 20  |........ ...... |
000001f0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 36 7b  |............. 6{|
00000200

Unknown BootLoader  on sdd5

00000000  00 00 00 00 00 00 00 00  41 00 00 00 00 00 00 00  |........A.......|
00000010  80 fc 94 ce f4 7f 00 00  b0 ff 94 ce f4 7f 00 00  |................|
00000020  10 fc 94 ce f4 7f 00 00  10 fc 94 ce f4 7f 00 00  |................|
00000030  a0 ff 94 ce f4 7f 00 00  10 fc 94 ce f4 7f 00 00  |................|
00000040  00 00 00 00 00 00 00 00  51 00 00 00 00 00 00 00  |........Q.......|
00000050  00 06 95 ce f4 7f 00 00  00 06 95 ce f4 7f 00 00  |................|
00000060  d0 f8 94 ce f4 7f 00 00  d0 f8 94 ce f4 7f 00 00  |................|
00000070  00 00 00 00 00 00 00 00  10 00 00 00 00 00 00 00  |................|
00000080  01 00 00 00 74 72 69 67  f0 07 95 ce f4 7f 00 00  |....trig........|
00000090  00 00 00 00 00 00 00 00  71 00 00 00 00 00 00 00  |........q.......|
000000a0  90 fc 94 ce f4 7f 00 00  90 fc 94 ce f4 7f 00 00  |................|
000000b0  a0 01 95 ce f4 7f 00 00  f0 02 95 ce f4 7f 00 00  |................|
000000c0  22 22 02 ce f4 7f 00 00  38 00 00 00 00 00 00 00  |""......8.......|
000000d0  d0 ff 94 ce f4 7f 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
000000f0  80 01 95 ce f4 7f 00 00  f0 fb 94 ce f4 7f 00 00  |................|
00000100  00 00 00 00 00 00 00 00  41 00 00 00 00 00 00 00  |........A.......|
00000110  f0 01 95 ce f4 7f 00 00  f0 01 95 ce f4 7f 00 00  |................|
00000120  50 fd 94 ce f4 7f 00 00  50 fd 94 ce f4 7f 00 00  |P.......P.......|
00000130  e0 01 95 ce f4 7f 00 00  50 fd 94 ce f4 7f 00 00  |........P.......|
00000140  00 00 00 00 00 00 00 00  51 00 00 00 00 00 00 00  |........Q.......|
00000150  b0 01 95 ce f4 7f 00 00  b0 01 95 ce f4 7f 00 00  |................|
00000160  60 01 95 ce f4 7f 00 00  60 01 95 ce f4 7f 00 00  |`.......`.......|
00000170  00 00 00 00 00 00 00 00  11 00 00 00 00 00 00 00  |................|
00000180  64 72 6d 2d 64 65 76 69  63 65 2d 61 64 64 65 64  |drm-device-added|
00000190  00 00 00 00 00 00 00 00  41 00 00 00 00 00 00 00  |........A.......|
000001a0  f0 02 95 ce f4 7f 00 00  b0 00 95 ce f4 7f 00 00  |................|
000001b0  50 01 95 ce f4 7f 00 00  50 01 95 ce f4 7f 00 00  |P.......P.......|
000001c0  a0 00 95 ce f4 7f 00 00  50 01 95 ce f4 7f 00 00  |........P.......|
000001d0  00 00 00 00 00 00 00 00  51 00 00 00 00 00 00 00  |........Q.......|
000001e0  c0 f4 94 ce f4 7f 00 00  c0 f4 94 ce f4 7f 00 00  |................|
000001f0  10 01 95 ce f4 7f 00 00  10 01 95 ce f4 7f 00 00  |................|
00000200

Unknown BootLoader  on sdd8

00000000  00 00 c0 07 10 00 c0 07  20 00 c0 07 5b 58 00 20  |........ ...[X. |
00000010  00 00 05 00 00 00 00 00  00 00 00 00 00 20 62 b0  |............. b.|
00000020  01 00 c0 07 11 00 c0 07  20 02 c0 07 00 00 00 20  |........ ...... |
00000030  00 00 05 00 00 00 00 00  00 00 00 00 00 20 61 f4  |............. a.|
00000040  02 00 c0 07 12 00 c0 07  20 04 c0 07 00 00 00 20  |........ ...... |
00000050  00 00 05 00 00 00 00 00  00 00 00 00 00 20 0f 55  |............. .U|
00000060  03 00 c0 07 13 00 c0 07  20 06 c0 07 fe 01 00 20  |........ ...... |
00000070  00 00 05 00 00 00 00 00  00 00 00 00 00 20 d4 bd  |............. ..|
00000080  04 00 c0 07 14 00 c0 07  20 08 c0 07 60 00 00 20  |........ ...`.. |
00000090  00 00 05 00 00 00 00 00  00 00 00 00 00 20 ce 49  |............. .I|
000000a0  05 00 c0 07 15 00 c0 07  20 0a c0 07 cb 02 00 20  |........ ...... |
000000b0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 e4 8d  |............. ..|
000000c0  06 00 c0 07 16 00 c0 07  20 0c c0 07 59 02 00 20  |........ ...Y.. |
000000d0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 06 b9  |............. ..|
000000e0  07 00 c0 07 17 00 c0 07  20 0e c0 07 fe 07 00 20  |........ ...... |
000000f0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 5d 1f  |............. ].|
00000100  08 00 c0 07 18 00 c0 07  20 10 c0 07 5a 0c 00 20  |........ ...Z.. |
00000110  00 00 05 00 00 00 00 00  00 00 00 00 00 20 99 9a  |............. ..|
00000120  09 00 c0 07 19 00 c0 07  20 12 c0 07 0b 02 00 20  |........ ...... |
00000130  00 00 05 00 00 00 00 00  00 00 00 00 00 20 66 b4  |............. f.|
00000140  0a 00 c0 07 1a 00 c0 07  20 14 c0 07 f2 00 00 20  |........ ...... |
00000150  00 00 05 00 00 00 00 00  00 00 00 00 00 20 49 d8  |............. I.|
00000160  0b 00 c0 07 1b 00 c0 07  20 16 c0 07 32 06 00 20  |........ ...2.. |
00000170  00 00 05 00 00 00 00 00  00 00 00 00 00 20 4d e5  |............. M.|
00000180  0c 00 c0 07 1c 00 c0 07  20 18 c0 07 0b 05 00 20  |........ ...... |
00000190  00 00 05 00 00 00 00 00  00 00 00 00 00 20 65 26  |............. e&|
000001a0  0d 00 c0 07 1d 00 c0 07  20 1a c0 07 38 06 00 20  |........ ...8.. |
000001b0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 b1 3d  |............. .=|
000001c0  0e 00 c0 07 1e 00 c0 07  20 1c c0 07 00 00 00 20  |........ ...... |
000001d0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 b1 50  |............. .P|
000001e0  0f 00 c0 07 1f 00 c0 07  20 1e c0 07 00 00 00 20  |........ ...... |
000001f0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 6a f0  |............. j.|
00000200



```Ah, I had already tested update-grub but it just detects what I have:

```

Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
```I wonder if I can tell grub to look inside **/mnt/hefaistos/ubuntu-studio/boot** where I have the kernel images I need...

---

### Post by oldfred on 2010-08-30
I do not know about RAID. 

This is a boot stanza to boot a partition as the root has a link to the most current kernel.

If you add something like this to 40_custom with the extra insmod raid commands in the standard boot stanza ??

From Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

Add these and change md0 to the partition for studio md1 or md2?
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod ext2
    set root='(md0)' change to md1 or md2?
 and change root=/dev/sda13 to root=your UUID for studio like the standard Ubuntu stanzas

Your UUIDs from script:
/dev/md0         38731683-48a9-4b24-aecc-24c379a8502a   ext4       ubuntu                        
/dev/md1         a135badc-3a73-45fe-83cc-d1e2f54b1891   ext4       Ubuntu-Studio                 
/dev/md2         f892daa7-4a6b-4752-bf78-88bef7df4bea   ext4       linux3   


This is a starting point but I do not know answer. If anything works let us know.

---

### Post by hefaistos2001 on 2010-08-30
Hi Oldfred! Thank you very much, you gave me just what I needed. Now I can access any of the two ubuntu's.

I got the ubuntu-studio entries from its corresponding ubuntu-studio grub.cfg and then pasted them to my ubuntu /etc/grub.d/40_custom file, so it was easier than I though, but I would be stuck forever without your help :D

Here are my ubuntu 40_custom contents:

```
 
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Ubuntu, with Linux 2.6.32-21-preempt' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod ext2
    set root='(md1)'
    search --no-floppy --fs-uuid --set a135badc-3a73-45fe-83cc-d1e2f54b1891
    linux    /boot/vmlinuz-2.6.32-21-preempt root=UUID=a135badc-3a73-45fe-83cc-d1e2f54b1891 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-preempt
}
menuentry 'Ubuntu, with Linux 2.6.32-21-preempt (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod ext2
    set root='(md1)'
    search --no-floppy --fs-uuid --set a135badc-3a73-45fe-83cc-d1e2f54b1891
    echo    'Loading Linux 2.6.32-21-preempt ...'
    linux    /boot/vmlinuz-2.6.32-21-preempt root=UUID=a135badc-3a73-45fe-83cc-d1e2f54b1891 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-preempt
}


```Next thing I'll try is to do this automagically, because I'm afraid no new kernel updates will be shown until I add them by hand... Anyway... I'll give this a try in a few weeks because at the moment I'm too busy and too happy to make any change... so thanks again!

Cheers!

---

### Post by oldfred on 2010-08-30
Glad you got it working. 

You can add one more entry somewhat like what you have done except change to use the links in root instead of the files in /boot. The links are updated on every kernel update so they always boot the most current kernel.

```
menuentry 'Ubuntu Studio Current Kernel'  {
    recordfail
    insmod raid
    insmod raid5rec
    insmod mdraid
    insmod ext2
    set root='(md1)'
    linux /vmlinuz root=UUID=a135badc-3a73-45fe-83cc-d1e2f54b1891 ro   quiet splash
    initrd /initrd.img
```

---

