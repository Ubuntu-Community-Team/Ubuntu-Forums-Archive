---
title: "Can You Silence On Screen Console Messages At Bootup?"
date: 2010-05-01
forum: General Help
---

### Post by DasFox on 2010-05-01
After grub loads the kernel I'll get an on screen message from the console showing: 

**cannot reserve MMIO region**

And I was wondering is there a way to silence console messages so you don't see them at bootup?

Could setting dmesg work:

-nlevel
              Set the level at which logging of messages is done to  the   console.   For  example,  -n  1 prevents all messages, expect  panic messages, from appearing on the console.

So typing at a term 'dmesg -n 1' will work?

THANKS

---

### Post by DasFox on 2010-05-01
anyone?


THANKS

---

### Post by DasFox on 2010-05-04
anyone please?

---

### Post by DasFox on 2010-05-07
still waiting on a reply...

This is what I have in /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="loglevel=0 splash

And it's still spitting out onto the screen after grub loads:

shpchp 0000:00:01.0: Cannot reserve MMIO region

---

