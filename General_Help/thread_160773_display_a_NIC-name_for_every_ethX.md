---
title: "display a NIC-name for every ethX?"
date: 2006-04-15
forum: General Help
---

### Post by lezz on 2006-04-15
hi

I've got 3 NIC:s and it's usually very hard to know which ethX goes to which card in my computer. ifconfig doesn't give me the NIC manufactor names. how am I supposed to find it out?

---

### Post by dcstar on 2006-04-15
[QUOTE=lezz]hi

I've got 3 NIC:s and it's usually very hard to know which ethX goes to which card in my computer. ifconfig doesn't give me the NIC manufactor names. how am I supposed to find it out?[/QUOTE]
lshw

---

### Post by IYY on 2006-04-15
It gives you the MAC address (HWaddr), which can be used to identify the card:

[http://coffer.com/mac_find/](http://coffer.com/mac_find/)

---

