---
title: "Nice loading screen, how do I get it back?"
date: 2006-03-08
forum: General Help
---

### Post by gumbald on 2006-03-08
After my last kernel upgrade by the update manager, the boot-up process has gone to white writing on black screen, rather than the brown below the ubuntu logo, how do I get this back please?

Couldn't work out what to search for this under so apologies if it's a frequent question...

TIA,
Jamie

---

### Post by treuss on 2006-03-08
Try putting "quite" and "splash" behind your kernel image in /etc/grub/menu.lst. something like:
kernel		/boot/vmlinuz root=/dev/hda7 lapic quiet splash

---

### Post by gumbald on 2006-03-08
My entry already reads:

```
title		Ubuntu, kernel 2.6.12-10-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot
```

---

### Post by gumbald on 2006-03-17
Nobody any thoughts? I do get the very first line of text with the Ubuntu logo, but then it reverts to black and white console text.

---

### Post by Xian on 2006-03-17
Try this:

$ sudo dpkg-reconfigure linux-image-$(uname -r)

---

