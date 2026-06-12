---
title: "Slow mouse/keyboard"
date: 2011-05-11
forum: General Help
---

### Post by calelettus on 2011-05-11
Installed Ubuntu Studio 11.04 and the mouse & keyboard are very slow/erratic. (I also tried installing Fedora 14 and the same thing happens so i suspect hardware may not be supported?

Windows 7 runs perfectly, FWIW.

Syslog reports:

May 11 05:45:53 homestudio kernel: [ 2377.704099] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* interrupt source ff000066 is not supported on this hardware (return code = 1)
May 11 05:46:00 homestudio gdm-session-worker[1251]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

Any ideas? Thanks!

---

### Post by mörgæs on 2011-05-11
Have you tried installing 10.10 (or a live boot, at least)?

---

### Post by calelettus on 2011-05-12
I'll try that and see what happens. Thanks for responding.

---

### Post by calelettus on 2011-05-13
That didn't help - same problem. I've also tried Ubuntu & Fedora live disks with the same results. Not even sure where to start looking.

---

### Post by mörgæs on 2011-05-13
Please give a complete hardware description.

Have you checked if your BIOS needs upgrade?

---

### Post by calelettus on 2011-05-19
This is on a HP DX5150 MT (Athlon64 4200X2) with 3g of RAM, a 1T hard drive and a Sapphire Radeon HD 4550 512MB 64-bit DDR3 PCI Express 2 Video Card added. (I've also tried without the Sapphire card using the integrated video which is also based on the ATI chipset with the same results.)

The BIOS is the latest available. I suspect ATI is the culprit.

---

### Post by mörgæs on 2011-05-19
> **calelettus said:**
> I suspect ATI is the culprit.

Can you disable it in the BIOS for testing?

---

