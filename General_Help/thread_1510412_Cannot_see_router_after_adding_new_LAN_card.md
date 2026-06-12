---
title: "Cannot see router after adding new LAN card"
date: 2010-06-15
forum: General Help
---

### Post by maxpathan on 2010-06-15
Hi
My on-board LAN died so I added a realtek RTL-8029.
I modified the BIOS so it used the PCI network card.

The light on the card flashes.

When I enter 'lspci' I can see the Ethernet controller.

I updated /etc/network/interface
I update /etc/udev/rules.d/70-persistent-net.rules.

I restarted the network using networking restart.

But i still cannot ping router.

PLEASE HELP :-(

---

### Post by maxpathan on 2010-06-16
I would appreciate any help.

Last night i spent 4 hours without luck.
In one post it recommended to power everything down, so I did that, I even removed and re-replaced the card, but no luck.

:confused:

regards
Max

---

### Post by maxpathan on 2010-06-28
The problem was that my router is faulty. Nothing wring with the LAN card.

---

