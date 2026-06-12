---
title: "Dual monitor set up"
date: 2012-08-07
forum: General Help
---

### Post by sagar_322 on 2012-08-07
Hi there, I have lenovo ideapad laptop and I want to connect external monitor from the laptop's VGA connector. I have LG L224WS monitor, its resolution is 1680x1050. But when I connect the monitor to laptop things in the monitor are looking bigger I cannot make  it to monitor's resolution. I am running ubuntu 10.04...
any help would be appreciated thanks in advance..

---

### Post by krytorii on 2012-08-07
What's the resolution of your laptop screen? What's probably happening is that you're outputting the same resolution to screens that are capable of different resolutins.

---

### Post by sagar_322 on 2012-08-07
Currently laptop resolution is 1366x768..

---

### Post by LiamOS on 2012-08-07
Try
```
xrandr --output VGA1 --auto --right-of LVDS1 --auto
```If those are not your screen names, use 
```
xrandr -q
```to discover what they actually are. 

Hope this works.

---

### Post by sagar_322 on 2012-08-08
> **LiamOS said:**
> Try
```
xrandr --output VGA1 --auto --right-of LVDS1 --auto
```If those are not your screen names, use 
```
xrandr -q
```to discover what they actually are. 

Hope this works.

No this did not work.. I am getting same screen.. :sad:

---

