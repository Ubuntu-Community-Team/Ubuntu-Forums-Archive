---
title: "Need Grub help"
date: 2009-10-12
forum: General Help
---

### Post by Spikey123 on 2009-10-12
I found info how to change Grub List but on my PC there is 4 hard drive Linux and Windows is on another Hard Drive. I wanted to ask on here then to mess up my grub and I learned from other versions grub can be tempermental

Ubuntu Version: Ubuntu 8.10, kernel 2.6.27-11-generic

My Output from sudo fdisk -l. The 320GB is the windows XP Pro.
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0bf80bf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x06b46b8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      969018   488385040+   7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13721371

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0c4b2ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         392     3148708+   7  HPFS/NTFS
/dev/sdd2             393        4865    35929372+   5  Extended
/dev/sdd5             393        4675    34403166   83  Linux
/dev/sdd6            4676        4865     1526143+  82  Linux swap / Solaris

```

---

### Post by Spikey123 on 2009-10-12
I just need help with the entry in the grub list

---

### Post by PrePenguin on 2009-10-12
Dont see that drive in your bootlist..

---

### Post by Spikey123 on 2009-10-12
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0bf80bf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

---

### Post by sdowney717 on 2009-10-12
update to karmic beta and you will get grub2.
it works better and is easier to update grub2.

[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

---

### Post by PrePenguin on 2009-10-12
I would just download easyBCD 1.7.2 its free and edit through windows .. Makes it much simpler in my mind since you are running windows anyways

---

### Post by Spikey123 on 2009-10-12
ok I did sudo update-grub. Overall I just want to get Windows XP to boot from grub that is on my 320GB drive.

menu.lst
```

default 0
timeout 20

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
# kopt=root=UUID=405d134c-d5bf-4da9-8b51-3c942112f519 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=405d134c-d5bf-4da9-8b51-3c942112f519

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

title Ubuntu 8.10, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=405d134c-d5bf-4da9-8b51-3c942112f519 ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=405d134c-d5bf-4da9-8b51-3c942112f519 ro  single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-9-generic
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=405d134c-d5bf-4da9-8b51-3c942112f519 ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=405d134c-d5bf-4da9-8b51-3c942112f519 ro  single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=405d134c-d5bf-4da9-8b51-3c942112f519 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=405d134c-d5bf-4da9-8b51-3c942112f519 ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```

I found on line to add this format 
title           Microsoft Windows XP Professional
root            (hd#,0)
savedefault
makeactive
chainloader     +1

but with the (hd #,0) what would be sda1

---

### Post by PrePenguin on 2009-10-12
> **Spikey123 said:**
> ok I did sudo update-grub
 
Taking it that worked? I did mine but its been a minute and I used easyBCD and just saved alot of work and could reconfigure my boot record and text anyway i wanted.

---

### Post by PrePenguin on 2009-10-12
title Ubuntu 8.10, kernel 2.6.27-9-generic
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=405d134c-d5bf-4da9-8b51-3c942112f519 ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=405d134c-d5bf-4da9-8b51-3c942112f519 ro  single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=405d134c-d5bf-4da9-8b51-3c942112f519 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=405d134c-d5bf-4da9-8b51-3c942112f519 ro  single
initrd /boot/initrd.img-2.6.27-7-generic
 
 
You can delete all that unless you want access to old kernel upon start-up

---

### Post by Spikey123 on 2009-10-12
oh I also forgot 

/boot/grub/device.map
 p, li { white-space: pre-wrap; }  (hd0)	/dev/sda

---

### Post by PrePenguin on 2009-10-12
> **Spikey123 said:**
> ok I did sudo update-grub. Overall I just want to get Windows XP to boot from grub that is on my 320GB drive.
 
menu.lst
```

default 0
timeout 20
 
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
# kopt=root=UUID=405d134c-d5bf-4da9-8b51-3c942112f519 ro
 
## default grub root device
## e.g. groot=(hd0,0)
# groot=405d134c-d5bf-4da9-8b51-3c942112f519
 
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
 
 
Leave all ^^^^ alone and just edit below of course leaving your latest kernel module and the ability to to boot recovery mode you can even remove the memtest if you would like below so it looks something like this
 
title Ubuntu 8.10, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=405d134c-d5bf-4da9-8b51-3c942112f519 ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic
 
title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=405d134c-d5bf-4da9-8b51-3c942112f519 ro  single
initrd /boot/initrd.img-2.6.27-11-generic
 
 
### END DEBIAN AUTOMAGIC KERNELS LIST

```
 
I found on line to add this format 
title Microsoft Windows XP Professional
root (hd#,0)
savedefault
makeactive
chainloader +1
 
but with the (hd #,0) what would be sda1
 
 You can add your windows boot option in there too if you would like with further editing I added some things above and took some out if you look through maybe you see the part I am getting at.

---

### Post by Spikey123 on 2009-10-12
I did this 
title Microsoft Windows XP Professional
root (hd0,0)
makeactive
chainloader +1

and this

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

and I try it is says Starting this and stays there with no hard drive activity

with my system Ubuntu and grub is on the 40GB drive and my Windows XP is on the 320MB. 

Also for that dude that use EasyBCD that is just for Vista I am on XP

---

### Post by PrePenguin on 2009-10-12
title Microsoft Windows XP Professional
root (hd#,0)
savedefault
makeactive
chainloader +1
 
title Ubuntu 8.10, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=405d134c-d5bf-4da9-8b51-3c942112f519 ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic
 
title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=405d134c-d5bf-4da9-8b51-3c942112f519 ro single
initrd /boot/initrd.img-2.6.27-11-generic
 
Also on Win XP you can just edit the boot.ini by running Msconfig or manually, you could not do this on Vista and i didnt remember if easy BCD was Vista only. I thought it would do XP too not sure just has the option to repair Vista default MFB.

---

### Post by Spikey123 on 2009-10-12
Here is the combos I tried 
For menu.lst
			 		   		 		 		title Microsoft Windows XP Professional
root (hd#,0)
savedefault
makeactive
chainloader +1

			 		   		 		 		title Microsoft Windows XP Professional
root (hd0)
savedefault
makeactive
chainloader +1

			 		   		 		 		title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

For device.map
(hd0)    /dev/sda
(hd0)    /dev/sda1
(hd0.0)    /dev/sda
(hd0.0)    /dev/sda1

I got error 23 and error phasing hardware

---

