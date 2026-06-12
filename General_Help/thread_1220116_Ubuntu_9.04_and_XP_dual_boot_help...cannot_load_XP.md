---
title: "Ubuntu 9.04 and XP dual boot help...cannot load XP..."
date: 2009-07-22
forum: General Help
---

### Post by fxRichard on 2009-07-22
I installed Ubuntu yesterday and now when I try to load XP with the grub loader it hangs and says "Starting Up..." if I remember correctly and cannot get past that point.  I downloaded boot_info_script032.sh and these are the results.....anyone have any input???

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   167,879,249   167,879,187   7 HPFS/NTFS
/dev/sda2         167,879,250   488,375,999   320,496,750   f W95 Ext d (LBA)
/dev/sda5         268,410,303   319,606,559    51,196,257   7 HPFS/NTFS
/dev/sda6         319,606,623   488,375,999   168,769,377   7 HPFS/NTFS
/dev/sda7         167,879,376   264,188,924    96,309,549  83 Linux
/dev/sda8         264,188,988   268,397,954     4,208,967  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="305C20615C2023D6" TYPE="ntfs" 
/dev/sda5: UUID="64CCF304CCF2CF74" TYPE="ntfs" 
/dev/sda6: UUID="DC40DE0640DDE6F4" TYPE="ntfs" 
/dev/sda7: UUID="731e06d6-7c54-4ba1-802b-faec5cd0568f" TYPE="ext3" 
/dev/sda8: UUID="96137867-b290-4532-b5b5-64e889aa582a" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/richard/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=richard)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=731e06d6-7c54-4ba1-802b-faec5cd0568f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=731e06d6-7c54-4ba1-802b-faec5cd0568f

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        731e06d6-7c54-4ba1-802b-faec5cd0568f
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=731e06d6-7c54-4ba1-802b-faec5cd0568f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        731e06d6-7c54-4ba1-802b-faec5cd0568f
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=731e06d6-7c54-4ba1-802b-faec5cd0568f ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        731e06d6-7c54-4ba1-802b-faec5cd0568f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=731e06d6-7c54-4ba1-802b-faec5cd0568f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        731e06d6-7c54-4ba1-802b-faec5cd0568f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=731e06d6-7c54-4ba1-802b-faec5cd0568f ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        731e06d6-7c54-4ba1-802b-faec5cd0568f
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=731e06d6-7c54-4ba1-802b-faec5cd0568f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=96137867-b290-4532-b5b5-64e889aa582a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  88.9GB: boot/grub/menu.lst
  88.9GB: boot/grub/stage2
  88.9GB: boot/initrd.img-2.6.28-11-generic
  89.0GB: boot/initrd.img-2.6.28-13-generic
  88.9GB: boot/vmlinuz-2.6.28-11-generic
  88.9GB: boot/vmlinuz-2.6.28-13-generic
  89.0GB: initrd.img
  88.9GB: initrd.img.old
  88.9GB: vmlinuz
  88.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

---

### Post by NightwishFan on 2009-07-22
Can you access the NTFS drive from Ubuntu or a live cd?

If so, then the drive is intact, perhaps try reinstalling grub in Ubuntu recovery mode. (I am fairly sure there is an option to do that in Jaunty)

If that does not work, download and burn a super grub disk and try to load Windows. (SGD is like a live cd with a super grub installed. It supports fixing Windows MBR as well.)

[http://prdownload.berlios.de/supergrub/super_grub_disk_0.9797.iso.bz2](http://prdownload.berlios.de/supergrub/super_grub_disk_0.9797.iso.bz2)

This file is bz2 compressed, so you have to unpack it before you burn to a CD. (Just right click extract here in Ubuntu)

---

### Post by fxRichard on 2009-07-22
Thanks, I can access the drive in Ubuntu.  I will try reinstalling grub right now and see what happens....be back in a few

---

### Post by fxRichard on 2009-07-22
Ok same thing after selecting rebuild grub or something like that..still says "Starting up ..."  going to try the super grub now...

---

### Post by NightwishFan on 2009-07-22
If super grub does not work, please try asking around about the testdisk application it may help.

Also, if you use the fixmbr/fix windows boot option in supergrub, it will remove grub and install Window MBR, so you will need to reinstall GRUB to boot ubuntu. (Or use supergrub to boot into Windows/Ubuntu.

Sorry I cannot help more, I have to leave. Good luck!

---

### Post by fxRichard on 2009-07-22
Thanks, I also tried this...

```

Try reinstalling grub first. Search these forums. Or try this:

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

```

But it did not change anything, I keep getting errors when trying to burn the ISO you sent to disc, will try it in windows.

---

### Post by fxRichard on 2009-07-22
Ehhh...forgot my other PC does not have a cd burner doh

---

### Post by TangoPappa on 2009-07-22
> **fxRichard said:**
> Ehhh...forgot my other PC does not have a cd burner doh

Richard, you can restore your master boot record to its default using MBRfix.   You can run this utility from a command prompt window; you don't need an XP installation disc to gain access to the XP recovery console.

     [http://www.sysint.no/en/Download.aspx](http://www.sysint.no/en/Download.aspx)

Once you're back up and running in XP, you can burn the CD you need to re-install GRUB.

Good luck!

Tom

---

### Post by TangoPappa on 2009-07-22
Errrr....  I forgot...  without XP running, how are you going to get to a command prompt window???  

Uhhhh....   I guess you get to explore the MBR restoration tools available on the LiveCD.  Or move the HDD from the dead machine into the working machine as the second HDD, if your machines are desktops.

Or, if you have your XP installation disc, boot from it, bring up the recovery console, and use fixmbr to restore your HDD.

Again, good luck!

Tom

---

### Post by fxRichard on 2009-07-22
lol thanks for the help.  Actually I am growing quite fond of Ubuntu and migrating all of my stuff over to it as I can still access my data through Ubuntu.  Just a matter of installing software I need etc.  The main problem is it's consuming a lot of my time tweaking and playing with compizfusion :)  Took awhile to get nvidia drivers setup as I run dual monitors on this pc but all in all I am very pleased so far!  I may work on getting XP back with the install cd I have but now that things are getting migrated to Ubuntu it's less of a concern.  Thanks again for the help.

---

### Post by Addikit on 2009-07-23
Do you think your grub menu.lst might not have the right info for your Windows XP Partition? Which is why it's hanging up when you select it?

:shrug:

---

