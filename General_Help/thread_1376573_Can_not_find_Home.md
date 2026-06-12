---
title: "Can not find :/Home"
date: 2010-01-09
forum: General Help
---

### Post by akiestudio on 2010-01-09
HI , just start Ubuntu 9.04 said:
File system chek failed a long is beging saved /var/long/fsck/checkfs if that location is writable Please repair the file systmen manually 
A maintenance shell will now be started 
Ctr+ D terminate this shell and resume system boot.
Give root password for maintenance or type Control +D to continue.

I did Ctr+D , and after login  said , that can not find /home.

I starte with the live cd:

sudo fisck -l and show that:

dev/sda1    id = 7 , HPTFS/NFTS
dev/sda2    id = 83 LINUX
dev/sda3    id = 5 EXTEND
dev/sda5    id = 82 LINUX/SWAP
dev/sda6    id = 5   EXTEND

I tried with :

unmount /dev/sda2:
can not mount sda2

And aslo i tried.

sudo touch /forcefsck && sudo reboot 

But did not work.

Th file etc/fstab said:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=7e1af8c8-6693-4e4d-8599-38d5ba1b0e21 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=158a1207-484a-4ea7-b87c-a49cb0927ba8 /home           ext3    relatime        0       2
# /windows was on /dev/sda7 during installation
UUID=0F97-262A  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=1bd0d370-2557-4bf3-a01e-f364da76a182 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

and my document etc/mtab said:

/dev/sda2 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

Can anyone help me , please , maybe just I need to edit one or both file, but I do not how to do it....Help please.

---

### Post by oldfred on 2010-01-09
I think you have a partition table error. You cannot have two extended partitions.
dev/sda3    id = 5 EXTEND
dev/sda5    id = 82 LINUX/SWAP
dev/sda6    id = 5   EXTEND

sda6 was home so it is misidentified.

You may be able to boot by removing the /home entry from fstab. It will automatically create a new home in root for you. If you have a lot of data in /home -sda6 that you have not backed up I would try testdisk. Someone else may have seen this problem and have a better way to repair the partition table, I have not.

---

### Post by akiestudio on 2010-01-09
I am new in Linux, what I should do it , could you please give me more details, I do not want to do the wrong steps, and how I can do a backup and restorer later ...regards

---

### Post by oldfred on 2010-01-09
More info on testdisk:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

For backup I just copy data to my cd/DVD and/or USB key . 
Other programs:
Make live CD or DVD
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

Other programs clonezilla and partimage.

---

### Post by akiestudio on 2010-01-10
How I can edit the etc/fstab, just I can read from windows, but I can not writte, and with the live cd, etc/fstab , is not the same...How I can give permiso to etc/fstab
Thank you

---

### Post by oldfred on 2010-01-10
From the liveCD go into the partition with your /etc/fstab. You can do it this way.

sudo mount /dev/sda2 /mnt  #should be your ubuntu install
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain you mounted the correct partition).
cd /mnt/etc  #check that is is the correct mount
gksudo gedit /mnt/etc/fstab
apt-get update
apt-get upgrade
#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

### Post by akiestudio on 2010-01-10
Now i restar and I got a black sreen with a withe line on the left-top, what I should do now?

---

### Post by oldfred on 2010-01-10
It normally means that you have to reinstall grub. It also could be an error in fstab that prevents it from loading.

It may be best to run this script so we can see your entire system.

From a LiveCD:
Download this script to your Desktop from 
[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)
sudo bash ~/Desktop/boot_info_script*.sh
This creates the file RESULTS.txt on your Desktop. Post the content of RESULTS.txt (use the code tags: #)

---

### Post by akiestudio on 2010-01-10
```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda7: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaafb72d0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   307,194,929   307,194,867   7 HPFS/NTFS
/dev/sda2         307,194,930   346,265,009    39,070,080  83 Linux
/dev/sda3         346,265,010   625,137,344   278,872,335   5 Extended
/dev/sda5         346,265,073   361,896,254    15,631,182  82 Linux swap / Solaris
/dev/sda6         361,896,318   596,268,539   234,372,222  85 Linux extended
/dev/sda7         596,268,603   625,137,344    28,868,742   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="B2D04C23D04BEC63" TYPE="ntfs" 
sda2: UUID="7e1af8c8-6693-4e4d-8599-38d5ba1b0e21" SEC_TYPE="ext2" TYPE="ext3" 
sda5: UUID="1bd0d370-2557-4bf3-a01e-f364da76a182" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda2/boot/grub/menu.lst: ===========================

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

#A splash image for the menu
#splashimage=/boot/grub/splashimages/debsplash.xpm.gz

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
# kopt=root=UUID=7e1af8c8-6693-4e4d-8599-38d5ba1b0e21 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7e1af8c8-6693-4e4d-8599-38d5ba1b0e21

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

title        Ubuntu 9.04, kernel 2.6.29-02062901-generic
uuid        7e1af8c8-6693-4e4d-8599-38d5ba1b0e21
kernel        /boot/vmlinuz-2.6.29-02062901-generic root=UUID=7e1af8c8-6693-4e4d-8599-38d5ba1b0e21 ro quiet splash 
initrd        /boot/initrd.img-2.6.29-02062901-generic
quiet

title        Ubuntu 9.04, kernel 2.6.29-02062901-generic (recovery mode)
uuid        7e1af8c8-6693-4e4d-8599-38d5ba1b0e21
kernel        /boot/vmlinuz-2.6.29-02062901-generic root=UUID=7e1af8c8-6693-4e4d-8599-38d5ba1b0e21 ro  single
initrd        /boot/initrd.img-2.6.29-02062901-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        7e1af8c8-6693-4e4d-8599-38d5ba1b0e21
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=7e1af8c8-6693-4e4d-8599-38d5ba1b0e21 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        7e1af8c8-6693-4e4d-8599-38d5ba1b0e21
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=7e1af8c8-6693-4e4d-8599-38d5ba1b0e21 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, memtest86+
uuid        7e1af8c8-6693-4e4d-8599-38d5ba1b0e21
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=7e1af8c8-6693-4e4d-8599-38d5ba1b0e21 /               ext3    relatime,errors=remount-ro 0       1
# /windows was on /dev/sda7 during installation
UUID=0F97-262A  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=1bd0d370-2557-4bf3-a01e-f364da76a182 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 168.0GB: boot/grub/menu.lst
 168.0GB: boot/grub/stage2
 168.1GB: boot/initrd.img-2.6.28-15-generic
 168.0GB: boot/initrd.img-2.6.29-02062901-generic
 168.0GB: boot/vmlinuz-2.6.28-15-generic
 168.1GB: boot/vmlinuz-2.6.29-02062901-generic
 168.0GB: initrd.img
 168.1GB: initrd.img.old
 168.1GB: vmlinuz
 168.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda6


Unknown BootLoader  on sda7



=============================== StdErr Messages: ===============================

hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda7: No such file or directory
hexdump: /dev/sda7: No such file or directory
```

---

### Post by oldfred on 2010-01-10
It still shows problems with sda6. And I do not see the uuid for sda7 so that may be why it is not booting.

Your fstab has an entry for 
# /windows was on /dev/sda7 during installation
UUID=0F97-262A  /windows        vfat    utf8,umask=007,gid=46 0       1

change to:
/dev/sda7 /windows   vfat   user,auto,fmask=0111,dmask=0000      0  0

---

### Post by akiestudio on 2010-01-10
Sorry , I have to change this:

# /windows was on /dev/sda7 during installation
UUID=0F97-262A  /windows        vfat    utf8,umask=007,gid=46 0       1


for this:
# /windows was on /dev/sda7 /windows   vfat   user,auto,fmask=0111,dmask=0000      0  0 	
UUID=0F97-262A  /windows        vfat    utf8,umask=007,gid=46 0       1
?

---

### Post by oldfred on 2010-01-11
No, not in the comment (#) but using sda instead of UUID to show the drive. UUID is preferred since it is less likely to change, partition changes can change sda listing. But if UUID is wrong it will not boot.

# /windows was on /dev/sda7 during installation
/dev/sda7 /windows   vfat   user,auto,fmask=0111,dmask=0000      0  0

---

### Post by akiestudio on 2010-01-11
Still I have the same, trouble, can not find /home....any help please, and thank you very much for your help :D

---

### Post by oldfred on 2010-01-11
Did you try testdisk on sda6. As long as it is mis classed as an extended partition it will not work.

It is in the repository so you can download it.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

