---
title: "Windows XP not in GRUB"
date: 2010-06-10
forum: General Help
---

### Post by Chi-Kun on 2010-06-10
I recently installed Linux Ubuntu, and was going to experiment with it for a little bit. I have been using Windows my entire life, and thought it would be cool to expand... boy was I wrong.

Upon installing Ubuntu, I thought, "Hey, this is a pretty sexy OS." A day later, I tried to boot up my Windows XP through GRUB to use FLStudios (Because Imageline + Wine = Fail) and found my Windows wasn't listed.

For the past month, without ANY knowledge of Linux as ALL, have been trying to find an answers. I know the basics (I mean REALLY basics) but need help.

I go into the Terminal and type "sudo update-grub"

This comes up


```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

I am no computer whiz, but I see nothing related to Win XP in there. I then tried opening up "sudo gedit /boot/grub/menu.lst"

It opens up, what is supposed to be a text doccument. It pops up, but nothing is in it. I typed this in. (What another thread on this website said)

```
title windows XP
root (hd0,1)
makeactive
chainloader +1
```

Here are some extra tibits from the terminal

Sudo fdisk -l


```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        6763    54275688    7  HPFS/NTFS
/dev/sda3            9334        9725     3148740   db  CP/M / CTOS / ...
/dev/sda4            6763        9333    20651009    5  Extended
/dev/sda5            6763        9221    19745792   83  Linux
/dev/sda6            9221        9333      904192   82  Linux swap / Solaris

```

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=c28845c4-83f4-4e3f-aebc-c7960a633717 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ba83a9cb-b698-47db-8a08-c07808e659cc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda2	/mnt/windows	ntfs-3g	defaults,umask=0	0	0
sudo mount -a

```

I installed Ubuntu via flash drive. I do not have the ability to redo, seeing my sister bricked it with a virus, and I do not have the ability to burn a CD (Busted drive). I really.. really need windows back..

---

### Post by kiddykoff on 2010-06-10
gedit probably opened up a blank document because no such file existed. Additionally, i believe those are instructions for grub legacy, and by default with Lucid, GRUB2 is installed. Check out this, 

[http://www.dedoimedo.com/computers/grub-2.html#mozTocId722095](http://www.dedoimedo.com/computers/grub-2.html#mozTocId722095)

---

### Post by yetiman64 on 2010-06-10
Hi Chi-Kun, could you use the link -[click here]("http://ubuntuforums.org/showthread.php?t=1291280")- and download and run the boot_info_script as described in the link.
And then post the results.txt content back here (please put in "code" tags). This will give very detailed information on your boot setup for others to help you out.

---

### Post by kiddykoff on 2010-06-10
you might want to take a look here too.

[https://wiki.ubuntu.com/Grub2#Dual-booting](https://wiki.ubuntu.com/Grub2#Dual-booting)

---

### Post by Chi-Kun on 2010-06-10
> **yetiman64 said:**
> Hi Chi-Kun, could you use the link -[click here]("http://ubuntuforums.org/showthread.php?t=1291280")- and download and run the boot_info_script as described in the link.
And then post the results.txt content back here (please put in "code" tags). This will give very detailed information on your boot setup for others to help you out.

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325   108,631,700   108,551,376   7 HPFS/NTFS
/dev/sda3         149,934,645   156,232,124     6,297,480  db CP/M / CTOS / ...
/dev/sda4         108,632,062   149,934,079    41,302,018   5 Extended
/dev/sda5         108,632,064   148,123,647    39,491,584  83 Linux
/dev/sda6         148,125,696   149,934,079     1,808,384  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D4-0713                              vfat       DellUtility                   
/dev/sda2        3E44F8B244F86E51                       ntfs                                     
/dev/sda3                                               vfat       DellRestore                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        c28845c4-83f4-4e3f-aebc-c7960a633717   ext4                                     
/dev/sda6        ba83a9cb-b698-47db-8a08-c07808e659cc   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /mnt/windows             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/menu.lst: ===========================

title windows XP
root (hd0,1)
makeactive
chainloader +1

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c28845c4-83f4-4e3f-aebc-c7960a633717
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c28845c4-83f4-4e3f-aebc-c7960a633717
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
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c28845c4-83f4-4e3f-aebc-c7960a633717
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=c28845c4-83f4-4e3f-aebc-c7960a633717 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c28845c4-83f4-4e3f-aebc-c7960a633717
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=c28845c4-83f4-4e3f-aebc-c7960a633717 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c28845c4-83f4-4e3f-aebc-c7960a633717
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=c28845c4-83f4-4e3f-aebc-c7960a633717 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c28845c4-83f4-4e3f-aebc-c7960a633717
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=c28845c4-83f4-4e3f-aebc-c7960a633717 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c28845c4-83f4-4e3f-aebc-c7960a633717
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c28845c4-83f4-4e3f-aebc-c7960a633717
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

=============================== sda5/etc/fstab: ===============================


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=c28845c4-83f4-4e3f-aebc-c7960a633717 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ba83a9cb-b698-47db-8a08-c07808e659cc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda2	/mnt/windows	ntfs-3g	defaults,umask=0	0	0
sudo mount -a


=================== sda5: Location of files loaded by Grub: ===================


  72.9GB: boot/grub/core.img
  71.2GB: boot/grub/grub.cfg
  71.2GB: boot/grub/menu.lst
  72.9GB: boot/initrd.img-2.6.32-21-generic
  74.4GB: boot/initrd.img-2.6.32-22-generic
  72.9GB: boot/vmlinuz-2.6.32-21-generic
  72.9GB: boot/vmlinuz-2.6.32-22-generic
  74.4GB: initrd.img
  72.9GB: initrd.img.old
  72.9GB: vmlinuz
  72.9GB: vmlinuz.old
```


Sooo... uhh... what does this mean? ._.

---

### Post by john newbuntu on 2010-06-10
The windows boot files in its boot sector (/dev/sda2) appear to be missing.  Please try what is posted here by meierfra to restore the files after booting to Ubuntu.  Once that is done, you will have to run "sudo update-grub" from a terminal.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

OR alternatively, if you have an XP installation CD, follow the directions on how to fix the boot sector as given here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  (see section 'restore XP bootloader')
After that you could use the method to restore ubuntu bootloader (see section How to restore the Ubuntu grub bootloader (9.10 and beyond))
But the second method might not work for you since you do not have a liveCD/usb

Since you use grub2, you do not need the file /boot/grub/menu.lst.  Please get rid of that.

---

### Post by kiddykoff on 2010-06-10
this command will output the grub configuration into a document called test in your Documents folder.

```
kurtis@Turion:~$ sudo grub-mkconfig --output=Documents/test
```

try looking in that file to see if there's a mention of windows. If there is run the command without the --output

```
kurtis@Turion:~$ sudo grub-mkconfig
```

---

### Post by Chi-Kun on 2010-06-10
> **john newbuntu said:**
> The windows boot files in its boot sector (/dev/sda2) appear to be missing.  Please try what is posted here by meierfra to restore the files after booting to Ubuntu.  Once that is done, you will have to run "sudo update-grub" from a terminal.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

OR alternatively, if you have an XP installation CD, follow the directions on how to fix the boot sector as given here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  (see section 'restore XP bootloader')
After that you could use the method to restore ubuntu bootloader (see section How to restore the Ubuntu grub bootloader (9.10 and beyond))
But the second method might not work for you since you do not have a liveCD/usb

Since you use grub2, you do not need the file /boot/grub/menu.lst.  Please get rid of that.

I got as far as "BackupBS" in the directions. I don' have that option, so it tells me to use my windows XP recovery disk, which I don't have. Even if I did have it, I couldn't use it, due to my messed use D:/ Drive. Ubuntu has split the size of my HDD, killed my D:/, and made it impossible to boot WinXP. Why bother now, seeing there is no failsafe in this OS.

---

### Post by Chi-Kun on 2010-06-10
> **kiddykoff said:**
> this command will output the grub configuration into a document called test in your Documents folder.

```
kurtis@Turion:~$ sudo grub-mkconfig --output=Documents/test
```

try looking in that file to see if there's a mention of windows. If there is run the command without the --output

```
kurtis@Turion:~$ sudo grub-mkconfig
```

Both commands are not found.

---

### Post by kiddykoff on 2010-06-10
> **Chi-Kun said:**
> Both commands are not found.
```
$ sudo apt-get install grub-common
```

then try to run the commands again

---

### Post by john newbuntu on 2010-06-10
Well, if you had had the XP installation/recovery CD, we could have at least got win to work properly by repairing C:\.  But yes you would have lost your D:\ volume information.

Sadly, testdisk was not very useful in repairing the boot sector.

You appear to have a dell restore partition that might restore your windows to the factory settings.  Usually, you can get to it by pressing a key during BIOS bootup.  Do you want to try that?  Prior to that, you might want to mount /dev/sda2 in ubuntu and copy off any information that you might want.

---

### Post by oldfred on 2010-06-10
If sda2 is really a bootable partition and just missing its boot files:

[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)

COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

BOOTCFG  /rebuild
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

---

### Post by Chi-Kun on 2010-07-11
Bumping this thread. Seeing I have tried EVERYTHING and all has failed, I was able to grab a copy of a Windows XP Recovery Disk. This is the dell disk that came with the computer, and trust me, it took FOREVER to find.

I insert the recovery disk; Nothing
I reboot; Nothing
I hold R at the boot screen; Nothing
I press and hold F11 at the boot screen; Nothing

What do?

---

### Post by Chi-Kun on 2010-07-11
Yet again, bumping.

---

### Post by oldfred on 2010-07-11
If in BIOS you set to boot the CD drive first does it not boot? Then the CD probably is defective.

---

### Post by Chi-Kun on 2010-07-12
> **oldfred said:**
> If in BIOS you set to boot the CD drive first does it not boot? Then the CD probably is defective.

Done that, didn't work, and I highly doubt that. The packaging for the CD was NEVER opened, and there is no way in hell, I am THIS unlucky. For every single bit of advice that was given to me by avid Linux users to fail. I am now beginning to think that Linux Ubuntu is the cause of all of this; That I actually downloaded spyware from the main site. I wouldn't doubt it, seeing all the other ****ed up **** this OS has done.

My computer is getting slower and slower, and I have yet to download one thing, so that rules out viruses. It deleted all of my files. It hides all the important stuff, and constantly moves. It's the formula for a virus. It has been three months, and now, I am getting ****ing pissed.

Is there ANY way to fix this? Right now, I am to the point where I am tearing out my hair and bashing my head against my desk with RAGE. I found my "windows" folder in my C: Drive, hidden in an audacity folder (Wtf?). It has the folders:

Commands, Fonts, Inf, Installer, Microsoft.NET, System, System32, temp, and Winsxs.

It has the files

explorer.exe, hh.exe, notepad.exe, regedit.exe, system.ini, twain.dll, twain32.dll, win.ini, winhelp.exe, and winhelp32.exe


I WOULD post a screenshot, but MIRACULOUSLY Printscrn doesn't work anymore (And neither does my screencap app). I wonder WHY! (Derp)

---

### Post by Chi-Kun on 2010-07-15
Thanks a ****ing lot, everyone. My computer is now officially dead. Now I am typing for a NETBOOK and SURPRISE SURPRISE! It's running on ****ing LINUX. I have been calm for months, and months, page after page of reading up on how I can fix this, but nope. Not even avid Linux-fags know what to do with the OS they regularly use. **** you, **** this operating system, and **** my life. Blah blah blah, rot in hell, blah blah, rage, blah. You get the picture.

I'm out.

---

