---
title: "Grub2 &amp; Win 7 No such a device."
date: 2010-03-30
forum: General Help
---

### Post by l4zy on 2010-03-30
Hi, 

I've got problem. Grub2 fails when trying to boot into Win 7 from Grub2 menu. 

No such a device.

I did run boot_info_script055.sh

Here is the result:
 [SIZE="2"]     Boot Info Script 0.55    dated February 15th, 2010

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for
    (UUID=34c6661d-7609-441c-b7b9-1d60d1e44fd5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:
    Boot files/dirs:

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

sdc3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:
    Boot files/dirs:

=========================== Drive/Partition Info :=============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf8000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       160,649       160,587  de Dell Utility
/dev/sda2             161,792     4,356,095     4,194,304   7 HPFS/NTFS
/dev/sda3    *      4,356,096 1,465,145,343 1,460,789,248   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc1066afe

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,465,145,343 1,465,143,296   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdc1              34    97,656,284    97,656,251 Linux or Data
/dev/sdc2      97,656,285   115,234,410    17,578,126 Linux Swap
/dev/sdc3     115,234,411 3,907,027,379 3,791,792,969 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D9-0915                              vfat       DellUtility
/dev/sda2        2A105251105223DB                       ntfs       RECOVERY
/dev/sda3        18BA55ECBA55C6C2                       ntfs       OS
/dev/sdb1        9C4E5FB34E5F8544                       ntfs       DATAPART1
/dev/sdc1        34c6661d-7609-441c-b7b9-1d60d1e44fd5   ext4
/dev/sdc2        14ee7afe-7dcd-4e94-aa6a-df38d35d8ec2   swap
/dev/sdc3        fceb3c4c-9649-4ffb-ad49-51c8361c4f10   ext4

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc3        /home                    ext4       (rw)


=========================== sdc1/boot/grub/grub.cfg: ===========================


[/SIZE]

My grub2 is pointing to /dev/sda3 where Win 7 bootloader is located if i understand right.

Here is info how my Linux / Windows boot options are in grub.cfg

[SIZE="2"]
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
        set root=(hd2,1)

        linux   /boot/vmlinuz-2.6.31-20-generic root=UUID=34c6661d-7609-441c-b7b9-1d60d1e44fd5 ro   quiet splash
        initrd  /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        insmod ext2
        set root=(hd2,1)

        linux   /boot/vmlinuz-2.6.31-20-generic root=UUID=34c6661d-7609-441c-b7b9-1d60d1e44fd5 ro single
        initrd  /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd2,1)

        linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=34c6661d-7609-441c-b7b9-1d60d1e44fd5 ro   quiet splash
        initrd  /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        insmod ext2
        set root=(hd2,1)

        linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=34c6661d-7609-441c-b7b9-1d60d1e44fd5 ro single
        initrd  /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry &#8220;Windows 7&#8243; {
insmod ntfs
set root=(hd0,3)
chainloader +1
}
### END /etc/grub.d/11_Windows ###
[/SIZE]


Any ideas ?

---

### Post by Mark Phelps on 2010-03-30
Unless I'm missing something, the GRUB 2 stanza looks OK for Win7.

So, what exactly are you seeing onscreen when you try to boot into Win7?

---

### Post by l4zy on 2010-03-30
When grub2 menu comes up i have Windows 7 (/dev/sda3) boot option. When i choose that, it gives me "no such a device".

---

