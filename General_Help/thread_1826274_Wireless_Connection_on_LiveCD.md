---
title: "Wireless Connection on LiveCD"
date: 2011-08-16
forum: General Help
---

### Post by Ravenbeast813 on 2011-08-16
Noob Alert!

I was trying to use my other computer that has Windows XP, and was running it on the LiveCD

I could not get on the internet! I had no wireless connections, when my laptop (Running Ubuntu already) can pick up the signals. I tried to put in my WEP, MAC, and my SSID and I could still not get it to work. No internet connections when I press the "Triangle Internet button at the top". What Am I doing wrong? I am using a Zyxel G-720 v3 wireless adapter to connect (worked fine with Windows XP).

---

### Post by gandaran on 2011-08-16
> **Ravenbeast813 said:**
> Noob Alert!

I was trying to use my other computer that has Windows XP, and was running it on the LiveCD

I could not get on the internet! I had no wireless connections, when my laptop (Running Ubuntu already) can pick up the signals. I tried to put in my WEP, MAC, and my SSID and I could still not get it to work. No internet connections when I press the "Triangle Internet button at the top". What Am I doing wrong? I am using a Zyxel G-720 v3 wireless adapter to connect (worked fine with Windows XP).
drivers! while the laptop has supported wireless device your PC may not so find out what wireless chipset brand and check additional drivers if any ready to activate.
internal devices
```
lspci
``` 
usb devices
```
lsusb
``` 
paste the output

---

