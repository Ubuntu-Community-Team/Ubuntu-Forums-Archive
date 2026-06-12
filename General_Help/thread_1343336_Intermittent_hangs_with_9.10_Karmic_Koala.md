---
title: "Intermittent hangs with 9.10 Karmic Koala"
date: 2009-12-01
forum: General Help
---

### Post by chorlya on 2009-12-01
I'm experiencing intermittent hangs with Ubuntu 9.10 I installed recently on an old P4 desktop. What happens is that screen would just freeze in such way that I can move the mouse cursor on screen, but nothing happens when I click something. Cursor stays the same as it was at the time of hang (it will be a hand cursor even when I move away from the link in Firefox, if hang occurred while cursor was hovering over a link) and I can't switch between windows or do anything in the currently active one. Only way to regain control is a restart via hard reset.

Hardware is P4 1.6GHz, 512MB and graphics is integrated on an Intel i845 chipset. Also, my screen resolution is 1920x1200, which is probably taxing the poor little GPU quite a bit.
I know its not exactly fast hardware, but could that be the only reason for hangs?

What additional information should I post here that might explain the hangs?

Thanks

---

### Post by dcstar on 2009-12-01
> **chorlya said:**
> I'm experiencing intermittent hangs with Ubuntu 9.10 I installed recently on an old P4 desktop. What happens is that screen would just freeze in such way that I can move the mouse cursor on screen, but nothing happens when I click something. Cursor stays the same as it was at the time of hang (it will be a hand cursor even when I move away from the link in Firefox, if hang occurred while cursor was hovering over a link) and I can't switch between windows or do anything in the currently active one. Only way to regain control is a restart via hard reset.

Hardware is P4 1.6GHz, 512MB and graphics is integrated on an Intel i845 chipset. Also, my screen resolution is 1920x1200, which is probably taxing the poor little GPU quite a bit.
I know its not exactly fast hardware, but could that be the only reason for hangs?

What additional information should I post here that might explain the hangs?

Thanks

With all ongoing hardware freezes you should boot up to the memtest option and give your system a good long test (at least an hour).

Linux pushes PC hardware to its full capabilities (unlike Windows), so you need to stress-test your hardware to see if it can handle the demands Linux will put on it.

If it passes, it then may be better to use an older Ubuntu release with older hardware.

---

