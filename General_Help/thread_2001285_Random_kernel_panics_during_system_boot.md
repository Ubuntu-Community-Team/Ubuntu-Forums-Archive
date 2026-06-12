---
title: "Random kernel panics during system boot"
date: 2012-06-10
forum: General Help
---

### Post by ring0mipt on 2012-06-10
Hello,

I'm experiencing random kernel panics during Kubuntu 12.04 boot (by the way, 11.10 also had this problem). It seems to occur only when I turn on my laptop for the first time, as far as I remember the problem never manifested itself when I reboot (properly). But if the kernel panics, it can take quite a few reboots to finally boot the system. Capslock starts flashing and I can see the last 25 lines of stack trace, but it doesn't seem to contain any useful info (I think that the stack is different every time).

How can I debug or report this problem? I have installed linux-crashdump package, but have no idea where it places crash dumps.

HP Pavilion dv6-2150er
Kubuntu 12.04 64-bit
I'm using latest nvidia proprietary drivers from Ubuntu repositories

---

