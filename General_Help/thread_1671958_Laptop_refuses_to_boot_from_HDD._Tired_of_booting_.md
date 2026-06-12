---
title: "Laptop refuses to boot from HDD. Tired of booting from LiveCD (please work this time)"
date: 2011-01-20
forum: General Help
---

### Post by theITgirl on 2011-01-20
Okay, so for the past couple of weeks, I have been booting from an Ubuntu LiveCD. Here's why:

When I boot my computer (emachines E528 laptop), it gets to the BIOS  loading screen (the one where you have the option to press a function  key to get to the BIOS settings), then it goes to a black screen and  looks like it is going to load GRUB, but instead of loading GRUB, the  computer reboots. It does this endlessly, unless I insert a LiveCD. So,  it's not the BIOS. That's good. When the Mint GUI (Linux Mint was the  LiveCD I was originally using as I just happened to have it on hand)  loaded for the first time, I checked all of the hard drive partitions  and they all seemed to load fine. So, it's not a mechanical problem with  the HDD. That's good.

At this point, I figured the MBR had become corrupted somehow. Now I  wasn't really sure exactly where the MBR was, or how it all worked, but I  was pretty sure that if I just reinstalled GRUB, everything would be  hunky dorey. Unfortunately, I hit a road block when trying to install  GRUB. That's not good. I am trying to follow the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=224351"), but I get the following error:

```
grub> find /boot/grub/stage1

Error 15: File not found
```

So then I tried following the instructions [here]("http://ubuntuforums.org/showpost.php?p=1361177&postcount=26"),  but I don't know how to tell which drive is sda1, sda2, etc. I'm  guessing there's some terminal command to figure it out, but I don't  know it and Google was less than helpful. I feel like something that  basic should be easy to find, but I digress.

At this point, I am getting very close to backing up everything and  reinstalling everything. Only problem with that is that I am not sure  how to access the files on my Ubuntu partition as they are encrypted (I  wrote down the key when I started it up, I just don't know how to bring  up a prompt that will let me enter the key). I really don't want to  reinstall and set everything back up, but if I have to I will.

So, I guess I just need to know how to tell which partition is  associated with which sda#, or how to access the files in my encrypted  Ubuntu home folder, or (hopefully) someone who can tell exactly what's  going on from why I have posted and can give me instructions for fixing  my problem.

Also, here's a breakdown of how my hard drive is partitioned. Not sure why, but I thought this might be helpful: [linky]("http://i.imgur.com/FvvDz.jpg").

**TLDR: **How do I tell which partition is associated to which sda#?  How do I open my encrypted home folder from my Ubuntu partition? After  reading my whole post, is there any further insight you could offer that  I may have overlooked?

---

### Post by b0b138 on 2011-01-20
post the output of sudo fdisk -l

---

### Post by Ad@m on 2011-01-20
So you are stuck at the first step of this [http://ubuntuforums.org/showpost.php?p=1361177&postcount=26](http://ubuntuforums.org/showpost.php?p=1361177&postcount=26)

To find out which partition is root or run the command 

sudo fdisk -l

and paste the output here so we can have a look.

---

### Post by theITgirl on 2011-01-20
> **b0b138 said:**
> post the output of sudo fdisk -l


```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb54e9766

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1698    13631488   27  Unknown
/dev/sda2   *        1698        1710      102400    7  HPFS/NTFS
/dev/sda3            1710       13902    97930225+   7  HPFS/NTFS
/dev/sda4           13902       30402   132533249    5  Extended
/dev/sda5           13902       29726   127107072   83  Linux
/dev/sda6           29726       30402     5425152   82  Linux swap / Solaris

Disk /dev/sdb: 4040 MB, 4040724480 bytes
125 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c11b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1018     3944719    c  W95 FAT32 (LBA)


```

---

### Post by theITgirl on 2011-01-20
I'm guessing I would need to mount sda2? 

I'm still pretty new to the whole mounting concept in Linux. I have been reading [TLCL]("http://linuxcommand.org/tlcl.php"), but I haven't gotten to that section yet.[URL="http://linuxcommand.org/tlcl.php"]
[/URL]

---

### Post by garvinrick4 on 2011-01-20
Linux is sda5 
Windows is sda3
Looks like a boot partition sda2
If so have to mount the boot partition and linux partition to install grub
What version of Windows are you using? 7

---

### Post by garvinrick4 on 2011-01-20
In your Live CD copy and paste these in one at a time.

```
sudo mkdir /media/boot
```
```
sudo mkdir /media/root
```
```
sudo mount /dev/sda2 /media/boot
```
```
sudo mount /dev/sda5 /media/root
```
```
sudo grub-install --recheck --root-directory=/media/root /dev/sda
```
```
sudo umount /media/boot
```
```
sudo umount /media/root
```
```
sudo reboot
```
Now in Ubuntu on hard drive:
```
sudo update-grub
```

---

### Post by theITgirl on 2011-01-20
> **garvinrick4 said:**
> Linux is sda5 
Windows is sda3
Looks like a boot partition sda2
If so have to mount the boot partition and linux partition to install grub
What version of Windows are you using? 7

64-bit

Why would I have to mount both? 

Also, following [these instructions]("http://ubuntuforums.org/showpost.php?p=1361177&postcount=26"), does that mean I would just do the second line twice (once for each partition)? like so:

```

sudo mount -t ext3 /dev/sda2 /mnt/root
sudo mount -t ext3 /dev/sda5 /mnt/root


```

---

### Post by garvinrick4 on 2011-01-20
#I am using the /media to mount instead of /mnt because of the boot partition:
It is just easier and I know it works.
#I have a boot partition and you do have to mount the boot partition
along with the /root partition when installing grub2
#If you want to follow another instruction page using /mnt it is OK.
#I use /mnt also when no boot partition because you do not need to make a directory
and works with no boot partition for me. There are quite a few different styles of mounting
and or binding according to what you are doing and who is doing it.

---

### Post by garvinrick4 on 2011-01-20
The instructions you have are for grub-legacy the older version of grub used in 
9.04 and back. What version of Ubuntu you using? Newer ones use grub2.

---

### Post by Quackers on 2011-01-20
From the live cd desktop please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by theITgirl on 2011-01-20
> **garvinrick4 said:**
> The instructions you have are for grub-legacy the older version of grub used in 
9.04 and back. What version of Ubuntu you using? Newer ones use grub2.

I am using 10.10. Using your instructions, when I rebooted, I was brought to a grub> prompt and I wasn't sure what to do. I tried "boot" but it said that the Linux kernel needs to be running first. I was scared to try anything else.

[QUOTE=Quackers]From the live cd desktop please go to the site below and download the  boot script to your DESKTOP and then open up a terminal (Applications  > Accessories > terminal) and run
     Code:
     sudo bash ~/Desktop/boot_info_script*.sh 
This will produce a results.txt file on your desktop. Please copy  the contents of that file and paste them in your next post between CODE  tags. For CODE tags click on New Reply (not quick reply)and then click  on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)[/QUOTE]

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    27,265,023    27,262,976  27 Hidden HPFS/NTFS
/dev/sda2    *     27,265,024    27,469,823       204,800   7 HPFS/NTFS
/dev/sda3          27,469,824   223,330,274   195,860,451   7 HPFS/NTFS
/dev/sda4         223,330,302   488,396,799   265,066,498   5 Extended
/dev/sda5         223,330,304   477,544,447   254,214,144  83 Linux
/dev/sda6         477,546,496   488,396,799    10,850,304  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        066EE8D76EE8C113                       ntfs       PQSERVICE                     
/dev/sda2        10DEEA1DDEE9FB3C                       ntfs       SYSTEM RESERVED               
/dev/sda3        3ECAECBACAEC6F97                       ntfs       eMachines                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        0014f920-52f5-4f0a-a2b3-4e62adefd107   ext4                                     
/dev/sda6        66c70785-a087-4c75-a3f1-7a4ac2157fdb   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)


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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 0014f920-52f5-4f0a-a2b3-4e62adefd107
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 0014f920-52f5-4f0a-a2b3-4e62adefd107
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 0014f920-52f5-4f0a-a2b3-4e62adefd107
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=0014f920-52f5-4f0a-a2b3-4e62adefd107 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 0014f920-52f5-4f0a-a2b3-4e62adefd107
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=0014f920-52f5-4f0a-a2b3-4e62adefd107 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 0014f920-52f5-4f0a-a2b3-4e62adefd107
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=0014f920-52f5-4f0a-a2b3-4e62adefd107 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 0014f920-52f5-4f0a-a2b3-4e62adefd107
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=0014f920-52f5-4f0a-a2b3-4e62adefd107 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 0014f920-52f5-4f0a-a2b3-4e62adefd107
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0014f920-52f5-4f0a-a2b3-4e62adefd107 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 0014f920-52f5-4f0a-a2b3-4e62adefd107
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0014f920-52f5-4f0a-a2b3-4e62adefd107 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 0014f920-52f5-4f0a-a2b3-4e62adefd107
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 0014f920-52f5-4f0a-a2b3-4e62adefd107
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 066ee8d76ee8c113
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 10deea1ddee9fb3c
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=0014f920-52f5-4f0a-a2b3-4e62adefd107 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=66c70785-a087-4c75-a3f1-7a4ac2157fdb none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 157.5GB: boot/grub/core.img
 221.9GB: boot/grub/grub.cfg
 157.4GB: boot/grub/stage2
 122.9GB: boot/initrd.img-2.6.35-22-generic
 116.8GB: boot/initrd.img-2.6.35-23-generic
 228.0GB: boot/initrd.img-2.6.35-24-generic
 157.5GB: boot/vmlinuz-2.6.35-22-generic
 157.5GB: boot/vmlinuz-2.6.35-23-generic
 157.8GB: boot/vmlinuz-2.6.35-24-generic
 228.0GB: initrd.img
 116.8GB: initrd.img.old
 157.8GB: vmlinuz
 157.5GB: vmlinuz.old

```

I can't wait for the day when I can actually read and understand this output.

---

### Post by garvinrick4 on 2011-01-20
You have installed grub-legacy to the mbr of sda 
Must purge and reinstall grub2
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099") 
There is the link:
If you need more help ask.
#grub is grub legacy:
#need grub-common and grub-pc installed
#You just got confused and installed grub-legacy instead of grub2 earlier.
#need to install it in mbr: previous instructions:

---

### Post by Quackers on 2011-01-20
In the guide that garvinrick4 has linked you to, you will need to use the chroot method. You have no separate /boot partition so you will just need to mount sda5 and install grub(2) to sda
If you don't understand anything come back here for help. It is better to get it right first time :-)

---

### Post by garvinrick4 on 2011-01-20
> **Quackers said:**
> In the guide that garvinrick4 has linked you to, you will need to use the chroot method. You have no separate /boot partition so you will just need to mount sda5 and install grub(2) to sda
If you don't understand anything come back here for help. It is better to get it right first time :-)What is sda2 if not a boot partition,  look under blkid portion of bootscript? System Reserved sda2. Did you look at the link OP was using to install grub in, was grub-legacy. Lets get this right the first time.

---

### Post by garvinrick4 on 2011-01-20
Good night theITgirl Quackers will help you out, hope you get up and running soon.
Enjoy your Ubuntu.

---

### Post by Quackers on 2011-01-20
sda2 is a Windows partition with 2 boot files in it.
The only /boot partition that needs mounting when installing grub is a linux /boot partition. As the OP doesn't have one of those it won't need mounting :wink:

---

### Post by theITgirl on 2011-01-21
> **Quackers said:**
> sda2 is a Windows partition with 2 boot files in it.
The only /boot partition that needs mounting when installing grub is a linux /boot partition. As the OP doesn't have one of those it won't need mounting :wink:

So is it a problem for windows then that I installed grub legacy on sda2? Also, how do I make my pc boot from sda5 instead of sda2? or does that happen when I restore grub to sda5? trying it now and will report on what happens.

**EDIT:** Yes! It worked! Not really sure why "sudo fdisk -l" still shows sda2 as the boot partition though. What exactly is going on there. Does that just redirect to sda5 or something? Being that you said it's a Windows boot partition, that doesn't seem likely. Hm... guess it's time to do some research.

---

### Post by oldfred on 2011-01-21
New installs of Windows7 creates a (hidden in windows) 100MB windows boot partition so you can encrypt the full windows install c: and in the future systems will require something separate for gpt partitions instead of our current MBR/msdos partitions. 

If you create the NTFS partition in advance then win7 will install to that using only one partition. A windows boot partition has nothing to do with a Linux boot partition.

Lots of info but just reviewing pictures is worthwhile if you want to understand booting and windows boot process. Win7 is identical to Vista except for the new win boot partition.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by garvinrick4 on 2011-01-21
###Quackers I was Wrong about installing grub2 with Windows boot partition:
#Could use /mnt with linux /root partition to install grub to mbr without mounting windows /boot partition or I could use /media with mounting both windows/boot and /root linux partition.
#So it works using both methods with of course using /mnt being the easier and 
quicker way because do not need to make directories.
#The style I was using was just using more code than necessary when a Windows
boot partition is present.
#Anyone reading this post the best commands for using a live CD and installing grub2
to mbr are with or without Windows /boot partition: 
```
sudo mount /dev/sdXY /mnt
``` Above X being drive letter and Y being partition number.
```
sudo grub-install --root-directory=/mnt /dev/sdX
```Above X being drive letter.
```
sudo umount /mnt
```## In my previous post I used /media to mount /root and with mounting windows /boot, will work but longer method and unnecessary.

---

