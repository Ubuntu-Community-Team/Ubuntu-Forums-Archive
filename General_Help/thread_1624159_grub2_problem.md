---
title: "grub2 problem"
date: 2010-11-17
forum: General Help
---

### Post by adv88 on 2010-11-17
Hello guys,
I recently installed backtrack4 R1 on my laptop and I have windows 7 already installed.
I am relatively new to linux, but I used backtrack to listen to network packets and study the TCP protocol. (I am a telecommunication student)

Anyway, everything worked fine and installed correctly.

I wanted to customize the GRUB menu so I installed grub2.
The problem is that the laptop won't boot again. The grub command line shows at startup.
I could successfully load the Windows7 (manually from the command line),
and some linux kernel which I don't know how to use it ( because I am not familiar with linux)

Anyway, my problem is that I don't know what's wrong and where to start and fix it.
It might be the configuration files... I would really appreciate any help!

---

### Post by drs305 on 2010-11-17
adv88,

Welcome to the Ubuntu forums.  :-)

Boot the LiveCD and go to the following site. Download the boot info script and then post the contents of the RESULTS.txt file the script generates.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

The script will give us a lot of information regarding your boot status that will help us troubleshoot your problem.

---

### Post by adv88 on 2010-11-17
Hello,
the following is the result of the command line. Thank you for your help

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 1.96 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 PwnSauce
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x029534c0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   930,878,349   930,468,750   7 HPFS/NTFS
/dev/sda3         950,005,760   976,771,071    26,765,312   7 HPFS/NTFS
/dev/sda4         930,886,425   950,003,774    19,117,350   5 Extended
/dev/sda5         930,886,488   950,003,774    19,117,287  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1AAC172CAC1701C5                       ntfs       SYSTEM                        
/dev/sda2        C834E27934E26A40                       ntfs                                     
/dev/sda3        E040167040164E22                       ntfs       RECOVERY                      
/dev/sda5        b4bd175f-f0b2-4bbf-b045-31f5932294ec   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd0        /media/cdrom0            iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /root/aaa                ext3       (rw)


=========================== sda5/boot/grub/menu.lst: ===========================

# By default, boot the first entry.
default 0

# Boot automatically after 30 secs.
timeout 30

vga=0x317image=/boot/grub/bt4.xpm.gz


title                Start BackTrack FrameBuffer (1024x768)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x317
initrd                /boot/initrd.gz

title                Start BackTrack FrameBuffer (800x600)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x314
initrd                /boot/initrd800.gz

title                Start BackTrack Forensics (no swap)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317
initrd                /boot/initrdfr.gz

title                Start BackTrack in Safe Graphical Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper xforcevesa rw quiet 
initrd                /boot/initrd.gz

title                Start Persistent Live CD
kernel                /boot/vmlinuz BOOT=casper boot=casper persistent rw quiet 
initrd                /boot/initrd.gz

title                Start BackTrack in Text Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent textonly rw quiet
initrd                /boot/initrd.gz

title                Start BackTrack Graphical Mode from RAM
kernel                /boot/vmlinuz BOOT=casper boot=casper toram nopersistent rw quiet 
initrd                /boot/initrd.gz

title                Memory Test
kernel                /boot/memtest86+.bin

title                Boot the First Hard Disk
root                (hd0)
chainloader +1
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
# kopt=root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a76c7835-eb6f-459f-a891-496f16bc00eb

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

vga=0x317image=a76c7835-eb6f-459f-a891-496f16bc00eb/boot/grub/vga=0x317.xpm.gz

title        Ubuntu 8.10, kernel 2.6.34
uuid        a76c7835-eb6f-459f-a891-496f16bc00eb
kernel        /boot/vmlinuz-2.6.34 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro vga=0x317 
initrd        /boot/initrd.img-2.6.34
quiet

title        Ubuntu 8.10, kernel 2.6.34 (recovery mode)
uuid        a76c7835-eb6f-459f-a891-496f16bc00eb
kernel        /boot/vmlinuz-2.6.34 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro  single
initrd        /boot/initrd.img-2.6.34

title        Ubuntu 8.10, memtest86+
uuid        a76c7835-eb6f-459f-a891-496f16bc00eb
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=b4bd175f-f0b2-4bbf-b045-31f5932294ec /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 478.0GB: boot/grub/core.img
 478.1GB: boot/grub/menu.lst
 478.3GB: boot/initrd.img-2.6.34
 478.1GB: boot/vmlinuz-2.6.34
 478.3GB: initrd.img
 478.1GB: vmlinuz


```

---

### Post by adv88 on 2010-11-17
Sorry for double posting, but I wanted to include the old backup file I took from the legacy version, as it seems the new version modified the file:
Thanks again!

```

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
timeout        20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

color cyan/blue white/blue

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
# kopt=root=UUID=b4bd175f-f0b2-4bbf-b045-31f5932294ec ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b4bd175f-f0b2-4bbf-b045-31f5932294ec

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

splashimage=b4bd175f-f0b2-4bbf-b045-31f5932294ec/boot/grub/bt4.xpm.gz

title        Ubuntu 8.10, kernel 2.6.34
uuid        b4bd175f-f0b2-4bbf-b045-31f5932294ec
kernel        /boot/vmlinuz-2.6.34 root=UUID=b4bd175f-f0b2-4bbf-b045-31f5932294ec ro quiet splash 
initrd        /boot/initrd.img-2.6.34
quiet

title        Ubuntu 8.10, kernel 2.6.34 (recovery mode)
uuid        b4bd175f-f0b2-4bbf-b045-31f5932294ec
kernel        /boot/vmlinuz-2.6.34 root=UUID=b4bd175f-f0b2-4bbf-b045-31f5932294ec ro  single
initrd        /boot/initrd.img-2.6.34

title        Ubuntu 8.10, memtest86+
uuid        b4bd175f-f0b2-4bbf-b045-31f5932294ec
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows 7
root        (hd0,0)
savedefault
makeactive
chainloader    +1


```

---

### Post by drs305 on 2010-11-17
You appear to have a mixture of Grub legacy and Grub 2.

I can't comment definitively since I've done my best to forget Grub legacy and have never used Backtrack.

I do see one likely problem however. In several places in your menu.lst, there is the following:
> 
**splashimage=b4bd175f-f0b2-4bbf-b045-31f5932294ec/boot/grub/bt4.xpm.gz**



Those may be the correct way to designate them but I don't know. There is also this line just before the first menu item:
> 
**vga=0x317image=/boot/grub/bt4.xpm.gz**

It looks to me like two lines got merged and possibly placed in the wrong place, but as I said I can't tell you definitively how your setup is supposed to look.

You can edit your files by mounting the partition via the LiveCD and editing the file, should you determine how/if the line(s) need changing:
```
sudo mount /dev/sda5 /mnt
gksu gedit /mnt/boot/grub/menu.lst
```

For a normal Ubuntu installation, I would suggest you use 'chroot' to purge any grub or grub2 (grub-pc) packages and reinstall grub 2 (grub-pc) from the LiveCD. 

I'll provide you with the link, but someone else should probably advise you whether a Backtrack install works the same was a Ubuntu.

[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by adv88 on 2010-11-17
Hello, and thanks for your help!
What you have wrote was very informative.

I have tried both what you have said. None of them made the grub work again, because it seems there is a problem with the configuration file.
(btw, it's a very nice link you have gave me about reinstalling  grub while on a live cd)

So to circumvent the problem, I reinstalled backtrack, and the boot loader was autoconfigured to take all boots by default.

I wasn't looking for that answer( reinstall backtrack ), but I'm ok with it for now :)

---

