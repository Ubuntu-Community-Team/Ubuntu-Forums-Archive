---
title: "Dual monitor woes"
date: 2011-06-26
forum: General Help
---

### Post by panache on 2011-06-26
Hi all,

I am having a lot of trouble using an external monitor with Natty.
I had no issues under 10.10.

Whether I am logged in to a Unity, Classic or Classic (No effects) session, plugging in an external monitor causes the system to hang - both screens become black, but for the mouse pointer. Any open windows appear to still be there "underneath" in that the cursor changes (eg from a pointer to a resize pointer to a text box cursor style pointer etc).
The only way I can get dual monitors to work is by having the monitor already plugged in when I turn on the laptop. However, if I unplug the monitor after booting up in this way, the system hangs.
It's incredibly frustrating because I have to perform a hard shutdown whenever it happens.

I have an intel graphics card and am using the open source drivers.
```
lspci | grep -i  vga
```
returns:
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```

Let me know if I can provide any more information that would be helpful.

Cheers

---

