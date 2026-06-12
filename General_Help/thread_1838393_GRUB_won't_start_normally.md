---
title: "GRUB won't start normally"
date: 2011-09-03
forum: General Help
---

### Post by aprochaska on 2011-09-03
I have a dual-boot configuration with Ubuntu 10.04 and Win XP running on a Dell Dimention 8400.  When I hard boot, the grub menu doesn't come up after the BIOS boot.  It just sits with a flashing cursor in the upper left corner.  However, when I boot to Setup (F2) and then exit to normal boot, grub comes up fine.  

I tried update-grub and it found all the partitions, but when I restarted I still hung until I went back and went through F2-Setup.

I've included system information below.
Any ideas about why the system can't start grub directly, and what I might do to fix it?

Thanks for any help.

Alan Prochaska

* * *

Ubuntu 10.04
Grub 1.98-1ubuntu12

Output of mount
> alan@prochaska-family:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb1 on /data1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5 on /data2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1 on /windows type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5 on /shared type vfat (rw,utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/alan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alan)
/dev/sdc2 on /media/IPOD type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
alan@prochaska-family:~$ ^C
/etc/fstab

> alan@prochaska-family:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=64490366-350e-424c-b84a-dd54cec9e34f /               ext3    errors=remount-ro 0       1
# /data1 was on /dev/sdb1 during installation
UUID=1C14E5D214E5AF48 /data1          ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /data2 was on /dev/sdb5 during installation
UUID=7C9CE3CA9CE37CD0 /data2          ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /shared was on /dev/sda5 during installation
UUID=1B5F-EE2B  /shared         vfat    utf8,umask=007,gid=46 0       1
# /windows was on /dev/sda1 during installation
UUID=5434E19334E1787E /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda3 during installation
UUID=f637f017-8c77-467c-81af-82ad09548789 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
alan@prochaska-family:~$ 
output of grub-update

> alan@prochaska-family:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found linux image: /boot/vmlinuz-2.6.32-32-generic
Found initrd image: /boot/initrd.img-2.6.32-32-generic
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-30-generic
Found initrd image: /boot/initrd.img-2.6.32-30-generic
Found linux image: /boot/vmlinuz-2.6.32-29-generic
Found initrd image: /boot/initrd.img-2.6.32-29-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
Found Microsoft Windows XP Professional on /dev/sdb1
done
alan@prochaska-family:~$ I found this useful post between dspetrov and coffeecat, but didn't find a solution in there.[INDENT][http://ubuntuforums.org/showthread.php?t=1716183](http://ubuntuforums.org/showthread.php?t=1716183)

[/INDENT]

---

### Post by oldfred on 2011-09-03
Post boot script's results.txt. Is one drive IDE/PATA and the other SATA? Sometimes drives do not come up to speed or something where it just does not want to boot from one or the other.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

You may want to houseclean out some old kernels. Will not help boot issue but will make menu less cluttered. I always keep one older one that works just in case something happens to the current one.

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by aprochaska on 2011-09-03
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda2 and looks at sector 73838091 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdc2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    41,945,714    41,945,652   7 NTFS / exFAT / HPFS
/dev/sda2          41,945,715    83,891,429    41,945,715  83 Linux
/dev/sda3          83,891,430    88,084,394     4,192,965  82 Linux swap / Solaris
/dev/sda4          88,084,395   288,077,579   199,993,185   5 Extended
/dev/sda5          88,084,458   288,077,579   199,993,122   b W95 FAT32


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   268,414,019   268,413,957   7 NTFS / exFAT / HPFS
/dev/sdb2         268,414,020   976,768,064   708,354,045   f W95 Extended (LBA)
/dev/sdb5         268,414,083   976,768,064   708,353,982   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 30.0 GB, 30005821440 bytes
255 heads, 62 sectors/track, 3706 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63       160,649       160,587   0 Empty
/dev/sdc2             160,650    58,605,118    58,444,469   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        5434E19334E1787E                       ntfs       Win XP 02
/dev/sda2        64490366-350e-424c-b84a-dd54cec9e34f   ext3       
/dev/sda3        f637f017-8c77-467c-81af-82ad09548789   swap       
/dev/sda5        1B5F-EE2B                              vfat       
/dev/sdb1        1C14E5D214E5AF48                       ntfs       
/dev/sdb5        7C9CE3CA9CE37CD0                       ntfs       Data
/dev/sdc2        27DF-0C35                              vfat       IPOD

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /windows                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /                        ext3       (rw,errors=remount-ro)
/dev/sda5        /shared                  vfat       (rw,utf8,umask=007,gid=46)
/dev/sdb1        /data1                   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /data2                   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc2        /media/IPOD              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
--------------------------------------------------------------------------------

=========================== sda2/boot/grub/grub.cfg: ===========================

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

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
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
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=64490366-350e-424c-b84a-dd54cec9e34f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=64490366-350e-424c-b84a-dd54cec9e34f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=64490366-350e-424c-b84a-dd54cec9e34f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
    echo    'Loading Linux 2.6.32-32-generic ...'
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=64490366-350e-424c-b84a-dd54cec9e34f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=64490366-350e-424c-b84a-dd54cec9e34f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
    echo    'Loading Linux 2.6.32-31-generic ...'
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=64490366-350e-424c-b84a-dd54cec9e34f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=64490366-350e-424c-b84a-dd54cec9e34f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=64490366-350e-424c-b84a-dd54cec9e34f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=64490366-350e-424c-b84a-dd54cec9e34f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=64490366-350e-424c-b84a-dd54cec9e34f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=64490366-350e-424c-b84a-dd54cec9e34f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=64490366-350e-424c-b84a-dd54cec9e34f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=64490366-350e-424c-b84a-dd54cec9e34f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
    echo    'Loading Linux 2.6.31-16-generic ...'
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=64490366-350e-424c-b84a-dd54cec9e34f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=64490366-350e-424c-b84a-dd54cec9e34f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
    echo    'Loading Linux 2.6.31-15-generic ...'
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=64490366-350e-424c-b84a-dd54cec9e34f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-15-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 64490366-350e-424c-b84a-dd54cec9e34f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5434E19334E1787E
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 1C14E5D214E5AF48
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=64490366-350e-424c-b84a-dd54cec9e34f /               ext3    errors=remount-ro 0       1
# /data1 was on /dev/sdb1 during installation
UUID=1C14E5D214E5AF48 /data1          ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /data2 was on /dev/sdb5 during installation
UUID=7C9CE3CA9CE37CD0 /data2          ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /shared was on /dev/sda5 during installation
UUID=1B5F-EE2B  /shared         vfat    utf8,umask=007,gid=46 0       1
# /windows was on /dev/sda1 during installation
UUID=5434E19334E1787E /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda3 during installation
UUID=f637f017-8c77-467c-81af-82ad09548789 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  35.165437222 = 37.758600704   boot/grub/core.img                             1
  35.209905148 = 37.806347776   boot/grub/grub.cfg                             2
  35.188394070 = 37.783250432   boot/initrd.img-2.6.31-15-generic              3
  35.219663143 = 37.816825344   boot/initrd.img-2.6.31-16-generic              4
  35.209897518 = 37.806339584   boot/initrd.img-2.6.32-28-generic             11
  35.176839352 = 37.770843648   boot/initrd.img-2.6.32-29-generic              8
  35.169225216 = 37.762668032   boot/initrd.img-2.6.32-30-generic              7
  35.156575680 = 37.749085696   boot/initrd.img-2.6.32-31-generic              9
  35.398526669 = 38.008878592   boot/initrd.img-2.6.32-32-generic              9
  35.405892849 = 38.016787968   boot/initrd.img-2.6.32-33-generic             12
  35.151418209 = 37.743547904   boot/vmlinuz-2.6.31-15-generic                 5
  35.247170925 = 37.846361600   boot/vmlinuz-2.6.31-16-generic                 2
  35.235471249 = 37.833799168   boot/vmlinuz-2.6.32-28-generic                 5
  35.202188015 = 37.798061568   boot/vmlinuz-2.6.32-29-generic                 3
  35.137902737 = 37.729035776   boot/vmlinuz-2.6.32-30-generic                 2
  35.192128658 = 37.787260416   boot/vmlinuz-2.6.32-31-generic                 4
  35.226155758 = 37.823796736   boot/vmlinuz-2.6.32-32-generic                10
  35.382966518 = 37.992171008   boot/vmlinuz-2.6.32-33-generic                 2
  35.405892849 = 38.016787968   initrd.img                                    12
  35.398526669 = 38.008878592   initrd.img.old                                 9
  35.382966518 = 37.992171008   vmlinuz                                        2
  35.226155758 = 37.823796736   vmlinuz.old                                   10

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdc

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 20 00 02  |.X.MSDOS5.0.. ..|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  3f 3e 7e 03 00 00 00 00  00 00 00 00 00 00 00 00  |?>~.............|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  01 00 29 52 36 8b a8 69  50 6f 64 00 4d 45 20 20  |..)R6..iPod.ME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 08  |{......|.N..V@..|
00000070  cd 13 73 05 b9 ff ff 8a  f1 66 0f b6 c6 40 66 0f  |..s......f...@f.|
00000080  b6 d1 80 e2 3f f7 e2 86  cd c0 ed 06 41 66 0f b7  |....?.......Af..|
00000090  c9 66 f7 e1 66 89 46 f8  83 7e 16 00 75 38 83 7e  |.f..f.F..~..u8.~|
000000a0  2a 00 77 32 66 8b 46 1c  66 83 c0 0c bb 00 80 b9  |*.w2f.F.f.......|
000000b0  01 00 e8 2b 00 e9 48 03  a0 fa 7d b4 7d 8b f0 ac  |...+..H...}.}...|
000000c0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000d0  ee a0 fb 7d eb e5 a0 f9  7d eb e0 98 cd 16 cd 19  |...}....}.......|
000000e0  66 60 66 3b 46 f8 0f 82  4a 00 66 6a 00 66 50 06  |f`f;F...J.fj.fP.|
000000f0  53 66 68 10 00 01 00 80  7e 02 00 0f 85 20 00 b4  |Sfh.....~.... ..|
00000100  41 bb aa 55 8a 56 40 cd  13 0f 82 1c 00 81 fb 55  |A..U.V@........U|
00000110  aa 0f 85 14 00 f6 c1 01  0f 84 0d 00 fe 46 02 b4  |.............F..|
00000120  42 8a 56 40 8b f4 cd 13  b0 f9 66 58 66 58 66 58  |B.V@......fXfXfX|
00000130  66 58 eb 2a 66 33 d2 66  0f b7 4e 18 66 f7 f1 fe  |fX.*f3.f..N.f...|
00000140  c2 8a ca 66 8b d0 66 c1  ea 10 f7 76 1a 86 d6 8a  |...f..f....v....|
00000150  56 40 8a e8 c0 e4 06 0a  cc b8 01 02 cd 13 66 61  |V@............fa|
00000160  0f 82 54 ff 81 c3 00 02  66 40 49 0f 85 71 ff c3  |..T.....f@I..q..|
00000170  4e 54 4c 44 52 20 20 20  20 20 20 00 00 00 00 00  |NTLDR      .....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 41 70  |..............Ap|
000001b0  70 6c 65 20 69 50 6f 64  20 20 20 20 20 20 00 01  |ple iPod      ..|
000001c0  01 00 00 fe 3f 09 3f 00  00 00 4b 73 02 00 00 00  |....?.?...Ks....|
000001d0  01 0a 0b fe fe ff 8a 73  02 00 b5 ca 7b 03 00 00  |.......s....{...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdc1

00000000  7b 7b 7e 7e 20 20 2f 2d  2d 2d 2d 2d 5c 20 20 20  |{{~~  /-----\   |
00000010  7b 7b 7e 7e 20 2f 20 20  20 20 20 20 20 5c 20 20  |{{~~ /       \  |
00000020  7b 7b 7e 7e 7c 20 20 20  20 20 20 20 20 20 7c 20  |{{~~|         | |
00000030  7b 7b 7e 7e 7c 20 53 20  54 20 4f 20 50 20 7c 20  |{{~~| S T O P | |
00000040  7b 7b 7e 7e 7c 20 20 20  20 20 20 20 20 20 7c 20  |{{~~|         | |
00000050  7b 7b 7e 7e 20 5c 20 20  20 20 20 20 20 2f 20 20  |{{~~ \       /  |
00000060  7b 7b 7e 7e 20 20 5c 2d  2d 2d 2d 2d 2f 20 20 20  |{{~~  \-----/   |
00000070  43 6f 70 79 72 69 67 68  74 28 43 29 20 32 30 30  |Copyright(C) 200|
00000080  31 20 41 70 70 6c 65 20  43 6f 6d 70 75 74 65 72  |1 Apple Computer|
00000090  2c 20 49 6e 63 2e 2d 2d  2d 2d 2d 2d 2d 2d 2d 2d  |, Inc.----------|
000000a0  2d 2d 2d 2d 2d 2d 2d 2d  2d 2d 2d 2d 2d 2d 2d 2d  |----------------|
*
000000f0  2d 2d 2d 2d 2d 2d 2d 2d  2d 2d 2d 2d 2d 2d 2d 00  |---------------.|
00000100  5d 69 68 5b 00 40 00 00  0c 01 03 00 00 00 00 00  |]ih[.@..........|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200

Unknown BootLoader on sdc2

00000000  eb 3c 90 2a 55 4f 4b 4a  49 48 43 00 02 20 20 00  |.<.*UOKJIHC..  .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 8a 73 02 00  |........?....s..|
00000020  b4 ca 7b 03 ba 37 00 00  00 00 00 00 02 00 00 00  |..{..7..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 35 0c df 27 49  50 4f 44 20 20 20 20 20  |..)5..'IPOD     |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 5b 7c ac  |  FAT32   ...[|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 7b  7b 7e 7e 7c 20 53 20 54  |.......{{~~| S T|
00000080  20 4f 20 50 20 7c 20 54  68 69 73 20 69 73 20 41  | O P | This is A|
00000090  70 70 6c 65 20 69 50 6f  64 20 6e 6f 74 20 61 20  |pple iPod not a |
000000a0  62 6f 6f 74 61 62 6c 65  20 64 69 73 6b 2e 50 6c  |bootable disk.Pl|
000000b0  65 61 73 65 20 74 72 79  20 61 67 61 69 6e 20 2e  |ease try again .|
000000c0  2e 2e 20 00 00 00 00 00  00 00 00 00 00 00 00 00  |.. .............|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




```

---

### Post by aprochaska on 2011-09-03
```
alan@prochaska-family:~/bin$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:    10.04
Codename:    lucid
alan@prochaska-family:~/bin$ ^C


```

---

### Post by oldfred on 2011-09-03
Are you booting from sda or sdb and which is the default in BIOS? Does changing the default make any difference? Boot script/grub does not always show drive correctly so eitherboth may work. You may be able to test with one time boot key. Try booting and choose which drive to boot from. Does one work and the other not?

---

### Post by aprochaska on 2011-09-04
It boots from sda.  sda has OS's, swap,  and minimal space for data.  sdb is a data drive (no OS).  Setup lists them as sata-0 and sata-1 because those are the names of the connectors on the motherboard.  Regarding boot sequence, Setup only allows control by device type: floppy, sata, ide, then CD.  I didn't see a way to specify to boot from one of the devices in a given type, but as I write that, it sounds strange.  The Boot Sequence choices only allowed specifying the device type, not the partiuclar device.  ???

What does BIOS do?  Does it follow a script?  Is it human readable and where does it live?

Sorry for the newbie questions.  I really appreciate your help.

---

### Post by oldfred on 2011-09-04
Each mfg. has a custom BIOS for its motherboard and configuration. Old IDE/PATA devices had simple BIOS and boot was controlled by jumpers on hard drive or location on cable (master/Slave setting).

Newer systems with SATA have BIOS that lets you choose as SATA has no jumpers. Some have another line even on a different page where which SATA drive is selected, other let you select hard drive and then have a sub menu of which hard drive. A few early SATA systems only let you boot from first drive which was usually a IDE drive.

[http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)

UEFI is replacing BIOS on new systems. But they have BIOS mode for now for compatibility with older devices and operating systems.

Even though boot script looks ok, you can try reinstalling grub2's boot loader to MBR from Ubuntu liveCD.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda2 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda2 if not correct:
sudo fdisk -l
#confirm that linux is sda2
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by aprochaska on 2011-09-04
How important is it to do that in a session booted from Live CD?  I made a current CD, booted from it, brought up a terminal and it couldn't find grub.  I assume that's because it didn't have any of my file systems mounted.  I found a thread describing that process, but it seems a little involved (worried about breaking something).

Would it achieve the same effect if I were to uninstall and reinstall grub2 via the Synaptic Package Manager when I'm booted normally?

Or could I run the commends you describe when booted normally (ie. not from Live CD)?  Would it be safe?

Thanks for info.

---

### Post by oldfred on 2011-09-05
If you are now booting you do not have to reinstall grub2's boot loader. Not sure where you are at. LiveCd is to get you to boot and be able to repair system that does not boot. You cannot directly work on installed system, but have to mount the partition to reinstall grub as posted above. Or you have to chroot into your system to do major repairs.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by aprochaska on 2011-09-18
I'm working about the BIOS-level startup problems by going into Setup and from there to grub.  I started a new thread to solve some problems with long startup time and file system references.  Unless it's unacceptable to the forum, I'm going to take care of that first, and then return to this.  Thanks for the help so far.

---

### Post by aprochaska on 2011-09-24
I installed Grub Customizer and used it to clean up my extra long list of ubuntu versions that had accumulated on the menu.  I cut it down to 4 versions.  Saved, restarted, and started up happened normally.  I think it must have saved and normalized whatever grub file was out of whack.

---

