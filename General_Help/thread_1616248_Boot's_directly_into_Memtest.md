---
title: "Boot's directly into Memtest"
date: 2010-11-08
forum: General Help
---

### Post by UnterUn on 2010-11-08
Hey everyone! Shut down as normal last night, no major changed yet after booting this morning my computer went straight into memtest86+. After finishing, and i rebooted, it did it again. So, i held shift to get into the grub and i am presented with the following:

```
GNU GRUB   version 1.98+2.0100804-5ubuntu3


Memory Test (memtest86+)
Memory Test (memtest86+, serial console 115200)


Use the [up] and [down] keys to select which entry is highlighted.
Press enter to boot the selected OS, 'e' to edit the commands
before booting or 'c' for a command-line
```I've read of solutions to this using a LiveCD which I do have. But i cannot eject the disc drive (button broken) - normally i do it in the terminal. Anyway...

_When i press 'e' for *Memory Test (Memtest86+) *i get:_

```
GNU GRUB   version 1.98+2.0100804-5ubuntu3


insmod part_msdos
insmod ext2
set root='(hd0, msdos1)'
search --no-floppy -fs-uuid --set 3eaaf981-a42b-47e6-b3ad-8eacbde23c25\

linux16 /boot/memtest86+.bin


Minimum Emacs-like screen editing is supported. TAB lists
completions. Press Ctrl-x to boot, Ctrl-c for a
command-line or ESC to discard edits and return to the GRUB menu.

```_When i press 'e' for *Memory Test (Memtest86+, serial console 115200)*__i get:_

```
GNU GRUB   version 1.98+2.0100804-5ubuntu3


insmod part_msdos
insmod ext2
set root='(hd0, msdos1)'
search --no-floppy -fs-uuid --set 3eaaf981-a42b-47e6-b3ad-8eacbde23c25\

linux16 /boot/memtest86+.bin **console=ttyS0, 115200n8**


Minimum Emacs-like screen editing is supported. TAB lists
completions. Press Ctrl-x to boot, Ctrl-c for a
command-line or ESC to discard edits and return to the GRUB menu.

```And now i have no idea what to do!

Thanks in advance!

---

### Post by bibble235 on 2010-11-08
I think the CD drive has a pinhole you can put a pin in to eject the CD. Both mine do.

---

### Post by UnterUn on 2010-11-08
Hey thanks for the help: I made a LiveUSB and reinstalled (Turns out there is a pinhole aswell by the way!) :)

---

