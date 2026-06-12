---
title: "New kernel not showing up"
date: 2009-07-04
forum: General Help
---

### Post by rfkrocktk on 2009-07-04
Within the last week or so, the new 2.6.28-13 kernel was added to the repository! Woo hoo!

The problem is that after installing it with the update manager, it's not showing up in my /boot/grub/menu.lst

ls /lib/modules yields: ```
2.6.28-11-generic  2.6.28-13-generic  2.6.28-13-server
```, so I know I have it installed, it's just not available to boot from. What should I do? What can I do to make it show up? (Yes, I did restart :P)

---

### Post by SteveDee on 2009-07-04
> **rfkrocktk said:**
> Within the last week or so, the new 2.6.28-13 kernel was added to the repository! Woo hoo!

The problem is that after installing it with the update manager, it's not showing up in my /boot/grub/menu.lst

ls /lib/modules yields: ```
2.6.28-11-generic  2.6.28-13-generic  2.6.28-13-server
```, so I know I have it installed, it's just not available to boot from. What should I do? What can I do to make it show up? (Yes, I did restart :P)

You can edit your menu.lst file:-
 - in a terminal type; gksu nautilus
 - in Nautilus {you now have root permissions} create a backup copy of /boot/grub/menu.lst
 - now select /boot/grub/menu.lst and open with Text Editor
 - Copy your most recent Linux kernel option to a space just above the existing one (see below), then edit this text block with the new kernel version. You will ONLY need to change the version text for "title", "kernel" and "initrd"

For example, within menu.lst you should have something like this, but based upon your file details:-

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=dc7c3e4c-73c1-4bd9-96ae-aca1405bd761 ro quiet splash vga=771 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=dc7c3e4c-73c1-4bd9-96ae-aca1405bd761 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dc7c3e4c-73c1-4bd9-96ae-aca1405bd761 ro quiet splash vga=771 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dc7c3e4c-73c1-4bd9-96ae-aca1405bd761 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

When you save menu.lst and re-boot, your system should auto boot into the first menu option (2.6.28-13).

---

