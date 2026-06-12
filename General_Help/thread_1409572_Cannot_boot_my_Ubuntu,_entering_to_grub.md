---
title: "Cannot boot my Ubuntu, entering to grub"
date: 2010-02-17
forum: General Help
---

### Post by bartomania on 2010-02-17
Hi guys,

I'm having a big problem on my machine. Yesterday we had some internet and power supply problems here in my neighborhood. Since I didn't have internet I was playing on my Ubuntu and decided to check out the "Computer Janitor" application, which I had never used. I told him to clean up an old kernel version (2.6.31-16... my current version is 2.6.31-19). The application froze and I thought it might had something to do with the internet connection being down. I didn't pay much attention to it.

A couple of ours later, there was a power micro-cut, the PC rebooted but instead of loading Ubuntu I got a Grub terminal. I don't know if it had anything to do with what I did with Computer Janitor (actually the kernel is still at /boot) or anything else, but the thing is I couldn't restore my computer boot.

I can boot my PC by doing this on the grub terminal

```

grub> root (hd0,0)
grub> kernel /vmlinuz-2.6.31-19-generic root=UUID=my_root_disc_uuid ro
grub> initrd /initrd.img-2.6.31-19-generic
grub> boot

```

I found someone who had a similar problem [here]("http://ubuntuforums.org/showthread.php?t=631286"). But the solution given for him, didn't work for me.

Something that might be important. When I am on the grub terminal, my main disc is hd0. But once I load my Ubuntu (following the procedure above), and I do "sudo grub", I see that my main disc is hd1.

I really don't know where else to look. Could you give me a hand?

Thanks!

---

### Post by meierfra. on 2010-02-17
Maybe you just have the regenerated your "menu.lst"

```
sudo update-grub
```

---

### Post by bartomania on 2010-02-19
Any ideas?

I tried using dpkg-reconfigure to reconfigure the kernel package... but nothing.

---

### Post by bartomania on 2010-02-19
> **meierfra. said:**
> Maybe you just have the regenerated your "menu.lst"

```
sudo update-grub
```

I'm sorry, I don't know why I missed your message. I'll try that. Thanks.

---

### Post by bartomania on 2010-02-19
> **meierfra. said:**
> Maybe you just have the regenerated your "menu.lst"

```
sudo update-grub
```

Well, now I've tried that but it's the same. It created the menu.lst file but nothing happend, still boots to the grub terminal.

---

### Post by skarychinezeguie on 2010-02-19
i'll tell you like i tell the peeps that call me at work. If you have your data backed up, it's not a big deal, but whenever you force a shutdown or suffer a power loss, while doing ANYTHING, chances are you're gonna have to reinstall the OS.

---

### Post by meierfra. on 2010-02-19
Let's have  closer look at your system. Follow these [instructions]("http://bootinfoscript.sourceforge.net") to run the Boot Info Script and post the RESULTS.txt

---

### Post by meierfra. on 2010-02-19
> chances are you're gonna have to reinstall the OS.
bartomania is able to boot into Ubuntu from the grub command line. So there is no reason to be so pessimistic.

---

### Post by bartomania on 2010-02-19
Here it goes:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on boot drive #2 
    in partition #1 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 17473 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

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

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f8002b1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63       240,974       240,912  83 Linux
/dev/sdb2         117,194,175   390,716,864   273,522,690   5 Extended
/dev/sdb5         382,909,275   390,716,864     7,807,590  82 Linux swap / Solaris
/dev/sdb6         117,194,301   382,893,209   265,698,909  83 Linux
/dev/sdb3    *        240,975   117,194,111   116,953,137  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   156,296,384   156,296,322  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        d06e7e8c-3d94-4ed6-93ab-c22eea29ed2b   ext2                                     
/dev/sdb1        e4e5aec7-b6bd-41dc-95db-635de7c59b4b   ext4                                     
/dev/sdb3        80d6757f-4fb8-4620-8af3-19950d785ddd   ext4                                     
/dev/sdb5        4ac833cc-ec5f-41a8-bc22-e75263298a5b   swap                                     
/dev/sdb6        7a2f4f88-27ad-4ddb-bb9d-ba7458d387ca   ext4                                     
/dev/sdc1        2ed17f3b-f37c-493a-91d6-8f554decfd21   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sdb1/grub/menu.lst: =============================

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
# kopt=root=UUID=80d6757f-4fb8-4620-8af3-19950d785ddd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e4e5aec7-b6bd-41dc-95db-635de7c59b4b

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


=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd.img-2.6.31-16-generic
    .0GB: initrd.img-2.6.31-17-generic
    .0GB: initrd.img-2.6.31-19-generic
    .0GB: vmlinuz-2.6.31-16-generic
    .0GB: vmlinuz-2.6.31-17-generic
    .0GB: vmlinuz-2.6.31-19-generic

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=80d6757f-4fb8-4620-8af3-19950d785ddd /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=e4e5aec7-b6bd-41dc-95db-635de7c59b4b /boot           ext4    relatime        0       2
# /home was on /dev/sdb6 during installation
UUID=7a2f4f88-27ad-4ddb-bb9d-ba7458d387ca /home           ext4    relatime        0       2
# swap was on /dev/sdb5 during installation
UUID=4ac833cc-ec5f-41a8-bc22-e75263298a5b none            swap    sw              0       0
UUID=d06e7e8c-3d94-4ed6-93ab-c22eea29ed2b /storage           ext2    relatime,rw,user,auto        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1       /storage        ext2   rw,user,auto,exec  0   0

```

---

### Post by meierfra. on 2010-02-19
You menu.lst does not list any OS's. But I don't understand why.

I noticed that your run the Boot Info Script from the LiveCD.  Did you also run "sudo update-grub" from the LiveCD? 

try this. Boot into Ubuntu (not the LiveCD)

```

sudo rm /boot/grub/*
sudo apt-get purge grub
sudo apt-get install grub
sudo update-grub
```

---

### Post by bartomania on 2010-02-19
> **meierfra. said:**
> You menu.lst does not list any OS's. But I don't understand why.

I noticed that your run the Boot Info Script from the LiveCD.  Did you also run "sudo update-grub" from the LiveCD? 

try this. Boot into Ubuntu (not the LiveCD)

```

sudo rm /boot/grub/*
sudo apt-get purge grub
sudo apt-get install grub
sudo update-grub
```

Well, I did that and now I'm getting Grub Error 15.
I booted from a LiveCD to repair it but now I see this:

```

root@ubuntu:~# fdisk -l /dev/sdb

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f8002b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          15      120456   83  Linux
/dev/sdb2            7296       24321   136761345    5  Extended
/dev/sdb3   *          16        7295    58476568+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sdb5           23836       24321     3903795   82  Linux swap / Solaris
/dev/sdb6            7296       23834   132849454+  83  Linux

```

I don't know what happened there. Why could /dev/sdb2 appear as "Extended", /dev/sdb3 have the boot flag and have boundary issues? Originally, /dev/sdb1 was my boot partition.

I guess there is no way out but reinstall, right?

---

### Post by meierfra. on 2010-02-19
> Why could /dev/sdb2 appear as "Extended",
An extended partition is a container for logical partition. You need an extended  partition whenever you have more than for regular partitions. But Ubuntu uses an extended partition even if  you have four or less partitions.

> /dev/sdb3 have the boot flag
boot flags are irrelevant when booting with grub.

> have boundary issues? 
A warning dating back to ancient times when computers still cared about cylindrical boundaries. So nothing to worry about.


> I guess there is no way out but reinstall, right? 
I still don't see a reason to reinstall.

> Well, I did that and now I'm getting Grub Error 15.
Did the grub menu appear?  
Could you run the boot info script again and post the RESULTS.txt

---

### Post by bartomania on 2010-02-19
> **meierfra. said:**
> 
I still don't see a reason to reinstall.

I'm glad to read that

> **meierfra. said:**
> 
Did the grub menu appear?  
Could you run the boot info script again and post the RESULTS.txt

Grub menu didn't appear. It just dies on Grub error 15. I booted from a LiveCD, so here it is

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on boot drive #2 
    in partition #1 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 17473 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

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

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f8002b1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63       240,974       240,912  83 Linux
/dev/sdb2         117,194,175   390,716,864   273,522,690   5 Extended
/dev/sdb5         382,909,275   390,716,864     7,807,590  82 Linux swap / Solaris
/dev/sdb6         117,194,301   382,893,209   265,698,909  83 Linux
/dev/sdb3    *        240,975   117,194,111   116,953,137  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   156,296,384   156,296,322  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        d06e7e8c-3d94-4ed6-93ab-c22eea29ed2b   ext2                                     
/dev/sdb1        e4e5aec7-b6bd-41dc-95db-635de7c59b4b   ext4                                     
/dev/sdb3        80d6757f-4fb8-4620-8af3-19950d785ddd   ext4                                     
/dev/sdb5        4ac833cc-ec5f-41a8-bc22-e75263298a5b   swap                                     
/dev/sdb6        7a2f4f88-27ad-4ddb-bb9d-ba7458d387ca   ext4                                     
/dev/sdc1        2ed17f3b-f37c-493a-91d6-8f554decfd21   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sdb1/grub/menu.lst: =============================

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
timeout		3

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
# kopt=root=UUID=80d6757f-4fb8-4620-8af3-19950d785ddd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e4e5aec7-b6bd-41dc-95db-635de7c59b4b

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

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		e4e5aec7-b6bd-41dc-95db-635de7c59b4b
kernel		/vmlinuz-2.6.31-19-generic root=UUID=80d6757f-4fb8-4620-8af3-19950d785ddd ro quiet splash 
initrd		/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		e4e5aec7-b6bd-41dc-95db-635de7c59b4b
kernel		/vmlinuz-2.6.31-19-generic root=UUID=80d6757f-4fb8-4620-8af3-19950d785ddd ro  single
initrd		/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		e4e5aec7-b6bd-41dc-95db-635de7c59b4b
kernel		/vmlinuz-2.6.31-17-generic root=UUID=80d6757f-4fb8-4620-8af3-19950d785ddd ro quiet splash 
initrd		/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		e4e5aec7-b6bd-41dc-95db-635de7c59b4b
kernel		/vmlinuz-2.6.31-17-generic root=UUID=80d6757f-4fb8-4620-8af3-19950d785ddd ro  single
initrd		/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		e4e5aec7-b6bd-41dc-95db-635de7c59b4b
kernel		/vmlinuz-2.6.31-16-generic root=UUID=80d6757f-4fb8-4620-8af3-19950d785ddd ro quiet splash 
initrd		/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		e4e5aec7-b6bd-41dc-95db-635de7c59b4b
kernel		/vmlinuz-2.6.31-16-generic root=UUID=80d6757f-4fb8-4620-8af3-19950d785ddd ro  single
initrd		/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, memtest86+
uuid		e4e5aec7-b6bd-41dc-95db-635de7c59b4b
kernel		/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: grub/menu.lst
    .0GB: initrd.img-2.6.31-16-generic
    .0GB: initrd.img-2.6.31-17-generic
    .0GB: initrd.img-2.6.31-19-generic
    .0GB: vmlinuz-2.6.31-16-generic
    .0GB: vmlinuz-2.6.31-17-generic
    .0GB: vmlinuz-2.6.31-19-generic

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=80d6757f-4fb8-4620-8af3-19950d785ddd /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=e4e5aec7-b6bd-41dc-95db-635de7c59b4b /boot           ext4    relatime        0       2
# /home was on /dev/sdb6 during installation
UUID=7a2f4f88-27ad-4ddb-bb9d-ba7458d387ca /home           ext4    relatime        0       2
# swap was on /dev/sdb5 during installation
UUID=4ac833cc-ec5f-41a8-bc22-e75263298a5b none            swap    sw              0       0
UUID=d06e7e8c-3d94-4ed6-93ab-c22eea29ed2b /storage           ext2    relatime,rw,user,auto        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1       /storage        ext2   rw,user,auto,exec  0   0

```

---

### Post by meierfra. on 2010-02-19
My bad.   I should have told you to run "grub-install" to replace the stage files in /boot/grub I had told you to delete. Do this:

```

sudo mount /dev/sdb3 /mnt
sudo mount /dev/sdb1 /mnt/boot
sudo cp /mnt/usr/lib/grub/i386-pc/* /mnt/boot/grub/
``` 


Just for double checking

```
ls -l /mnt/boot/grub/stage2
```
If this returns  "No such file or directory"  report all error messages you got.

 Otherwise, reboot and hope for the best

---

### Post by bartomania on 2010-02-19
> **meierfra. said:**
> My bad.   I should have told you to run "grub-install" to replace the stage files in /boot/grub I had told you to delete. Do this:

```

sudo mount /dev/sdb3 /mnt
sudo mount /dev/sdb1 /mnt/boot
sudo cp /mnt/usr/lib/grub/i386-pc/* /mnt/boot/grub/
``` 


Just for double checking

```
ls -l /mnt/boot/grub/stage2
```
If this returns  "No such file or directory"  report all error messages you got.

 Otherwise, reboot and hope for the best

Great! Now it's working!

I did as you said, when I rebooted I got the grub terminal again. I booted as I've been doing this last couple of days, and then repeated the whole process:

```

sudo rm /boot/grub/*
sudo apt-get purge grub
sudo apt-get install grub
sudo grub-install /dev/sdb1
sudo update-grub

```

Rebooted and it started as normal :)

Thank you so much, meierfra!

---

