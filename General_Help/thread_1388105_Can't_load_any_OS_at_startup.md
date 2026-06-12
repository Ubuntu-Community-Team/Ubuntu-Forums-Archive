---
title: "Can't load any OS at startup"
date: 2010-01-22
forum: General Help
---

### Post by Krzysztow on 2010-01-22
Hello,

I have a problem with loading. When I turn on the computer, the Grub2 shows up and asks me to choose what OS to start. And from today on, whatever I choose, I end up with nothing. When Linux (Ubuntu) is chosen, then the blinking logo is shown (depicting it's loading) and after some time I can only see a black screen. In case when Windows is chosen, the black screen appears immediately. 
Being frankly, I have no idea what could happen and how to solve this issue. Kive cd works fine but don't know what I could do with it. A week ago I changed a booting order in my BIOS, so that GRUB2  is loading very fast now. Then I also chose:

sudo dkpg-reconfigure grub-pc
and selected the disk that had my boot partition. 

For a week or so it worked fine. Now I have this problem and need badly some help - it is a examination time at my faculty and many (or the most) of the data is on the computer -> now I cannot back it up, cause don't have that much disk space.

Please, help me. Thank You in advance.

My configuration:
Grub 2
Ubuntu Karmic 9.10 and Win XP
[FONT=Czcionka tekstu podstawowego][SIZE=3]AMD    Athlon X2 4800+ 2x2,5GHz
[/SIZE][/FONT][FONT=Czcionka tekstu podstawowego][SIZE=3]Asus    M2N-SLI Deluxe[/SIZE][/FONT]

---

### Post by Krzysztow on 2010-01-22
Moreover, when I try Linux recocvery mode, the Reecovery Menu appears, however it is not usable. When I press the arrowkey, letters are painted on it (like in command line). It is then written:

"/dev/sd8: 2858 files, 26954/1402331 clusters
General error mounting filesystems
A maintenance shell will now be starrted 
CONTROL-D will terminate this shell and re-try
root@krzys-desktop:~#

When, for instance I write grub (recovery menu says it will update grub bootloader), then I get:
"the program grub is currently not installed. You can install it by typing: apt-get install grub.

---

### Post by lidex on 2010-01-22
So you have more than one HDD? What is installed on each?

Boot into your LiveCD environment and run this command (in a terminal):
```
sudo fdisk -l
```
Post the output back here.
Also run this command;
```
sudo update-grub
```
Reboot

---

### Post by Krzysztow on 2010-01-23
Thank You so much for being interested.

As soon as I get back from work to my place, I'll do it and post the output.

Hope the problem is solvable. Thanks once more!

---

### Post by Krzysztow on 2010-01-23
So yes, I have two HDD drives. First (sda) is with Windows XP and second sdb with Ubuntu Karmic.

sudo fdisk -l output:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4c494c48

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       38912   292077765    f  W95 Ext'd (LBA)
/dev/sda5            2551       15298   102398278+   7  HPFS/NTFS
/dev/sda6           15299       17848    20482843+   7  HPFS/NTFS
/dev/sda7           17849       30596   102398278+   7  HPFS/NTFS
/dev/sda8           30597       38912    66798238+   7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002c21d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4863    39062016   83  Linux
/dev/sdb2            4864       30401   205133985    5  Extended
/dev/sdb5            4864        5361     4000153+  82  Linux swap / Solaris
/dev/sdb6            5362       15087    78124063+  83  Linux
/dev/sdb7           15088       24813    78124063+  83  Linux
/dev/sdb8           24814       30401    44885578+   b  W95 FAT32

and sudo update-grub:
grub-probe: error: cannot find a device for /.


Thank You for help, really!

---

### Post by lidex on 2010-01-23
Can you post the contents of /boot/grub/device.map?

---

### Post by Krzysztow on 2010-01-24
After going to my Linux partition and writting "sudo gedit /media/Linux/boot/device.map" I got file that showed nothing. Hopefully this is the problem and is easy to solve. Thank You.

---

### Post by Krzysztow on 2010-01-24
Sorry for mistakenly written wrong location. I opened my Linux partition and wrote sudo gedit /boot/grub/device.map and got nothing. In the folder "boot/grub/", there is only grubenv file. 
So I suppose there should be one and this is a problem. I assure You, I haven't deleted it, because recently I haven't played with linux - just used it for working.
I tried to do, as is written in [http://www.gnu.org/software/grub/manual/html_node/Device-map.html](http://www.gnu.org/software/grub/manual/html_node/Device-map.html), however I get a message:

The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub
grub: command not found

I don't know if I can install grub being on Live-cd, so haven't done it and am waiting for Your advice. Thanks.
------------
However I have grub.old folder in /boot one. The device.map there gives the following output:
(hd0)    /dev/sda
(hd1)    /dev/sdb
I believe this grub.old folder was created when I updated grub to version 2 (in fact 1.97 or so) about two moths ago.

---

### Post by Krzysztow on 2010-01-25
If that is of any help I did as is written in [http://ubuntuforums.org/showthread.php?t=1368745](http://ubuntuforums.org/showthread.php?t=1368745)  #5. What I get is below:

```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=5f3e10e7-a976-4507-99de-2af29318a68f)/boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4c494c48

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750   625,121,279   584,155,530   f W95 Ext d (LBA)
/dev/sda5          40,965,813   245,762,369   204,796,557   7 HPFS/NTFS
/dev/sda6         245,762,433   286,728,119    40,965,687   7 HPFS/NTFS
/dev/sda7         286,728,183   491,524,739   204,796,557   7 HPFS/NTFS
/dev/sda8         491,524,803   625,121,279   133,596,477   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002c21d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,124,094    78,124,032  83 Linux
/dev/sdb2          78,124,095   488,392,064   410,267,970   5 Extended
/dev/sdb5          78,124,158    86,124,464     8,000,307  82 Linux swap / Solaris
/dev/sdb6          86,124,528   242,372,654   156,248,127  83 Linux
/dev/sdb7         242,372,718   398,620,844   156,248,127  83 Linux
/dev/sdb8         398,620,908   488,392,064    89,771,157   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="EC80E3DE80E3ACF0" LABEL="Windows XP" TYPE="ntfs" 
/dev/sda5: UUID="EABC023ABC0201B5" LABEL="Program Files" TYPE="ntfs" 
/dev/sda6: UUID="CC0028450028393A" TYPE="ntfs" 
/dev/sda7: UUID="6CDC2B8ADC2B4E20" LABEL="Windows 7" TYPE="ntfs" 
/dev/sda8: UUID="28C4B914C4B8E4EA" LABEL="Local Disk" TYPE="ntfs" 
/dev/sdb1: LABEL="Linux" UUID="5f3e10e7-a976-4507-99de-2af29318a68f" TYPE="ext4" 
/dev/sdb5: UUID="cf632651-b475-4c5c-81a9-0be8263cb00d" TYPE="swap" 
/dev/sdb6: LABEL="firstDisk" UUID="1b7f9a1f-db11-45d4-9665-c07ba200201c" TYPE="ext4" 
/dev/sdb7: LABEL="secondDisk" UUID="7d4572ee-4f61-4c3f-ba78-8cbe105b0347" TYPE="ext4" 
/dev/sdb8: LABEL="COMMON DISK" UUID="E1D3-48F7" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/Linux type ext4 (rw,nosuid,nodev,uhelper=devkit)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 

=========================== sdb1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=5f3e10e7-a976-4507-99de-2af29318a68f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5f3e10e7-a976-4507-99de-2af29318a68f

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        5f3e10e7-a976-4507-99de-2af29318a68f
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=5f3e10e7-a976-4507-99de-2af29318a68f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        5f3e10e7-a976-4507-99de-2af29318a68f
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=5f3e10e7-a976-4507-99de-2af29318a68f ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        5f3e10e7-a976-4507-99de-2af29318a68f
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=5f3e10e7-a976-4507-99de-2af29318a68f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        5f3e10e7-a976-4507-99de-2af29318a68f
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=5f3e10e7-a976-4507-99de-2af29318a68f ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        5f3e10e7-a976-4507-99de-2af29318a68f
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=5f3e10e7-a976-4507-99de-2af29318a68f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        5f3e10e7-a976-4507-99de-2af29318a68f
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=5f3e10e7-a976-4507-99de-2af29318a68f ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        5f3e10e7-a976-4507-99de-2af29318a68f
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        5f3e10e7-a976-4507-99de-2af29318a68f
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 5f3e10e7-a976-4507-99de-2af29318a68f
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 5f3e10e7-a976-4507-99de-2af29318a68f
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=5f3e10e7-a976-4507-99de-2af29318a68f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 5f3e10e7-a976-4507-99de-2af29318a68f
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=5f3e10e7-a976-4507-99de-2af29318a68f ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 5f3e10e7-a976-4507-99de-2af29318a68f
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=5f3e10e7-a976-4507-99de-2af29318a68f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 5f3e10e7-a976-4507-99de-2af29318a68f
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=5f3e10e7-a976-4507-99de-2af29318a68f ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 5f3e10e7-a976-4507-99de-2af29318a68f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=5f3e10e7-a976-4507-99de-2af29318a68f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 5f3e10e7-a976-4507-99de-2af29318a68f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=5f3e10e7-a976-4507-99de-2af29318a68f ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set ec80e3de80e3acf0
    chainloader +1
}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=5f3e10e7-a976-4507-99de-2af29318a68f /               ext4    errors=remount-ro 0       1
# /fatDisk was on /dev/sdb8 during installation
UUID=E1D3-48F7  /fatDisk        vfat    utf8,umask=007,gid=46 0       1
# /firstDisk was on /dev/sdb6 during installation
UUID=1b7f9a1f-db11-45d4-9665-c07ba200201c /firstDisk      ext4    defaults        0       2
# /secondDisk was on /dev/sdb7 during installation
UUID=7d4572ee-4f61-4c3f-ba78-8cbe105b0347 /secondDisk     ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=cf632651-b475-4c5c-81a9-0be8263cb00d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

```Now the device.map file is showing:


```

(hd0)    /dev/sda
(hd1)    /dev/sdb

```And I have my grub files back. However still, after grub2 prompt, no OS loads.


---
I reinstalled GRUB2 using steps described in [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")
This didn't help much. However after some playing around (being logged with live cd) I noticed, that anytime I wanted to edit (with gedit) grub.conf (maybe even any text file) I got an error that (I don't remember exactly what was writted) dsub couldn't read the file (dsub was mentioned for sure). So looking on some forums, I found that people had this error and had to reinstall hal completely. I did it and then, my Ubuntu started, however only in bash mode. I think, there was written that removing hal would also affect gnome package, so probably this is the case. So far I couldn't recover gnome package, but both OS'es load (success). Hope the mentioned inconvenience will be overcome in the nearest future. 

I think the problem may be ticked as solved, since the problem now is not well described by the topic. Or maybe case should be firstly finished?

Anyway, thank You lidex for help and Your patience.

---

### Post by lidex on 2010-01-25
Nice work - you'd make a good detective. So you are coming to the grub prompt now, correct? Looks like grub> ?

---

### Post by Krzysztow on 2010-01-25
I even can boot to Ubuntu, but only to the bash mode. I provide login and password and it's ok. I just coudln't run desktop envirnment. But I also couldn't dwell on that - will try in next days, since I have some dues for tommorow and Wednesday. At least windwos is working, so I can complete some tasks. 
If You have some ideas, please share them. Otherwise don't waste Your time now, as long as I can't provide more specific information. When I catch up with the things I will try again and I will be very glad if You could help me.

Thank You so much! Best regards,
Krzysztof.

---

### Post by gimcrack on 2010-01-25
The menu grub is nice, but I have several SATA HDD's. Instead of rewriting grub all the time. I press F12 to my bio's boot menu. I click on which OS I like to boot in to.

So if you can't fix grub or get tired editing it, try the F12 button when rebooting to get into the bio's boot menu.

---

### Post by Krzysztow on 2010-01-25
OK, I couldn't help myself. I tried once again and guess what... this message is being written from gnome desktop :D What I had to do now was just to install hal package again ```
 sudo apt-get install hal 
``` and (not sure if was needed) gnome-device-manager  ```
 sudo apt-get install gnome-device-manager 
```. The latter one was advised while installing hal. Then  ```
 sudo apt-get install uuntu-desktop 
``` and all is fine.

Thanks to all of You who helped me, especially Lidex. Without Your tips I would still be having no system at all.

---

