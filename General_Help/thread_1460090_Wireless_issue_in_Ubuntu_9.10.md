---
title: "Wireless issue in Ubuntu 9.10"
date: 2010-04-22
forum: General Help
---

### Post by Jguy on 2010-04-22
First off, I've tagged this as wubi for clarification. I use Wubi because I need an solid Ubuntu installation but do not want to partition the hard drive on the laptop (yet) as it's still under warranty. It's an HP Pavilion DV7-3063CL. 

So far it's worked solidly for the most part except for a wireless issue. After a solid hour or so of being connected to any wireless network, the network drops out and Ubuntu attempts to reconnect, as it should, except it never succeeds. If it's a WEP protected network, then Ubuntu will prompt for a password for the network 3 times. I enter the passcode 3 times, all double and triple checking the accuracy, and then Ubuntu gives up and the wireless card goes into 'sleep' mode. The bars are shown in the status indicator section, but there is an 'X' in the bottom right of the icon. If it's a non-WEP protected network, the laptop will attempt to reconnect to it for about a minute and a half, and then it fails and does the above. The only way to get it to connect to the same network is to reboot the laptop. (I can connect to other networks and then after an hour it does the same thing and then I can't connect to that one, either)

lspci detects the following:

08:00.0 Network Controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

The Wireless Adapter worked with wubi right out of the box, so there was no drivers needed (restricted or others). 

I'm a bit puzzled at why this could be happening. Does anyone have any suggestions?

---

