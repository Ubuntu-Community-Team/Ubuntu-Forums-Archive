---
title: "Improve Performance?"
date: 2012-06-27
forum: General Help
---

### Post by davidftechman on 2012-06-27
how can i improve the overall performance of ubuntu?

---

### Post by zombifier25 on 2012-06-27
What's your system specs?

---

### Post by davidftechman on 2012-06-27
766 mb ram ddr2 amd anthlon x2 1.90 ghz dual core amd radeon x1250 256 mb video memory 1440x900 resolution

---

### Post by zombifier25 on 2012-06-27
Ubuntu will run on 766MB, but it will not run well. You can install a lighter environment on it to make it faster, like LXDE (the package lxde-core) When installed, log out, and choose LXDE at login.

---

### Post by davidftechman on 2012-06-27
> **zombifier25 said:**
> Ubuntu will run on 766MB, but it will not run well. You can install a lighter environment on it to make it faster, like LXDE (the package lxde-core) When installed, log out, and choose LXDE at login.

are theyre any tweaks i can do like in windows? im dual booting with vista and it runs amazing chrome launches in 2 secs same with ms office etc.

---

### Post by zombifier25 on 2012-06-27
No. Only Windows needs a lot of tweaking to make it fast.

The issue here is your ancient computer. Vista is a rather old OS, so it runs well. The latest Ubuntu, not so much.

Like what I said, try LXDE and see if performance improves.

---

### Post by HermanAB on 2012-06-27
Add more RAM, or run Lubuntu on that thing.

---

### Post by TheHitcher on 2012-06-27
I found a few sites to optimise mine on an old 700mhz laptop and it went from ~5 secs just to refocus a window to everything being instant

just a google it i think (can't find my bookmark cos i'm at work) but it involved turning off a few animations that you never notice and loading some low-fat settings, mine was kubuntu specific but there'll be a few similar i reckon:

[https://help.ubuntu.com/community/How%20to%20make%20Kubuntu%20(KDE)%20blazing%20fast%20and%20optimise%20it%20for%20performance%20%7C%20kio_http](https://help.ubuntu.com/community/How%20to%20make%20Kubuntu%20(KDE)%20blazing%20fast%20and%20optimise%20it%20for%20performance%20%7C%20kio_http)

(or you could just install kubuntu, probably a lot lighter than unity which I didn't much like anyway)

---

### Post by black veils on 2012-06-27
[COLOR=Teal]**suggestion 1. **[/COLOR] use xubuntu/xubuntu-desktop or lubuntu/lubuntu-desktop.


[COLOR=Teal]**suggestion 2.**[/COLOR]  open the **terminal**, copy-paste:
```

cat /proc/sys/vm/swappiness

```Press Enter.

The result will probably be 60.

To change this into a more sensible value, copy-paste this into the terminal:
```
gksudo gedit /etc/sysctl.conf
```Press Enter.

Scroll to the bottom of the text file (add your swappiness parameter to override the default) and copy/paste the following line into the file:

```
vm.swappiness=10
```or make the number smaller.
Close the text file and reboot your computer.

After the reboot, check the new swappiness value.

---

### Post by philinux on 2012-06-27
> **davidftechman said:**
> how can i improve the overall performance of ubuntu?

Which version of ubuntu are you running?

---

