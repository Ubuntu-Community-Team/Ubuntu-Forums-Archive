---
title: "NTLDR missing after selecting windows from Grub Boot menu"
date: 2009-08-13
forum: General Help
---

### Post by Gin&amp;Tonic on 2009-08-13
Just a quick FYI I am a total N00B in Linux..

So after installing Ubuntu I get the NTLDR missing error whenever I try to boot into windows from grub.

I am sure somehow its just not pointing to the right partition or something but I am at a lost as where to begin. All help is greatly appreciated!!

---

### Post by Gin&amp;Tonic on 2009-08-13
:popcorn:

---

### Post by Gin&amp;Tonic on 2009-08-14
> **Gin&Tonic said:**
> Just a quick FYI I am a total N00B in Linux..

So after installing Ubuntu I get the NTLDR missing error whenever I try to boot into windows from grub.

I am sure somehow its just not pointing to the right partition or something but I am at a lost as where to begin. All help is greatly appreciated!!



BUMP.... I really need some help here..

---

### Post by gabry79Italy on 2009-08-14
post me back output of code
sudo fdisk -l
cat /boot/grub/menu.lst

---

### Post by malachi1990 on 2009-08-14
Can you mount the drive while in ubuntu? 

Easiest way to check is (on your desktop) go to Places > XYZ.A MEDIA where the XYZ.A is the size of your partition.  If you have two or three there, choose the largest (I'm assuming you're only using one hdd).

(If you can't, it means the partition is corrupt, and you will need to reinstall windows.  If you can, a windows repair may be helpful, but know that both of these options will overwrite Grub, and you will need to take steps to fix it.)

---

### Post by Gin&amp;Tonic on 2009-08-14
> **gabry79Italy said:**
> post me back output of code
sudo fdisk -l
cat /boot/grub/menu.lst


Ok quick update... I have been searching these boards and have gotten rid of the NTLDR error. Instead whenever I select my XP os it just says "starting up..." with a heart underneath and a blinking cursor next to it. and it doesnt do anything else.

I have a total of 4 hard drives on this system. 3-500gb storage drives and 1-150gb raptor that runs my os's
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22a034df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22a034d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74137413

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        8041    64589301    7  HPFS/NTFS
/dev/sdc2            8042       18240    81923467+   f  W95 Ext'd (LBA)
/dev/sdc5            8042       10591    20482843+  83  Linux
/dev/sdc6           10592       15690    40957686    b  W95 FAT32
/dev/sdc7           15691       18240    20482843+  82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabb03723

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60801   488384001   42  SFS
```


```
default 0
timeout 10

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
# kopt=root=UUID=37b55c9b-3882-48bc-baf1-18b1b21547c8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=37b55c9b-3882-48bc-baf1-18b1b21547c8

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

title Ubuntu 9.04, kernel 2.6.28-14-generic
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=37b55c9b-3882-48bc-baf1-18b1b21547c8 ro quiet splash
initrd /boot/initrd.img-2.6.28-14-generic

title Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=37b55c9b-3882-48bc-baf1-18b1b21547c8 ro  single
initrd /boot/initrd.img-2.6.28-14-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=37b55c9b-3882-48bc-baf1-18b1b21547c8 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=37b55c9b-3882-48bc-baf1-18b1b21547c8 ro  single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Microsoft Windows XP Professional
rootnoverify (hd2,0)
chainloader +1
```

Really appreciate the help guys.

---

### Post by lisati on 2009-08-14
I've had similar problems in the past. If memory serves correctly, you need to boot from a Windows recovery or installation CD and choose the "repair" option. Be aware, however, that Windows can mess with your MBR, so stand by with an Ubuntu Live CD just in case you need to reinstall grub.

---

### Post by gabry79Italy on 2009-08-14
Ok try this:
sudo -s
apt-get install ntfsprogs
ntfsfix /dev/sdc1
exit
reboot your pc in windows 
If those above have worked and windows have been loaded correctly go to Start-RUN-CMD 
You will be in prompt MSDOS and write this code:
chkdsk /r
Reboot again in windows

---

### Post by Gin&amp;Tonic on 2009-08-15
> **gabry79Italy said:**
> Ok try this:
sudo -s
apt-get install ntfsprogs
ntfsfix /dev/sdc1
exit
reboot your pc in windows 
If those above have worked and windows have been loaded correctly go to Start-RUN-CMD 
You will be in prompt MSDOS and write this code:
chkdsk /r
Reboot again in windows


Hey guys just wanted to thank everyone for there help. I actually was able to resolve the problem by reloading windows...(i wanted a smaller partition anyways) and then reinstalling grub from a live cd. 

thanks again though.

---

