---
title: "GRUB command line appears on start up. YIKES"
date: 2010-02-14
forum: General Help
---

### Post by theronstar on 2010-02-14
Hello. I just booted into Linux and the Update Manager prompted me to restart. After the restart the GRUB interface I expect to see is no longer there and now it is just a command line that says press tab for more options.
 
I have not got a clue with shell language as I have had no time to learn it as of yet. Do I need to uninstall and reinstall Linux or is there a command that can be typed that boots up the operating system. Even better is there something I can do that can return me to seeing the interface like I was used to. Thanks for reading my question

---

### Post by Swagman on 2010-02-14
startx ?

---

### Post by theronstar on 2010-02-14
So I just type startx onto the command line? btw this is the command line at system start up. Not the command line you see on a desktop.

---

### Post by rnerwein on 2010-02-14
hi
let us see how your command line looks like. is it
grub resue>
if yes then run following commands step by step.
ls
set prefix=(hdX,Y)/boot/grub   ( where X and Y are your boot partitons )
set root=(hdX,Y)
insmod /boot/grub/linux.mod
linux /vmlinuz root=/dev/sdXY ro
initrd /initrd.img

boot

good luck
ciao

---

