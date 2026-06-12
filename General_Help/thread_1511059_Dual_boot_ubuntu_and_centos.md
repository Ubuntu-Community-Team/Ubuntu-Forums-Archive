---
title: "Dual boot ubuntu and centos"
date: 2010-06-16
forum: General Help
---

### Post by babyboi on 2010-06-16
Hello please i am trying to dual boot ubuntu and centos. I installed centos first and ubuntu second. I have ubuntus grub 2 loaded on start up but it does not contain centos in the menu.

I have also tried running the sudo update-grub. it shows the following 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-21-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found CentOS release 5.5 (Final) on /dev/sda5
done

But on reboot I still dont have centos in the menu. 

please help guys. how do i include centos in the menu and have it bootable?

**roy@labstation:~$ sudo fdisk -l**

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x80000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14        6387    51199155   83  Linux
/dev/sda3            6388       12761    51199155   83  Linux
/dev/sda4           12762       30394   141637072+   5  Extended
/dev/sda5           12762       14036    10241406   83  Linux
/dev/sda6           14037       14546     4096543+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf93556d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29172   234315776   83  Linux
/dev/sdb2           29172       30395     9822209    5  Extended
/dev/sdb5           29172       30395     9822208   82  Linux swap / Solaris

---

### Post by oldfred on 2010-06-16
Welcome to the forums. 

It says it found it so it should be in the menu on reboot.

With multiple systems I use this debugging boot issue tool just to track what is where and document the system in case I break it and want to go back.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

---

### Post by babyboi on 2010-06-16
Thanks for the reply oldfred. here is the result. 

roy@labstation:~$ cat RESULTS.txt
```
                Boot Info Script 0.55    dated February 15th, 2010

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:
    Operating System:
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:
    Operating System:
    Boot files/dirs:

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:
    Operating System:
    Boot files/dirs:

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:
    Operating System:  CentOS release 5.5 (Final)
                       Kernel on an
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       208,844       208,782  83 Linux
/dev/sda2             208,845   102,607,154   102,398,310  83 Linux
/dev/sda3         102,607,155   205,005,464   102,398,310  83 Linux
/dev/sda4         205,005,465   488,279,609   283,274,145   5 Extended
/dev/sda5         205,005,528   225,488,339    20,482,812  83 Linux
/dev/sda6         225,488,403   233,681,489     8,193,087  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   468,633,599   468,631,552  83 Linux
/dev/sdb2         468,635,646   488,280,063    19,644,418   5 Extended
/dev/sdb5         468,635,648   488,280,063    19,644,416  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        ec32db33-4e61-4cf0-ab7a-c1ad31fa1f67   ext3       /boot
/dev/sda2        43a6a708-2359-48e1-959f-3ae653f8fe42   ext3       /opt
/dev/sda3        7d152f95-3d5c-428f-ae31-8cb6c2356f23   ext3       /home1
/dev/sda4: PTTYPE="dos"
/dev/sda5        7c4f6c9f-1b31-48a3-827c-4d740c917347   ext3       /
/dev/sda6                                               swap       SWAP-sda6
/dev/sda: PTTYPE="dos"
/dev/sdb1        a54a7659-de88-4be2-b0d0-cf6cb9bdb5e4   ext4
/dev/sdb2: PTTYPE="dos"
/dev/sdb5        cf1f63f7-6a1e-41fb-805f-0f8964cce169   swap
/dev/sdb: PTTYPE="dos"

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


============================= sda1/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/sda5
#          initrd /initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu
title CentOS (2.6.18-194.3.1.el5PAE)
        root (hd0,0)
        kernel /vmlinuz-2.6.18-194.3.1.el5PAE ro root=LABEL=/
        initrd /initrd-2.6.18-194.3.1.el5PAE.img
title CentOS (2.6.18-194.el5PAE)
        root (hd0,0)
        kernel /vmlinuz-2.6.18-194.el5PAE ro root=LABEL=/
        initrd /initrd-2.6.18-194.el5PAE.img

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/grub.conf
    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd-2.6.18-194.3.1.el5PAE.img
    .0GB: initrd-2.6.18-194.el5PAE.img
    .0GB: vmlinuz-2.6.18-194.3.1.el5PAE
    .0GB: vmlinuz-2.6.18-194.el5PAE

=============================== sda5/etc/fstab: ===============================

LABEL=/                 /                       ext3    defaults        1 1
LABEL=/home1            /home                   ext3    defaults        1 2
LABEL=/opt              /opt                    ext3    defaults        1 2
LABEL=/boot             /boot                   ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
LABEL=SWAP-sda6         swap                    swap    defaults        0 0

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set a54a7659-de88-4be2-b0d0-cf6cb9bdb5e4
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set a54a7659-de88-4be2-b0d0-cf6cb9bdb5e4
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd1,1)'
        search --no-floppy --fs-uuid --set a54a7659-de88-4be2-b0d0-cf6cb9bdb5e4
        linux   /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=a54a7659-de88-4be2-b0d0-cf6cb9bdb5e4 ro   quiet
        initrd  /boot/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd1,1)'
        search --no-floppy --fs-uuid --set a54a7659-de88-4be2-b0d0-cf6cb9bdb5e4
        echo    'Loading Linux 2.6.32-21-generic-pae ...'
        linux   /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=a54a7659-de88-4be2-b0d0-cf6cb9bdb5e4 ro single
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.32-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        insmod ext2
        set root='(hd1,1)'
        search --no-floppy --fs-uuid --set a54a7659-de88-4be2-b0d0-cf6cb9bdb5e4
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod ext2
        set root='(hd1,1)'
        search --no-floppy --fs-uuid --set a54a7659-de88-4be2-b0d0-cf6cb9bdb5e4
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=a54a7659-de88-4be2-b0d0-cf6cb9bdb5e4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=cf1f63f7-6a1e-41fb-805f-0f8964cce169 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   8.7GB: boot/grub/core.img
  34.5GB: boot/grub/grub.cfg
   8.7GB: boot/initrd.img-2.6.32-21-generic-pae
   8.7GB: boot/vmlinuz-2.6.32-21-generic-pae
   8.7GB: initrd.img
   8.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda6

00000000  00 78 30 30 00 78 30 30  00 78 30 30 00 78 30 30  |.x00.x00.x00.x00|
*
00000200
```

---

### Post by oldfred on 2010-06-16
I would install grub2 for Ubuntu to sdb, I prefer to have to boot loader on the same drive as the install. I would probably let centos install its boot loader to sda. At least then you can switch in BIOS to boot either. I do not know if that will fix it but then we could manually add an entry to 40_custom or add a chainboot entry to 40_custom. 

I do not know why the output says it is found but then does not add it to your grbu.cfg.

(The script or grub2 has a issue with the newest grub2 and reports drive incorrectly so the sda that says same drive is not correct.)

---

### Post by babyboi on 2010-06-16
> **oldfred said:**
>  I prefer to have to boot loader on the same drive as the install.

I installed another Ubuntu on the free space on sda and installed grub in sda but still had the same problem. No centos in menu. But it found the older Ubuntu in sdb :(

An other suggestion?

---

### Post by oldfred on 2010-06-16
I was hoping to chainboot as the entry is a lot easier and you do not have to run update grub in Ubuntu everytime you get a new kernel in Centos, but you do get two levels of menus.

You can manually add a centos entry but have to convert from grub to grub2 style.

After supper I will see if I can figure out an entry.

---

### Post by oldfred on 2010-06-16
I do not know of the label entry works from grub2.

title "CentOS (2.6.18-194.3.1.el5PAE)" {
        set root = (hd0,1)
        kernel /vmlinuz-2.6.18-194.3.1.el5PAE ro root=LABEL=/
        initrd /initrd-2.6.18-194.3.1.el5PAE.img
}

Note that partitions are numbered differently in grub2 and the set root must be in the grub2 numbering not centOS numbering.

---

### Post by babyboi on 2010-06-17
Please what file do I add this entry to?

---

### Post by oldfred on 2010-06-17
Copy to 40_custom and run sudo update-grub.

gksudo gedit /etc/grub.d/40_custom

More info:
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by babyboi on 2010-06-17
That did not work. What does the 1 in set root = (hd0,1) represent? partition number?

I also tried changing the 1 with other existing partitions but still no luck.

---

### Post by oldfred on 2010-06-17
Grub2 starts at 1 where old grub started numbering partitions at 0.

/dev/sda1        ec32db33-4e61-4cf0-ab7a-c1ad31fa1f67   ext3       /boot

Is that not your boot partition for CentOS? Which is hd0,1

If you had installed the CentOS boot loader to the MBR or the PBR we could chainboot. But the entry should work it that is your boot partition. OR did you overwrite it with the new Ubuntu install?

---

### Post by babyboi on 2010-06-17
Can you suggest how to go about a fresh install, I dont mind starting afresh. 

I have 2 250GB hdds and I want to dual boot centos and ubuntu. i dont care how the partitioning goes. they can go on either drive or both on same hard drive.  Could u just suggest how I go about it e.g. 

install centos to ist 
/boot sda
/     sda1
/swap sda2

install ubuntu to 2nd sda 
/boot sdb
/     sdb1
/swap sdb2
install grub2 to sda

---

### Post by oldfred on 2010-06-17
Unless you have an old computer I would not create separate /boot for Ubuntu. Do not know, some installs require separate /boot, does CentOS? I would install Centos boot loader to sda and grub2 from Ubuntu to sdb and set BIOS to boot sdb.

If you want to share data between them, you should also create /data partition(s) so you can mount and use the same data in both. You should not share /home as the different versions of application may not write compatible data.

You want to have grub or grub2 installed to the same drive as the install.

---

### Post by babyboi on 2010-06-19
Oldfred, thanks for all the replies. They were all definitely useful. I started all over and installed in this order and it worked. 

Installed CentOS first and Ubuntu second. 

Installed CentOS with 
/ 50gb on sda
/swap 10gb on sda
/data 200gb on sdb

installed ubuntu with 
/ 50gb on sda
/swap 10gb on sda (shared with centos) 
/data 200gb on sdb (shared with centos)

It even found CentOS during installation and was on the menu screen by default with out me having to modify anything. Still yet to figure out why it did not work previously but I guess there is a significance of setting a /boot when installing. Will check it up.

---

### Post by oldfred on 2010-06-19
Sometimes we spend hours even days fixing things (maybe so we understand it better) when a reinstall is the quicker/easier solution.

Glad you got it working.

I boot from sdc and I found that my sda drive become hd1 (not hd0 as expected) in the initial boot of a sda partition. Was that perhaps the problem with the stanza I originally gave you?

---

