---
title: "Dual boot difficulties (ubuntu and vista)"
date: 2009-10-01
forum: General Help
---

### Post by dharmabum4732 on 2009-10-01
Hello,

I am attempting to dual boot Ubuntu 9.04 and windows vista (with Ubuntu installed first).  I followed the procedure outlined in this guide [http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm") , but I can't seem to get vista to boot.  I think the problem that I'm running into may have to do with the placement of Ubuntu and vista on my hard drives: the vista installation is located on sda1 and Ubuntu is located on sdc1.

I've tried to research this problem before posting here on the forums, but I can't seem to find a solution.

Any insight would be greatly appreciated!

Thanks,
-Max

---

### Post by Zimmer on 2009-10-01
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

The info around this site may help.
Personally, I had Vista loaded first and I use EasyBCD...

---

### Post by dharmabum4732 on 2009-10-01
If it is of any help, here is the output of "sudo fdisk -l":
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe58e3c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00088bed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS
/dev/sdb4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00037c27

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      180945  1453440681   83  Linux
/dev/sdc3          180946      182401    11695320    5  Extended
/dev/sdc5          180946      182401    11695288+  82  Linux swap / Solaris
```

---

### Post by dharmabum4732 on 2009-10-01
Thanks for your reply Zimmer!

I will check out the link.

---

### Post by arrange on 2009-10-01
Could you post the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/") here?

---

### Post by oldfred on 2009-10-01
If sda is your boot drive and windows is on sda1 this is all you have to add to menu.lst

title Windows Vista, chainloader (on /dev/sda1)
rootnoverify (hd0,0)
savedefault
chainloader +1

If it is on sdb1 or another drive boots first you will need map commands in addition to make windows think it is first.

If you repartitioned your sda drive you may have created issues with the start of the sda1 partition :
starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.

If my quick answer does not work arrange has the correct suggestion with the bootinfo script.

---

### Post by dharmabum4732 on 2009-10-01
Hi arrange,

Thanks for your reply!  Here is the output of boot_info_script:

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbe58e3c5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00088bed

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00037c27

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 2,906,881,424 2,906,881,362  83 Linux
/dev/sdc3       2,906,881,425 2,930,272,064    23,390,640   5 Extended
/dev/sdc5       2,906,881,488 2,930,272,064    23,390,577  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="39CD1C681A6A223F" LABEL="NTFS1" TYPE="ntfs" 
/dev/sdb1: UUID="EC12AB7A12AB4902" TYPE="ntfs" 
/dev/sdc1: UUID="ec4e28f3-b3b0-414c-947a-56b3bc2a5ecc" TYPE="ext4" 
/dev/sdc5: UUID="d345e323-a7f4-4448-b451-ffdac1bfe24b" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sdb1 on /media/NTFS2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/NTFS1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/max/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=max)
/home/max/.mozilla/firefox/firefox on /home/max/.mozilla/firefox/9ouys4e0.default type tmpfs (rw,nosuid,nodev,size=200M,uid=1000,gid=1000,user=max)


=========================== sdc1/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=ec4e28f3-b3b0-414c-947a-56b3bc2a5ecc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ec4e28f3-b3b0-414c-947a-56b3bc2a5ecc

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
# defoptions=quiet

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

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		ec4e28f3-b3b0-414c-947a-56b3bc2a5ecc
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=ec4e28f3-b3b0-414c-947a-56b3bc2a5ecc ro quiet
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		ec4e28f3-b3b0-414c-947a-56b3bc2a5ecc
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=ec4e28f3-b3b0-414c-947a-56b3bc2a5ecc ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, memtest86+
uuid		ec4e28f3-b3b0-414c-947a-56b3bc2a5ecc
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Vista
rootnoverify (hd2,1)
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader+1

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdc1 :
UUID=ec4e28f3-b3b0-414c-947a-56b3bc2a5ecc / ext4 relatime,errors=remount-ro 0 1
# Entry for /dev/sdc5 :
UUID=d345e323-a7f4-4448-b451-ffdac1bfe24b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
firefox /home/max/.mozilla/firefox/9ouys4e0.default tmpfs size=200M,noauto,user,exec,uid=1000,gid=1000 0 0
/dev/sdb1 /media/NTFS2 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/NTFS1 ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sdc1: Location of files loaded by Grub: ===================


   5.5GB: boot/grub/menu.lst
 774.4GB: boot/grub/stage2
 774.4GB: boot/initrd.img-2.6.28-12-generic
 774.4GB: boot/vmlinuz-2.6.28-12-generic
 774.4GB: initrd.img.old
 774.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg sdh 
```

Please let me know if there is any other information that might be helpful.

Thanks,
-Max

---

### Post by dharmabum4732 on 2009-10-01
Hi Oldfred,

Thanks for your response!

I tried the method you outlined in your post, but when I selected that boot option, I received the following message:

Error 13: Invalid or unsupported executable format


Thanks again,
-Max

---

### Post by arrange on 2009-10-01
In my opinion you should be able to boot Vista with```
title Windows Vista
rootnoverify (hd0,0)
makeactive
chainloader +1
```

If that doesn't work, and you're still getting the Error 13 message, you may have to fix the *sda1* Vista boot sector (don't know exactly how it's done).

---

### Post by dharmabum4732 on 2009-10-01
Arrange,

Thanks again for your quick response.  I modified the menu.lst entry according to your advice, but I still get the "Error 13."  I will now look into fixing the sda1 vista boot sector.

Thanks,
-Max

---

### Post by dharmabum4732 on 2009-10-01
Update:

I think my problem might have to do with mapping:

After reviewing the posts so far, I noticed something in Oldfred's post that I hadn't noticed before.  He said > If sda is your boot drive and windows is on sda1, which got me thinking that maybe sda was not my boot drive.  I checked the boot device priority in my BIOS, and it showed that sda was actually last on the list.  I switched sda to the first priority, and now I am in Windows.

This brings up another question though.  Is there a way to choose which operating system to boot without having to enter BIOS each time?  Does this have to do with "mapping" in menu.lst?

Thanks again everyone!
-Max

---

### Post by arrange on 2009-10-01
I think mapping will not help you here because it is used to trick Windows into thinking it is on the first drive, which in your case it actually is. But you can give it a try anyway :)

Could you please copy the Windows part of *menu.lst* that is giving you the *Error 13* message?

---

### Post by oldfred on 2009-10-01
You could install Grub to the first drive and overwrite the windows boot. I would leave the windows boot (only incase you ever wanted to boot it separately again) and put the ubuntu disk first again in BIOS. But windows is only happy if it is first so in grub we map it to think it is first.
 If third drive sdc or hd2 in grub ( change if 2nd drive or hd1)

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Vista on sdc1
rootnoverify    (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

---

### Post by dharmabum4732 on 2009-10-03
Oldfred,

Your advice did the trick!  Thank you!

Sorry about the delay of my response,
-Max

---

