---
title: "ubuntu wont boot"
date: 2010-04-14
forum: General Help
---

### Post by slgtheindividual on 2010-04-14
I'm dual booting ubuntu and windows 7, booted ubuntu lots of times  before it worked fine, for some reason it wont boot today, it says  something like 'vga=799 has deprecated' I cant quite catch it, it  flashes on then the screen goes blank and wont load, any help would be  useful =]

---

### Post by drs305 on 2010-04-14
There have been several updates lately that are causing boot problems. If it's a Grub2 problem, the following may help. The "vga" deprecated message is something to note but should not prevent booting. These instructions will help if it's a grub problem. If the problem is a video driver or occurs after Grub 2 passes control to the kernel, the problem is something else.

Here is a quick way to try to get Ubuntu to boot.
Get to the Grub 2 menu. If you don't see it, hold down the SHIFT key during boot.
Once you see the menu, try pressing "c" to get to the grub prompt.
Then type the following, pressing ENTER after each line. Don't type the # symbol and what follows, those are just notes for you.
```

set prefix=(hdX,Y)/boot/grub  # Set to your Ubuntu partition. sda5 is (hd0,5)
set root=(hdX,Y)  # Example: sda5 would be "set root=(hd0,5)
linux /vmlinuz root=/dev/sdXY ro  # Example: ... root=/dev/sda5 ro
initrd /initrd.img
boot

```

See if that boots it.

---

### Post by oldfred on 2010-04-14
If drs305s instructions get you into your system can you look at /etc/default/grub to see if the VGA entry is there?  If it is you will want to delete it and sudo update-grub.

Was this an upgrade and you had this entry in your old menu.lst?

---

### Post by slgtheindividual on 2010-04-21
got it to boot, thankyou for the help

---

