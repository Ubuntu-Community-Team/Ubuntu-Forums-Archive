---
title: "Grub nt Detecting Windows 7"
date: 2009-08-02
forum: General Help
---

### Post by ajithboygenius on 2009-08-02
Hi .. i have installed windows 7 lately & sday i got the ubuntu 9.04 .. so installed it

Now at the grub only ubuntu is visible .. cant find Windows

I have two HDD one of them has Linux (80 GB -Disk /dev/sda: 80.0 GB, 80026361856 bytes ) and the Other HDD has Windows 7 (160 GB -Disk /dev/sdb: 160.0 GB, 160041885696 bytes)

Even if i change the boot priority in BIOS for HDD 0 then .. it boots grub to load ubuntu bt changing the priority back to HDD 1 ... am getttin a grub error 17 ....

My Fdisk - l output is 

===========================================================

[html]
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22c5426d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1459    11717968+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2            1460        2918    11719417+   c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            2919        9727    54693292+   f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda5            2919        4448    12289693+   7  HPFS/NTFS
/dev/sda6            4449        6998    20482843+   7  HPFS/NTFS
/dev/sda7            6999        8910    15358108+   7  HPFS/NTFS
/dev/sda8            8911        9003      746991    b  W95 FAT32
/dev/sda9            9004        9727     5815498+   b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5fa6f80a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3916    31455238+   c  W95 FAT32 (LBA)
/dev/sdb2   *        3917        7740    30716280    c  W95 FAT32 (LBA)
/dev/sdb3            7741       19457    94116802+   f  W95 Ext'd (LBA)
/dev/sdb5            7741        9698    15727603+   b  W95 FAT32
/dev/sdb6            9699       13614    31455238+   b  W95 FAT32
/dev/sdb7           13615       16225    20972826    b  W95 FAT32
/dev/sdb8           16226       19293    24641536    7  HPFS/NTFS
/dev/sdb9           19294       19457     1317298+  82  Linux swap / Solaris
[/html]==============================================================

My **windows 7** is in ---- sdb
**The swap** is in    -------- sdb 
**Linux **is in   --------------  sda

Am unable to understand what excatly to add at the*** /boot/grub/menu.list*** :confused:


here is my output of menu.lust
[html]


title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8
kernel        /boot/memtest86+.bin
quiet
[/html]Can u please help me out soon ..... :( :(

---

### Post by louieb on 2009-08-02
Does not look good. Looking for a primary partition with file system of NTFS and the boot flag set to ON.   

Just wondering did you install Ubuntu on a partition that had another windows install?  Windows pretty much requires its boot files to be in a primary partition.

Want to look at some more information about your setup. Please follow the [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")  and put the results.txt file in you next post. 

BTW instructions say to run from live CD but the script can be run from your hard drive install too.

---

### Post by ajithboygenius on 2009-08-03
Hii ... ya as u said i did install ubuntu on Windows :D ..... 

I had windows 7 installed bt its diskspace was low .. so i again reinstalled windows 7 in another partition and then installed ubuntu 9.04 in the previous windows 

and the output for boot_info_script is ... 


[html]============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/bcd /BOOT/bcd /Boot/bcd /boot/BCD /BOOT/BCD 
                       /Boot/BCD

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 479. But according to the info from fdisk, 
                       sdb8 starts at sector 260655104.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x22c5426d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    23,435,999    23,435,937  83 Linux
/dev/sda2          23,438,835    46,877,669    23,438,835   c W95 FAT32 (LBA)
/dev/sda3          46,877,670   156,264,254   109,386,585   f W95 Ext d (LBA)
/dev/sda5          46,877,733    71,457,119    24,579,387   7 HPFS/NTFS
/dev/sda6          71,457,183   112,422,869    40,965,687   7 HPFS/NTFS
/dev/sda7         112,422,933   143,139,149    30,716,217   7 HPFS/NTFS
/dev/sda8         143,139,213   144,633,194     1,493,982   b W95 FAT32
/dev/sda9         144,633,258   156,264,254    11,630,997   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5fa6f80a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    62,910,539    62,910,477   c W95 FAT32 (LBA)
/dev/sdb2          62,910,540   124,343,099    61,432,560   c W95 FAT32 (LBA)
/dev/sdb3         124,343,100   312,576,704   188,233,605   f W95 Ext d (LBA)
/dev/sdb5         124,343,163   155,798,369    31,455,207   b W95 FAT32
/dev/sdb6         155,798,433   218,708,909    62,910,477   b W95 FAT32
/dev/sdb7         218,708,973   260,654,624    41,945,652   b W95 FAT32
/dev/sdb8         260,655,104   309,938,175    49,283,072   7 HPFS/NTFS
/dev/sdb9         309,942,108   312,576,704     2,634,597  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8" TYPE="ext3" 
/dev/sda2: LABEL="FILMZZ" UUID="04C2-DD42" TYPE="vfat" 
/dev/sda5: UUID="30B88ABFB88A82D8" LABEL="Misc" TYPE="ntfs" 
/dev/sda6: UUID="9C3C5F253C5EFA2A" LABEL="SOFTWARES" TYPE="ntfs" 
/dev/sda7: UUID="4E08FEBC08FEA1DF" LABEL="Filmz" TYPE="ntfs" 
/dev/sda8: LABEL="NEW VOLUME" UUID="342B-6179" TYPE="vfat" 
/dev/sda9: LABEL="vM-4w-M-ShM-3IM-%R^Y" UUID="50A1-A9AD" TYPE="vfat" 
/dev/sdb1: LABEL="SONGS" UUID="3CB0-D807" TYPE="vfat" 
/dev/sdb2: LABEL="FILMS" UUID="D0E1-A4FB" TYPE="vfat" 
/dev/sdb5: LABEL="PICS" UUID="FC1C-3EFE" TYPE="vfat" 
/dev/sdb6: LABEL="SOFTWARE" UUID="9C49-4B2B" TYPE="vfat" 
/dev/sdb7: LABEL="GAMES" UUID="8C66-AF96" TYPE="vfat" 
/dev/sdb8: UUID="522C11242C11051F" LABEL="Windowzzz" TYPE="ntfs" 
/dev/sdb9: UUID="1a129930-f892-40da-9b3e-69c5f4f1f0de" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/renjith/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=renjith)
/dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=renjith)


=========================== sda1/boot/grub/menu.lst: ===========================

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
timeout        6

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
# kopt=root=UUID=a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8

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

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8
kernel        /boot/memtest86+.bin
quiet



### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb9 during installation
UUID=1a129930-f892-40da-9b3e-69c5f4f1f0de none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.2GB: boot/grub/menu.lst
   4.2GB: boot/grub/stage2
   4.1GB: boot/initrd.img-2.6.28-11-generic
   4.1GB: boot/initrd.img-2.6.28-14-generic
   4.0GB: boot/vmlinuz-2.6.28-11-generic
   4.1GB: boot/vmlinuz-2.6.28-14-generic
   4.1GB: initrd.img
   4.1GB: initrd.img.old
   4.1GB: vmlinuz
   4.0GB: vmlinuz.old[/html]
** and in this line (a part from the above)**


[html]
blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="a2a0c5aa-da02-4ba4-8231-71dd38b4f2b8" TYPE="ext3" 
/dev/sda2: LABEL="FILMZZ" UUID="04C2-DD42" TYPE="vfat" 
/dev/sda5: UUID="30B88ABFB88A82D8" LABEL="Misc" TYPE="ntfs" 
/dev/sda6: UUID="9C3C5F253C5EFA2A" LABEL="SOFTWARES" TYPE="ntfs" 
/dev/sda7: UUID="4E08FEBC08FEA1DF" LABEL="Filmz" TYPE="ntfs" 
/dev/sda8: LABEL="NEW VOLUME" UUID="342B-6179" TYPE="vfat" 
/dev/sda9: LABEL="vM-4w-M-ShM-3IM-%R^Y" UUID="50A1-A9AD" TYPE="vfat" 
/dev/sdb1: LABEL="SONGS" UUID="3CB0-D807" TYPE="vfat" 
/dev/sdb2: LABEL="FILMS" UUID="D0E1-A4FB" TYPE="vfat" 
/dev/sdb5: LABEL="PICS" UUID="FC1C-3EFE" TYPE="vfat" 
/dev/sdb6: LABEL="SOFTWARE" UUID="9C49-4B2B" TYPE="vfat" 
/dev/sdb7: LABEL="GAMES" UUID="8C66-AF96" TYPE="vfat" 
/dev/sdb8: UUID="522C11242C11051F" LABEL="Windowzzz" TYPE="ntfs" 
/dev/sdb9: UUID="1a129930-f892-40da-9b3e-69c5f4f1f0de" TYPE="swap" 
[/html]
My latest windows was installed  in sdb8 labelled as Windowzzz .... (i renamed it after browsing that dir frm linux... )

am very much confused nw .. i tried to put windows 7 DVD and tried for repair bt still no luck :( 


plllzz... can u help me out in fixin my boot for windows 7 along with ubuntu ... i dnt want to reinstall windows again :( ..... plz help me out !!

---

### Post by ajithboygenius on 2009-08-03
plz.. help me out ...

---

### Post by louieb on 2009-08-03
Really think your out of luck. I've only heard of one guy that got windows to boot from a logical partition with GRUB  and that was XP. Heres the post. 
[http://ubuntuforums.org/showpost.php?p=7488261&postcount=17](http://ubuntuforums.org/showpost.php?p=7488261&postcount=17) 

Might want to look at the whole tread thought. 

Just a guess you could try reinstalled Ubuntu and Windows 7 -  only this time install win 7 in sda1 and put Ubuntu were windows was.  Probably will need to format the current win 7 partition is so the new install of win 7 does not find it.

---

### Post by ajithboygenius on 2009-08-05
hmm... kk so **better to reinstall WINDOWS 7** again (on the same windows drive.. hoping it wud write the MBR on other primarty partition in the same disk (which wud nt b linux partition ) )..... 

[B]I have done reinstalling windows 7 

now how to get back the grub[/B]  .. i mean how to reinstall the grub with dual booting option for ubuntu and windows 7 ... 

plz temme how to install 



........

now i ran the ubuntu live and took the info frm is ... and the output of fdisk -l is
[html]
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22c5426d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1459    11717968+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        1460        2918    11719417+   c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            2919        9727    54693292+   f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda5            2919        4448    12289693+   7  HPFS/NTFS
/dev/sda6            4449        6998    20482843+   7  HPFS/NTFS
/dev/sda7            6999        8910    15358108+   7  HPFS/NTFS
/dev/sda8            8911        9003      746991    b  W95 FAT32
/dev/sda9            9004        9727     5815498+   b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5fa6f80a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3916    31455238+   c  W95 FAT32 (LBA)
/dev/sdb2            3917        7740    30716280    c  W95 FAT32 (LBA)
/dev/sdb3            7741       19457    94116802+   f  W95 Ext'd (LBA)
/dev/sdb5            7741        9698    15727603+   b  W95 FAT32
/dev/sdb6            9699       13614    31455238+   b  W95 FAT32
/dev/sdb7           13615       16225    20972826    b  W95 FAT32
/dev/sdb8           16226       19293    24641536    7  HPFS/NTFS
/dev/sdb9           19294       19457     1317298+  82  Linux swap / Solaris
[/html][U][I]the boot flag for windows is in the correct partition i guess (but its still LBA where i reinstalled windows 7 )
[/I][/U] 

**now hw to reinstall grub and how to configure for the dual boot**   :confused::confused:

---

### Post by louieb on 2009-08-05
Is it booting to win 7 now?

---

### Post by nhanquy on 2009-08-05
Put this at the end of /boot/grub/menu.lst:
```

title           Microsoft Windows at sda5? 
root            (hd0,4)
savedefault
makeactive
chainloader     +1

title           Microsoft Windows  at sdb2?
root            (hd0,1)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader     +1

```to see if you can boot it ....

---

