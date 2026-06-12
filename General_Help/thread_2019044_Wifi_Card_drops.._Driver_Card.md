---
title: "Wifi Card drops.. Driver? Card?"
date: 2012-07-07
forum: General Help
---

### Post by Zerocool Djx on 2012-07-07
So I'm having drop signal loss and a friend suggested that I use a another wifi card as the current one maybe shot. How can I tell which wifi cards are supported by my motherboard/bios so I can make an informed decision to purchases a new one?

---

### Post by Bucky Ball on 2012-07-07
Open a terminal and paste this in:

```
sudo lshw -C network
```

That will tell us what's already there, whether it's compatible/connected/ has drivers and other things.

Paste the output of that command back here. ;)

The card was previously working fine???

---

### Post by Zerocool Djx on 2012-07-07
> **Bucky Ball said:**
> Open a terminal and paste this in:

```
sudo lshw -C network
```That will tell us what's already there, whether it's compatible/connected/ has drivers and other things.

Paste the output of that command back here. ;)

The card was previously working fine???

 Hey thanks for the reply,.. I cannot connect that comp to the internet but I see what your command did. The only think it lists is the LAN Wired network. So yea the card has got to be shot. I just got this comp a week ago and it had XP on it, that got tossed within 20 min of owning it, lol. The LAN one is a Realtek. From what I read up on this computer (Toshiba Sat) is that it came with a b/g network card. But if I got to buy one I would like to put in a b/g/n one for the "N" Boost. But, when I look online there several options. Someone said that you need to match the bios. I found a few that look like the one that is in there, half sized, pins, ant location etc. I mean if it fits will it work?

---

### Post by Bucky Ball on 2012-07-07
Realtek, Intel, Broadcom, Atheros. All (98%) pretty reliably work. I have a Tosher Sat Pro so I'll have a look what I've got in a second. The Compaq 610 I'm on at the moment has:

```
 *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlan0
       version: 02
       serial: 00:1f:3c:e3:ac:48
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
```


PS: It can get confusing with some brands because they put the bits together rather than manufacture the whole card. So, though they might work, it might be hard to find out the wireless chip (i.e. NoNameWireless card with a Broadcom, working wireless chip). You can do a general search for 'ubuntu wireless card' and see what pops up.

---

### Post by Zerocool Djx on 2012-07-07
> **Bucky Ball said:**
> Realtek, Intel, Broadcom, Atheros. All (98%) pretty reliably work. I have a Tosher Sat Pro so I'll have a look what I've got in a second. The Compaq 610 I'm on at the moment has:

```
 *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlan0
       version: 02
       serial: 00:1f:3c:e3:ac:48
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
```
PS: It can get confusing with some brands because they put the bits together rather than manufacture the whole card. So, though they might work, it might be hard to find out the wireless chip (i.e. NoNameWireless card with a Broadcom, working wireless chip). You can do a general search for 'ubuntu wireless card' and see what pops up.

Well,. I found one on eBay for like under 6 bucks with free shipping I am going to give it a shot, see what happens. I mean, this thing didn't even come up on lspci so it's toast. No burn marks or anything so it's prolly just old. I did notice a lot of dust in the case tho, will remove all that soon.

---

### Post by Bucky Ball on 2012-07-07
This is what I have in my Satellite Pro L510:

```
*-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: b4:82:fe:3c:ad:72
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=2.6.38-12-generic firmware=N/A ip=192.168.0.160 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
```

---

