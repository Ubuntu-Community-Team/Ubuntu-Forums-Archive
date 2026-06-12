---
title: "Airmon-ng (AirCrack Suite) Unknown Chipset and -1 Channel"
date: 2011-04-17
forum: General Help
---

### Post by Habboblob on 2011-04-17
I've got a NetGear WN111v2 Wireless N Adapter, and when ever I run:

```
airmon-ng
```
I recieve the following:
```
Interface	Chipset		Driver
wlan0		Unknown 	ar9170usb - [phy0]

```

But I have seen that when I use BackTrack 4 my chipset does not come up with Unknown

I think that because I am getting an unknown chipset, whenever I try to use a tool such as aireplay to lock onto any channel, such as channel 2 for example, it says that I am only channel -1, which is incorrect.

In backtrack4 I did not run into any of those problems, and backtrack 4 had also stated that my driver was ar9170 with all the tools working. But I no longer have backtrack 4, and would like to use Ubuntu.

I have Ubuntu 10.10.

Please help me.
Thanks.

---

### Post by Habboblob on 2011-06-04
Bump. Still need help.

---

### Post by micael3000 on 2011-06-27
Bump!

In my case, it is eth1 :(

> Interface       Chipset         Driver

eth1            Unknown                 wl (monitor mode enabled)

---

### Post by josephmills on 2011-06-27
you might need to patch you driver with the compat wireless drivers

---

### Post by micael3000 on 2011-06-27
Hi,

At "additional drivers" I have a wireless driver installed... What do you mean? :s

Thanks!

---

