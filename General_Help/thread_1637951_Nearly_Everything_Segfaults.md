---
title: "Nearly Everything Segfaults"
date: 2010-12-05
forum: General Help
---

### Post by PhosPhoton on 2010-12-05
Hi all

I'm having a very serious issue that is making ubuntu virtually useless to me.

After modifying x-cursor-theme in /etc/alternatives I've been having this problem.

Nearly every important program is segfault for some unknown reason, and all segfaults are reproducable. Nautilus segfaults when trying to type in a filename to find it (the little textbox in the bottom right does not even show up, nautilus just crashes), gnome-terminal segfaults on launch (I'm using xterm now), chrome and epiphany segfault when I try type in the addressbar, epiphany segfaults when selecting text (this is the second time I'm typing this now), gedit segfaults when trying to type something, gnome-panel segfaults whenever using the Alt-F2 run dialog (the dialog segfaults too). This is all I have tested so far. Things that do work include compiz, rhythmbox, xterm, docky, synapse, blender.

EDIT: It seems a lot of programs (calculator, gedit, pidgin) segfault when I type or select text. I just found out firefox works perfectly (is this because it is not a very gtk+ application? That means there is definitely something to do with gnome, etc)

EDIT: The error message (from gdb) always tells me something like this:
Program received signal SIGSEGV, Segmentation fault.
0x00007ffff49d07ad in _IO_file_doallocate () from /lib/libc.so.6

This is probably got nothing to do with these programs themselves, but rather some underlying problem with gdm itself. It is also probably because I changed x-cursor-theme, but I would never have imagined it would do so much damage! I even tried setting it back to how it was but it didn't do anything. Now Ubuntu is totally screwed up AND my cursors still don't work.

I'm running Maverick 64-bit on a Core 2 Duo E7200 2.5GHz
4GB DDR2-800 (2x 2GB)
Intel G1 chipset (Intel Integrated Express Grpahics) ("intel" xserver driver)
2x Seagate SATA  Hard drives (500GB + 1000GB)
LiteON Dual-Layer DVD Re-Writer

Please tell me if you need more information.

Thanks

---

### Post by PhosPhoton on 2010-12-05
Ok I solved this :)

Turns out one of my cursor themes was inheriting itself!

---

