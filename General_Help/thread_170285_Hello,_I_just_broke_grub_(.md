---
title: "Hello, I just broke grub :("
date: 2006-05-04
forum: General Help
---

### Post by tallyho on 2006-05-04
I run Windows XP Home & Breezy 5.10 on the same hd using ntldr as the boot manager & have grub installed at the beggining of /dev/hda2/ (/boot). I switched on the machine today and it booted fine (windows & ubuntu). Ubuntu tell's me 68 updates available (I did not list them or check them :/) I just clicked go. Installed with no errors, rebooted.. and on selecting Grub from the ntldr menu, it just hangs with the word "GRUB  _" followed by the curser. I can see all my partitions (using DSL live) but have no idea whats happened.

Heres my what the uncommented sections of my menu.lst looks like (hope someone can help)

***********
title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,1)
kernel		/vmlinuz-2.6.12-10-386 root=/dev/hda4 ro quiet splash
initrd		/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.12-10-386 root=/dev/hda4 ro single
initrd		/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/vmlinuz-2.6.12-9-386 root=/dev/hda4 ro quiet splash
initrd		/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.12-9-386 root=/dev/hda4 ro single
initrd		/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1

******************

---

### Post by Irony on 2006-05-04
One of the updates is a kernel update which will have changed your menu.lst.

Is your kernel on hda4 if not change the menu.lst entry. I assume root is on hda4 (hd0,3) rather than hd0,1 if so change the menu.lst entry.

---

