---
title: "Grub Error 21"
date: 2010-06-02
forum: General Help
---

### Post by grumpy.biatch on 2010-06-02
I had a dual boot system with Windows7 and Ubuntu 10.04. This morning I installed mandriva on external hard disk. It killed the grub and I couldnt get in Ubuntu. Tried GAG but it got complicated and gave some errors. Unistalled GAG and I can now only log in to Windows. I wish to retain all distros. Please help:confused:

---

### Post by Bucky Ball on 2010-06-02
This could be of some help:

[http://members.iinet.net.au/~herman546/](http://members.iinet.net.au/~herman546/)

Scroll down and find the grub pages ...

---

### Post by grumpy.biatch on 2010-06-02
> **Bucky Ball said:**
> This could be of some help:

[http://members.iinet.net.au/~herman546/]("http://members.iinet.net.au/%7Eherman546/")

Scroll down and find the grub pages ...


I know Herman, will give it a go.

---

### Post by yetiman64 on 2010-06-02
Probably the best tool for troubleshooting grub errors/boot problems is to run the boot_info_script. How to get it and use it is available here (a very good guide)

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

It can be used from a live cd if you have one and as you have currently lost Ubuntu booting.

Run it and paste the results in code tags back here and someone will likely be able to help.

---

### Post by Bucky Ball on 2010-06-02
Yetiman64, totally off topic but, they grow some strange ducks in Queensland by the looks of your pic. Just as well I'm here in SA cos that could get vicious! lol. All the best ...

---

### Post by grumpy.biatch on 2010-06-02
> **yetiman64 said:**
> Probably the best tool for troubleshooting grub errors/boot problems is to run the boot_info_script. How to get it and use it is available here (a very good guide)

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

It can be used from a live cd if you have one and as you have currently lost Ubuntu booting.

Run it and paste the results in code tags back here and someone will likely be able to help.

Thanks for the tip. I have figured out the problem, just need boot loader tools. The mandriva install killed Ubuntu Grub and installed its own. Later I tried GaG but it wasnt much help so I uninstalled it, which in return installed MBR that sees Windows and data partition on primary. I am bit scared with Ubuntu documentation on various counts it caused enormous stress and ruined whatever left. :P

---

### Post by grumpy.biatch on 2010-06-04
> **grumpy.biatch said:**
> Thanks for the tip. I have figured out the problem, just need boot loader tools. The mandriva install killed Ubuntu Grub and installed its own. Later I tried GaG but it wasnt much help so I uninstalled it, which in return installed MBR that sees Windows and data partition on primary. I am bit scared with Ubuntu documentation on various counts it caused enormous stress and ruined whatever left. :P

I've now tried lots of stuff but yet to see any effect. Below please find hdd geo and error messages -

**root@ubuntu**:/home/ubuntu# fdisk -l 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004557c

  [B] Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223       34997   239167687+   7  HPFS/NTFS
/dev/sda3           34998       38913    31455081    5  Extended
/dev/sda5           34998       37607    20964627+  83  Linux
/dev/sda6           37608       38259     5237158+  82  Linux swap /  Solaris

[/B]**ubuntu@ubuntu:~**$ sudo mount /dev/sda3 /mnt/
mount: you must specify the filesystem type

**ubuntu@ubuntu**:~$ grub
The program 'grub' is currently not installed.  You can install it by  typing:
sudo apt-get install grub

**ubuntu@ubuntu**:~$ find /boot/grub/stage1
find: `/boot/grub/stage1': No such file or directory

**sudo grub-install /dev/sda3** 
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is  /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

:confused:

When i manually mount the file-system I can see the boot folder and grub in it.

---

### Post by yetiman64 on 2010-06-04
It seems like you're operating from a live cd at the moment "ubuntu@ubuntu". You're also using 10.04 and the "stage1" command is no longer of use in grub2. 

Please check the link in post 4 and follow the instructions for downloading and using the bootinfo script (will be needed here by the looks) and post its output here between code tags.

Can you boot windows still? Suspect you can't without grub but would like to confirm as it was mentioned earlier.

By the way, the bootinfo script can be used from the live cd environment I think you're currently in.

---

### Post by grumpy.biatch on 2010-06-04
> **yetiman64 said:**
> It seems like you're operating from a live cd at the moment "ubuntu@ubuntu". You're also using 10.04 and the "stage1" command is no longer of use in grub2. 

Please check the link in post 4 and follow the instructions for downloading and using the bootinfo script (will be needed here by the looks) and post its output here between code tags.

Can you boot windows still? Suspect you can't without grub but would like to confirm as it was mentioned earlier.

By the way, the bootinfo script can be used from the live cd environment I think you're currently in.


Well, well, well..........

It is getting funny, let me enlighten you

1. I had a perfect dual booting system till day before.
2. I installed Mandriva on external HDD and somehow it fixed its own Grub and after restart I couldnt find Ubuntu. 
3. I used GAG, the boot manager but it couldnt configure Ubuntu or Mandriva. I uninstalled it and it restored MBR. 
4. Now I can not boot in any Linux, I see windows and I can use windows.
5. When I open Gparted from live cd I get to see a correct geometry. 

The boot tool that You ask for wont serve me at all. My Bios is fine and not broken.

---

### Post by grumpy.biatch on 2010-06-04
> **yetiman64 said:**
> It seems like you're operating from a live cd at the moment "ubuntu@ubuntu". You're also using 10.04 and the "stage1" command is no longer of use in grub2. 

Please check the link in post 4 and follow the instructions for downloading and using the bootinfo script (will be needed here by the looks) and post its output here between code tags.

Can you boot windows still? Suspect you can't without grub but would like to confirm as it was mentioned earlier.

By the way, the bootinfo script can be used from the live cd environment I think you're currently in.


OKay, I thought why not to try. Below is the out put

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => GAG is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 HPFS/NTFS
/dev/sda2          83,891,430   562,226,804   478,335,375   7 HPFS/NTFS
/dev/sda3         562,227,183   625,137,344    62,910,162   5 Extended
/dev/sda5         562,227,200   604,156,454    41,929,255  83 Linux
/dev/sda6         604,156,518   614,630,834    10,474,317  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        79C332AC3B624E50                       ntfs       Windows 7                     
/dev/sda2        7FDBAA5A767F2490                       ntfs       DATA                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        67fc1344-6980-4902-956d-91d182ac9498   ext4                                     
/dev/sda6        22340fc7-4a6d-47e2-bd9a-65d20cb3da86   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/67fc1344-6980-4902-956d-91d182ac9498 ext4       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set 67fc1344-6980-4902-956d-91d182ac9498
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
search --no-floppy --fs-uuid --set 67fc1344-6980-4902-956d-91d182ac9498
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
    search --no-floppy --fs-uuid --set 67fc1344-6980-4902-956d-91d182ac9498
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=67fc1344-6980-4902-956d-91d182ac9498 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 67fc1344-6980-4902-956d-91d182ac9498
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=67fc1344-6980-4902-956d-91d182ac9498 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 67fc1344-6980-4902-956d-91d182ac9498
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=67fc1344-6980-4902-956d-91d182ac9498 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 67fc1344-6980-4902-956d-91d182ac9498
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=67fc1344-6980-4902-956d-91d182ac9498 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 67fc1344-6980-4902-956d-91d182ac9498
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 67fc1344-6980-4902-956d-91d182ac9498
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 79c332ac3b624e50
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=67fc1344-6980-4902-956d-91d182ac9498 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=22340fc7-4a6d-47e2-bd9a-65d20cb3da86 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 288.0GB: boot/grub/core.img
 288.3GB: boot/grub/grub.cfg
 289.4GB: boot/initrd.img-2.6.32-21-generic
 289.4GB: boot/initrd.img-2.6.32-22-generic
 289.4GB: boot/vmlinuz-2.6.32-21-generic
 289.4GB: boot/vmlinuz-2.6.32-22-generic
 289.4GB: initrd.img
 289.4GB: initrd.img.old
 289.4GB: vmlinuz
 289.4GB: vmlinuz.old

---

### Post by yetiman64 on 2010-06-04
Everything seems fine but for 
> ============================= Boot Info Summary: ==============================

 => GAG is installed in the MBR of /dev/sda You will need to Re-install grub to the MBR from the live disk with /dev/sda5 being the root partition. 
From the live disk
```
sudo mount /dev/sda5 /mnt
```Then
```
sudo grub-install --root-directory=/mnt /dev/sda
```.
Then
```
sudo umount /mnt
```And then reboot the machine, grub menu should come up now.
Note windows 7 loader is listed in grub.cfg so re-installing grub will also give access to windows. To access an external os later on just plug it in then in 10.04 run
```
sudo update-grub
```and it should be picked up as bootable by Lucid and added to the menu. To remove from the menu unplug and use the "update-grub" command abve again.

Edit: this is where i got most of the info [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
.particularly section 13.

---

### Post by grumpy.biatch on 2010-06-04
> **yetiman64 said:**
> Everything seems fine but for 
 You will need to Re-install grub to the MBR from the live disk with /dev/sda5 being the root partition. 
From the live disk
```
sudo mount /dev/sda5 /mnt
```Then
```
sudo grub-install --root-directory=/mnt /dev/sda
```.
Then
```
sudo umount /mnt
```And then reboot the machine, grub menu should come up now.
Note windows 7 loader is listed in grub.cfg so re-installing grub will also give access to windows. To access an external os later on just plug it in then in 10.04 run
```
sudo update-grub
```and it should be picked up as bootable by Lucid and added to the menu. To remove from the menu unplug and use the "update-grub" command abve again.

Edit: this is where i got most of the info [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
.particularly section 13.


Yeti:

This is what I got so far -

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo umount /mnt
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

---

### Post by grumpy.biatch on 2010-06-04
> **grumpy.biatch said:**
> Yeti:

This is what I got so far -

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo umount /mnt
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).


Yeti,

I got in, thanks a bunch.

Best,

Dave

---

### Post by MrRichard on 2010-11-09
> **yetiman64 said:**
> Everything seems fine but for 
 You will need to Re-install grub to the MBR from the live disk with /dev/sda5 being the root partition. 
From the live disk
```
sudo mount /dev/sda5 /mnt
```Then
```
sudo grub-install --root-directory=/mnt /dev/sda
```.
Then
```
sudo umount /mnt
```And then reboot the machine, grub menu should come up now.
Note windows 7 loader is listed in grub.cfg so re-installing grub will also give access to windows. To access an external os later on just plug it in then in 10.04 run
```
sudo update-grub
```and it should be picked up as bootable by Lucid and added to the menu. To remove from the menu unplug and use the "update-grub" command abve again.

Edit: this is where i got most of the info [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
.particularly section 13.

I know this an old post, but THANK YOU SO MUCH! You saved me a lot of lost work! :biggrin:

---

### Post by fiddler616 on 2011-04-18
Many many thanks from me, too.

---

### Post by Rag888 on 2012-01-11
Yetiman, you da MAN!!

Thankyou so much for the solution.

I have tried EVERYTHING from Boot Repair CD to command line Boot Repair but it FAILED!

I was just going to remove Ubuntu for good, when I saw your solution and thought to give it a try and guess what, it worked!

Thanks agian.

---

### Post by oldos2er on 2012-01-12
Closed, necromancy.

---

