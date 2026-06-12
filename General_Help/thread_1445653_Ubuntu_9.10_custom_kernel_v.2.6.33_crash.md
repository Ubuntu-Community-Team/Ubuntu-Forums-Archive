---
title: "Ubuntu 9.10 custom kernel v.2.6.33 crash"
date: 2010-04-02
forum: General Help
---

### Post by cooprocks123e on 2010-04-02
I wasn't using my laptop for at least a few hours, but when I looked at it, it had seemed to crash. I am hoping to figure out what caused this, and to prevent it from happening again. I believe it has something to do with drm or b43 as that is what I could decipher from the screen. I have checked some logs and found nothing irregular. I do not want this to happen again. I am running kernel 2.6.33.1 with no patches and a custom config tailored to my processor. The reason I am running 2.6.33.1 is because of support for my Wifi. Any help would be appreciated very much.

---

### Post by prodigy_ on 2010-04-02
First of all, try a stock kernel and see if it'll still crash. I'd recommend 2.6.31-19.56.

---

### Post by cooprocks123e on 2010-04-02
Before I do that, considering only kernel 2.6.32+ supports my wifi, I believe that I read something about the NetworkManager applet crashing the whole system, so I configured /etc/network/interfaces for wifi and I am crossing my fingers.

Do they have an Ubuntu kernel v.2.6.32+? If so, please send me a link.

---

### Post by cooprocks123e on 2010-04-02
They do. I should have Googled first. I also use custom kernel for Atom-specific customizations.

---

### Post by Linuxforall on 2010-04-02
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

They have it up to 2.6.33 here.

---

### Post by cooprocks123e on 2010-04-02
My laptop has been on for another hour now and is fine.
I feel like writing a guide:

How to get some Wifi(bcm4312) to stop crashing:
1) ```
sudo nano /etc/network/interfaces
``` and add the following (assuming your wifi is wlan0):

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys (or whatever your ssid is)
```
2) Run the following: ```
sudo ifup wlan0
```
3) Right-click the network icon and uncheck "Enable Wireless"
If that doesn't fix the crashes, right-click again and uncheck "Enable Networking"

You are welcome.

---

