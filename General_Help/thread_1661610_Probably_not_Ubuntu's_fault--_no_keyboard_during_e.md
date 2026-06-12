---
title: "Probably not Ubuntu's fault-- no keyboard during early boot"
date: 2011-01-06
forum: General Help
---

### Post by mjpatey on 2011-01-06
Because this problem is occurring before Ubuntu loads, it's probably not an Ubuntu problem, though maybe it was initially caused by it?

For some reason, my keyboard is no longer working during the early stages of boot.  That means I can't hit DEL to enter Setup, or select a boot device manually, etc.  Also, it means if GRUB is set to wait indefinitely for user input (which mine had set itself to do after a weird failure today), it will hang there forever, as I have no way to select an OS to boot into.

I've tried different keyboards (all of the PS/2 variety), and they all work once booted into Ubuntu.  A lightbulb just went off above my head, and I'll try a USB keyboard in just a moment... but in the meantime, anybody have a clue what might have happened, or how to fix this?

Thanks for any input you may have!

-Mark

---

### Post by mjpatey on 2011-01-06
OK, I've figured it out... I had the PS/2 keyboard plugged into the **mouse's** PS/2 port.

Ubuntu had no problem with this!  But my BIOS balked-- it obviously only looks for a keyboard plugged into the keyboard PS/2 port and any USB ports (it did see a USB keyboard just now when tested).

So it was user error, and was only difficult to figure out because Ubuntu was more permissive than the BIOS, so I had no idea I'd plugged into the wrong port.

Solved by the dummy himself!  :-)

-Mark

---

### Post by LarsO on 2011-02-05
I also had no keyboard during part of boot (including mouse). I noticed it after a kernel upgrade and for some reason it wanted me to pick a kernel version during boot from the grub list.
I had to enable legacy usb support in the bios which caused the mouse and keyboard to function during grub.
After successful boot I could restart and disable the legacy usb support and things were fine again...
Sure beats having to load from a liveCD and edit grub list somewhere to set a timer...

---

