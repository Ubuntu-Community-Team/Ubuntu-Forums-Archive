---
title: "Wireless Connection in Ubuntu 5.10"
date: 2006-02-27
forum: General Help
---

### Post by john_markh on 2006-02-27
Hi,
I have installed Ubuntu on my laptop (HP pavilion ze4949ea).
I have this strange problem with wireless network. The button that suppose to activate the network card (wireless) is just don't work! :-k 
When I try to activate it using Network Adminisrator utility, everything goes OK, but no connection is availbe (dahhaaa, network card is not activated).
I know that wireless network card is working, because I have additiional partition with XP on it (that is how I still have access to internet \\:D/ )

---

### Post by e-blade on 2006-02-28
Have you installed the drivers? Wifi things in Ubuntu is not necessarily easy.

---

### Post by john_markh on 2006-02-28
:-k 
Drivers ?
It was working fine (for a few short moments) until I have upgraded my kernel. Now, it don't work at all, not even when I boot using previous kernel version.

---

### Post by john_markh on 2006-03-04
Well, I have installed ipw2200, firmware and ie8000.
The problem is with wireless button (button that enables wireless). I check in event log, there is some problem with mapping.

[SIZE="1"]Mar  2 21:45:06 localhost kernel: [4295021.230000] ipw2200: Radio Frequency Kill Switch is On:
Mar  2 21:45:06 localhost kernel: [4295021.230000] Kill switch must be turned off for wireless networking to work.
Mar  2 21:47:47 localhost kernel: [4295182.975000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Mar  2 21:47:47 localhost kernel: [4295182.975000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Mar  2 21:47:47 localhost kernel: [4295183.055000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Mar  2 21:47:47 localhost kernel: [4295183.055000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.[/SIZE]

Anyone ?

---

