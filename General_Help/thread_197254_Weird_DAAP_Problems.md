---
title: "Weird DAAP Problems"
date: 2006-06-15
forum: General Help
---

### Post by justintime32 on 2006-06-15
I just got this laptop, and it has an intergrated wireless card (yes, Broadcom :(). I had trouble getting it up initially, so I just plugged in an old Dell TrueMobile card I had sitting around, and that worked great.

Today I finally got the card working under Ndiswrapper, and DAAP music sharing stopped working.

Here's the output of 'avahi-browse -a' on the Laptop:
```
+ wlan0 IPv4 Laptop                                        iTunes Audio Access  local
+ wlan0 IPv4 JustinLaptop [00:0b:7d:0a:71:56]              Workstation          local
```
And for the desktop:
```
+ wlan0 IPv4 Justin's Music                                iTunes Audio Access  local
+ wlan0 IPv4 JustyComp [00:0c:41:14:17:97]                 Workstation          local
+ wlan0 IPv4 justin's remote desktop                       VNC Remote Access    local
```
The Desktop also has a Linksys Broadcom wireless card with Ndiswrapper, however that did work before when I used the older card in the laptop. Also, they are both using the same version of Ndiswrapper, and the same exact ndis driver. So I don't know why it wouldn't work.

Could it have anything to do with the fact that I disabled NetworkManager on the desktop? That doesn't seem like it would influence anything, but you never really know...

---

### Post by justintime32 on 2006-06-16
*bump*

---

