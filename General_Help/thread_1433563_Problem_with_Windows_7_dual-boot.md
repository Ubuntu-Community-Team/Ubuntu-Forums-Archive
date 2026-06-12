---
title: "Problem with Windows 7 dual-boot"
date: 2010-03-19
forum: General Help
---

### Post by agentalexandre on 2010-03-19
Hey all,
A few months ago I installed Karmic as a dual boot with Windows 7 on the same hard disk. The install worked fine and I've been happily using only Ubuntu since. Recently, I needed to boot into Windows 7, with no luck. I get a BSOD, with error codes 0x000007B(0x80786B58, rest are generic). I know this is not a Windows support forum, but I really have no where else to go. I booted the Windows 7 install disk and attempted repair - the installer was unable to repair. I tried chkdsk, it give some error about how it can't access the disk.
I suspect that the problem has arisen from the fact that I am constantly accessing my Windows 7 partition from within Ubuntu.
Any help would be greatly appreciated.
Please ask for any information if I missed anything.
Thanks in advance.

---

### Post by agentalexandre on 2010-03-20
bump

---

### Post by derekeverett on 2010-03-20
That's frustrating for sure. I wish I had better advice but I don't.

Did you try to google the error codes and see if you find anything helpful? Short of re-installing everything from scratch....

---

### Post by agentalexandre on 2010-03-20
Thanks for the reply.
Yeah, I googled for hours trying to find a solution. I did find an instance on this forum where someone else had exactly the same problem, but no one ever replied to this post.
I attempted to reinstall 7 over the broken parition yesterday, but the installer doesn't even see the harddrive. Now I fear if I do a total wipe of the disk, the installer still won't see the disk.
I also booted up an old installation disk of XP but it simply Blue Screens with the same error code as 7. It makes me think that something on the harddrive is corrupt that is preventing Windows from loading, but I have no idea what.

---

### Post by derekeverett on 2010-03-20
You can always make a live CD of G-Parted and boot from that. You could re-partition and format your drives with it too.

I don't know sorry if that's not much help. But I guess that's what I would do in your situation.

---

### Post by oldfred on 2010-03-20
I cannot help with specific problem. I think you have gone thru the suggestions of chkdsk and repair that my limited knowledge of windows  would recommend.

But I think this is one reason I suggest a separate shared data partition so you are not writing directly into the windows operating system partition. I have seen windows only users recommend a data partition for the same reason. When you get it going again I would suggest adding a data partition.

This probes the entire system and may tell something:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by sandyd on 2010-03-20
These error codes (after looking in my huge stack of MSCIT books....)
mean...

let me take the portions apart for you...
0x7b - inacceable boot device
0x80786B58 - typically means the same thing as 0x7b, it just provides details on the type of boot problem. (im not going into detail cause theirs no point)

This generally indicates that windows cannot find the partition that it is supposed to boot from.

Seeing that the windows 7 installer cannot see the partitions, I would say that there is a problem with the partition tables.

however, since you can still boot into ubuntu, can you run
```

sudo fdisk -l
```and the boot info script described above

---

### Post by agentalexandre on 2010-03-21
> **carlee said:**
> 
however, since you can still boot into ubuntu, can you run
```

sudo fdisk -l
```and the boot info script described above
sudo fdisk -l gives me:
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc5d33725

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1698    13639153+  27  Unknown
/dev/sda2            1699       20305   149460727+   5  Extended
/dev/sda3           20306       38452   145752064   42  SFS
/dev/sda4           38452       38914     3710296   42  SFS
/dev/sda5   *        1699       20305   149460696   83  Linux
[CODE]
```[/CODE]
sda1 and sda4 are both OEM/factory restore partitions. sda3 is the Windows 7 partition that BSOD's.

I will try the boot script when I get home later today.
Thanks.

---

### Post by lightspd on 2010-03-21
This may or may not be helpful to you.  I haven't done duel boot with Windows and Linux in a long time, but I do remember there used to be an issue with windows on duel boot systems, if Windows wasn't the first partition on the drive.  Like I said, don't know if it will help you or even still applies, just something that came to mind.

---

### Post by agentalexandre on 2010-03-21
Here are the results of that boot script:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda4 has 
                       7419903 sectors, but according to the info from fdisk, 
                       it has 7420591 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc5d33725

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    27,278,369    27,278,307  27 Hidden HPFS/NTFS
/dev/sda2          27,278,370   326,199,824   298,921,455   5 Extended
/dev/sda5    *     27,278,433   326,199,824   298,921,392  83 Linux
/dev/sda3         326,215,680   617,719,807   291,504,128  42 SFS
/dev/sda4         617,719,808   625,140,399     7,420,592  42 SFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D284D60484D5EACD                       ntfs       PQSERVICE                     
/dev/sda3        78C45055C45017A8                       ntfs       Windows 7                     
/dev/sda4        AA9A9DBD9A9D868B                       ntfs                                     
/dev/sda5        c032568f-f676-4a2f-90d7-b3162ffc0f1c   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /media/Windows 7         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set c032568f-f676-4a2f-90d7-b3162ffc0f1c
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set c032568f-f676-4a2f-90d7-b3162ffc0f1c
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=c032568f-f676-4a2f-90d7-b3162ffc0f1c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set c032568f-f676-4a2f-90d7-b3162ffc0f1c
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=c032568f-f676-4a2f-90d7-b3162ffc0f1c ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set c032568f-f676-4a2f-90d7-b3162ffc0f1c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c032568f-f676-4a2f-90d7-b3162ffc0f1c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set c032568f-f676-4a2f-90d7-b3162ffc0f1c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c032568f-f676-4a2f-90d7-b3162ffc0f1c ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d284d60484d5eacd
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 78c45055c45017a8
	chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda4)" {
	insmod ntfs
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set aa9a9dbd9a9d868b
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
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=c032568f-f676-4a2f-90d7-b3162ffc0f1c / ext4 errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda3 /media/Windows\0407 ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda5: Location of files loaded by Grub: ===================


  15.9GB: boot/grub/core.img
  41.5GB: boot/grub/grub.cfg
  14.5GB: boot/initrd.img-2.6.31-14-generic
  16.0GB: boot/initrd.img-2.6.31-19-generic
  14.4GB: boot/vmlinuz-2.6.31-14-generic
  14.7GB: boot/vmlinuz-2.6.31-19-generic
  16.0GB: initrd.img
  14.5GB: initrd.img.old
  14.7GB: vmlinuz
  14.4GB: vmlinuz.old

================================ sda4/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /maxmem=768

```

---

### Post by oldfred on 2010-03-21
the windows boot loader jumps to the partition with a boot flag and that is just about all it does. You have the boot flag on the linux partition and linux does not use a boot flag. 

Try moving the boot flag to your sda3 partition. You can use gparted, disk utility or command line in Ubuntu.

set boot flag on for sda3 (off on others)
sudo sfdisk -A3 /dev/sda

---

### Post by agentalexandre on 2010-03-21
> **oldfred said:**
> the windows boot loader jumps to the partition with a boot flag and that is just about all it does. You have the boot flag on the linux partition and linux does not use a boot flag. 

Try moving the boot flag to your sda3 partition. You can use gparted, disk utility or command line in Ubuntu.

set boot flag on for sda3 (off on others)
sudo sfdisk -A3 /dev/sda
I have grub2 set up with Windows 7 in the list, so I am still able to access Windows 7, it BSODs while loading the system, so I don't really think this would change anything, but correct me if I'm wrong.
The install disc no longer sees the harddisk to repair, but at one point it did. I repaired it and windows took over as the boot loader, I was unable to access Ubuntu and it would go straight into Windows 7 (then BSOD). It took me almost 4 hours to finally get grub working again. Would this command do the same thing?

---

### Post by agentalexandre on 2010-03-21
bump

---

### Post by agentalexandre on 2010-03-21
> **oldfred said:**
> the windows boot loader jumps to the partition with a boot flag and that is just about all it does. You have the boot flag on the linux partition and linux does not use a boot flag. 

Try moving the boot flag to your sda3 partition. You can use gparted, disk utility or command line in Ubuntu.

set boot flag on for sda3 (off on others)
sudo sfdisk -A3 /dev/sda
Forget about what I said before, I tried it, didn't affect Grub, but I still got a BSOD, however I have noticed something very strange:

In Gparted I have two partitions (that are of concern right now), one which is a factory restore partition which contains vista (doesn't boot, complains about missing BCD). The other is my Windows 7 drive.

```
Vista: /dev/sda1 - UUID: D284D60484D5EACD
7    : /dev/sda3 - UUID: 78C45055C45017A8
```

However Grub is telling a completely different story:

```

menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d284d60484d5eacd
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 78c45055c45017a8
	chainloader +1
}

```
The Windows 7 loader does not link to the right disk(should be /dev/sda3), but it still loads Windows 7. The Vista loader also does not link to the right disk (should be /dev/sda3), but it still loads Vista.
I consider myself to be a pretty competent person when it comes to computers, but I am up to my neck in stuff I don't usually do. I have installed operating systems over and over again, fixed MBRs, installed OSx86, the works, however this has left me completley stumped, what the hell is wrong?

---

### Post by oldfred on 2010-03-21
I think Vista and 7 are close enough that some of the linux software cannot tell the difference. The boot_info script seemed to get it correct and it is just running a lot of linux commands and parsing the data.

The repair disk was also looking for the boot (active) partition and that was why it could not repair the linux partition with the flag.. With grub I am not sure the boot flag is required or not. With old grub that was the makeactive flag in the boot stanza for when you had two windows partitions and wanted to boot the other one that did not have the flag. Grub2 does not have a makeactive command, so I assume it does not need it.

---

### Post by sandyd on 2010-03-22
hey guys,  I think you missed something. although the boot info script correctly identifies the windows partition (/dev/sda1) as ntfs, fdisk lists it as unknown. which indicates a problem w/ the partition..

---

### Post by Laysan_A on 2010-03-22
Hey,

I can't offer any real help. I'm struggling with my own windows boot problem after a resize of the windows partition (xp though).

You might want to look at the gparted site. There is some info there on dual boot problems, though nothing I saw on windows 7.
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

Good luck!

---

### Post by agentalexandre on 2010-03-22
Here is a screenshot from Gparted if it helps:
[IMG]http://img693.imageshack.us/img693/2312/screenshotdevsdagparted.png[/IMG]

---

### Post by Mark Phelps on 2010-03-22
If you CAN boot into Win7 but get a BSOD in the process, suggest going to sevenforums.com (Win7 forums) and checking their Crashes and Debugging forum for help on your BSOD.

If you CAN'T boot into Win7, have you tried running Startup Repair from a Win7 Install DVD or Win7 Repair CD?  That's generally the best approach for restoring full Win7 boot capability.

---

