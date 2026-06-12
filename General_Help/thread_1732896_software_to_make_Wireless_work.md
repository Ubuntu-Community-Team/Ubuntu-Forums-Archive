---
title: "software to make Wireless work?"
date: 2011-04-18
forum: General Help
---

### Post by Lexfilez on 2011-04-18
I can not get the wireless to work on my hp netbook 1010nr after install, if i get on line with an ethernet cable what software do i need to download to make the wireless work?

---

### Post by gandaran on 2011-04-18
using the ethernet cable internet run the software update command
```
sudo apt-get update
```
then look in system » administration » additional drivers for the wireless card driver and enable it.
if theres no driver there post the output of
```
lspci
lsusb
```
so we can see what brand of wireless card.

---

### Post by Lexfilez on 2011-04-18
Thanks very much, I will do that if it does not work. 
Thanks again.
 
> **gandaran said:**
> using the ethernet cable internet run the software update command
```
sudo apt-get update
```
then look in system » administration » additional drivers for the wireless card driver and enable it.
if theres no driver there post the output of
```
lspci
lsusb
```
so we can see what brand of wireless card.

---

