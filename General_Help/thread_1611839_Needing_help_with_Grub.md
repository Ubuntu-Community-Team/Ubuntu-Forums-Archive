---
title: "Needing help with Grub"
date: 2010-11-02
forum: General Help
---

### Post by Shalimar on 2010-11-02
I have Windows on my computer and decided to instal Ubuntu on my second HD, it worked perfectly on the cd but when i intalled it and tyed to ru i got this error:

GRUB Loading stage 1.5.
GRUB loading, please wait...
Error 17

I tryed to reinstal grub via pronpt but it didnt worked so i decided to take 2GB for the swap and instal Kurumin cause the grub of Kurumin i knew worked. But i just cant configure it properlly :(. Error message:

root (hd1,0)
Filesystm type is ext2fs, partition type 0x83
makeactive
chainloader +2

Error 13: Invalid or unsuported executable format

So anyone can help me either fix Ubuntu grub or configure Kurumin one?

---

### Post by Shalimar on 2010-11-02
I tryed to change the configuration fo the Kurumin Grub and now i get:

root (hd1,0)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/linux 2.6.35-22.33

Error 2: Bad file or directory type

What am i doing wrong? Is the kernel wrong? Or i need to put some boot especifications after it?

---

### Post by garvinrick4 on 2010-11-02
insert a live cd and  download this script to DESKTOP and then run the
code given in terminal: Post results to this thread will be on Desktop in file.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

gives full account of your boot files. takes about 30 seconds total to run

---

### Post by Shalimar on 2010-11-02
```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:   Kurumin Linux, Debian Etch 
                       [http://www.guiadohardware.net](http://www.guiadohardware.net) Digite seu login e 
                       senha. startx : Inicia o modo grafico configurar-video 
                       : Redetecta a placa de video /etc/init.d/kdm restart : 
                       Reinicia o gerenciador de login mcedit : Editor de 
                       texto links : Navegador web halt : Desliga o micro
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,121,279   625,121,217   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   299,808,767   299,806,720  83 Linux
/dev/sdb2         299,810,814   312,580,095    12,769,282   5 Extended
/dev/sdb5         299,821,095   308,480,129     8,659,035  82 Linux swap / Solaris
/dev/sdb6         308,480,193   312,576,704     4,096,512  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        E4D86106D860D876                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        922ca5a9-a405-4034-aef4-70b70970154f   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        e3ece307-392e-4f86-8973-076e67f10675   swap                                     
/dev/sdb6        c1d80928-14b3-4535-b325-4d3a1c3eea21   ext3       Kurumin                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: grub/core.img

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
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 922ca5a9-a405-4034-aef4-70b70970154f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 922ca5a9-a405-4034-aef4-70b70970154f
set locale_dir=($root)/boot/grub/locale
set lang=pt
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 922ca5a9-a405-4034-aef4-70b70970154f
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=922ca5a9-a405-4034-aef4-70b70970154f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 922ca5a9-a405-4034-aef4-70b70970154f
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=922ca5a9-a405-4034-aef4-70b70970154f ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 922ca5a9-a405-4034-aef4-70b70970154f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 922ca5a9-a405-4034-aef4-70b70970154f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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
UUID=922ca5a9-a405-4034-aef4-70b70970154f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=22b01796-08a8-49d8-a5d7-488a82818c9c none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 137.6GB: boot/grub/core.img
 103.2GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
    .3GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: initrd.img
    .3GB: vmlinuz

=========================== sdb6/boot/grub/menu.lst: ===========================

default 0
timeout 9
color cyan/blue white/blue
gfxmenu (hd1,5)/boot/message

title Kurumin Linux
root (hd1,5)
kernel /boot/vmlinuz-2.6.18.1-slh-up-2 ro nomce quiet apm=power-off vga=791 
initrd /boot/initrd.img-2.6.18.1-slh-up-2

title Ubuntu Linux
root (hd1,0)
kernel /boot/linux 2.6.35-22.33

title Microsoft Windows XP Professional (sda1)
root (hd0,0)
makeactive
chainloader +1

title           memtest86
root            (hd1,5)
kernel          /boot/memtest86.bin


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: filesystem table.
#
# filesystem  mountpoint  type  options  dump  pass
/dev/sdb6  /  ext3  defaults  0  1
/dev/sdb5  none  swap  sw  0  0
proc  /proc  proc  defaults  0  0
/dev/fd0 /mnt/floppy vfat users,rw,noauto 0 0
/dev/cdrom  /mnt/cdrom  iso9660  defaults,ro,user,noexec,noauto  0  0

# partições encontradas pelo instalador:
/dev/sda1 /mnt/sda1 ntfs noauto,users,exec,ro,umask=000 0 0
/dev/sdb1 /mnt/sdb1 ext3 noauto,users,exec 0 0
sys /sys sysfs noauto 0 0
/dev/pts /dev/pts devpts mode=0622 0 0
usbfs /proc/bus/usb usbfs defaults 0 0

=================== sdb6: Location of files loaded by Grub: ===================


 159.5GB: boot/grub/menu.lst
 159.5GB: boot/grub/stage2
 158.4GB: boot/initrd.img-2.6.18.1-slh-up-2
 159.5GB: boot/vmlinuz
 159.5GB: boot/vmlinuz-2.6.18.1-slh-up-2
 159.5GB: vmlinuz
```

---

### Post by s.fox on 2010-11-02
Please use code tags for large volumes of text. Thank you. :)

---

### Post by wilee-nilee on 2010-11-02
garvinrick4 will be your best help here, it may be just a matter of reloading grub2 to the mbr and booting the partition running grub2. You have installed a OS that is running grub-legacy and it has the boot now. Your other Linux is grub2.

The distro you installed does not have a solid base you might look at the wikipedia stuff.

Edit: argh and I missed the grub file in sda1.

---

### Post by garvinrick4 on 2010-11-02
Your Windows is first to get boot right: If sdb is external USB unplug: if not not to worry:
Put in Ubuntu live cd (install cd) and choose Try Ubuntu:
Open a terminal and run this code:
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```will say errors ignore we just need mbr.
###Or if you have a Windows xp cd you can run this:
                      XP fix boot from [Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
How to restore the Windows install grub  XP bootloader For this you will need your Windows install grub XP installation CD. Boot into it now. You will get to a part where it asks if you want to repair or recover. To do so, press "r". If prompted, enter your Windows install grub XP administrator password. This will leave you at at a command line, so type in the following two commands: 

```
 fixboot 
``` ```
fixmbr 
``````
 exit 
``` Either which way you chose Windows is now bootable in sda: Now make sure sda is the first in boot order(BIOS) and sdb is second for now. Boot into Windows. Now set sdb to boot first of course if USB external plug in. Put in Ubuntu live cd (install cd and choose tryubuntu) open a terminal:copy and paste
```
sudo mkdir /media/root
``````
sudo mount /dev/sdb1 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sdb
``````
sudo umount /media/root
``` (not a typo umount)
Now take Cd out and reboot into sdb Ubuntu and run:
```
sudo update-grub
```If sdb boots first will be able to boot all Operating Systems installed.
If sda boots first just Windows will boot: (No linux in sda to look for grub)
So use you BIOS to boot with sda or sdb
Hopefully will get all of legacy out of grub config. grub2 and grub legacy do not work well together, you should be Ok now.

---

### Post by Shalimar on 2010-11-03
It worked thanks, but now i have to keep pressing F10 every boot but besides that it is good. :)

---

### Post by garvinrick4 on 2010-11-03
> **Shalimar said:**
> It worked thanks, but now i have to keep pressing F10 every boot but besides that it is good. :) Or you can set sdb to boot first in BIOS at every boot and will show all installs in all drives thru grub2. There is a spot in BIOS to set boot as default and a spot to as you do F10 to select on at every boot. Find the way to start sdb before sda as default, it is there. Happy code worked and your machine is up and running. Enjoy your Ubuntu.

---

