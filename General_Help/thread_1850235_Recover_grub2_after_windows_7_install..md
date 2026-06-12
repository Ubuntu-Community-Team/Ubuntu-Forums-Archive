---
title: "Recover grub2 after windows 7 install."
date: 2011-09-26
forum: General Help
---

### Post by satish_j on 2011-09-26
Iam currently dual-booting WinXP and Lucid Lynx.I have a free partition where i am planning to install Win7.
Pls guide me the steps(or links) for same.I know that if windows is installed over Ubuntu,it replaces the MBR and i would not be able to boot into Ubuntu.How do i go for it without affecting MBR?

---

### Post by elliotn on 2011-09-26
u can recover grub or reinstall grub from a LiveCd.

---

### Post by raja.genupula on 2011-09-26
Hi you can install windows , you can get your grub back by using **boot-repair**

Follow this link 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

all the best

---

### Post by satish_j on 2011-09-26
One more quick question..
If i boot from LiveCd and format the unallocated space using NTFS,will i then be able to install Win 7 directly from XP,into the NTFS formatted partition?

---

### Post by Mark Phelps on 2011-09-26
> **satish_j said:**
> How do i go for it without affecting MBR?


Guess everyone responding missed THIS comment ...

Basically, you -- cant'.  Installing ANY Windows OS will overwrite the MBR of the drive on which it is installed.  You are not offered a choice in that.

Whether you then choose to overwrite the MBR a second time with GRUB is up to you.

You will need to boot from the Win7 DVD to install it.  If you attempt to install it from inside XP, while it may work, it's likely to disable your XP -- because there is no upgrade path from XP to Win7.

---

### Post by satish_j on 2011-09-30
Ok,i saw from the link provided that ppa has to be added for installing Boot-repair.Adding ppas is one thing i always try to avoid.
Do i have no other option here?
Also,once installed,how do i access it??..from gnome menu??
edit..
i got it how to access it from the link..somehow i missed it reading in first time..

---

### Post by satish_j on 2011-10-02
Cannot add the repository from Live CD..getting foll err:
```

error reading https://launchpad.net/api/1.0/~yannubuntu/+archive/boot-repair:<urlopen error[error -2]Name or service not known

```
Pls..need urgent help..win7 got installed successfully,but,now in absence of Grub,cannot access Ubuntu

---

### Post by philinux on 2011-10-02
This might help you from the live cd.

[http://www.lancelhoff.com/restore-grub2-after-installing-windows/](http://www.lancelhoff.com/restore-grub2-after-installing-windows/)

---

### Post by Mark Phelps on 2011-10-02
Folks are not responding to your requests because this is an Ubuntu forum -- NOT a Windows forum -- and your thread title, now that you have Win7 installed, is misleading.

You would do better starting a new thread asking about reinstalling GRUB2.  You will get more responses that way.

---

### Post by philinux on 2011-10-02
> **Mark Phelps said:**
> Folks are not responding to your requests because this is an Ubuntu forum -- NOT a Windows forum -- and your thread title, now that you have Win7 installed, is misleading.

You would do better starting a new thread asking about reinstalling GRUB2.  You will get more responses that way.

I'll fix the title.

Done

---

### Post by satish_j on 2011-10-02
> **philinux said:**
> I'll fix the title.

Done

Thanks for fixing the title..
BTW,i tried the link that you provided and it worked like charm.
Also,after updating grub using:
```

sudo update-grub2

```
win7 is detected,but not win xp..
Is there anyway to get Ubunru,Win7,WinXP all three to show in GRub??
BTW,Iam writing this from Ubuntu now..

---

### Post by philinux on 2011-10-02
Go here and follow instructions. Post back the results.

 [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
Also the output of this.

sudo fdisk -l

---

### Post by satish_j on 2011-10-05
> **philinux said:**
> Go here and follow instructions. Post back the results.

 [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
Also the output of this.

sudo fdisk -l

Sorry fo the late reply:
Here is the output of fdisk -l../dev/sda1 is the missing XP partition
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc5e1c5e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        7649    40957717+   5  Extended
/dev/sda3            7650       13387    46082048    7  HPFS/NTFS
/dev/sda4           13387       19458    48766976   83  Linux
/dev/sda5            2551        2614      514048+  82  Linux swap / Solaris
/dev/sda6            2615        7649    40443606    7  HPFS/NTFS

```
AND,BELOW IS THE CONTENTS OF RESULTS.TXT
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 4 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 NTFS / exFAT / HPFS
/dev/sda2          40,965,750   122,881,184    81,915,435   5 Extended
/dev/sda5          40,965,813    41,993,909     1,028,097  82 Linux swap / Solaris
/dev/sda6          41,993,973   122,881,184    80,887,212   7 NTFS / exFAT / HPFS
/dev/sda3         122,882,048   215,046,143    92,164,096   7 NTFS / exFAT / HPFS
/dev/sda4         215,046,144   312,580,095    97,533,952  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        F03C0B933C0B544E                       ntfs       
/dev/sda3        589CF1959CF16E3E                       ntfs       
/dev/sda4        3b3a0f99-fb76-4d16-970c-5a514fcd22b1   ext4       
/dev/sda5        571820c5-35bb-434a-80ec-35e6216861d6   swap       
/dev/sda6        6B1A1C7E21C4B0CE                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT

--------------------------------------------------------------------------------

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set default="8"
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 3b3a0f99-fb76-4d16-970c-5a514fcd22b1
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 3b3a0f99-fb76-4d16-970c-5a514fcd22b1
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=9
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 3b3a0f99-fb76-4d16-970c-5a514fcd22b1
insmod jpeg
if background_image /home/satish/Desktop/Splash/question-mark-funny-face.jpg ; then
  set color_normal=black/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 3b3a0f99-fb76-4d16-970c-5a514fcd22b1
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=3b3a0f99-fb76-4d16-970c-5a514fcd22b1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 3b3a0f99-fb76-4d16-970c-5a514fcd22b1
	echo	'Loading Linux 2.6.32-33-generic ...'
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=3b3a0f99-fb76-4d16-970c-5a514fcd22b1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f03c0b933c0b544e
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda4/etc/fstab: ================================

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
UUID=3b3a0f99-fb76-4d16-970c-5a514fcd22b1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0a8713bc-be38-436a-8ffa-4c2d1401dcdb none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 146.667079926 = 157.482577920  boot/grub/core.img                             1
 105.428878784 = 113.203396608  boot/grub/grub.cfg                             1
 104.586917877 = 112.299347968  boot/initrd.img-2.6.32-33-generic              1
 148.983257294 = 159.969554432  boot/vmlinuz-2.6.32-33-generic                 1
 104.586917877 = 112.299347968  initrd.img                                     1
 148.983257294 = 159.969554432  vmlinuz                                        1

```
Now what??

---

### Post by satish_j on 2011-10-06
Pls help someone...

---

### Post by satish_j on 2011-10-07
A regrettable bump..

---

### Post by oldfred on 2011-10-07
Windows only boots from one active (boot flag) partition. When you boot Windows 7 it should give you a choice to boot XP also.

Discusses Vista but 7 is the same except it usually installs with a separte hidden /boot of 100MB.
To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

Since 7 is in a primary partition you may be able to move its boot files and the boot flag to the sda3 partition and repair it to make it bootable. Then move flag back to XP and repair it or it may still work.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7
/bootmgr /Boot/BCD /Windows/System32/winload.exe 


Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by satish_j on 2011-10-10
got it..Win7 is using its own grub menu,which has XP in the list.I never tried booting into win7 after recovering grub..
Initially,grub2 menu is displayed on boot,which lists Lucid,Lucid recovery and Win7.Selecting Win7 from this list gives another menu which has Win7 and 'earlier verion of windows'(i.e XP)as options.
So,if i need to boot into XP,i need to go through 2 OS menus..;)

---

