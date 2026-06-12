---
title: "GRUB2 and Windows: can't boot XP from GRUB2"
date: 2010-05-06
forum: General Help
---

### Post by Objekt on 2010-05-06
I'm having an odd dual-boot problem.  Briefly, I can't boot Windows XP from its entry on the GRUB2 menu.

If I set the disk order in BIOS so that the machine boots off the drive with Windows XP, XP starts normally.  However, if I boot off the Ubuntu drive, which brings up the GRUB2 menu, choosing the "Windows 7 loader" option (why it says Windows 7 when there's only Windows XP is another question!) just makes my system reboot.

It appears there's some problem with the way GRUB2 attempts to start Windows XP, but I can't figure out what.  

I'm also wondering why GRUB2 thinks it sees the Windows 7 loader.  There shouldn't be any Windows 7 anything anywhere.  I once had a Windows 7 RC install on the same disk as Windows XP, but I wiped the Windows 7 system partition and reallocated its space as just another NTFS partition.

FWIW, GRUB2 is installed on the MBR of the disk containing my Ubuntu install.  Windows XP has a different drive all to itself.

---

### Post by replikanxxl on 2010-05-08
i have a similar problem. i used to have ubuntu on one harddrive. and windows XP in another harddrive. when i updated to ubuntu LTS 10.04 , the ubuntu is working still. but the windows XP is not booting. it has the entry at grub menu (its grub 1.98 btw) . but when i choose it in menu and press enter , i wait a lot and nothing happens . just a black screen and a flashing underscore.hope someone helps soon !!!

---

### Post by jscherer92 on 2010-05-08
You need to do a sudo apt-get update grub. I am sure that is what the command is. Hope this helps.

- Justin -
[http://tutorials-for-all.dyndns.org.x10hosting.com](http://tutorials-for-all.dyndns.org.x10hosting.com)

---

### Post by wilee-nilee on 2010-05-08
Post this script in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

For others having this problem please start your own thread and post the script. To put in code tags for a scrolling text, paste the read out of the script in a reply highlight it then tick on the # sign in the reply panel. This script is very hard to read without it being in a code box.

---

### Post by raxvan on 2010-05-09
I have the exact same problem as replikanxxl.
i get a black screen and nothing happens , nothing loads (on Ctrl+Alt+delete the computer restarts).

Thanks , and please help , i'm in urgent need of windows.

This is the script rezult:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 176628507 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    49,158,899    49,158,837   7 HPFS/NTFS
/dev/sda2          49,158,900   312,576,704   263,417,805   f W95 Ext d (LBA)
/dev/sda5          49,158,963    53,255,474     4,096,512   7 HPFS/NTFS
/dev/sda6          53,255,538   176,136,659   122,881,122   7 HPFS/NTFS
/dev/sda7         176,136,723   306,921,824   130,785,102  83 Linux
/dev/sda8         306,921,888   312,576,704     5,654,817  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DC9CB5E99CB5BE78                       ntfs       win                           
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1A4031DD4031BFF5                       ntfs       Tiny                          
/dev/sda6        C868C6E968C6D57A                       ntfs       D1                            
/dev/sda7        5001034b-7309-42df-a831-500b77abae19   ext4                                     
/dev/sda8        ccc9f4cc-a39c-4adf-bd01-fe8a1e7ffcc2   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /media/Tiny              fuseblk    (rw,nosuid,nodev,allow_other,blksize=2048)
/dev/sda1        /media/win               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6        /media/D1                fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
redirect=usebiossettings 
redirectbaudrate= 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 5001034b-7309-42df-a831-500b77abae19
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 5001034b-7309-42df-a831-500b77abae19
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 5001034b-7309-42df-a831-500b77abae19
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=5001034b-7309-42df-a831-500b77abae19 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 5001034b-7309-42df-a831-500b77abae19
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=5001034b-7309-42df-a831-500b77abae19 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 5001034b-7309-42df-a831-500b77abae19
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=5001034b-7309-42df-a831-500b77abae19 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 5001034b-7309-42df-a831-500b77abae19
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=5001034b-7309-42df-a831-500b77abae19 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 5001034b-7309-42df-a831-500b77abae19
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 5001034b-7309-42df-a831-500b77abae19
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=5001034b-7309-42df-a831-500b77abae19 / ext4 errors=remount-ro 0 1
# Entry for /dev/sda8 :
UUID=ccc9f4cc-a39c-4adf-bd01-fe8a1e7ffcc2 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda5 /media/Tiny ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/win ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda6 /media/D1 ntfs-3g rw,suid,dev,exec,auto,user,async,locale=en_US.UTF-8 0 0

=================== sda7: Location of files loaded by Grub: ===================


  90.4GB: boot/grub/core.img
  95.5GB: boot/grub/grub.cfg
 117.0GB: boot/initrd.img-2.6.31-21-generic
 127.6GB: boot/initrd.img-2.6.32-22-generic
 143.9GB: boot/vmlinuz-2.6.31-21-generic
 102.6GB: boot/vmlinuz-2.6.32-22-generic
 127.6GB: initrd.img
 117.0GB: initrd.img.old
 102.6GB: vmlinuz
 143.9GB: vmlinuz.old

```

---

### Post by Objekt on 2010-05-10
> **jscherer92 said:**
> You need to do a sudo apt-get update grub. I am sure that is what the command is. Hope this helps.

- Justin -
[http://tutorials-for-all.dyndns.org.x10hosting.com](http://tutorials-for-all.dyndns.org.x10hosting.com)

Negative.  There is no such command.  apt-get doesn't take "update" as an argument.

Maybe you meant "sudo update-grub."  I already did that a couple of times.  

There's a problem with the way grub2 calls the Windows bootloader.

Latest results of the bootinfo script:

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc
 => Grub 0.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
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

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf2a6f2a6

Partition  Boot         Start           End          Size  Id System

/dev/sda2          40,965,750 1,953,520,064 1,912,554,315   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcc9eeb12

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    30,105,809    30,105,747  83 Linux
/dev/sdb2          30,105,810   142,657,199   112,551,390   5 Extended
/dev/sdb5          30,105,873    37,913,399     7,807,527  82 Linux swap / Solaris
/dev/sdb6          37,913,463   142,657,199   104,743,737  83 Linux
/dev/sdb3         142,657,200   321,669,494   179,012,295  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sdc1       1,041,349,365 1,088,451,944    47,102,580   7 HPFS/NTFS
/dev/sdc2                  63   998,343,359   998,343,297   7 HPFS/NTFS
/dev/sdc3    *    998,343,360 1,041,349,364    43,006,005   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x59ecdd5e

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   625,137,344   625,137,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="1AA469BAA46998D1" LABEL="Storage" TYPE="ntfs" 
/dev/sdb1: UUID="075bba33-2604-4962-8456-bc020ec81c33" TYPE="ext3" 
/dev/sdb3: LABEL="UbuntuStorage" UUID="d6dbe37d-d487-474d-9e14-9db95cb10297" TYPE="ext3" 
/dev/sdb5: UUID="6af0cef2-ebe2-45b5-8f09-f05b2d8802cd" TYPE="swap" 
/dev/sdb6: UUID="4e708513-c001-465a-84cb-3f8f24ffac39" TYPE="ext3" 
/dev/sdc1: UUID="CA58B57358B55EBF" LABEL="MoreNTFS" TYPE="ntfs" 
/dev/sdc2: UUID="3C482AA9482A61BE" LABEL="NotWin7" TYPE="ntfs" 
/dev/sdc3: UUID="BC009A320099F41C" LABEL="NewXP" TYPE="ntfs" 
/dev/sdd1: UUID="B86C9ABE6C9A773A" LABEL="OldWD" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /proc/bus/usb type usbfs (rw,devgid=1001,devmode=664)
/dev/sda2 on /media/Storage type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdd1 on /media/OldWD type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc2 on /media/NotWin7 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb3 on /media/UbuntuStorage type ext3 (rw)
/dev/sdb6 on /home type ext3 (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/objekt910/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=objekt910)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set default="3"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set 075bba33-2604-4962-8456-bc020ec81c33
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
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.33-020633-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 075bba33-2604-4962-8456-bc020ec81c33
	linux	/boot/vmlinuz-2.6.33-020633-generic root=UUID=075bba33-2604-4962-8456-bc020ec81c33 ro   quiet splash
	initrd	/boot/initrd.img-2.6.33-020633-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 075bba33-2604-4962-8456-bc020ec81c33
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=075bba33-2604-4962-8456-bc020ec81c33 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 075bba33-2604-4962-8456-bc020ec81c33
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=075bba33-2604-4962-8456-bc020ec81c33 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-9-rt" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 075bba33-2604-4962-8456-bc020ec81c33
	linux	/boot/vmlinuz-2.6.31-9-rt root=UUID=075bba33-2604-4962-8456-bc020ec81c33 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-9-rt
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc3)" {
	insmod ntfs
	set root=(hd2,3)
	search --no-floppy --fs-uuid --set bc009a320099f41c
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

proc            /proc           proc    defaults        0       0
UUID=075bba33-2604-4962-8456-bc020ec81c33 /               ext3    errors=remount-ro 0       1
UUID=4e708513-c001-465a-84cb-3f8f24ffac39 /home           ext3    defaults        0       2
UUID=6af0cef2-ebe2-45b5-8f09-f05b2d8802cd none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy  auto    rw,user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0

#experimental line
/dev/sda2 /media/Storage ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1

#mounting NTFS data partitions
#old WD 320 GB drive
UUID=B86C9ABE6C9A773A /media/OldWD ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1
#storage partition on second 1 TB drive
UUID=3C482AA9482A61BE /media/NotWin7 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1

#yet another for the new ext3 partition
#old reference: /dev/sdc3 

UUID=d6dbe37d-d487-474d-9e14-9db95cb10297	/media/UbuntuStorage ext3 defaults 0 2

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-19-generic
    .0GB: boot/initrd.img-2.6.31-20-generic
    .0GB: boot/initrd.img-2.6.31-9-rt
    .0GB: boot/initrd.img-2.6.33-020633-generic
    .0GB: boot/vmlinuz-2.6.31-19-generic
    .0GB: boot/vmlinuz-2.6.31-20-generic
    .0GB: boot/vmlinuz-2.6.31-9-rt
    .0GB: boot/vmlinuz-2.6.33-020633-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

================================ sdc3/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

Hope this helps.

---

### Post by oldfred on 2010-05-10
Did you at some point switch drives 0 & 2?

Your boot.ini from XP:
rdisk(0)partition(3)

Your Ubuntu windows boot:
set root=(hd2,3)

---

### Post by Objekt on 2010-05-13
Not sure what you mean.  I have to "switch" drives every time I want to boot one OS or the other.  That is, I have to go into BIOS and manually set either the drive containing Windows XP (sdc) or the drive containing Ubuntu (sdb) as "first" to boot XP or Ubuntu, respectively.  So the order of disks changes, depending on which OS I'm running.

Physically, I have two 1 TB drives connected to the first two SATA ports, then the 160 GB drive, then the 320 GB drive (1,2,3,4).  This is reflected in the bootinfo script results, where the drives are called sda, sdb, sdc, and sdd, according to that order.  I haven't changed any of that since long before my current problem.

---

### Post by oldfred on 2010-05-13
No the boot.ini says windows is in drive 0 and everything else says it is drive 2.

Grub usually then adds this command so windows will think it is still  drive 0 - drivemap -s is switch drives.

drivemap -s (hd2) ${root}
or
drivemap -s (hd2) (hd0)

I would add this to 40_custom and see if it works:

menuentry "Windows 7 (loader) (on /dev/sdc3)" {
    insmod ntfs
    set root=(hd2,3)
    search --no-floppy --fs-uuid --set bc009a320099f41c
    drivemap -s (hd2) ${root}
    chainloader +1
}

---

### Post by Objekt on 2010-05-13
That looks like it might work. 

I can't figure out why GRUB2 insists on referring to Windows 7, and it's a little worrying.  I thought I had removed all traces of Windows 7 from my machine, by uninstalling the Windows 7 RC, reformatting its partition, and reinstalling the Windows XP bootloader with the Windows XP Recovery Console (fixmbr & fixboot commands).

---

### Post by oldfred on 2010-05-13
I do not know what grub looks for but in your sdc3 partition are two win7 boot files still:
/bootmgr /Boot/BCD

Not sure what else since this is all the boot script reports.

---

### Post by Objekt on 2010-05-14
THANKS!  That was exactly the problem!  

I moved those Win7 leftovers, bootmgr and the whole "/boot" folder, to a differently-named folder (I wasn't brave enough to delete them outright).  Then ran "sudo update-grub" again.  This time, GRUB2 detected my "Windows XP" install instead of calling it "Windows 7."  More importantly, I can now boot Windows XP from the GRUB2 menu.

This one's solved. :)

---

### Post by oldfred on 2010-05-14
Glad you got it working. :)

And it is good to know that those left over files can be the cause of the win7 listing. We have seen several others with that issue and usually suggest a lot of editing to either the scripting logic or a 40_custom entry. Renaming files you are not sure you want to delete is always the best way to test as then you can rename them back.

---

