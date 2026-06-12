---
title: "firewire iPod, or usb printer, not both!"
date: 2006-02-19
forum: General Help
---

### Post by colokevin on 2006-02-19
I installed Ubuntu and most of my devices (including my USB printer), work fine.  Then I spent yesterday getting my iPod (via 1394 connection), up and running.  Basically, the only way I could get it running was if I rebooted with the iPod connected.  Then, whenever I disconnected/reconnected the Pod, it was recognized and mounted fine.

This morning, I attempted to print something.  No go.  I tried bringing up the gnome-cups-manager, and it simply died.  The application I tried printing from, also died.  The /var/log/cups/error_log says:
E [19/Feb/2006:09:33:15 -0700] StartListening: Unable to bind socket for address 7f000001:631 - Cannot assign requested address.

So, I rebooted w/ the iPod UNPLUGGED, and now the printer is working fine.

This obviously points to some kind of address conflict.  Can anyone offer any kind of advice?  I'd like to be able to use both my printer and my pod at any time without rebooting.

Thanks in advance!

---

### Post by colokevin on 2006-02-19
Update: I upgraded my kernel and iPod & printer now appear to be playing nice together.  Ah well.

---

### Post by macsimski on 2006-03-02
interesting. with what did you upgrade your kernel? what kernel did you use before and after. please help us. i'm having the same kind of problems. i'm on kubuntu breezy and still on the default kernel

---

