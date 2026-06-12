---
title: "Dual boot: Ubuntu 11.4 and Debian 6"
date: 2011-04-30
forum: General Help
---

### Post by _ari on 2011-04-30
I am _really sorry_ to bother you guys, but i figured out that it might be the best way to go for me right now...

Wanted to get rid of Windows forever and switch completely to Ubuntu, which is i guess the best choice for a former Windows user, but also wanted to check out Debian / have it installed on my Notebook (HP625)

I am not an expert, but no total noob either and installed dual boot systems many times before (mostly WindowsXP/Windows7 along with Ubuntu).

This is what i did:
1) Installed Ubuntu with "/", "/home" and "/swap" and left some space for Debian
2) Installed Debian 6.0... It recognized Ubuntu and asked me if it should use the free space in order to keep the other operating system "alive" and if i want to choose between my operating systems on startup. So logically i guessed it's going to work out, but that wasn't the case.

When i now start up my Computer, i get the following message:
[B]"Non-System disk or disk error
replace and strike any key when ready"[/B]
Mainboard is set up to "AHCI", tried switching it to "IDE" but it said, that there might be a data loss by doing so (Just wanted to try if it then maybe would work)...

From another source i got a tip using a Live CD and the terminal to fix it, so:
1) Started Knoppix 6.4.3 and typed in: **"sudo grub"** which gives me the information that i currently have Gnu Grub Version 0.97 (I guess Debian overwrote Ubuntu Grub?)
2) By typing in **"find /boot/grub/stage1"** i get
**"Error 15: File not found"**


I know that i probably did all this to myself and i should have read maybe more carefully, but having at least some computer skills makes you think you should be able to install two operating systems :(

**_Is there a safe way to reinstall Grub without loosing any data at all? (or another solution?)_**
[Need the Notebook so not getting an answer quickly and i will reinstall all with reading some information before, but to be honest: Try to avoid it cause it's annoying]

Should i have installed Debian first maybe?


Thanks for your time and help
_ari

---

### Post by Joe of loath on 2011-04-30
Boot an Ubuntu live CD, chroot into Ubuntu, and tell it to rebuild grub.

[http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/](http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/)

---

### Post by _ari on 2011-04-30
Thank you so much for helping a stupid idiot by giving him information he should have been able to find for himself.
Will try it immediately and post if it worked

---

### Post by Joe of loath on 2011-04-30
Careful, chroot becomes addictive, and you end up running two Linux distributions at once :lol:

---

### Post by _ari on 2011-04-30
Thank you again for your help...
Followed the instructions and then changed the Partition Flag "boot" to the Ubuntu Partition (sda1) with GParted.
Took me some time to figure out how it all worked (Linux Noob)...

Finally i got it :)

It probably isn't sth your are happy about, but maybe you are the one responsible for one more Linux User on this fine planet...

Greetings, _ari

---

### Post by giannilmbd on 2011-04-30
Hi,
I've got exactly the same problem.

I've successfully installed Ubuntu 11 (64bit) on an external WD MyPassport external HD. I managed to fix some initial problems with GRUB using dpkg-reconfigue grub-pc: now Ubuntu boots fine.

Unfortunately if I try to boot into Debian 6 (installed on the same HD) I get the "file not found" error message.

Could you please give me more details on how you fixed the problem?

Cheers

Gianni

---

### Post by Joe of loath on 2011-04-30
Have you tried the blog post I linked?

---

### Post by giannilmbd on 2011-04-30
Yes, I've checked [http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/](http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/)
but it seems to me that that post tries to fix a Grub that doesn't work at all. 

In my case Grub offers all the installed OSs and correctly boots into Ubuntu 11 if that OS is selected.
What doesn't work is the booting into Debian. The latter is installed in an extended partition on the same HD where Ubuntu is installed. Grub doesn't find the kernel (although it is where it should be)

Could it be that installing on an extended partition is the problem? What could be an alternative to that?

---

### Post by oldfred on 2011-04-30
Extended partitions are not an issue with Linux. Grub2's osprober uses other installs menu.lst or grub config files to configure its entry. If the entry is not correct then the osprober will not have a good entry.

Probably best to post boot info script to see if we can see what is out of place.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by giannilmbd on 2011-04-30
Here it is
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2can.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for b2d.
 => Windows is installed in the MBR of /dev/sdg
 => No boot loader is installed in the MBR of /dev/sdh

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
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 6.0
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,344,579   156,344,517   7 HPFS/NTFS
/dev/sda2         156,344,641   312,576,704   156,232,064   5 Extended
/dev/sda5         156,344,643   304,785,179   148,440,537  83 Linux
/dev/sda6         304,785,243   312,576,704     7,791,462  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500074283008 bytes
255 heads, 63 sectors/track, 60797 cylinders, total 976707584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   197,072,360   197,070,313  83 Linux
/dev/sdb2         197,072,894   976,705,535   779,632,642   5 Extended
/dev/sdb5         972,517,376   976,705,535     4,188,160  82 Linux swap / Solaris
/dev/sdb6    *    197,072,896   964,464,639   767,391,744  83 Linux
/dev/sdb7         964,466,688   972,511,231     8,044,544  82 Linux swap / Solaris


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 8053 MB, 8053063680 bytes
183 heads, 32 sectors/track, 2685 cylinders, total 15728640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             32    15,728,639    15,728,608   c W95 FAT32 (LBA)


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdh1                  63   781,417,664   781,417,602   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A4C03240C032194E                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        51c288ac-45a0-4365-a664-5408ab70ebf4   ext4                                     
/dev/sda6        16333dc8-bd1c-47a5-84c7-14dd4c8f3222   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        efd20ac3-d1c1-4b94-b909-43aa44f17481   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        f1727bee-20a7-4dce-bd5c-f40cbcd2486a   swap                                     
/dev/sdb6        06fce64e-7019-4ba2-b77c-e8ecd4a0c5df   ext3       debian                        
/dev/sdb7        58894bc0-6ef8-45a5-a0de-82648eaa8290   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdg1        277D-5A35                              vfat       CORSAIR                       
/dev/sdg: PTTYPE="dos" 
/dev/sdh1        00FC-FD32                              vfat       TREKSTOR                      
/dev/sdh: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb6        /media/debian            ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdg1        /media/CORSAIR           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdh1        /media/TREKSTOR          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect /usepmtimer

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro  splash quiet  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single  splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux	/boot/vmlinuz-2.6.38-7-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro  splash quiet  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	echo	'Loading Linux 2.6.38-7-generic ...'
	linux	/boot/vmlinuz-2.6.38-7-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single  splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro  splash quiet  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single  splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro  splash quiet  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single  splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro  splash quiet  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single  splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro  splash quiet  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single  splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro  splash quiet  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single  splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro  splash quiet  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single  splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro  splash quiet  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single  splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro  splash quiet  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single  splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro  splash quiet  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	echo	'Loading Linux 2.6.31-17-generic ...'
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single  splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro  splash quiet  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	echo	'Loading Linux 2.6.31-14-generic ...'
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single  splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-14-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Professional x64 Edition (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root A4C03240C032194E
	drivemap -s (hd0) ${root}
	chainloader +1
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=16333dc8-bd1c-47a5-84c7-14dd4c8f3222 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  80.1GB: boot/grub/core.img
  89.1GB: boot/grub/grub.cfg
  80.6GB: boot/initrd.img-2.6.31-14-generic
  80.4GB: boot/initrd.img-2.6.31-17-generic
  93.6GB: boot/initrd.img-2.6.31-20-generic
 100.8GB: boot/initrd.img-2.6.31-21-generic
 101.0GB: boot/initrd.img-2.6.32-21-generic
 110.1GB: boot/initrd.img-2.6.32-22-generic
 124.4GB: boot/initrd.img-2.6.32-23-generic
 118.5GB: boot/initrd.img-2.6.32-24-generic
 119.9GB: boot/initrd.img-2.6.32-25-generic
 126.9GB: boot/initrd.img-2.6.32-26-generic
 134.4GB: boot/initrd.img-2.6.38-7-generic
 117.2GB: boot/initrd.img-2.6.38-8-generic
  80.2GB: boot/vmlinuz-2.6.31-14-generic
  80.2GB: boot/vmlinuz-2.6.31-17-generic
  83.8GB: boot/vmlinuz-2.6.31-20-generic
  90.8GB: boot/vmlinuz-2.6.31-21-generic
  96.9GB: boot/vmlinuz-2.6.32-21-generic
 100.8GB: boot/vmlinuz-2.6.32-22-generic
  96.7GB: boot/vmlinuz-2.6.32-23-generic
 105.4GB: boot/vmlinuz-2.6.32-24-generic
 110.1GB: boot/vmlinuz-2.6.32-25-generic
  88.7GB: boot/vmlinuz-2.6.32-26-generic
 132.0GB: boot/vmlinuz-2.6.38-7-generic
 125.1GB: boot/vmlinuz-2.6.38-8-generic
 117.2GB: initrd.img
 134.4GB: initrd.img.old
 125.1GB: vmlinuz
 132.0GB: vmlinuz.old

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root efd20ac3-d1c1-4b94-b909-43aa44f17481
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root efd20ac3-d1c1-4b94-b909-43aa44f17481
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root efd20ac3-d1c1-4b94-b909-43aa44f17481
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=efd20ac3-d1c1-4b94-b909-43aa44f17481 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root efd20ac3-d1c1-4b94-b909-43aa44f17481
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=efd20ac3-d1c1-4b94-b909-43aa44f17481 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root efd20ac3-d1c1-4b94-b909-43aa44f17481
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root efd20ac3-d1c1-4b94-b909-43aa44f17481
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Professional x64 Edition (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root A4C03240C032194E
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro splash quiet quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single splash quiet
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-7-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.38-7-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro splash quiet quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Ubuntu, with Linux 2.6.38-7-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.38-7-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single splash quiet
	initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.32-26-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro splash quiet quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.32-26-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single splash quiet
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro splash quiet quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single splash quiet
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro splash quiet quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single splash quiet
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro splash quiet quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single splash quiet
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro splash quiet quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single splash quiet
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro splash quiet quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single splash quiet
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro splash quiet quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro splash quiet quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-17-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro splash quiet quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, with Linux 2.6.31-17-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, with Linux 2.6.31-14-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro splash quiet quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, with Linux 2.6.31-14-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 51c288ac-45a0-4365-a664-5408ab70ebf4
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=51c288ac-45a0-4365-a664-5408ab70ebf4 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-5-amd64 (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 06fce64e-7019-4ba2-b77c-e8ecd4a0c5df
	linux /boot/vmlinuz-2.6.32-5-amd64 root=UUID=06fce64e-7019-4ba2-b77c-e8ecd4a0c5df ro quiet
	initrd /boot/initrd.img-2.6.32-5-amd64
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-5-amd64 (recovery mode) (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root 06fce64e-7019-4ba2-b77c-e8ecd4a0c5df
	linux /boot/vmlinuz-2.6.32-5-amd64 root=UUID=06fce64e-7019-4ba2-b77c-e8ecd4a0c5df ro single
	initrd /boot/initrd.img-2.6.32-5-amd64
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=efd20ac3-d1c1-4b94-b909-43aa44f17481 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c6bc53aa-3317-4c2d-90da-6d515075d4b1 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .8GB: boot/grub/core.img
  86.0GB: boot/grub/grub.cfg
   1.8GB: boot/initrd.img-2.6.38-8-generic
    .3GB: boot/vmlinuz-2.6.38-8-generic
   1.8GB: initrd.img
    .3GB: vmlinuz

=========================== sdb6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 06fce64e-7019-4ba2-b77c-e8ecd4a0c5df
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 06fce64e-7019-4ba2-b77c-e8ecd4a0c5df
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 06fce64e-7019-4ba2-b77c-e8ecd4a0c5df
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Debian GNU/Linux, with Linux 2.6.32-5-amd64' --class debian --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 06fce64e-7019-4ba2-b77c-e8ecd4a0c5df
	echo	'Loading Linux 2.6.32-5-amd64 ...'
	linux	/boot/vmlinuz-2.6.32-5-amd64 root=UUID=06fce64e-7019-4ba2-b77c-e8ecd4a0c5df ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-5-amd64
}
menuentry 'Debian GNU/Linux, with Linux 2.6.32-5-amd64 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 06fce64e-7019-4ba2-b77c-e8ecd4a0c5df
	echo	'Loading Linux 2.6.32-5-amd64 ...'
	linux	/boot/vmlinuz-2.6.32-5-amd64 root=UUID=06fce64e-7019-4ba2-b77c-e8ecd4a0c5df ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-5-amd64
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set efd20ac3-d1c1-4b94-b909-43aa44f17481
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=efd20ac3-d1c1-4b94-b909-43aa44f17481 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set efd20ac3-d1c1-4b94-b909-43aa44f17481
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=efd20ac3-d1c1-4b94-b909-43aa44f17481 ro single
	initrd /boot/initrd.img-2.6.38-8-generic
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

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=06fce64e-7019-4ba2-b77c-e8ecd4a0c5df /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=58894bc0-6ef8-45a5-a0de-82648eaa8290 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /media/usb0     auto    rw,user,noauto  0       0
/dev/sda2       /media/usb1     auto    rw,user,noauto  0       0
/dev/sda5       /media/usb2     auto    rw,user,noauto  0       0
/dev/sda6       /media/usb3     auto    rw,user,noauto  0       0
/dev/sda7       /media/usb4     auto    rw,user,noauto  0       0

=================== sdb6: Location of files loaded by Grub: ===================


 175.6GB: boot/grub/core.img
 175.6GB: boot/grub/grub.cfg
 175.6GB: boot/initrd.img-2.6.32-5-amd64
 175.7GB: boot/vmlinuz-2.6.32-5-amd64
 175.6GB: initrd.img
 175.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 00 00  00 00 00 80 98 5f 19 00  |............._..|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  80 27 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |.'.t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  00 00 00 00 00 00 00 00  |...<.u..........|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  00 00 00 00 00 00 00 00  b8 ae ff 01 00 00 00 00  |................|
00000010  07 00 00 00 6f 04 00 00  00 00 00 00 00 00 00 00  |....o...........|
00000020  c0 ae ff 01 00 00 00 00  07 00 00 00 70 04 00 00  |............p...|
00000030  00 00 00 00 00 00 00 00  c8 ae ff 01 00 00 00 00  |................|
00000040  07 00 00 00 71 04 00 00  00 00 00 00 00 00 00 00  |....q...........|
00000050  d0 ae ff 01 00 00 00 00  07 00 00 00 5e 0c 00 00  |............^...|
00000060  00 00 00 00 00 00 00 00  d8 ae ff 01 00 00 00 00  |................|
00000070  07 00 00 00 3f 0a 00 00  00 00 00 00 00 00 00 00  |....?...........|
00000080  e0 ae ff 01 00 00 00 00  07 00 00 00 94 10 00 00  |................|
00000090  00 00 00 00 00 00 00 00  e8 ae ff 01 00 00 00 00  |................|
000000a0  07 00 00 00 72 04 00 00  00 00 00 00 00 00 00 00  |....r...........|
000000b0  f0 ae ff 01 00 00 00 00  07 00 00 00 59 12 00 00  |............Y...|
000000c0  00 00 00 00 00 00 00 00  f8 ae ff 01 00 00 00 00  |................|
000000d0  07 00 00 00 cd 16 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 af ff 01 00 00 00 00  07 00 00 00 73 04 00 00  |............s...|
000000f0  00 00 00 00 00 00 00 00  08 af ff 01 00 00 00 00  |................|
00000100  07 00 00 00 f7 08 00 00  00 00 00 00 00 00 00 00  |................|
00000110  10 af ff 01 00 00 00 00  07 00 00 00 a3 09 00 00  |................|
00000120  00 00 00 00 00 00 00 00  18 af ff 01 00 00 00 00  |................|
00000130  07 00 00 00 74 04 00 00  00 00 00 00 00 00 00 00  |....t...........|
00000140  20 af ff 01 00 00 00 00  07 00 00 00 37 14 00 00  | ...........7...|
00000150  00 00 00 00 00 00 00 00  28 af ff 01 00 00 00 00  |........(.......|
00000160  07 00 00 00 1c 0d 00 00  00 00 00 00 00 00 00 00  |................|
00000170  30 af ff 01 00 00 00 00  07 00 00 00 63 0e 00 00  |0...........c...|
00000180  00 00 00 00 00 00 00 00  38 af ff 01 00 00 00 00  |........8.......|
00000190  07 00 00 00 f7 0d 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  40 af ff 01 00 00 00 00  07 00 00 00 ca 12 00 00  |@...............|
000001b0  00 00 00 00 00 00 00 00  48 af ff 01 00 00 00 fe  |........H.......|
000001c0  ff ff 82 fe ff ff 02 58  38 2e 00 e8 3f 00 00 fe  |.......X8...?...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 78 bd 2d 00 00  |...........x.-..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

---

### Post by giannilmbd on 2011-04-30
Just to be sure, the relevant disk is sdb (where you see both Ubuntu and Debian)

---

### Post by oldfred on 2011-04-30
When you installed it was sda. But that should not matter to Ubuntu or Debian as grub2 uses UUIDs and the search overides the set root command. You could try editing the grub entry with an e and see if changing the set root makes any difference.

You also have  a group of partitions in Debian's fstab, but they do not use UUIDs perhaps not finding them causes a problem. It is looking for an sda7 which does not exist.

```
/dev/sda2       /media/usb1     auto    rw,user,noauto  0       0
/dev/sda5       /media/usb2     auto    rw,user,noauto  0       0
/dev/sda6       /media/usb3     auto    rw,user,noauto  0       0
/dev/sda7       /media/usb4     auto    rw,user,noauto  0       0

```

You may want to house clean old kernels to reduce menu size.

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
HOWTO: Remove Older Kernels via GUI Tweak
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)
A easy way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

You have two MBRs, but old verison of boot script does not parse grub1.99 correctly, so I cannot tell if each boots Ubuntu or Debian.
For your info if you want, still being tested and only difference for you should be the MBRs.
Get last development version of Boot Info Script:
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

Do not have boot flag on sda6 (unless using lilo). Windows requires boot flag to boot with window's boot loader on a primary partition. Some BIOS required a boot flag on a primary partition, so put yours on any of sdb1 thru 4. Grub does not use a boot flag.

---

### Post by giannilmbd on 2011-04-30
Thanks a lot.

I'll try your suggestions and see if I can fix the problem

Cheers

---

### Post by _ari on 2011-04-30
Sorry, i really just fixed it by doing what [Joe of loath]("http://ubuntuforums.org/member.php?u=148361") said...
Maybe i should mention that i did it with the partition where Debian was on, and also with the one Ubuntu was on... you have your partitions flagged right?
I have the feeling your problem still exists even though you know - i guess - more about linux then i do...
I am really sorry for not being able to help you :(
[Guess someone other will, or maybe already did... write how the posted solutions worked for you]

Greetings, ari

---

### Post by Joe of loath on 2011-04-30
I had a similar problem on one of my Arch installs - it wasn't finding the partition with the kernel on. I can't remember how I fixed it, since it was an Arch specific problem, but rebuilding Debian's initrd might work.

---

