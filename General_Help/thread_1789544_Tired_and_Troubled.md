---
title: "Tired and Troubled"
date: 2011-06-23
forum: General Help
---

### Post by noobE on 2011-06-23
Hello ubuntu. Im currently in the middle of making the switch to linux, I just seem to have a problem with connecting to the internet. The terminal say my wifi is disabled yet the light on the laptop says otherwise.

Any and all advice is welcome.

---

### Post by wildmanne39 on 2011-06-24
> **noobE said:**
> Hello ubuntu. Im currently in the middle of making the switch to linux, I just seem to have a problem with connecting to the internet. The terminal say my wifi is disabled yet the light on the laptop says otherwise.

Any and all advice is welcome.Hi, run these commands in a terminal
```
sudo lshw -C network 
```
```
lspci -nn
```
```
iwconfig
```
```
lsmod

```
 and post the outcome  here by clicking on new reply and click # and paste the information between the brackets. Please post them one at a time.

---

### Post by Bucky Ball on 2011-06-24
Have you/can you plug in an ethernet cable, get updates, and check System>Administration>Hardware Drivers (or Additional Drivers, depending what release you're using)?

---

