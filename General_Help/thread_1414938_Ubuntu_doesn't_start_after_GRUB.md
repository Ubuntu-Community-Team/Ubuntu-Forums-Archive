---
title: "Ubuntu doesn't start after GRUB"
date: 2010-02-24
forum: General Help
---

### Post by G.W.C. on 2010-02-24
I installed Ubuntu some days ago, so I dont know a whole lot about it. I was trying to make any IM program to work with MSN (which seems almost imposible) and then i tried upgrading the system. It asked me to reboot the computer, and so I did and now I cant start Ubuntu (in the graphical desktop mode, the command line works fine). 

I have Ubuntu shared with Windows Vista, thats how im writing this post.

I would thank you very much if you could help me solve this. I dont really know a whole lot about Linux or so, so if you could try to explain it to my level i would thank you even more.

---

### Post by jessel on 2010-02-24
> **G.W.C. said:**
> I installed Ubuntu some days ago, so I dont know a whole lot about it. I was trying to make any IM program to work with MSN (which seems almost imposible) and then i tried upgrading the system. It asked me to reboot the computer, and so I did and now I cant start Ubuntu (in the graphical desktop mode, the command line works fine). 

I have Ubuntu shared with Windows Vista, thats how im writing this post.

I would thank you very much if you could help me solve this. I dont really know a whole lot about Linux or so, so if you could try to explain it to my level i would thank you even more.

i think that maybe when you upgraded you (or the upgrade) may have messed up grub, but i'm not 100% sure. re-installing grub from the command line is easy, but you have to be very careful. 

step one , get to the grub prompt. you will see when grub is loading a menu option for how to do this. i think you hit "c", but i'm not sure.

step two,
```
grub> (hd0,2)
```note that hd0,2 is a path to the boot partition, here is how it maps out: sda1=(hd0,0); sda2=(hd0,1); sda3=(hd0,2); sdb1=(hd1,0) ; and so on

step three
```
grub> setup (hd0)
```note that if you said (hd0,5) above, you will say (hd0) here, this implies the MBR of the disk, at this point you will get some output and you'll have a good idea if any errors were encountered

step four
```
grub> reboot
```i think this is the easiest way to proceed, any changes from the update should now be accounted for.

let me know.

DISCLAIMER: 1) this procedure is for grub, if your system uses grub2, i have no idea if it will work. 2) you should check the grub man page (its easy to find on google)

---

### Post by G.W.C. on 2010-02-24
I tried, aparently mine is in (hd0,5). I checked the version (sorry for  not checking before) and I have 1.97 beta 4 (i believe).

Anyways  The first command (hd0,5) grub doesnt recognice. Nor it recognices  setup, just reboot. I tried calling help command, but didn't saw  anything similar.

Though, I dont know if its a GRUB problem. I  can load the Ubuntu from command line (recovery mode) and it aparently  works. Maybe there is a way of calling the desktop from the command  line, but I dont know how.

Thank you very much for your help.

---

### Post by jessel on 2010-02-24
[QUOTE
Anyways  The first command (hd0,5) grub doesnt recognice. Nor it recognices  setup, just reboot. I tried calling help command, but didn't saw  anything similar.[/QUOTE]

SORRY! I meant:
```
grub> root (hd0,5)
```the command being root (sets root device) and the target being (hd0,5) (where your boot partition lives)

---

### Post by G.W.C. on 2010-02-24
Now I have another problem (I'm sorry if this is double posting). I saw somewhere that i might have to reinstall grub, so i went sudo gurb-install hd0 into the linux console, but now the gurb window doesnt display the windows options. Is there any way to undo what I did, or pop again the WIndows partitions or even comand-line-boot windows?

EDIT

I managed to load windows with

rootnoverify (hd*,*)
makeactive
chainloader +1
boot

Still, i would like Windows back on Grub menu. I'll try to find out on my own.

---

### Post by jessel on 2010-02-24
> **G.W.C. said:**
> Now I have another problem (I'm sorry if this is double posting). I saw somewhere that i might have to reinstall grub, so i went sudo gurb-install hd0 into the linux console, but now the gurb window doesnt display the windows options. Is there any way to undo what I did, or pop again the WIndows partitions or even comand-line-boot windows?

There is no undo, BUT it is acutally pretty easy to get back to where you were. 

I need:
1) the layout of your disks and partitions
2) a description that explains what partitions are for loading what operating systems (i would prefer not to read /etc/fstab manually, but thats the information i'm after)
3) a copy of of the file /boot/grub.menu.lst

The commands I outlined previously will re-install grub. This is the best way, and any time you install a new kernel and it shows up in the boot menu, you have re-installed grub. There is another way "grub-install" to re-install grub, but I don't use it because i couldn't get it to work for me ever since i installed windows on a separate hard drive. this does the same thing but it is not as general purpose.

Either method will fail, if the menu.lst file is messed up!

Another point is that you can get to the grub command line, from a linux console with the command "grub" and "quit" will get you back to the regular command prompt. the only caveat is that you are not supposed to install grub onto a mounted partition. i'm not sure why.

So, with the information above, I can re-write your menu.lst file so you can re-install. Really this is not hard and you should just read the grub man-page, but you are probably frustrated so i am offering to help...

---

### Post by Fxy on 2010-02-24
If you can get to command line try typing **startx**...  Your desktop should appear after typing that, if instead you get an error post it here & we can help...

---

### Post by G.W.C. on 2010-02-24
Ok, first of all, thank you Fxy for your help cuz without it I would never have entered in Ubuntu, and then never have been able to reach menu.lst. I added to the original menu.lst a entry on top that is Windows Vista and i think I made it default.

So here is the information for hessel (to whom I thank very much also for all his help):

Disposit. Boot       Start         End      Blocks   Id  System
/dev/sda1                1        1698    13631488   27  Unknown
/dev/sda2    *        1698       31299   237772800    7  HPFS/NTFS -> Windows Recovery System
/dev/sda3            31299       57391   209583935    7  HPFS/NTFS -> Windows VIsta
/dev/sda4            57392       60801    27390825    5  Ext
/dev/sda5            57392       60654    26210016   83  Linux
/dev/sda6            60655       60801     1180746   82  Linux swap / Solaris


This is the Fstab file

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=ebe3a858-187b-45e8-9a4a-5785be873bb1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b18d0d9c-580d-4d60-ad97-41fb03d367ff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Menu.LST

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
timeout        3

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
# kopt=root=UUID=ebe3a858-187b-45e8-9a4a-5785be873bb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ebe3a858-187b-45e8-9a4a-5785be873bb1

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

title        Windows Vista
rootnoverify    (hd0,1)
makeactive
chainloader    +1

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        ebe3a858-187b-45e8-9a4a-5785be873bb1
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=ebe3a858-187b-45e8-9a4a-5785be873bb1 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        ebe3a858-187b-45e8-9a4a-5785be873bb1
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=ebe3a858-187b-45e8-9a4a-5785be873bb1 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        ebe3a858-187b-45e8-9a4a-5785be873bb1
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=ebe3a858-187b-45e8-9a4a-5785be873bb1 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        ebe3a858-187b-45e8-9a4a-5785be873bb1
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=ebe3a858-187b-45e8-9a4a-5785be873bb1 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        ebe3a858-187b-45e8-9a4a-5785be873bb1
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=ebe3a858-187b-45e8-9a4a-5785be873bb1 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        ebe3a858-187b-45e8-9a4a-5785be873bb1
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=ebe3a858-187b-45e8-9a4a-5785be873bb1 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        ebe3a858-187b-45e8-9a4a-5785be873bb1
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        ebe3a858-187b-45e8-9a4a-5785be873bb1
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by jessel on 2010-02-24
> title        Windows Vista
rootnoverify    (hd0,1)
makeactive
chainloader    +1rootnoverify (hd0,2) would make more sense, according to your partition table? but this doesn't help at all as far as booting ubuntu.

> title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        ebe3a858-187b-45e8-9a4a-5785be873bb1
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=ebe3a858-187b-45e8-9a4a-5785be873bb1 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quietthis looks fine.

take a look at your system logs and dmesg.

---

