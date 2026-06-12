---
title: "Removing the 30-second delay"
date: 2009-09-16
forum: General Help
---

### Post by Poderoso on 2009-09-16
Hi, new poster and Ubuntu user here. My question is regarding booting persistent Ubuntu from a USB-memory stick; is there an easy way to remove (or reduce) the 30-second delay before it automatically begins loading Ubuntu?

I've set up a synergy client (keyboard and mouse sharing) on the computer that I use the USB Ubuntu on and therefore have no need for a physical keyboard or a mouse on that computer. The downside is that it takes 30 extra seconds to boot the computer because I can't press enter to skip the countdown.

Thanks in advance!

---

### Post by scragar on 2009-09-16
```
sudo gedit /boot/grub/menu.lst
```
Edit the line:
```
timeout    30
```To read whatever time you want it to wait(including 0 for instant boot :p).

---

### Post by kerry_s on 2009-09-16
> To read whatever time you want it to wait(including 0 for instant boot ).

0 would disable the count down, so it will sit there waiting for him to hit enter.

---

### Post by scragar on 2009-09-16
> **kerry_s said:**
> 0 would disable the count down, so it will sit there waiting for him to hit enter.

I thought that was -1.

Anyway, set it to 1 then, just in case.

---

### Post by itsjareds on 2009-09-16
You can set it to a 5 second timeout and turn off _displaying_ the GRUB menu until you hit ESC by entering these two lines in /boot/grub/menu.lst:

```
timeout 5
hiddenmenu
```

This will just pause your startup by 5 seconds, then boot with your default OS. If you want to change which OS to boot in during these 5 seconds (screen is empty), then press the Escape key and the normal menu will appear with the timeout stopped.

---

### Post by Poderoso on 2009-09-18
Thanks scragarand and itsjareds, but there is no such directory as "grub" under "boot". In fact, there are no sub-directories or .lst files there. 

There is however a menu.lst file with the correct lines and all in /usr/share/doc/grub/ but reducing the countdown in this file does no change at all to the way ubuntu boots up.

---

### Post by itsjareds on 2009-09-18
That's odd. The menu.lst you found is just an example boot menu. There is nothing inside your /boot directory? What is the output of:

```
ls -A /boot/
```

---

### Post by Poderoso on 2009-09-18
> **itsjareds said:**
> That's odd. The menu.lst you found is just an example boot menu. There is nothing inside your /boot directory? What is the output of:

```
ls -A /boot/
```

abi-2.6.28-11-generic         System.map-2.6.28-11-generic
abi-2.6.28-15-generic         System.map-2.6.28-15-generic
config-2.6.28-11-generic      vmcoreinfo-2.6.28-11-generic
config-2.6.28-15-generic      vmcoreinfo-2.6.28-15-generic
initrd.img-2.6.28-15-generic  vmlinuz-2.6.28-15-generic
memtest86+.bin

---

### Post by jocko on 2009-09-18
> **itsjareds said:**
> That's odd. The menu.lst you found is just an example boot menu. There is nothing inside your /boot directory? What is the output of:

```
ls -A /boot/
```
He said he uses a persistent live usb. It does not have grub.
I'm not sure if this is going to do it, but you should have a file named syslinux.cfg in the root of the usb. Mine looks like this:
```
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
gfxboot bootlogo
```

I guess you could try changing "timeout 300" to something else (apparently in tenths of seconds)

---

### Post by Poderoso on 2009-09-18
> **jocko said:**
> He said he uses a persistent live usb. It does not have grub.
I'm not sure if this is going to do it, but you should have a file named syslinux.cfg in the root of the usb. Mine looks like this:
```
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
gfxboot bootlogo
```I guess you could try changing "timeout 300" to something else (apparently in tenths of seconds)

Thanks, that did the trick!

---

