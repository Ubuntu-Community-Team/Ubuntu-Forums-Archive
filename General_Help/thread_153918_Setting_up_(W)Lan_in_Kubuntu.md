---
title: "Setting up (W)Lan in Kubuntu"
date: 2006-04-02
forum: General Help
---

### Post by dknoppix on 2006-04-02
Hey everyone,

I have everything installed, and its working fine, except I can't get my ethernet and wlan connection set up. I have the ethernet cabled plugged in, but I don't know how to connect to it.

For the wireless card, I have a Netgear WG111v2, and I don't know how to configure it. (I will primarily use the wifi connection)

dk 8)

---

### Post by steffennielsen on 2006-04-06
Please give me the output from these two commands:

---

ifconfig

iwconfig

---

You should be able to connect your ethernet using the command:

sudo ifup eth0 (or whatever the output from "ifconfig" is!)

The wireless part is configurable with this command:

sudo kate /etc/network/interfaces

---

