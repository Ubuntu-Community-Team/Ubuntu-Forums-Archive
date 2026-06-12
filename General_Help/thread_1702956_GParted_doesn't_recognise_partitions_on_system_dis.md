---
title: "GParted doesn't recognise partitions on system disk"
date: 2011-03-08
forum: General Help
---

### Post by ottadini on 2011-03-08
Hi, I seem to have a wee problem with the partitions / partition table on my system disk. It's a dual-boot Ubuntu+WinXP system, WinXP installed first to sda1:

```
ben@claude:~$ sudo fdisk -l

omitting empty partition (5)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x744da541

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       38913   251128080    f  W95 Ext'd (LBA)
/dev/sda3           26112       38913   102832033+   7  HPFS/NTFS
/dev/sda5            7650        8865     9767457   83  Linux
/dev/sda6            8866       25625   134624668+  83  Linux
/dev/sda7           25626       26111     3903763+  82  Linux swap / Solaris
```Attachment is a screenshot of the gnome disk utility. 
GParted sees nothing, all one unallocated space

I want to fix it, but don't want to risk losing all the data on it. How can I clone it? How will I be able to boot from the clone?
Ben.

---

### Post by coffeecat on 2011-03-08
> **ottadini said:**
> GParted sees nothing, all one unallocated space

That's a common indicator of an illegal entry in the partition table. And indeed...

> **ottadini said:**
> ```
ben@claude:~$ sudo fdisk -l

omitting empty partition (5)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x744da541

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            [COLOR=Red]7650       38913[/COLOR]   251128080    f  W95 Ext'd (LBA)
/dev/sda3          [COLOR=Red] 26112       38913[/COLOR]   102832033+   7  HPFS/NTFS
/dev/sda5            7650        8865     9767457   83  Linux
/dev/sda6            8866       25625   134624668+  83  Linux
/dev/sda7           25626       26111     3903763+  82  Linux swap / Solaris
```

You have a primary partition (sda3) sitting inside an extended partition (sda2) which is an impossibility.

I'll make an educated guess. It was the XP installer that did this. There have been threads about this before.

One way to fix this would be to edit the partition table so that sda3 becomes sda8, i.e. a logical partition. That will heal the partition table, but Windows will then only boot if the Windows boot files are in sda1, which they probably are.

I'll rustle up some help with this, because more than one helping in this situation is useful. In the meantime, please post the fdisk output with modified options. We'll need this to repair the partition table. Specifically, post the output of:

```
sudo fdisk -lu
```Also, please go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot script and post the contents of your RESULTS.txt. This will give us a little more information about your Windows partition.

---

### Post by ottadini on 2011-03-08
Hi coffeecat, thanks for helping out!

I have two other HDDs in my system at the moment, so the results.txt also includes them.

```
ben@claude:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x744da541

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   122881184    61440561    7  HPFS/NTFS
/dev/sda2       122881185   625137344   251128080    f  W95 Ext'd (LBA)
/dev/sda3       419473278   625137344   102832033+   7  HPFS/NTFS
/dev/sda5       122881311   142416224     9767457   83  Linux
/dev/sda6       142416288   411665624   134624668+  83  Linux
/dev/sda7       411665688   419473214     3903763+  82  Linux swap / Solaris

``````
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda3 starts at sector 419473278.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   122,881,184   122,881,122   7 HPFS/NTFS
/dev/sda2         122,881,185   625,137,344   502,256,160   f W95 Ext d (LBA)
Extended  partition  linking to another extended partition
/dev/sda5         122,881,311   142,416,224    19,534,914  83 Linux
/dev/sda6         142,416,288   411,665,624   269,249,337  83 Linux
/dev/sda7         411,665,688   419,473,214     7,807,527  82 Linux swap / Solaris
/dev/sda3         419,473,278   625,137,344   205,664,067   7 HPFS/NTFS

/dev/sda2 overlaps with /dev/sda3

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 3,907,024,064 3,907,024,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   625,137,344   625,137,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        060C6D800C6D6C1D                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        146FA9B0B6A44D89                       ntfs       Data                          
/dev/sda5        db07372c-202b-4d32-abaf-3e1afc604b32   ext4                                     
/dev/sda6        6b9c028a-c58e-4b22-a157-bedd7247dcb7   ext4       homes                         
/dev/sda7        fb90e6d1-740b-4470-957b-fdf2266106ce   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        003ABB1739377B81                       ntfs       dingo                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        0A20939C20938CF7                       ntfs       BACKUP                        
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext4       (rw)
/dev/sda3        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1        /media/BACKUP            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/dingo             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set db07372c-202b-4d32-abaf-3e1afc604b32
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set db07372c-202b-4d32-abaf-3e1afc604b32
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set db07372c-202b-4d32-abaf-3e1afc604b32
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=db07372c-202b-4d32-abaf-3e1afc604b32 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set db07372c-202b-4d32-abaf-3e1afc604b32
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=db07372c-202b-4d32-abaf-3e1afc604b32 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set db07372c-202b-4d32-abaf-3e1afc604b32
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=db07372c-202b-4d32-abaf-3e1afc604b32 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set db07372c-202b-4d32-abaf-3e1afc604b32
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=db07372c-202b-4d32-abaf-3e1afc604b32 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set db07372c-202b-4d32-abaf-3e1afc604b32
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=db07372c-202b-4d32-abaf-3e1afc604b32 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set db07372c-202b-4d32-abaf-3e1afc604b32
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=db07372c-202b-4d32-abaf-3e1afc604b32 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set db07372c-202b-4d32-abaf-3e1afc604b32
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set db07372c-202b-4d32-abaf-3e1afc604b32
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 060c6d800c6d6c1d
    drivemap -s (hd0) ${root}
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
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    defaults    0    0
#Entry for /dev/sda5 :
UUID=db07372c-202b-4d32-abaf-3e1afc604b32    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda6 :
UUID=6b9c028a-c58e-4b22-a157-bedd7247dcb7    /home    ext4    defaults    0    2
#Entry for /dev/sdc1 :
UUID=0A20939C20938CF7    /media/BACKUP    ntfs-3g    defaults,locale=en_AU.utf8    0    0
#Entry for /dev/sda3 :
UUID=146FA9B0B6A44D89    /media/Data    ntfs-3g    defaults,locale=en_AU.utf8    0    0
#Entry for /dev/sdb1 :
UUID=003ABB1739377B81    /media/dingo    ntfs-3g    defaults,locale=en_AU.utf8    0    0
#Entry for /dev/sda7 :
UUID=fb90e6d1-740b-4470-957b-fdf2266106ce    none    swap    sw    0    0
/dev/scd0    /media/cdrom0    udf,iso9660    user,noauto,exec,utf8    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0
UUID="146FA9B0B6A44D89"    /media/Data    ntfs-3g    defaults,locale=en_AU.utf8    0    0
UUID="0A20939C20938CF7"    /media/BACKUP    ntfs-3g    defaults,locale=en_AU.utf8    0    0



=================== sda5: Location of files loaded by Grub: ===================


  63.3GB: boot/grub/core.img
  66.2GB: boot/grub/grub.cfg
  70.0GB: boot/initrd.img-2.6.32-27-generic
  70.4GB: boot/initrd.img-2.6.32-28-generic
  71.4GB: boot/initrd.img-2.6.32-29-generic
  69.4GB: boot/vmlinuz-2.6.32-27-generic
  70.1GB: boot/vmlinuz-2.6.32-28-generic
  70.3GB: boot/vmlinuz-2.6.32-29-generic
  71.4GB: initrd.img
  70.4GB: initrd.img.old
  70.3GB: vmlinuz
  70.1GB: vmlinuz.old
```

---

### Post by coffeecat on 2011-03-08
Hi

Yes, that all confirms it nicely. Indeed, if you look through your boot script output, you'll see that every mention of sda3 is where sda8 would be and, indeed, I believe that is the fix: editing the partition table so that sda3 becomes sda8.

Just a word of explanation in case this is not clear to you. A logical partition is numbered 5 and upwards. A primary partition (or extended) between 1 and 4. An extended partition is a container for logical partitions. If you look at your outputs, you'll see that what is mislabelled as sda3 (by definition a primary partition) is sitting inside sda2, which is an extended. Impossible.

The good news is that your Windows boot files are in the primary partition sda1 and the rest of Windows seems to be in sda3/sda8. That means that Windows should still be bootable after you convert sda3 > sda8 and make it a legal logical partition.

I will have to log off soon, so I may not be able to see you through this today, but here's a useful link which tells you how to edit a partition table:

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

It's for a different situation - an extended partition extending beyond the end of the physical disk - but it tells you how to edit a partition table.

You should backup any data first. You will be editing the partition table. There is a potential for disaster. Ideally, it would be good to clone the whole drive with dd, but that will take hours.

For starters, please run this command:

```
sudo sfdisk -d /dev/sda > parts.txt
```And post the contents of parts.txt. Be careful to get the '>' the right way round. :-s

Could you please also post some notes on how you got to this state. Did you create the partitions in Ubuntu? Did you install Ubuntu or Windows first? Why did you choose to split Windows over two partitions? Did you have to delete/create any partitions in the XP installer? I'm doing some research on how and when the Windows installer does this. I've only managed yet to reproduce one scenario, but this is different from yours.

---

### Post by ottadini on 2011-03-08
Here is the output from sfdisk:

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=122881122, Id= 7, bootable
/dev/sda2 : start=122881185, size=502256160, Id= f
/dev/sda3 : start=419473278, size=205664067, Id= 7
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=122881311, size= 19534914, Id=83
/dev/sda6 : start=142416288, size=269249337, Id=83
/dev/sda7 : start=411665688, size=  7807527, Id=82
```If I clone the entire HDD with dd, how will it handle the bogus partitions? 

Thanks for explanations, I understand the problem now, but as to how it came about, I'm at a loss.

The disk was originally setup via Windows XP install CD partition manager. I decided on the partitioning based on one of the psychocat suggestions, and altered it slightly to fit my purpose. I wanted one partition to be available to both OSes, so created the ~100 GB partition in NTFS for that reason.

I installed Windows first, so I'm pretty sure, but not absolutely certain, that I created the primary partition using the windows tool, but the rest I did with the live Ubuntu CD (karmic).

It was a while ago, I've been living with this for some time, figuring that as long as it was working I didn't want to stuff around with it. 

ben.

---

### Post by coffeecat on 2011-03-08
> **ottadini said:**
> If I clone the entire HDD with dd, how will it handle the bogus partitions? 

Sorry. I didn't explain myself very well. I meant that if you dd a complete clone and everything went pear-shaped, you'd have a complete backup.

> **ottadini said:**
> so created the ~100 GB partition in NTFS for that reason.

The 100gb NTFS partition is sda3 which should be sda8. Because of this:

```
sda3: ________________________________________________________________________   

     File system:       ntfs
     Boot sector type:  Windows XP
     Boot sector info:  [COLOR=Red]According to the info in the boot sector, sda3 starts
                        at sector 63. But according to the info from fdisk,
                        sda3 starts at sector 419473278.
 [/COLOR]    Operating System:
     Boot files/dirs:    

```I suspect that some of the Windows system is on that partition rather than it being just a data partition. Perhaps you could check.

The other little oddity I noticed is that although your /etc/fstab identifies your sda5 root partition and sda6 home partition correctly, your grub.cfg seems to think root is sda6. That doesn't matter because the UUID for sda5 is correct in grub.cfg and that is what matters.

Anyway, I believe this is the edited parts.txt you need:

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=122881122, Id= 7, bootable
/dev/sda2 : start=122881185, size=502256160, Id= f
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=122881311, size= 19534914, Id=83
/dev/sda6 : start=142416288, size=269249337, Id=83
/dev/sda7 : start=411665688, size=  7807527, Id=82
/dev/sda8 : start=419473278, size=205664067, Id= 7
```

You can use the command in that link to write the edited parts.txt with the --force option. But since...

> **ottadini said:**
> It was a while ago, I've been living with this for some time, figuring that as long as it was working I didn't want to stuff around with it. 

... there's no particular hurry, may I suggest you delay using that? It's late here and I may have made an error from tiredness, and I have to log off now anyway. Before I do, I will pm someone else to look at this - a real expert.

---

### Post by srs5694 on 2011-03-08
Coffeecat's fixed sfdisk output looks correct to me, but I can't promise I haven't overlooked something.

Another option is to try a new program I'm writing to help fix this sort of problem; however, at the moment it's very experimental. I'll send you details via a PM.

---

### Post by ottadini on 2011-03-09
Hi again,
I have access to a 320 GB drive so as to clone my system drive (also 320GB). I have some questions... feel free to tell me to go elsewhere for answers. 

I figure dd is the way to go as suggested. The dd command I plan to use is: 
```
# dd if=/dev/sda of=/dev/sdc conv=noerror,sync bs=1024
```
[LIST=1]
[*] 'noerror' just because the source disk might have some errors. How can I check for errors before running dd?
[*]The cluster size of the drives is 512, will bs=1024 be an issue?  Apparently this setting will speed things up. (How long will 320GB take  anyway?)
[*]Does the second drive need to be wiped?
[*] Because I am wanting to clone my system drive, I guess I'll need to invoke dd from a live cd. Any recommendations?
[*]How does dd affect the source? Will i be insane using it without a full backup? (To backup the drive, would I be insane to use dd?).
[/LIST]

---

### Post by coffeecat on 2011-03-09
Your dd command looks OK, but tbh, I don't use dd much. I mentioned cloning with dd because this is a counsel of perfection. When I was in a similar situation to you with a much more comprehensively corrupted partition table I didn't bother to clone the drive because I had effective backups of all my data and I reckoned it would be quicker for me to re-install the various OSs I had on the several partitions than wait for a dd to complete. To your question, how long will 320GB take, the answer is several hours. And as far as the conv=noerror,sync option is concerned, I can't see that doing any harm, but as far as I understand that would only be of use if you suspected source hard drive errors or incipient failure and I don't think you have any evidence of that. Perhaps someone else might be able to comment better.

But some people do prefer to clone the drive in a situation like this, and it was only fair on you to mention that.

I was unguarded in my choice of words last night. Using the phrase going "pear-shaped" implied things worse than I had intended. All things being equal, the worst you could do is to corrupt the partition table more than it is already. But, strange to say, that doesn't really matter. You have a copy of the sfdisk output of the partition table as it is now. If need be, you can simply write that back to restore the partition table to where it is now using sfdisk.

Since srs5694 concurs with my suggestion for the edit to the partition table, just for completeness here is what you do. You must do this from a live CD. Save the partition table I posted as a text file called parts_edited.txt - or whatever you want. Then from a live CD terminal:

```
sfdisk --force /dev/sda < parts_edited.txt
```... adjusting the path to parts_edited.txt as appropriate, of course.

**EDIT**: or, of course, use the terminal app that srs5694 was going to pm you with.

---

### Post by Quackers on 2011-03-09
Like coffeecat, I have never used dd to copy a whole disc. I have only used it for mbr backup/messing about :-)
I have seen this command used for your purposes
```
dd if=/dev/sda of=/dev/sdc conv=notrunc,noerror
```
notrunc means no truncation, and noerror prevents dd from stopping if it finds an error.

---

### Post by ottadini on 2011-03-10
Thanks all for the tips on dd. I've now run dd from a systemrescuecd:
```
root@sysresccd /root % dd if=/dev/sda of=/dev/sdc conv=notrunc,noerror
625140335+0 records in
625140335+0 records out
320071851520 bytes (320 GB) copied, 21411.3 s, 14.9 MB/s

```That's nearly six hours. Apparently IDE drives on the same bus (i.e. primary master and primary slave) are slow to clone, so if I had instead put my second drive onto the secondary bus it might have been quicker. 

```
root@sysresccd /root % fdisk -l
omitting empty partition (5)

Disk /dev/sda: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x744da541

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   122881184    61440561    7  HPFS/NTFS
/dev/sda2       122881185   625137344   251128080    f  W95 Ext'd (LBA)
/dev/sda3       419473278   625137344   102832033+   7  HPFS/NTFS
/dev/sda5       122881311   142416224     9767457   83  Linux
/dev/sda6       142416288   411665624   134624668+  83  Linux
/dev/sda7       411665688   419473214     3903763+  82  Linux swap / Solaris


Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x744da541

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   122881184    61440561    7  HPFS/NTFS
/dev/sdc2       122881185   625137344   251128080    f  W95 Ext'd (LBA)
/dev/sdc3       419473278   625137344   102832033+   7  HPFS/NTFS
/dev/sdc5       122881311   142416224     9767457   83  Linux
/dev/sdc6       142416288   411665624   134624668+  83  Linux
/dev/sdc7       411665688   419473214     3903763+  82  Linux swap / Solaris

```Everything is nearly identical, even the disk identifiers are the same. I think I'll now power down, remove sda and try to boot with sdc before altering the partitions. 

Ben.

---

### Post by ottadini on 2011-03-10
Sorry for using this thread as a diary!
I checked the cloned drive by installing it as boot drive, and it was fine. I saw all my partitions and files. So, I restarted the box with sysrescuecd, and used sfdisk to re-write the partition table. That completed successfully, but I couldn't then boot from the drive, instead I got some grub error, and landed in a 'grub rescue >' prompt.

Not having any idea how to proceed, I am planning on returning the partition table to its original state with sfdisk again, and perhaps trying the fixparts binary from srs5694.

edit: i also should mention that the sfdisk command gave this warning:
```

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```
I have no idea what that means, but I suspect I should act on it?

---

### Post by srs5694 on 2011-03-10
> **ottadini said:**
> Sorry for using this thread as a diary!
I checked the cloned drive by installing it as boot drive, and it was fine. I saw all my partitions and files. So, I restarted the box with sysrescuecd, and used sfdisk to re-write the partition table. That completed successfully, but I couldn't then boot from the drive, instead I got some grub error, and landed in a 'grub rescue >' prompt.

Try using [Super GRUB 2 Disk.](http://www.supergrubdisk.org/) It's conceivable it will be able to locate your GRUB files and boot the computer. If so, you should be able to then type "sudo grub-install" at a shell prompt to get the system booting from the hard disk again.

> Not having any idea how to proceed, I am planning on returning the partition table to its original state with sfdisk again, and perhaps trying the fixparts binary from srs5694.

It's a bit puzzling to me that you've got the GRUB error in the first place, since oldfred's modified sfdisk file doesn't change the identifier for the partition where GRUB resides (/dev/sda6). I'm doubtful that my fixparts program would do any better in this case, although I suppose it might if there's some error or quirk in oldfred's file that neither of us has noticed.

> edit: i also should mention that the sfdisk command gave this warning:
```

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```I have no idea what that means, but I suspect I should act on it?

Don't worry about it. It relates to very old versions of DOS, which had bugs in their FORMAT program. These bugs would cause FORMAT to use old data inside the partition to determine the size of the filesystem they created rather than the size specified in the partition table. The command specified would erase this old data, forcing FORMAT to use the actual partition size. Since this bug is in very old DOS software, you needn't be concerned with it. Besides which, what you did didn't create any new DOS partitions or change existing ones.

---

### Post by ottadini on 2011-03-13
Just a reply to summarise everything wot I did:

[LIST=1]
[*]used dd to clone system drive
[*]saved existing partition table using sfdisk
[*]booted into system using a live CD
[*]edited partition table output and saved back to cloned drive using sfdisk
[*]installed clone as boot drive
[*]rebooted using clone
[*]boot failed on clone (apparently due to moving partitions around)
[*]booted with super grub2 rescue disk
[*]re-installed grub
[*]re-booted, clone now being used as system drive.
[/LIST]
Thanks for the help everyone!

---

### Post by Quackers on 2011-03-13
We like happy endings :-)
Well done!

---

### Post by coffeecat on 2011-03-13
Good result. :)

I presume Windows is booting OK?

---

