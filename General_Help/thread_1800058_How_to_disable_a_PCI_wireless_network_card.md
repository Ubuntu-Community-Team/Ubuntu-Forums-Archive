---
title: "How to disable a PCI wireless network card"
date: 2011-07-08
forum: General Help
---

### Post by Tehhund on 2011-07-08
I have a PCI wireless network card that seems to be having issues with Ubuntu. It can't connect to my wireless network - it just asks for my WPA2 passphrase over and over again. Luckily, I have a USB adapter that connects just fine. But I'd like to disable the PCI card so it will stop asking for my wireless password and just use the USB adapter.

Disabling ALL wireless connections or deleting the wireless network both won't work because I need to use the USB adapter. Thanks!

---

### Post by Tuskator on 2011-07-08
If I were you I would just open up the computer and take out the card assuming it is removable. If it isn't I remember a configuration file somewhere where I think you can remove "auto wlan0" or whatever name your card is to disable it. If your card isn't removable sorry I couldn't be much help.

---

### Post by Tehhund on 2011-07-08
Thanks, but I'm trying to leave the card installed in case I need it later on.

---

### Post by no2498 on 2011-07-08
? can you turn it off by right clicking your connection

---

### Post by Tehhund on 2011-07-08
> **no2498 said:**
> ? can you turn it off by right clicking your connection

Um, no. Where would I right-click to disable it?

---

### Post by no2498 on 2011-07-08
mine is up top im on 10.04

looks like an 1 arrow up and 1 down

---

### Post by Tuskator on 2011-07-08
> **Tuskator said:**
> If I were you I would just open up the computer and take out the card assuming it is removable. If it isn't I remember a configuration file somewhere where I think you can remove "auto wlan0" or whatever name your card is to disable it. If your card isn't removable sorry I couldn't be much help.
Found the config file: /etc/network/interfaces
If you run ```
sudo gedit /etc/network/interfaces
``` and place a # before the lines involving you wireless card it should be disabled.

---

