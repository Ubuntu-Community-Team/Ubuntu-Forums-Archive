---
title: "Tri-boot Ubuntu, Backtrack 4 and Windows 7"
date: 2009-09-22
forum: General Help
---

### Post by Adrian123 on 2009-09-22
Hi, I am having some issues tri-booting these three operating systems. First i installed ubuntu then backtrack, and finally windows 7. I have ubuntu and backtrack workign just fine and i have tried the for all values of (hd0) still no luck. 
```
title Windows 7
root (hd0,1)
chainloader +1
```I read somewhere windows 7 might not be on aprimary partition however it booted fine after i installed it. Later i booted from ubuntu live cd and restored GRUB. Here is what i have in fdisk and my menu.lst

Thanks for your time guys. sorry for the newb question but I am really digging ubuntu.

```

adrian@adrian-laptop:~$ sudo fdisk -lu
[sudo] password for adrian: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000f385

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    29302559    14651248+  83  Linux
/dev/sda2        29302560    52741394    11719417+   5  Extended
/dev/sda3   *    52742144    52946943      102400    7  HPFS/NTFS
/dev/sda4        52946944   390719487   168886272    7  HPFS/NTFS
/dev/sda5        29302623    48837599     9767488+  83  Linux
/dev/sda6        48837663    52741394     1951866   82  Linux swap / Solaris
adrian@adrian-laptop:~$ 
adrian@adrian-laptop:~$ 


``````
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
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

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
# kopt=root=UUID=5abbbce4-b7b5-4222-92d9-e1dfaef6b0df ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5abbbce4-b7b5-4222-92d9-e1dfaef6b0df

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        5abbbce4-b7b5-4222-92d9-e1dfaef6b0df
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=5abbbce4-b7b5-4222-92d9-e1dfaef6b0df ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        5abbbce4-b7b5-4222-92d9-e1dfaef6b0df
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=5abbbce4-b7b5-4222-92d9-e1dfaef6b0df ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5abbbce4-b7b5-4222-92d9-e1dfaef6b0df
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5abbbce4-b7b5-4222-92d9-e1dfaef6b0df ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5abbbce4-b7b5-4222-92d9-e1dfaef6b0df
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5abbbce4-b7b5-4222-92d9-e1dfaef6b0df ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5abbbce4-b7b5-4222-92d9-e1dfaef6b0df
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Backtrack 4 Pre
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.29.4 root=UUID=cff9e5cf-8e40-4e1a-913b-35338913093a ro quiet splash 
initrd        /boot/initrd.img-2.6.29.4
quiet

title        Microsoft Windows 7 RC
root        (hd0,4)
savedefault
makeactive
chainloader +1

```

---

### Post by ks07 on 2009-09-22
I would check the HD numbers in your menu.lst. From what I can see, the Win 7 and Backtrack both point to HD0,4. Am I right in thinking that they are not installed on the same partition?

Presuming Win 7 is installed on /dev/sda3, try changing the Win 7 entry to ```
title        Microsoft Windows 7 RC
root        (hd0,3)
savedefault
makeactive
chainloader +1 
```

---

### Post by Adrian123 on 2009-09-22
You were right. I must have not been paying attention earlier. I am not getting the same error message off of (hd0, 3). I get a missing BOOTMNGR which I assume is from Windows 7. Do you know why I destroyed that when I reinstalled GRUB. And how can I fix it? Thanks alot ks07.

---

### Post by ks07 on 2009-09-22
> **Adrian123 said:**
> You were right. I must have not been paying attention earlier. I am not getting the same error message off of (hd0, 3). I get a missing BOOTMNGR which I assume is from Windows 7. Do you know why I destroyed that when I reinstalled GRUB. And how can I fix it? Thanks alot ks07.
I can't help you much seeing as I don't use Windows 7, but after a quick search it seems a lot of people have had the same problem with 7 and Vista.

Take a look at [this]("http://forums.techarena.in/operating-systems/1128154.htm"), it looks like you need to boot into the recovery mode and let it fix itself. Whether this will break GRUB or not is completely unknown to me. It can't hurt to try.

EDIT: [s]After some more searching, It appears that Windows 7 installs a seperate boot partition, which could actually be the HD0,4[/s] Looking back, this is unlikely, looking at the location of the boot flag and the partition sizes. Just out of interest, does the Backtrack option in GRUB work? It looks like it points to your Win 7 installation drive.

---

### Post by Adrian123 on 2009-09-22
Well I decided to uninstall windows 7 and backtrack 4, deleting both partitions. After i re-installed windows 7 and added the boot information to the grub menu.lst. Now they both boot fine now i am going to try to reinstall backtrack 4.

---

### Post by ks07 on 2009-09-23
> **Adrian123 said:**
> Well I decided to uninstall windows 7 and backtrack 4, deleting both partitions. After i re-installed windows 7 and added the boot information to the grub menu.lst. Now they both boot fine now i am going to try to reinstall backtrack 4.
A bit of a drastic method, but I'm glad you've got somewhere now. Seeing as backtrack 4 is linux it should play nicely with your current setup. Hope it works out well.

---

### Post by bradmayne04 on 2010-06-13
I'm using karmic (see my signature for full info) I'm downloading backtrack 4 final right now and would love to install alongside my other two OS's.  I'm kinda nervous though cuz I really do not want to have to reinstall any OS.  I started a thread and then found this thread through google search (i dunno why the forums search didn't turn this thread up) and advice?

---

