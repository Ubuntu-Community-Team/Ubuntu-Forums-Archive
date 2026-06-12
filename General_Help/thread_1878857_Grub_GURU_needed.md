---
title: "Grub GURU needed"
date: 2011-11-10
forum: General Help
---

### Post by spiky001 on 2011-11-10
I,m trying to setup grub 1.99. The setup of hardrives I have are sda Ubuntu 11.94 sdb Ubuntu 11.10 and sdc LFS what I would like is for LFS to be independant from the other deives/OS/ and grubs. I want to choose sdc LFS via bios and grub only have LFS listed. I dont want it listed in the other grubs. Hope this makes sense so far.
 ```
   
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        2491     9764864   83  Linux
/dev/sda3            2491       14594    97212417    5  Extended
/dev/sda5            2491        2613      975872   82  Linux swap / Solaris
/dev/sda6            2613       14594    96235520   83  Linux 
Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x414d8374

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1912    15358108+  83  Linux
/dev/sdb2            1913        2039     1020127+  82  Linux swap / Solaris /dev/sdb3            2040        5864    30720612+  83  Linux
/dev/sdb4            5864       12162    50585601    5  Extended /dev/sdb5            5864        7776    15360000   83  Linux /dev/sdb6            7777        7904     1024000   82  Linux swap / Solaris /dev/sdb7            7904       12162    34199552   83  Linux

Disk /dev/sdc: 40.0 GB, 40007761920 bytes 255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x2bd28d09 
   Device Boot      Start         End      Blocks   Id  System /dev/sdc1               1        1913    15360000   83  Linux /dev/sdc2            1913        2043     1048576   82  Linux swap / Solaris /dev/sdc3            2043        4864    22660096   83  Linux

```Running  ```

grub-mkdevicemap --device-map=device.map
```output cat device.map```

  (hd0)    /dev/disk/by-id/ata-Hitachi_HTS541612J9SA00_SB2D01E4GKEVWB 
(hd1)    /dev/disk/by-id/usb-FUJITSU_MHV2100AH-0:0
 (hd2)    /dev/disk/by-id/usb-Generic_External_37364A503332363853202020-0:0
```

LFS dose work and boot I removed all other drives set lfs to boot as sda etc etc it loaded and run

I do hope some one can help fix this problem.

---

### Post by ggeminii on 2011-11-10
What i have understood from your post is that you want your LFS disk to list only the LFS and not other drives and OS.
So this means you have to install grub separately on sdc and create grub.cfg manually with menuentry only for LFS.
Copy only the entry for LFS from your current grub.cfg and paste it in your new grub.cfg which will reside on sdc.
If you need help creating grub.cfg maually you can ask .

---

### Post by matt_symes on 2011-11-10
Hi

Does this in anyway help ?

[http://ubuntuforums.org/showthread.php?p=8871846](http://ubuntuforums.org/showthread.php?p=8871846)

I see you built LFS again then. Was it painful ? :D

Kind regards

---

### Post by spiky001 on 2011-11-10
I have set grub cfg as ```
# Begin /boot/grub/grub.cfg  set default=0 set timeout=5 insmod ext2 set root=(hd2,1)  menuentry &quot;GNU/Linux, Linux 3.1-lfs-7.0&quot; {         linux   /boot/vmlinuz-3.1-lfs-7.0 root=/dev/sdc1 ro } 
``` also fstab points to sdc1 / sdc2 swap

---

### Post by oldfred on 2011-11-10
Post boot script to see where everything is installed:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by spiky001 on 2011-11-11
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    20,482,874    20,482,812   7 NTFS / exFAT / HPFS
/dev/sda2          20,484,096    40,013,823    19,529,728  83 Linux
/dev/sda3          40,015,870   234,440,703   194,424,834   5 Extended
/dev/sda5          40,015,872    41,967,615     1,951,744  82 Linux swap / Solaris
/dev/sda6          41,969,664   234,440,703   192,471,040  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    30,716,279    30,716,217  83 Linux
/dev/sdb2          30,716,280    32,756,534     2,040,255  82 Linux swap / Solaris
/dev/sdb3          32,756,535    94,197,759    61,441,225  83 Linux
/dev/sdb4          94,199,806   195,371,007   101,171,202   5 Extended
/dev/sdb5          94,199,808   124,919,807    30,720,000  83 Linux
/dev/sdb6         124,921,856   126,969,855     2,048,000  82 Linux swap / Solaris
/dev/sdb7         126,971,904   195,371,007    68,399,104  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048    30,722,047    30,720,000  83 Linux
/dev/sdc2          30,722,048    32,819,199     2,097,152  82 Linux swap / Solaris
/dev/sdc3          32,819,200    78,139,391    45,320,192  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        8C0898E90898D414                       ntfs       
/dev/sda2        cecadb42-40ac-43a3-8dd8-fb2d1e594002   ext4       
/dev/sda5        ab6d2feb-fd4c-420f-89a7-ef33ca842b64   swap       
/dev/sda6        ee5c9ede-d4f2-413c-acc7-646b4804cbc7   ext4       
/dev/sdb1        897e754d-973c-4314-bb7e-d5f73389bea9   ext3       
/dev/sdb2        ef6f6071-202b-48a6-9049-0f01b272f561   swap       
/dev/sdb3        30832ce5-cd07-4c2f-90b1-d350eafcbd7a   ext3       
/dev/sdb5        95a2f16e-4312-487b-a077-9baa139feb23   ext4       
/dev/sdb6        81472a3d-397d-4170-abbc-5b790e9340b9   swap       
/dev/sdb7        8c7d982c-4dff-4b21-86d8-578290bb18c9   ext4       
/dev/sdc1        b40b41dd-302c-4b9f-b61c-972568c6357c   ext4       LFS-7rc2
/dev/sdc2        6fed66b1-48b8-4747-a0ce-8f09f3aecc23   swap       
/dev/sdc3        85e24b07-c46a-4e7f-8085-a340a304c67c   ext4       LFS-7rc2-home

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)
/dev/sdb1        /media/897e754d-973c-4314-bb7e-d5f73389bea9 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb3        /media/30832ce5-cd07-4c2f-90b1-d350eafcbd7a ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb5        /media/95a2f16e-4312-487b-a077-9baa139feb23 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb7        /media/8c7d982c-4dff-4b21-86d8-578290bb18c9 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/LFS-7rc2          ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc3        /media/LFS-7rc2-home     ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root cecadb42-40ac-43a3-8dd8-fb2d1e594002
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root cecadb42-40ac-43a3-8dd8-fb2d1e594002
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root cecadb42-40ac-43a3-8dd8-fb2d1e594002
    linux    /boot/vmlinuz-2.6.38-12-generic root=UUID=cecadb42-40ac-43a3-8dd8-fb2d1e594002 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root cecadb42-40ac-43a3-8dd8-fb2d1e594002
    echo    'Loading Linux 2.6.38-12-generic ...'
    linux    /boot/vmlinuz-2.6.38-12-generic root=UUID=cecadb42-40ac-43a3-8dd8-fb2d1e594002 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root cecadb42-40ac-43a3-8dd8-fb2d1e594002
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=cecadb42-40ac-43a3-8dd8-fb2d1e594002 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root cecadb42-40ac-43a3-8dd8-fb2d1e594002
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=cecadb42-40ac-43a3-8dd8-fb2d1e594002 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root cecadb42-40ac-43a3-8dd8-fb2d1e594002
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=cecadb42-40ac-43a3-8dd8-fb2d1e594002 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root cecadb42-40ac-43a3-8dd8-fb2d1e594002
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=cecadb42-40ac-43a3-8dd8-fb2d1e594002 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root cecadb42-40ac-43a3-8dd8-fb2d1e594002
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=cecadb42-40ac-43a3-8dd8-fb2d1e594002 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root cecadb42-40ac-43a3-8dd8-fb2d1e594002
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=cecadb42-40ac-43a3-8dd8-fb2d1e594002 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root cecadb42-40ac-43a3-8dd8-fb2d1e594002
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root cecadb42-40ac-43a3-8dd8-fb2d1e594002
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 8C0898E90898D414
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "PLANET-SPIKE - 2.6.38.3 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 897e754d-973c-4314-bb7e-d5f73389bea9
    linux /boot/vmlinux-2.6.38.3-lfs-6.7 root=/dev/sda1 ro
}
menuentry "GNU/Linux, with Linux 2.6.35.4-lfs-6.7 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 897e754d-973c-4314-bb7e-d5f73389bea9
    linux /boot/vmlinux-2.6.35.4-lfs-6.7 root=/dev/sda1 ro
}
menuentry "GNU/Linux, with Linux 2.6.35.4-lfs-6.7 (recovery mode) (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 897e754d-973c-4314-bb7e-d5f73389bea9
    linux /boot/vmlinux-2.6.35.4-lfs-6.7 root=/dev/sda1 ro single
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 95a2f16e-4312-487b-a077-9baa139feb23
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=95a2f16e-4312-487b-a077-9baa139feb23 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 95a2f16e-4312-487b-a077-9baa139feb23
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=95a2f16e-4312-487b-a077-9baa139feb23 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-12-generic
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
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=cecadb42-40ac-43a3-8dd8-fb2d1e594002 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=ee5c9ede-d4f2-413c-acc7-646b4804cbc7 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=ab6d2feb-fd4c-420f-89a7-ef33ca842b64 none            swap    sw              0       0
# swap was on /dev/sdb2 during installation
UUID=d9b60e96-ca8f-4d72-a4ec-a4be5eafd5c7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   9.920185089 = 10.651717632   boot/grub/core.img                             1
  10.028800964 = 10.768343040   boot/grub/grub.cfg                             1
  12.779548645 = 13.721935872   boot/initrd.img-2.6.38-10-generic              1
  13.404769897 = 14.393262080   boot/initrd.img-2.6.38-11-generic              2
  13.021736145 = 13.981982720   boot/initrd.img-2.6.38-12-generic              2
  11.865482330 = 12.740464640   boot/initrd.img-2.6.38-8-generic               2
  12.701480865 = 13.638111232   boot/vmlinuz-2.6.38-10-generic                 2
  12.404605865 = 13.319344128   boot/vmlinuz-2.6.38-11-generic                 2
  11.744449615 = 12.610506752   boot/vmlinuz-2.6.38-12-generic                 2
  10.986328125 = 11.796480000   boot/vmlinuz-2.6.38-8-generic                  2
  13.021736145 = 13.981982720   initrd.img                                     2
  13.404769897 = 14.393262080   initrd.img.old                                 2
  11.744449615 = 12.610506752   vmlinuz                                        2
  12.404605865 = 13.319344128   vmlinuz.old                                    2

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 897e754d-973c-4314-bb7e-d5f73389bea9
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "PLANET-SPIKE - 2.6.38.3" --class gnu-linux --class gnu --class os {
        echo    Loading Linux 2.6.38.3-lfs-6.7 ...
        linux   /boot/vmlinux-2.6.38.3-lfs-6.7 root=/dev/sda1 ro
}
menuentry "PLANET-SPIKE -2.6.38.3 (recovery mode)" --class gnu-linux --class gnu --class os {
         echo   Loading Linux 2.6.38.3-lfs-6.7
         linux  /boot/vmlinux 2.6.38.3 root=/sda1 ro single
}
menuentry "GNU/Linux, with Linux 2.6.35.4-lfs-6.7" --class gnu-linux --class gnu --class os {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 897e754d-973c-4314-bb7e-d5f73389bea9
    echo    Loading Linux 2.6.35.4-lfs-6.7 ...
    linux    /boot/vmlinux-2.6.35.4-lfs-6.7 root=/dev/sda1 ro  
}
menuentry "GNU/Linux, with Linux 2.6.35.4-lfs-6.7 (recovery mode)" --class gnu-linux --class gnu --class os {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 897e754d-973c-4314-bb7e-d5f73389bea9
    echo    Loading Linux 2.6.35.4-lfs-6.7 ...
    linux    /boot/vmlinux-2.6.35.4-lfs-6.7 root=/dev/sda1 ro single 
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# Begin /etc/fstab

# file system  mount-point  type    option           dump fsck
#                                                         order

/dev/sda1      /            ext3     defaults          1    1
/dev/sda2      swap         swap     pri=1             0    0
/dev/sda3      /home        ext3     defaults          0    0
proc           /proc        proc     defaults          0    0
sysfs          /sys         sysfs    defaults          0    0
devpts         /dev/pts     devpts   gid=4,mode=620    0    0
tmpfs          /dev/shm     tmpfs    defaults          0    0
# End /etc/fstab

--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  11.054809093 = 11.870010880   boot/grub/core.img                             1
  11.070346355 = 11.886693888   boot/grub/grub.cfg                             1

=========================== sdb5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set=root 95a2f16e-4312-487b-a077-9baa139feb23
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos5)'
  search --no-floppy --fs-uuid --set=root 95a2f16e-4312-487b-a077-9baa139feb23
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 95a2f16e-4312-487b-a077-9baa139feb23
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=95a2f16e-4312-487b-a077-9baa139feb23 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 95a2f16e-4312-487b-a077-9baa139feb23
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=95a2f16e-4312-487b-a077-9baa139feb23 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 95a2f16e-4312-487b-a077-9baa139feb23
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 95a2f16e-4312-487b-a077-9baa139feb23
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 8C0898E90898D414
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root cecadb42-40ac-43a3-8dd8-fb2d1e594002
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=cecadb42-40ac-43a3-8dd8-fb2d1e594002 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root cecadb42-40ac-43a3-8dd8-fb2d1e594002
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=cecadb42-40ac-43a3-8dd8-fb2d1e594002 ro single
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root cecadb42-40ac-43a3-8dd8-fb2d1e594002
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=cecadb42-40ac-43a3-8dd8-fb2d1e594002 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root cecadb42-40ac-43a3-8dd8-fb2d1e594002
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=cecadb42-40ac-43a3-8dd8-fb2d1e594002 ro single
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root cecadb42-40ac-43a3-8dd8-fb2d1e594002
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=cecadb42-40ac-43a3-8dd8-fb2d1e594002 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root cecadb42-40ac-43a3-8dd8-fb2d1e594002
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=cecadb42-40ac-43a3-8dd8-fb2d1e594002 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "PLANET-SPIKE - 2.6.38.3 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 897e754d-973c-4314-bb7e-d5f73389bea9
    linux /boot/vmlinux-2.6.38.3-lfs-6.7 root=/dev/sda1 ro
}
menuentry "GNU/Linux, with Linux 2.6.35.4-lfs-6.7 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 897e754d-973c-4314-bb7e-d5f73389bea9
    linux /boot/vmlinux-2.6.35.4-lfs-6.7 root=/dev/sda1 ro
}
menuentry "GNU/Linux, with Linux 2.6.35.4-lfs-6.7 (recovery mode) (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 897e754d-973c-4314-bb7e-d5f73389bea9
    linux /boot/vmlinux-2.6.35.4-lfs-6.7 root=/dev/sda1 ro single
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
--------------------------------------------------------------------------------

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=95a2f16e-4312-487b-a077-9baa139feb23 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=8c7d982c-4dff-4b21-86d8-578290bb18c9 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=ab6d2feb-fd4c-420f-89a7-ef33ca842b64 none            swap    sw              0       0
# swap was on /dev/sdb2 during installation
UUID=ef6f6071-202b-48a6-9049-0f01b272f561 none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
UUID=81472a3d-397d-4170-abbc-5b790e9340b9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  49.372287750 = 53.013090304   boot/grub/core.img                             1
  49.372303009 = 53.013106688   boot/grub/grub.cfg                             1
  46.422847748 = 49.846153216   boot/initrd.img-3.0.0-12-generic               3
  49.313655853 = 52.950134784   boot/vmlinuz-3.0.0-12-generic                  1
  46.422847748 = 49.846153216   initrd.img                                     3
  49.313655853 = 52.950134784   vmlinuz                                        1

=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
# Begin /boot/grub/grub.cfg
set default=0
set timeout=5

insmod ext2
set root=(/dev/sdc,msdos2)

menuentry "GNU/Linux, Linux 3.1-lfs-7.0" {
        linux   /boot/vmlinuz-3.1-lfs-7.0 root=UUID="b40b41dd-302c-4b9f-b61c-972568c6357c
}
--------------------------------------------------------------------------------

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# Begin /etc/fstab

# file system  mount-point  type   options         dump  fsck
#                                                        order

/dev/sdc1      /            ext4   defaults        1     1
/dev/sdc2      swap         swap   pri=1           0     0
proc           /proc        proc   defaults        0     0
sysfs          /sys         sysfs  defaults        0     0
devpts         /dev/pts     devpts gid=4,mode=620  0     0
tmpfs          /run         tmpfs  defaults        0     0
# End /etc/fstab
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   2.128582001 = 2.285547520    boot/grub/core.img                             1
   2.131839752 = 2.289045504    boot/grub/grub.cfg                             1
   2.216602325 = 2.380058624    boot/vmlinuz-3.1-lfs-7.0                       1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  4c 49 53 54 88 04 00 00  73 74 72 6c 73 74 72 68  |LIST....strlstrh|
00000010  38 00 00 00 76 69 64 73  6d 72 6c 65 00 00 00 00  |8...vidsmrle....|
00000020  00 00 00 00 00 00 00 00  0a 00 00 00 64 00 00 00  |............d...|
00000030  00 00 00 00 17 00 00 00  f6 06 00 00 10 27 00 00  |.............'..|
00000040  00 00 00 00 00 00 00 00  10 01 3c 00 73 74 72 66  |..........<.strf|
00000050  1c 04 00 00 28 00 00 00  10 01 00 00 3c 00 00 00  |....(.......<...|
00000060  01 00 08 00 01 00 00 00  80 7f 00 00 00 00 00 00  |................|
00000070  00 00 00 00 fd 00 00 00  00 00 00 00 59 6c 73 00  |............Yls.|
00000080  53 70 79 00 66 66 66 00  60 69 6c 00 6c 6a 68 00  |Spy.fff.`il.ljh.|
00000090  7a 68 73 00 73 73 71 00  ca 79 3d 00 8a 7a 6b 00  |zhs.ssq..y=..zk.|
000000a0  94 6a 7e 00 cc 7c 40 00  00 99 00 00 10 9f 0f 00  |.j~..|@.........|
000000b0  10 9f 10 00 20 a6 1d 00  20 a6 20 00 30 ac 2d 00  |.... ... . .0.-.|
000000c0  30 ac 30 00 40 b3 3c 00  40 b3 40 00 50 b9 4a 00  |0.0.@.<.@.@.P.J.|
000000d0  60 ba 5a 00 60 bf 60 00  70 c6 6a 00 70 c6 70 00  |`.Z.`.`.p.j.p.p.|
000000e0  fe ab 37 00 83 83 7b 00  92 81 71 00 a0 82 67 00  |..7...{...q...g.|
000000f0  c8 82 4d 00 d9 92 59 00  f9 ab 44 00 fe b0 43 00  |..M...Y...D...C.|
00000100  e5 a3 51 00 fc b7 56 00  ca 8e 62 00 de 99 61 00  |..Q...V...b...a.|
00000110  c3 99 7d 00 e1 9c 64 00  d3 a7 7d 00 e4 a2 6b 00  |..}...d...}...k.|
00000120  ed b2 6a 00 f0 b5 6a 00  e9 ab 74 00 ed b1 7a 00  |..j...j...t...z.|
00000130  f1 b9 7b 00 80 ca 76 00  fe c0 67 00 fd c4 75 00  |..{...v...g...u.|
00000140  39 7c 93 00 46 76 86 00  72 7a b3 00 8a 6a 8a 00  |9|..Fv..rz...j..|
00000150  fe 00 fe 00 fd 0a f8 00  ff 3c ff 00 2d 83 9f 00  |.........<..-...|
00000160  33 80 99 00 15 8e b6 00  24 87 a8 00 31 8c a9 00  |3.......$...1...|
00000170  26 93 b5 00 37 99 b9 00  65 a8 b4 00 0e 9a c8 00  |&...7...e.......|
00000180  14 96 c3 00 0f a2 d2 00  17 a7 d5 00 35 a6 c9 00  |............5...|
00000190  25 ac da 00 30 ae da 00  2a b3 dc 00 3c b6 dc 00  |%...0...*...<...|
000001a0  36 b5 e4 00 5c 89 d8 00  69 8e db 00 45 a7 de 00  |6...\...i...E...|
000001b0  5a ad de 00 45 b9 db 00  50 b9 d7 00 60 bf 00 fe  |Z...E...P...`...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c8 1d 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 c8  1d 00 00 e8 78 0b 00 00  |............x...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
unlzma: Decoder error

```
The problem is I cant get lfs to boot on sdc. It will boot when all drives are removed and it is set up as sda

---

### Post by oldfred on 2011-11-11
You have some settings by device /dev/sdXY and some by UUID. In Ubuntu an incorrect set root by device will be overridden by a search line.

> menuentry "PLANET-SPIKE - 2.6.38.3 (on [COLOR=Red]/dev/sdb1[/COLOR])" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root [COLOR=Red]897e754d-973c-4314-bb7e-d5f73389bea9[/COLOR]
    linux /boot/vmlinux-2.6.38.3-lfs-6.7 root=/dev/[COLOR=Red]sda1[/COLOR] ro
}
fstab:
/dev/[COLOR=Red]sda1[/COLOR]      /            ext3     defaults          1    1
/dev/[COLOR=Red]sda2[/COLOR]      swap         swap     pri=1             0    0
There is no search line to correct /dev entries so if they are not correct it will not work.
UUID is for [COLOR=Red]sdc1[/COLOR].
sdc1/boot/grub/grub.cfg:
> set root=(/dev/sdc,[COLOR=Red]msdos2[/COLOR])

menuentry "GNU/Linux, Linux 3.1-lfs-7.0" {
        linux   /boot/vmlinuz-3.1-lfs-7.0 root=UUID="b40b41dd-302c-4b9f-b61c-972568c6357c
}


Lots of inconsistencies. You need to finalize which drive is where and then make sure each has all UUIDs that are correct or device (/dev/sdXY) that match UUID as drives are set. Some system do not always have a BIOS that brings up drives in same order that adds to confusion and that is why Ubuntu uses UUIDs that do not change.

---

### Post by spiky001 on 2011-11-11
Sorry oldfred I was playing with that yesterday forgot that I hadn,t changed it back > set root=(/dev/sdc,[COLOR=Red]msdos2[/COLOR])

menuentry "GNU/Linux, Linux 3.1-lfs-7.0" {
        linux   /boot/vmlinuz-3.1-lfs-7.0 root=UUID="b40b41dd-302c-4b9f-b61c-972568c6357c
}                      should read ```
set root=(hd2,1)

menuentry "GNU/Linux, Linux 3.1-lfs-7.0" {
        linux   /boot/vmlinuz-3.1-lfs-7.0 root=/dev/sdc1 ro
}                      
```This 1 is not the 1 in Question > menuentry "PLANET-SPIKE - 2.6.38.3 (on [COLOR=Red]/dev/sdb1[/COLOR])" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root [COLOR=Red]897e754d-973c-4314-bb7e-d5f73389bea9[/COLOR]
    linux /boot/vmlinux-2.6.38.3-lfs-6.7 root=/dev/[COLOR=Red]sda1[/COLOR] ro
}
fstab:
/dev/[COLOR=Red]sda1[/COLOR]      /            ext3     defaults          1    1
/dev/[COLOR=Red]sda2[/COLOR]      swap         swap     pri=1             0    0                      The script was run from Ubuntu sda1. All I want is lfs which is on sdc to load it,s own grub and boot "Ignore the 1 on sdb thats an old install (LEARNING)

SDA has the machine OS windows and Ubuntu 11.04 
SDB has 11.10 plussome other lfs builds IGNORE
SDC HAS LFS (NEW BUILD) I did try the UUID as blkid reported 
/dev/sdc1: LABEL="LFS-7rc2" UUID="b40b41dd-302c-4b9f-b61c-972568c6357c" TYPE="ext4"
That is what I was trying last night

---

### Post by oldfred on 2011-11-11
When booting from sdc, you may need to change the hd2 to hd0. I found that the boot drive in grub is always hd0 when I directly booted my flash drives or other numbered drives & tried to chain load to another MBR. Drive order varied in grub. Boot drive in BIOS is always hd0. Leave linux line to sdc1 as by then it sees drives in device order.

try this:

set root=(hd0,1)

menuentry "GNU/Linux, Linux 3.1-lfs-7.0" {
        linux   /boot/vmlinuz-3.1-lfs-7.0 root=/dev/sdc1 ro
}

---

### Post by spiky001 on 2011-11-11
I tried that got > Please append "root=boot"
here are avalble partitions sda1 sda2 >>>sda6
kernel panicnot syncing VFS root fs unknownI have tried lots of variations as well. I know the laptop will boot from USB drives as I can select 2nd drive with 11.10 on and it will boot with it,s own grub

---

### Post by oldfred on 2011-11-11
If you boot directly from sdc does it see it as sda? or only when you boot with just that drive?

Some BIOS promote USB drives to sda in drive order?

---

### Post by spiky001 on 2011-11-12
Ok been experimenting again, I removed all drives except lfs on usb  booted live cd chroot into lfs ran grub-install /dev/sda redone fstab & grub.cfg wont boot, I then put the drive into laptop ide it boots (without changing sda settings)???? Ok so now I,m thinking somewhere else is causing the problem. Any thoughts!!!

---

### Post by oldfred on 2011-11-12
Then it may be some BIOS setting. And that can take more experimentation.

BIOS issues I have seen:

> BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
core unlocker feature on asus m4a87td usb3 was causing the problem
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
Old gpt data on drive
Disable Quickboot in BIOS
BIOS setting, Keyboard response in grub really slow
Fast Boot setting prevents keyboard from working & other issues
Bios not loading no key works - disconnected power for about 10-15 minutes and the bios reset itself.
After update, It had reset to the BIOS defaults, setting the video to ONBOARD and switching off the dynamic video memory allocation (manually allocating 32Mb instead of leaving it as AUTO).
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.

It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.


---

### Post by spiky001 on 2011-11-12
Dont think it,s bios I have 11.10 on sdb with it,s own grub that boots and I have run BT4 from usb with it,s own grub on this laptop Thks for support, I,m not getting much back from Linuxquestions/LFS forum either

---

### Post by spiky001 on 2011-11-12
Ok can I add this 40 custom entry

### BEGIN /etc/grub.d/40_custom ###
 # This file provides an easy way to add custom menu entries.  Simply type the 
# menu entries you want to add after this comment.  Be careful not to change 
# the 'exec tail' line above.

 insmod ext2 set root=(hd2,1) 
 menuentry "GNU/Linux, Linux 3.1-lfs-7.0" {
 linux   /boot/vmlinuz-3.1-lfs-7.0 root=/dev/sdc1 ro
 }
### END /etc/grub.d/40_custom ###


 I want to see if it will boot from grub on sda. Is it just a case of adding the lines to grub.cfg do I need to run any commands.
Or would it be better to run update-grub

---

### Post by oldfred on 2011-11-12
If you add something to 40_custom, then you have to run sudo update-grub to get it written into grub.cfg.

---

### Post by spiky001 on 2011-11-13
Thks for help oldfred I fixed the problem by adding rootdelay to grub.cfg this allows time for the usb drive to load.

---

