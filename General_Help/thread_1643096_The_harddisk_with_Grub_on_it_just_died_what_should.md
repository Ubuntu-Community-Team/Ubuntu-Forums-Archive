---
title: "The harddisk with Grub on it just died: what should I do?"
date: 2010-12-11
forum: General Help
---

### Post by stefangr1 on 2010-12-11
The oldest disk in my system just died (sort of). Luckily I have a backup of the 1TB of data that is/was on it, unfortunately it's the only disk with a bootloader (Grub), so now I have trouble booting. This time it succeeded without error the 6th time I tried, but I'm afraid this ain't going to work another time.

How can I install Grub on the other disks?

I tried (got there trough a tutorial):

```
stefan@linux:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> find /boot/grub/stage2
find /boot/grub/stage2
```

So that doesn't work.

EDIT: I was attempting this with grub1, while I think I should in fact have used grub2.

Now I runned:
```
stefan@linux:/boot/grub$ sudo grub-install --recheck /dev/sdb
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
stefan@linux:/boot/grub$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

Does this mean that grub (which was previously installed on the now broken /dev/sda) has been successfully installed on /dev/sdb such that I'll be able to boot...?

---

### Post by sikander3786 on 2010-12-11
You need to point Grub to the install partition as well. Here is how to do that.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

If you are not sure, we can give the exact commands for that. For that, you need to post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

---

### Post by stefangr1 on 2010-12-11
OK, here we go:```
stefan@linux:~/Desktop$ cat RESULTS.txt
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=081ca744-2037-4a56-90a9-d0de13547156)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for 
    (UUID=081ca744-2037-4a56-90a9-d0de13547156)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks at sector 13939138 of 
    the same hard drive for core.img, core.img is at this location on /dev/sdc 
    and looks on partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d40d7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,953,520,064 1,953,520,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000db4f3

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 3,907,024,064 3,907,024,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdc1              34    97,656,284    97,656,251 System/Boot Partition
/dev/sdc2      97,656,285 3,907,029,134 3,809,372,850 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0de0af9a-2e53-4af9-bdfd-0965b591a122   ext3       med1                          
/dev/sdb1        7cac2526-8f21-40d8-83d2-e1151054915f   ext3       med2                          
/dev/sdc1        081ca744-2037-4a56-90a9-d0de13547156   ext4                                     
/dev/sdc2        d8caedcf-e0ac-47d2-9fdd-deb2881c8148   ext3       med3                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc2        /media/med3              ext3       (rw)
/dev/sdb1        /media/med2              ext3       (rw)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd2,1)
search --no-floppy --fs-uuid --set 081ca744-2037-4a56-90a9-d0de13547156
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
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 081ca744-2037-4a56-90a9-d0de13547156
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=081ca744-2037-4a56-90a9-d0de13547156 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 081ca744-2037-4a56-90a9-d0de13547156
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=081ca744-2037-4a56-90a9-d0de13547156 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
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
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=081ca744-2037-4a56-90a9-d0de13547156 /               ext4    errors=remount-ro 0       0
# /media/med1 was on /dev/sda1 during installation
UUID=0de0af9a-2e53-4af9-bdfd-0965b591a122 /media/med1     ext3    defaults        0       0
# /media/med4 was on /dev/sdc2 during installation
UUID=d8caedcf-e0ac-47d2-9fdd-deb2881c8148 /media/med3     ext3    defaults        0       0
# /media/med3 was on /dev/sdb1 during installation
#UUID=ffbfb429-86b5-4afd-85e4-888d8c6dcea3 /media/med3     ext3    defaults        0       0
# /media/med2 was on /dev/sdb2 during installation
#UUID=82738892-d2a2-450f-9877-6c52b0f18d35 /media/med2     ext3    defaults        0       0
UUID=7cac2526-8f21-40d8-83d2-e1151054915f /media/med2     ext3    defaults        0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


   7.1GB: boot/grub/core.img
   7.1GB: boot/grub/grub.cfg
   8.4GB: boot/initrd.img-2.6.31-14-generic
   2.4GB: boot/vmlinuz-2.6.31-14-generic
   8.4GB: initrd.img
   2.4GB: vmlinuz
```

---

### Post by sikander3786 on 2010-12-11
Multiple problems in that boot script output. Solution: Chroot your Ubuntu install from a 9.10 or higher Live CD. Purge and then re-install Grub as mentioned here.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by efflandt on 2010-12-11
It looks like grub2 is installed on the mbr of all 3 of your hard drives, so if the mbr of sda is broken, it looks like it should work if you set you BIOS to boot sdc (or sdb), since both point to the rest of grub on sdc1 (by UUID).

---

### Post by stefangr1 on 2010-12-11
> **efflandt said:**
> It looks like grub2 is installed on the mbr of all 3 of your hard drives, so if the mbr of sda is broken, it looks like it should work if you set you BIOS to boot sdc (or sdb), since both point to the rest of grub on sdc1 (by UUID).

It's working, it seems that```

sudo grub-install --recheck /dev/sdb
sudo update-grub
```
dit the trick.

The harddisk is now working again, but there is a gradually increasing number of S.M.A.R.T. errors:
```
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   077   077   011    Pre-fail  Always       -       7780
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       687
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       11585
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       5451
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       687
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       0
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
184 Unknown_Attribute       0x0033   025   025   000    Pre-fail  Always       -       75
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   066   060   000    Old_age   Always       -       34 (Lifetime Min/Max 32/34)
194 Temperature_Celsius     0x0022   064   059   000    Old_age   Always       -       36 (Lifetime Min/Max 32/37)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       3937973
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       912
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       1
201 Soft_Read_Error_Rate    0x000a   100   100   000    Old_age   Always       -       0

```

---

### Post by stefangr1 on 2010-12-11
> **sikander3786 said:**
> Multiple problems in that boot script output. Solution: Chroot your Ubuntu install from a 9.10 or higher Live CD. Purge and then re-install Grub as mentioned here.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

If I may ask: what did you think that was wrong in the output of the boot script you suggested to run? I don't see anything that seems wrong...

I think chrooting using the Ubuntu cd is for the case where it won't boot anymore. If I look at the tutorials, the procedure for installing is much more simple when you can stil get in.

Anyway: Grub's fixed, so thanks alot for your time!

---

### Post by Roasted on 2010-12-11
> **sikander3786 said:**
> You need to point Grub to the install partition as well. Here is how to do that.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

If you are not sure, we can give the exact commands for that. For that, you need to post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

I don't mean to jack the thread but I think this may be relevant in case the poster runs into this. I recently installed XP AFTER Ubuntu and had to restore grub. I used the instructions above. It restored grub, but it did not restore my ability to boot to Windows. It was Ubuntu only. In the directions, it says "sudo update-grub". I had to run (thanks to the help of these forums) "sudo update-grub2" to bring back Windows on the boot list.

Is there a reason why the official documentation doesn't say that? Or did I goof up originally somehow?

---

### Post by oldfred on 2010-12-11
A suggestion:

With gpt you should also create a small bios_grub partition for grub to install into. With gpt it can be any where on the drive.

[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)
In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.

This link says they just installed grub2 to the drive and it found the BIOS boot partition.
[http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html](http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html)
Legacy BIOS issues with gpt
[http://www.rodsbooks.com/gdisk/bios.html](http://www.rodsbooks.com/gdisk/bios.html)

---

