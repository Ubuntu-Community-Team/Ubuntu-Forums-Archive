---
title: "Can not change file owners on a rade drive"
date: 2011-05-07
forum: General Help
---

### Post by Robbyx on 2011-05-07
I have tried chown and pcman in root mode but I can not change the owner or group of the directories and files on this drive. I think my inability to open both firefox and thunderbird are connected to this problem. Both profiles are on the rade drive. There are no .parentlock files in the profiles and yet the report is that both programs are in use, even after restarting the computer. I have had to install cromium to go online in lieu of FF:

this is my fstab. this is the line refers to the rade ntfs drive:

# /media/mydocs was on /dev/sdc1 during installation
UUID=724E07853D78E7A8 /media/mydocs   ntfs    defaults,umask=0022,gid=46 0       0

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=45a2e92c-c759-4732-9662-988da7f8ea7b /home           ext3    defaults        0       2
# /media/g was on /dev/sda5 during installation
UUID=7b859c36-c68d-408f-9425-de9f525f3c71 /media/g        reiserfs defaults        0       2
# /media/mydocs was on /dev/sdc1 during installation
UUID=724E07853D78E7A8 /media/mydocs   ntfs    defaults,umask=0022,gid=46 0       0
# /media/video was on /dev/sda6 during installation
UUID=86290d05-e673-4310-9f3e-93af30cc13af /media/video    reiserfs defaults        0       2
# swap was on /dev/sda4 during installation
UUID=e36cb6cf-f372-4418-bd8b-f36a27dc3e76 none            swap    sw              0       0

---

### Post by Robbyx on 2011-05-07
Gparted is showing the following error messages for the drive. do i have to use a windows disk to repair it?

Is there an ubuntu way of repairing the drive?


> GParted 0.7.0 --enable-libparted-dmraid

Libparted 2.3

Check and repair file system (ntfs) on /dev/sdb1  00:00:26    ( ERROR )
    	
calibrate /dev/sdb1  00:00:00    ( SUCCESS )
    	
path: /dev/sdb1
start: 63
end: 488392064
size: 488392002 (232.88 GiB)
check file system on /dev/sdb1 for errors and (if possible) fix them  00:00:26    ( ERROR )
    	
ntfsresize -P -i -f -v /dev/sdb1
    	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sdb1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 250056704512 bytes (250057 MB)
Current device size: 250056705024 bytes (250057 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Cluster accounting failed at 12687607 (0xc198f7): missing cluster in $Bitmap
.....

Cluster accounting failed at 44434564 (0x2a60484): extra cluster in $Bitmap
Filesystem check failed! Totally 128 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired

---

### Post by oldfred on 2011-05-08
I have both Firefox & Thunderbird profiles still in my shared NTFS partition for when I used XP a lot. You cannot change permissions or ownership on NTFS. They are set at time of mount in fstab.

You need a windows disk to run chkdsk. The ntfsfix only does minor repairs and sets the chkdsk flag. If it is not a boot able disk then it is locked as once flag is set Linux programs will not normally open it to prevent further damage that chkdsk might not be able to fix. 

You can use any windows disk to run chkdsk. 

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

To repair windows with mounting issues from your Windows XP CD - Do not run fixMBR unless you want windows boot loader in the MBR.
fixboot C:
XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by Robbyx on 2011-05-09
I have a win2k pro installation disk. I have booted from it and gone through to the repair console. It then drops me to c:\ From there I can not find the rade drive that i wish to repair. I have tried the various letters of the alphabet.  It is a mirrored 3ware hardware raded drive. **Do you know what  i should do next?**


**I assume there is no program that will allow me to keep the data on the drive and change its file structure to a more linux friendly format.**

---

### Post by oldfred on 2011-05-09
Post this so we can see your entire configuration:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Robbyx on 2011-05-09
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2can.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97-os.1 is installed in the MBR of /dev/sdc and looks on the same 
    drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

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

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    59,842,124    59,842,062  83 Linux
/dev/sda2          59,842,125   122,849,054    63,006,930  83 Linux
/dev/sda3         122,849,116   964,815,704   841,966,589   5 Extended
/dev/sda5         122,849,118   337,364,999   214,515,882  83 Linux
/dev/sda6         337,365,063   964,815,704   627,450,642  83 Linux
/dev/sda4         964,815,705   976,768,064    11,952,360  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250058301440 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2055 MB, 2055208960 bytes
16 heads, 32 sectors/track, 7840 cylinders, total 4014080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  32     4,014,079     4,014,048   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4a60ff9d-f704-4d04-a829-4c4702f5c203   ext3                                     
/dev/sda2        45a2e92c-c759-4732-9662-988da7f8ea7b   ext3                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        e36cb6cf-f372-4418-bd8b-f36a27dc3e76   swap                                     
/dev/sda5        7b859c36-c68d-408f-9425-de9f525f3c71   reiserfs                                 
/dev/sda6        86290d05-e673-4310-9f3e-93af30cc13af   reiserfs                                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        724E07853D78E7A8                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        B72D-6759                              vfat       KINGSTON                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/usb0              vfat       (rw,noexec,nodev,sync,noatime,nodiratime)
/dev/sdb1        /media/mydocs            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /home                    ext3       (rw,commit=0)
/dev/sda5        /media/g                 reiserfs   (rw)
/dev/sda6        /media/video             reiserfs   (rw)


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
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
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
menuentry 'Ubuntu, with Linux 2.6.38-9-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	linux	/boot/vmlinuz-2.6.38-9-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-9-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	echo	'Loading Linux 2.6.38-9-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-9-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-9-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	echo	'Loading Linux 2.6.35-27-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	echo	'Loading Linux 2.6.35-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	echo	'Loading Linux 2.6.35-23-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 4a60ff9d-f704-4d04-a829-4c4702f5c203
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=45a2e92c-c759-4732-9662-988da7f8ea7b /home           ext3    defaults        0       2
# /media/g was on /dev/sda5 during installation
UUID=7b859c36-c68d-408f-9425-de9f525f3c71 /media/g        reiserfs defaults        0       2
# /media/mydocs was on /dev/sdc1 during installation
UUID=724E07853D78E7A8 /media/mydocs   ntfs    defaults,umask=0022,gid=46           0       2
# /media/video was on /dev/sda6 during installation
UUID=86290d05-e673-4310-9f3e-93af30cc13af /media/video    reiserfs defaults        0       2
# swap was on /dev/sda4 during installation
UUID=e36cb6cf-f372-4418-bd8b-f36a27dc3e76 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  24.7GB: boot/grub/core.img
  24.8GB: boot/grub/grub.cfg
  24.7GB: boot/initrd.img-2.6.35-23-generic-pae
  24.8GB: boot/initrd.img-2.6.35-24-generic-pae
  24.7GB: boot/initrd.img-2.6.35-25-generic-pae
  24.7GB: boot/initrd.img-2.6.35-27-generic-pae
  24.7GB: boot/initrd.img-2.6.35-28-generic-pae
  24.8GB: boot/initrd.img-2.6.38-8-generic-pae
  24.8GB: boot/initrd.img-2.6.38-9-generic-pae
  24.7GB: boot/vmlinuz-2.6.35-23-generic-pae
  24.7GB: boot/vmlinuz-2.6.35-24-generic-pae
  24.7GB: boot/vmlinuz-2.6.35-25-generic-pae
  24.7GB: boot/vmlinuz-2.6.35-27-generic-pae
  24.7GB: boot/vmlinuz-2.6.35-28-generic-pae
  24.8GB: boot/vmlinuz-2.6.38-8-generic-pae
  24.7GB: boot/vmlinuz-2.6.38-9-generic-pae
  24.8GB: initrd.img
  24.8GB: initrd.img.old
  24.7GB: vmlinuz
  24.8GB: vmlinuz.old
```

---

### Post by oldfred on 2011-05-10
Do you have an extra digit in your fstab entry?

# /media/mydocs was on /dev/sdc1 during installation
UUID=724E07853D78E7A8 /media/mydocs   ntfs    defaults,umask=[COLOR=Red]0022[/COLOR],gid=46           0       2

I do not have umask nor gid entries, just default. 

But I have seen those recommended but usually with umask=007.

umask=007 will give the owner and group read/write access to the mountpoint
gid=46 is group=plugdev. All members of plugdev will have read/write access and all local login users are members of plugdev by default.

---

