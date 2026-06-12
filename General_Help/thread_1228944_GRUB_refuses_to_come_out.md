---
title: "GRUB refuses to come out"
date: 2009-08-01
forum: General Help
---

### Post by Neoranger on 2009-08-01
Hello. I have an odd problem with GRUB. I used to have XP and Ubuntu installed in my system. I decided to try out Kubuntu 9.04, so I wiped the Ubuntu install clean (format) and everything seemed to work well. A while later I cleaned out my XP install and replaced it with Vista. Naturally, Vista decided to hog the boot and GRUB disappeared, but I easily brought it back with the standard "grub>root (hd0,x) -> setup (hd0).

Now, the hard drive died, so I replaced it and attempted to reinstall both systems. I installed XP and then Kubuntu, but for some reason, GRUB won't show up. It didn't disappear, it just never worked. On boot the system goes straight to XP. I tried bringing it back the same way and while I get no errors during the setup, it won't work.

I just find it odd, because last time (and every other time before, with Ubuntu), installing after Windows seemed to work fine. Any ideas? The only difference I can think of between the old setup and the new one is that the filesystem in my previous install was ext4, while this time I went with ext3... but I don't see how that could be relevant.

---

### Post by michy99 on 2009-08-01
Boot up a Live CD and mount your file system.Note: Change /dev/sda1 to whatever partition Ubuntu is on.```
sudo mkdir /disk
sudo mount -t ext3 /dev/sda1 /disk
```Now run these commands and post the output here:```
cat /disk/boot/grub/menu.lst
sudo fdisk -l
```

---

### Post by Neoranger on 2009-08-01
```
ubuntu@ubuntu:~$ sudo mkdir /disk                                
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda4 /disk
ubuntu@ubuntu:~$ cat /disk/boot/grub/menu.lst
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
default         0                                                             

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).                                          
timeout         10                                                             

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)              
# makeactive                         
# chainloader   +1                   
#                                    
# title         Linux                
# root          (hd0,1)              
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=f89b96c1-b59b-46ee-a287-d7e24d7bca34 ro          

## default grub root device
## e.g. groot=(hd0,0)      
# groot=f89b96c1-b59b-46ee-a287-d7e24d7bca34

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

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            f89b96c1-b59b-46ee-a287-d7e24d7bca34
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=f89b96c1-b59b-46ee-a287-d7e24d7bca34 ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            f89b96c1-b59b-46ee-a287-d7e24d7bca34
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=f89b96c1-b59b-46ee-a287-d7e24d7bca34 ro  single
initrd          /boot/initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, memtest86+
uuid            f89b96c1-b59b-46ee-a287-d7e24d7bca34
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows Vista (loader)
rootnoverify    (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f17b5c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25497   204800000    7  HPFS/NTFS
/dev/sda2           25497       50993   204800000    7  HPFS/NTFS
/dev/sda3           91114       91201      706860    5  Extended
/dev/sda4   *       50994       91113   322263900   83  Linux
/dev/sda5           91114       91201      706828+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
102 heads, 51 sectors/track, 281651 cylinders
Units = cylinders of 5202 * 512 = 2663424 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      281650   732571624+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4662dc78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS
```

Hm, I see my original attempt to install Vista has left its marks. I thought it'd be gone, since I had to reformat the drive to install XP. On sdb1, no less, the non-OS drive.

---

### Post by Neoranger on 2009-08-04
/bump

So, I tried a couple of things, different installs and the like... It occured to me, though, that Windows seems to read the old hard drive (the one I use for downloads) as the first drive and the new one (that has the OS installed) as second and MBR seems to be installed in the first drive. So, I tried installing Kubuntu again and installing grub in the Downloads drive, inserting it into the MBR, but the only thing I managed to do was mess up MBR as well. I restored it, but I'm still at loss regarding GRUB. Still can't see the boot menu and I seem to be completely locked out from Kubuntu.

No other ideas, someone?

---

### Post by oldfred on 2009-08-04
If you cannot see Ubuntu and you have done some partition changes your UUID's may have changed. From the install disk try:
sudo blkid 
or 
ls -l /dev/disk/by-uuid
Check that your linux partitions match the entry in your menu.lst.
If you change the boot order in bios that can change the whether grub or windows boot as a different MBR is used.

---

