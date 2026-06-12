---
title: "no wireless connection"
date: 2010-04-05
forum: General Help
---

### Post by ujoni08 on 2010-04-05
I have had Ubuntu on my own laptop for a few weeks, and I really like it. I bought my daughter a new mini laptop (Samsung N130) a few days ago, which came with XP. It has no CD/DVD drive, so I downloaded Ubuntu onto a 2GB memory stick, and installed it from there. The installation went fine, but I can't go online. When I click on the network manager icon there is no wireless network shown. It only shows wired network and VPN connections.  If I right-click, it doesn't show 'enable wireless', just 'enable networking'. I think I have switched on the wireless network card, which seems to be F9 on her laptop, with an antenna icon. There is an LED showing with that same icon. On my laptop it lists all the wireless routers in the neighbourhood, and shows I'm connected to mine, but this laptop shows nothing. Am I missing something?
Thanks,
Jon

---

### Post by nem75 on 2010-04-05
Jon,

check the network diagnosis tool in System -> Administration - does it show the wireless card in the "devices" drop-down?

If not you might want to enter

```
lspci
```

in a terminal to find out which WLAN chip the machine uses.

---

### Post by ujoni08 on 2010-04-06
It shows a loopback interface and an ethernet interface, but no wireless interface. Could you explain your next piece of advice in more detail, please? I am new to Ubuntu, and don't have a lot of computing experience anyway. (Edit) I found 'terminal' and entered 'lspci'. It shows a lot of stuff about display controllers, etc. then Network controller: Realtek Semiconductor Device 8192 (rev 01) and Ethernet Controller: Realtek Semiconductor RTL8181E/RTL8102E PCI Express fast ethernet controller. I can't see anything about a wireless controller.
Many thanks,
Jon

---

### Post by nem75 on 2010-04-06
> **ujoni08 said:**
> I found 'terminal' and entered 'lspci'. It shows a lot of stuff about display controllers, etc. then Network controller: Realtek Semiconductor Device 8192 (rev 01) and Ethernet Controller: Realtek Semiconductor RTL8181E/RTL8102E PCI Express fast ethernet controller. I can't see anything about a wireless controller.

Then I'd hazard a guess that the wireless is in fact not switched on.

---

### Post by ujoni08 on 2010-04-06
I took it back to the shop and got a replacement, which works fine on wireless.
Thanks for the help.
Jon

---

