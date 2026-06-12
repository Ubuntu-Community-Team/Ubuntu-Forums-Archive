---
title: "virtual box"
date: 2010-10-17
forum: General Help
---

### Post by nads_da_man on 2010-10-17
hi there folks....
could any one please assist in showing me a way how to enable wireless on virtualbox v3 on maverick....i managed some how to get the usb working on it...only thing is remaining is wireless...guest is "windows xp"
thankz lotz in advance ppl...

---

### Post by Vaphell on 2010-10-17
does the wireless work on host system? i'd imagine that the guest system uses host's connection to use the network

---

### Post by nads_da_man on 2010-10-18
yes it works on the host...

---

### Post by Robert Lutken on 2010-10-18
Not too sure about wireless but you may need to change the network settings card in virtual box settings to a different network card, when seting up mine, it connected straight through my normal connection however i needed to change the settings in virtual box so it selects the correct network card, hope this helps.
Rob

---

### Post by sepo on 2010-10-18
You don't need to see the wireless connection on your vbox guest. Your guest just need an underlying connection on your host (wired or wireless....it doesn't matter :)
Just be sure that in your guest's Network settings you enabled the network adapter as NAT.

---

### Post by nads_da_man on 2010-10-18
thanks alot folks:)

---

