---
title: "Ubuntu 9.04 root.disk"
date: 2009-07-31
forum: General Help
---

### Post by sdort on 2009-07-31
I only started Ubuntu 9.04 yesterday, and today i restarted it, it said something like: Alert! Cannot find host/ubuntu/disk/root.disk. Then is says
(infarmaf)
I switched back to Vista and found the location of ubuntu, and went to disk, and there was a file that is named root.disk  .  its in the right location, but it still doesnt work. any help??

---

### Post by SuaSwe on 2009-07-31
Do you have a menu.lst file (possibly located in C:\ubuntu\disks\boot\grub\menu.lst), and if so, could you attach it?

At which point during the boot process does this error appear? And is it possible that it's saying (initramfs) as opposed to (infarmaf)?

---

### Post by sdort on 2009-08-01
how do you attach it??
when the loading bar finishes and then it stuffs up.
it says busybox....(initramfs)

---

### Post by SuaSwe on 2009-08-01
If you go to C:\ubuntu\disks\boot\grub\ (somewhere around there anyway) in Windows, can you see the file menu.lst? You can post it here (from Windows) by going into Post Reply and hitting the attachment paperclip thingy.

Your Windows installation is still working, isn't it? The 'initramfs' message means that something's messing up boot (no surprises there then!) and menu.lst might give us some clues.

---

### Post by sdort on 2009-08-02
the attachment failed coz the uploader didnt support .lst files...   =(

---

### Post by SuaSwe on 2009-08-02
Can you open it and copy the content into a .txt file, then attach? Or even just copy-paste it into your message? Whichever way as long as we can see the text. :)

---

### Post by sdort on 2009-08-03
open with notepad and:
 
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
default  0
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout  3
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
# title  Windows 95/98/NT/2000
# root  (hd0,0)
# makeactive
# chainloader +1
#
# title  Linux
# root  (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=ED3E01C9BCEB7B8D loop=/ubuntu/disks/root.disk ro
## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks
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
title  Ubuntu 9.04, kernel 2.6.28-14-generic
root  ()/ubuntu/disks
kernel  /boot/vmlinuz-2.6.28-14-generic root=UUID=ED3E01C9BCEB7B8D loop=/ubuntu/disks/root.disk ro quiet splash 
initrd  /boot/initrd.img-2.6.28-14-generic
title  Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
root  ()/ubuntu/disks
kernel  /boot/vmlinuz-2.6.28-14-generic root=UUID=ED3E01C9BCEB7B8D loop=/ubuntu/disks/root.disk ro  single
initrd  /boot/initrd.img-2.6.28-14-generic
title  Ubuntu 9.04, kernel 2.6.28-11-generic
root  ()/ubuntu/disks
kernel  /boot/vmlinuz-2.6.28-11-generic root=UUID=ED3E01C9BCEB7B8D loop=/ubuntu/disks/root.disk ro quiet splash 
initrd  /boot/initrd.img-2.6.28-11-generic
title  Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root  ()/ubuntu/disks
kernel  /boot/vmlinuz-2.6.28-11-generic root=UUID=ED3E01C9BCEB7B8D loop=/ubuntu/disks/root.disk ro  single
initrd  /boot/initrd.img-2.6.28-11-generic
title  Ubuntu 9.04, memtest86+
root  ()/ubuntu/disks
kernel  /boot/memtest86+.bin
### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title  Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title  Windows Vista (loader)
rootnoverify (hd0,0)
savedefault
chainloader +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title  Windows Vista (loader)
rootnoverify (hd0,1)
savedefault
chainloader +1

---

