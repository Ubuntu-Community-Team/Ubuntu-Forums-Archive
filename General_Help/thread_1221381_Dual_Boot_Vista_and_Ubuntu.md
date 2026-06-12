---
title: "Dual Boot Vista and Ubuntu"
date: 2009-07-23
forum: General Help
---

### Post by Sneblot on 2009-07-23
I am having problems dual booting my Vista and Ubuntu machine I have a 250Gb HDD which is partitioned as thus 200Gb Vista 20Gb Ubuntu and 600Mb Swap. I have tried to sort out the boot loader with EasyBCD, I can log into windows fine but when I try Ubuntu I get stuck at some text saying its looking for the grubbootloader or something like that. Any one know how to get round this?

---

### Post by darolu on 2009-07-23
You need to reinstall GRUB; boot with your Ubuntu LiveCD (or flash drive) and open a terminal:
```
sudo grub
```

```
find /boot/grub/stage1
```
It will give you something like hd0,2, change X and Y accordingly:
```
grub> root (hdX,Y)
```
```
grub> setup (hd0)
```
and you exit grub:
```
grub> quit
```

That should fix it; you can then install the start up manager and configure Grub:
```
sudo apt-get install startupmanager
```

---

### Post by Sneblot on 2009-07-23
I followed your advice right up till the last point its now telling me that E:/ could not find startupmanager.

---

### Post by rbc on 2009-07-23
Don't worry about startupmanager for now. It's a GUI frontend to edit menu.lst You can install later

---

### Post by Sneblot on 2009-07-23
Ok so tried to restart into ubuntu and it now gives this message:-
```

Booting 'find /NST/menu.lst'

find --set-root --ignorefloppys /NST/menu.lst
  (hd0,0)

filesystem type is ntfs, partion type 0x7
configfile /NST/menu.lst
Turning on gate A20... Succsess.
Starting cmain()... find --set-root --ignorefloppys /boot/grub/menu.lst
```

Any ideas on what this means or how I can put it right?

---

### Post by Sneblot on 2009-07-23
Ok so I tried this last page from a tutorial I found [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4) Now I have found the /boot/grub/menu.lst and I have the information 
```

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		eaae3936-f89b-46da-bb84-0d8567ca2255
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=eaae3936-f89b-46da-bb84-0d8567ca2255 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		eaae3936-f89b-46da-bb84-0d8567ca2255
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=eaae3936-f89b-46da-bb84-0d8567ca2255 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		eaae3936-f89b-46da-bb84-0d8567ca2255
kernel		/boot/memtest86+.bin
quiet

title		Windows Vista (loader)
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```
Everyting looked as if it was going ok hit enter on the NeoGrub option got the four OS choices but each of the ubuntu options came up the same right at the end it said can not find file. Does this mean I have to re-install ubuntu??

---

### Post by Sneblot on 2009-07-23
!bump!

---

### Post by darolu on 2009-07-25
NeoGrub? Did you install with Wubi? On your first post you said Ubuntu was on a different partition so I thought you installed booting from the CD. Try editing the one at "X:\Ubuntu\winboot\grub\menu.lst" or similar path, if that doesn't work, create a directory named "NST" on C:/ or whatever unit Vista uses (where your Ubuntu installation is); then create a menu.lst file there and copy paste the menu.lst (the one you posted) lines there; this should fix your problem.

---

