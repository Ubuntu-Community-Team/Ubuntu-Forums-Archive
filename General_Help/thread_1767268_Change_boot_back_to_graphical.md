---
title: "Change boot back to graphical?"
date: 2011-05-25
forum: General Help
---

### Post by schwim on 2011-05-25
Hi there everyone,

A few upgrades ago, my boot process went from graphical to text(with the purple bg Ubuntu text and dots) and I was wondering if I could modify something to get my graphical boot process back?

---

### Post by 5149.5 on 2011-05-25
See this [link]("http://goo.gl/TKms") for grub modifications.

Edit /etc/default/grub.
```

change GRUB_CMDLINE_LINUX_DEFAULT="quiet"
to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
run sudo update-grub

```

---

### Post by wgarcia on 2011-05-25
It seems that the application that gets you the graphical boot interface (called plymouth) now is not working for your graphical card. There are some ATI and NVIDIA cards for which plymouth may fail, check which graphical you have and google around for problems and solutions for your graphical card.

---

### Post by schwim on 2011-05-25
Thanks to both of you for your help.

I attempted to change the setting in /etc/default/grub, but I don't have a file called grub at that location.  ls -la goes from devpts to halt.

Should I create a file with that setting or am I missing a lot more?  Computer boots fine, I just wanted to get the graphical boot process back.

Thanks again for your time.

---

### Post by schwim on 2011-05-26
Anyone at all?

---

### Post by wgarcia on 2011-05-26
Maybe it would be useful to know what type of graphic card you have, if you don't know it you can it by opening a terminal and entering:

lspci | grep -i vga

---

### Post by schwim on 2011-05-26
Very sorry for not providing it earlier.

> 01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)

---

### Post by wgarcia on 2011-05-26
Check this post , it is for Maverick but I think it also helps in fixing this problem for Natty. Also check the warnings in the post on reverting things if they go wrong:

[http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html](http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html)

---

### Post by timgood on 2011-05-26
If you are using Nvidia drivers download this [script]("http://www.webalice.it/bernardi82/software/fixplymouth-natty"). Make it executable by```
chmod +x fixplymouth-natty
``` and run it by ```
./fixplymouth-natty
```. Select the appropriate resolution you are running in and enter it exactly as shown. Reboot and you will have Plymouth back and running in all its glory.

---

### Post by wgarcia on 2011-05-27
This script is for grub2, and from what seems to be inferred from above there is no /etc/default/grub in this system so maybe there is still "legacy" grub?

---

### Post by schwim on 2011-05-28
Would simply installing grubpc upgrade my grub install or is it more indepth of a process than that?

---

### Post by schwim on 2011-07-01
My question unfortunately remains.

---

### Post by schwim on 2011-07-02
> **schwim said:**
> Would simply installing grubpc upgrade my grub install or is it more indepth of a process than that?
...

---

### Post by schwim on 2011-07-05
> **schwim said:**
> Would simply installing grubpc upgrade my grub install or is it more indepth of a process than that?
....

---

### Post by schwim on 2011-07-07
> **schwim said:**
> Would simply installing grubpc upgrade my grub install or is it more indepth of a process than that?
....

---

### Post by philinux on 2011-07-07
Post back the output of this.

```
apt-cache policy grub-pc
```

I assume you have activated the proprietary nvidia drivers from system>Admin>additional drivers?

---

### Post by schwim on 2011-07-07
Hi there and thanks very much for the reply:

> 
grub-pc:
  Installed: (none)
  Candidate: 1.99~rc1-13ubuntu3
  Version table:
     1.99~rc1-13ubuntu3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main i386 Packages
schwim@schwim-work:~$


apt-get shows that ndivia drivers are installed, but when I look at the additional drivers window, it states:

> 
NVIDIA accelerated graphics driver(version current) [Recommended](installed)

This driver is activated but not currently in use.


So it seems that it's installed but it's not being used.

---

### Post by philinux on 2011-07-07
> **schwim said:**
> Hi there and thanks very much for the reply:



apt-get shows that ndivia drivers are installed, but when I look at the additional drivers window, it states:



So it seems that it's installed but it's not being used.

The not activated thing appears on my install. I seem to recollect thats a bug with jockey-gtk. (the additional driver app).

If grub-pc is not installed it means you're likely booting with legacy grub I guess.
Lets see exactly whats booting your machine.
Download this script and follow the instruction in the link. Post back the results.txt file after you've run it.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by schwim on 2011-07-07
This is the output:

> 
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       128,519       128,457  de Dell Utility
/dev/sda2             129,024    31,586,303    31,457,280   7 NTFS / exFAT / HPFS
/dev/sda3    *     31,586,304   406,753,959   375,167,656   7 NTFS / exFAT / HPFS
/dev/sda4         406,765,800   625,137,344   218,371,545   5 Extended
/dev/sda5         406,765,863   616,173,074   209,407,212  83 Linux
/dev/sda6         616,173,138   625,137,344     8,964,207  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D8-0B1D                              vfat       DellUtility
/dev/sda2        80F8BD80F8BD74CE                       ntfs       RECOVERY
/dev/sda3        D076BFAB76BF9128                       ntfs       OS
/dev/sda5        f4440a05-caf7-431d-aab2-5fd3175c4a3f   ext3       
/dev/sda6        91432e22-b675-4d59-aeee-8ad4c1f0bc8d   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=f4440a05-caf7-431d-aab2-5fd3175c4a3f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f4440a05-caf7-431d-aab2-5fd3175c4a3f

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

title        Ubuntu 11.04, kernel 2.6.38-8-generic-pae
uuid        f4440a05-caf7-431d-aab2-5fd3175c4a3f
kernel        /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=f4440a05-caf7-431d-aab2-5fd3175c4a3f ro quiet splash 
initrd        /boot/initrd.img-2.6.38-8-generic-pae
quiet

title        Ubuntu 11.04, kernel 2.6.38-8-generic-pae (recovery mode)
uuid        f4440a05-caf7-431d-aab2-5fd3175c4a3f
kernel        /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=f4440a05-caf7-431d-aab2-5fd3175c4a3f ro  single
initrd        /boot/initrd.img-2.6.38-8-generic-pae

title        Ubuntu 11.04, kernel 2.6.38-8-generic
uuid        f4440a05-caf7-431d-aab2-5fd3175c4a3f
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=f4440a05-caf7-431d-aab2-5fd3175c4a3f ro quiet splash 
initrd        /boot/initrd.img-2.6.38-8-generic
quiet

title        Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid        f4440a05-caf7-431d-aab2-5fd3175c4a3f
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=f4440a05-caf7-431d-aab2-5fd3175c4a3f ro  single
initrd        /boot/initrd.img-2.6.38-8-generic

title        Ubuntu 11.04, kernel 2.6.35-28-generic
uuid        f4440a05-caf7-431d-aab2-5fd3175c4a3f
kernel        /boot/vmlinuz-2.6.35-28-generic root=UUID=f4440a05-caf7-431d-aab2-5fd3175c4a3f ro quiet splash 
initrd        /boot/initrd.img-2.6.35-28-generic
quiet

title        Ubuntu 11.04, kernel 2.6.35-28-generic (recovery mode)
uuid        f4440a05-caf7-431d-aab2-5fd3175c4a3f
kernel        /boot/vmlinuz-2.6.35-28-generic root=UUID=f4440a05-caf7-431d-aab2-5fd3175c4a3f ro  single
initrd        /boot/initrd.img-2.6.35-28-generic

title        Ubuntu 11.04, memtest86+
uuid        f4440a05-caf7-431d-aab2-5fd3175c4a3f
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista (loader)
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader    +1

--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=f4440a05-caf7-431d-aab2-5fd3175c4a3f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=91432e22-b675-4d59-aeee-8ad4c1f0bc8d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


//192.168.1.199/Websites /mnt/websites cifs noperms,guest,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0
//192.168.1.199/Audio /mnt/audio cifs noperms,guest,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0
//192.168.1.199/General /mnt/storage cifs noperms,guest,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0


--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 293.207885265 = 314.829569536  boot/grub/menu.lst                             1
 288.664321423 = 309.950955008  boot/grub/stage2                               2
 293.202254772 = 314.823523840  boot/initrd.img-2.6.35-28-generic              8
 293.288527966 = 314.916158976  boot/initrd.img-2.6.38-8-generic              10
 288.615348339 = 309.898370560  boot/initrd.img-2.6.38-8-generic-pae           8
 288.829726696 = 310.128557568  boot/vmlinuz-2.6.35-28-generic                15
 293.210139751 = 314.831990272  boot/vmlinuz-2.6.38-8-generic                 69
 293.221606731 = 314.844302848  boot/vmlinuz-2.6.38-8-generic-pae              5
 288.615348339 = 309.898370560  initrd.img                                     8
 293.288527966 = 314.916158976  initrd.img.old                                10
 293.221606731 = 314.844302848  vmlinuz                                        5
 293.210139751 = 314.831990272  vmlinuz.old                                   69

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 


---

### Post by wildmanne39 on 2011-07-08
Hi, my understanding is that natty can not boot from grub legacy which is what you have installed. Here is a link for purging grub2 and then reinstalling it from a livecd. You may have to do something a little different to purge grub legacy because the grub config files are saved in a different place, but you do need to install grub2.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by schwim on 2011-07-08
Thanks very much for the link wildmanne.  It went a long way to remind me of the absolutely absurd measures that are often necessary to do something that should be quite simple in linux.  It also made me realize that I should consider myself lucky that my linux install works at all. Just like the old days.

Thanks to everyone that took the time to try to help!

---

### Post by wildmanne39 on 2011-07-08
> **schwim said:**
> Thanks very much for the link wildmanne.  It went a long way to remind me of the absolutely absurd measures that are often necessary to do something that should be quite simple in linux.  It also made me realize that I should consider myself lucky that my linux install works at all. Just like the old days.

Thanks to everyone that took the time to try to help!Hi, your welcome, maybe someone else will pop in here and help with your problem if that link does not fix it.

---

