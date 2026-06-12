---
title: "Hardware initiate failed, please check device"
date: 2009-11-27
forum: General Help
---

### Post by Naoko15 on 2009-11-27
Hello everyone. I've got windows xp and ubuntu 9.10 installed and i've had no problems with grub so far. Today when i tried to boot i got this message: 

"Hardware initiate failed, please check device the bios does not seem to be installed. Press <g>"

When i press g Windows loads, but my Ubuntu seems to have dissaperared. I think it's got something to do with my hdd being sata, as my moherboard needs raid drivers loaded to work. 

I've got a backup of my home files i made last night with deja dup, but i need to access Ubuntu to restore it. 

Any ideas? Thanks!

---

### Post by Naoko15 on 2009-11-27
Tried to load Ubuntu with Super Grub Disk and live cd with no luck :( 

Sata raid drivers are installed correctly in Windows.

---

### Post by Naoko15 on 2009-11-30
Ok, so i got to restore grub successfully with Ubuntu 9.10 live cd. The problem now is that when i tried to get in Windows XP i got an "nltdr missing" message. I fixed windows' mbr via the installation cd's repair console but now grub is missing again. 

I've been looking all around the forum but won't find any clear solution to this problem.

Help please :(

---

### Post by john newbuntu on 2009-11-30
If I am right, the "ntldr missing" requires copying 2 files ntldr and ntdetect.com from the CD to the C:\ drive using recovery console.  It does not require an MBR overwrite.  I would try again by just restoring these files when I get this error.

---

### Post by Naoko15 on 2009-11-30
Thanks for your reply. I restored grub again and copied both files (ntldr and ntdetect) without overwriting mbr but got the same problem...ntldr is still missing

---

### Post by Naoko15 on 2009-11-30
Here i post the result of Boot Info Script just in case it is of any help:

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros, 234441648 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x009b009a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,931,499    81,931,437   7 HPFS/NTFS
/dev/sda2          81,931,500   234,436,544   152,505,045   f W95 Ext d (LBA)
/dev/sda5          81,931,563   228,139,064   146,207,502  83 Linux
/dev/sda6         228,139,128   234,436,544     6,297,417  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x8c8dfb63

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disco /dev/sdc: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x10e410e3

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   565,921,754   565,921,692   7 HPFS/NTFS
/dev/sdc2         565,921,755   976,768,064   410,846,310   f W95 Ext d (LBA)
/dev/sdc5         565,921,818   976,768,064   410,846,247  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="A60CA5D80CA5A431" TYPE="ntfs" 
/dev/sda5: UUID="d8f83b8d-b2de-4207-a03c-db8ecf69e71d" TYPE="ext3" 
/dev/sda6: UUID="ec07a613-4dac-4ca8-ab39-37ab6bb05a63" TYPE="swap" 
/dev/sdb1: UUID="5A74F85D74F83D77" LABEL="DISCO BACKUP" TYPE="ntfs" 
/dev/sdc1: UUID="4EFCF775FCF75625" LABEL="DATOS" TYPE="ntfs" 
/dev/sdc5: LABEL="LINUX" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
gvfs-fuse-daemon on /home/belen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=belen)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d8f83b8d-b2de-4207-a03c-db8ecf69e71d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d8f83b8d-b2de-4207-a03c-db8ecf69e71d

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

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        d8f83b8d-b2de-4207-a03c-db8ecf69e71d
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=d8f83b8d-b2de-4207-a03c-db8ecf69e71d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        d8f83b8d-b2de-4207-a03c-db8ecf69e71d
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=d8f83b8d-b2de-4207-a03c-db8ecf69e71d ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        d8f83b8d-b2de-4207-a03c-db8ecf69e71d
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=d8f83b8d-b2de-4207-a03c-db8ecf69e71d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        d8f83b8d-b2de-4207-a03c-db8ecf69e71d
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=d8f83b8d-b2de-4207-a03c-db8ecf69e71d ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        d8f83b8d-b2de-4207-a03c-db8ecf69e71d
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=d8f83b8d-b2de-4207-a03c-db8ecf69e71d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        d8f83b8d-b2de-4207-a03c-db8ecf69e71d
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=d8f83b8d-b2de-4207-a03c-db8ecf69e71d ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Chainload into GRUB 2
root        d8f83b8d-b2de-4207-a03c-db8ecf69e71d
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        d8f83b8d-b2de-4207-a03c-db8ecf69e71d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=d8f83b8d-b2de-4207-a03c-db8ecf69e71d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=ec07a613-4dac-4ca8-ab39-37ab6bb05a63 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  41.9GB: boot/grub/menu.lst
  41.9GB: boot/grub/stage2
  41.9GB: boot/initrd.img-2.6.28-16-generic
  41.9GB: boot/initrd.img-2.6.31-14-generic
  41.9GB: boot/initrd.img-2.6.31-15-generic
  41.9GB: boot/vmlinuz-2.6.28-16-generic
  41.9GB: boot/vmlinuz-2.6.31-14-generic
  41.9GB: boot/vmlinuz-2.6.31-15-generic
  41.9GB: initrd.img
  41.9GB: initrd.img.old
  41.9GB: vmlinuz
  41.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc5

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
00000200


=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo/sdc1: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))


```

---

### Post by john newbuntu on 2009-12-01
At the very top of your log, it says:
 => Windows is installed in the MBR of /dev/sdb

So, windows is booting from your second disk.  Try copying those
2 files over to this disk in the recovery mode.(I am not sure if this is the D:\ drive or
some other letter) and remove it from C:\

---

### Post by Naoko15 on 2009-12-01
> **john newbuntu said:**
> At the very top of your log, it says:
 => Windows is installed in the MBR of /dev/sdb

So, windows is booting from your second disk.  Try copying those
2 files over to this disk in the recovery mode.(I am not sure if this is the D:\ drive or
some other letter) and remove it from C:\

Ok i did what you said and now it tells me that the following file is missing: 

<windows root>\system32\hal.dll

There's no operating system installed in that drive, so i guess that's why it won't boot. Maybe the problem is that grub is pointing at the wrong drive for windows to load? i havent got much idea. What do you think?

```
Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x009b009a

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        5100    40965718+   7  HPFS/NTFS
/dev/sda2            5101       14593    76252522+   f  W95 Ext'd (LBA)
/dev/sda5            5101       14201    73103751   83  Linux
/dev/sda6           14202       14593     3148708+  82  Linux swap / Solaris

Disco /dev/sdb: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x8c8dfb63

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS

Disco /dev/sdc: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x10e410e3

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1   *           1       35227   282960846    7  HPFS/NTFS
/dev/sdc2           35228       60801   205423155    f  W95 Ext'd (LBA)
/dev/sdc5           35228       60801   205423123+  83  Linux
belen@belen-linux:~$ 

```

---

### Post by john newbuntu on 2009-12-02
Try this.  Go back to what you had before (the 2 files - ntldr and ntdetect on your c:\ drive - aka /dev/sda1) and linux booting properly.

First run the command:
```
sudo blkid
```

You will get something like this for /dev/sda1:
/dev/sda1: UUID="5cd43ae0c43bcad2" TYPE="ntfs" 

Make a note of that UUID corresponding to /dev/sda1. Now edit the file /etc/grub.d/40_custom as root.
```
gksudo gedit /etc/grub.d/40_custom
```
and add the following entries to the END of the file.  Do not remove any lines from this file.  Replace the value of --set with the UUID you obtained running the sudo blkid command.

> 
echo "Adding Windows XP custom entry" >&2
menuentry "Windows XP custom (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 5cd43ae0c43bcad2
    chainloader +1
}

save the file.  Finally run:
sudo update-grub.

Now reboot and see if you can find the windows XP custom menu and try logging on to it.

---

### Post by Naoko15 on 2009-12-02
It didnt work, i get the "ntldr is missing" message again :(

---

### Post by john newbuntu on 2009-12-02
Sorry I am out of ideas.  Can someone else pitch in here and help him?

---

### Post by Naoko15 on 2009-12-02
Thank you so much for your help, i really appreciate it. It's really weird, as dual boot worked for me before and ive never had any problem with it. If it worked before it should work again.

Does anyone else have any ideas i could try? please! Any help will be very very welcome

---

### Post by Naoko15 on 2009-12-03
Can someone help , please? Unfortunately i need Windows for my job  :(

---

### Post by Naoko15 on 2009-12-03
Ok, so i created a boot floppy disk. Now i'm able to access XP with it. It is ok as a temporary fix, but still i'd like my grub to work properly

---

