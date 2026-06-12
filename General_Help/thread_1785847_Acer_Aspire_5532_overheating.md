---
title: "Acer Aspire 5532 overheating"
date: 2011-06-18
forum: General Help
---

### Post by HcoJustin on 2011-06-18
Had the laptop for about a year, when in Windows it never happens, but seems to happen frequently in Xubuntu 11.04. I've looked almost everywhere for increasing the fan speeds, because it never kicks into high gear, just a steady pace for idle use. lm-sensors doesn't show fan speeds, just the temps of the CPU. 

As far as [this]("http://ubuntuforums.org/showthread.php?t=1740140") thread goes, I've already got the latest kernel.

Fan is clear of dust, and it runs at an average temperature until the GPU is needed

Edit:
```
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +85.0°C  (crit = +200.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +76.0°C                                    
Core1 Temp:  -49.0°C  
```

Shortly after this it shuts off from overheating. When I can get it to cool off I'll give what I can for that.

```
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +34.0°C  (crit = +200.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +26.0°C                                    
Core1 Temp:  -49.0°C   
```

That's on a fresh boot after all night


= = = = =
Mörgæs 2013-12-05:
Using a fresh install of Lubuntu 13.10 everything works fine. Does not get more than 60 °C

---

### Post by HcoJustin on 2011-06-19
Well I seem to have solved it... 

[http://www.netbooktech.com/2008/09/17/fix-the-acer-aspire-one-noisy-fan-for-both-windows-and-linux/](http://www.netbooktech.com/2008/09/17/fix-the-acer-aspire-one-noisy-fan-for-both-windows-and-linux/)

It hasn't shutdown from an overheat, and the hottest it gets is around 82°C, but its not hot to the touch on the bottom like before. Any way this could be included automatically? It seems like lots of people are having problems with this

---

