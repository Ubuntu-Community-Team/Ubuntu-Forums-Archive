---
title: "Making a WIFI AP with a laptop?"
date: 2006-06-07
forum: General Help
---

### Post by DiamondX on 2006-06-07
I have a laptop that I got recently. It is a Dell E1505, everything stock except for a 1GB memory upgrade (was free, Im on a budget). It came with WiFi and wired ethernet, both onboard. I have a wired router, but no wireless AP. I was wondering if I can plug in my ethernet port, and make my WiFi card act as a AP? I assume it would be done with some program from one of the repositories. If there is such a program, I think I could figure it out.

---

### Post by DiamondX on 2006-06-07
Hate to bump, but in 3 hours this post got pushed to page 3. Is it even possible (to make an access point with a wifi card)?

---

### Post by elamericano on 2006-06-07
Absolutely, but your card need to support it at the driver level in order to do some of the 802.11 AP functionality, like beaconing. Basically it's just another mode, not unlike Ad Hoc. I have an atheros based card, and using wlanconfig I can create my interface in the following modes: sta, adhoc, ap, monitor, wds, ahdemo. I don't know what all those do, but I've used the first four. Some cards call this mode "software ap", but the madwifi drivers are the only ones I know for sure support this on Linux.

This mode gives you ability to create open and wep networks, but if you want better security you can run hostapd on your computer and do virtually anything (many APs use this code internally): [http://hostap.epitest.fi/hostapd/](http://hostap.epitest.fi/hostapd/)

---

### Post by Ivan Matveich on 2006-06-07
It is tricky, but you can set this up by editing /etc/network/interfaces

```

auto lo
iface lo inet loopback

auto ethernet
iface ethernet inet dhcp

auto wireless
iface wireless inet static
        address 192.168.2.1
        netmask 255.255.255.0
        wireless-essid Something
        wireless-mode Master
        wireless-channel 10
        wireless-rate 11M

```

(Set the interface names "wireless" and "ethernet" in /etc/iftab.)

Then edit /etc/network/options

```

ip_forward=yes
spoofprotect=yes
syncookies=no

```

and reboot. Check these things:

1) does firefox on laptop load google.com?
2) do your other laptops see the "Something" access point?

If yes, then configure them as follows:

```

Manual IP configuration
Address: 192.168.2.2 (or .3, .4, .5 ... .254)
Gateway: 192.168.2.1
Network/netmask: 255.255.255.0
DNS/Nameserver: [whatever your ISP/router provides, check your laptop's /etc/resolv.conf]

```

and run "ping 192.168.2.2" on the laptop command line. (Make sure the other laptop is turned on and configured to use the "Something" access point.) You should see ping replies.

Now try loading google.com on the other laptop. Your router may not want to forward traffic from 192.168.2.x (ie, the other laptop), in which case this step will fail. Then we can talk about IP masquerading...

---

### Post by grsing on 2006-06-07
It won't really be an access point, but you can set up what is called an Ad-hoc network (or peer-to-peer, computer-to-computer, terminology varies, but you get the idea, only computers connecting wirelessly without an AP).  Then you connect one of them to the wired internet and have it share the connection with everyone else on the network.  I did it fairly early on when I found a PCI wireless card for very cheap and didn't have an AP, so it definitely can be done.  As for how to do it on Ubuntu, I haven't the faintest idea, but it is possible (it looks like it might be possible with the "create a new network" option in Network Manger (which you'll have to install from the repositories), but I've never tried it).

edit: those other replies weren't there when I started typing , but it's good to know it is actually possible to make it an AP.

---

### Post by Ivan Matveich on 2006-06-07
[QUOTE=grsing]edit: those other replies weren't there when I started typing , but it's good to know it is actually possible to make it an AP.[/QUOTE]

I'm actually not sure that his chipset supports master mode. Some drivers have issues with ad-hoc mode too, so it is not clear-cut which to recommend.

So, DiamondX, you can substitute "Ad-Hoc" for "Master" in your /etc/network/interfaces configuration, if that helps, and proceed just the same.

---

### Post by elamericano on 2006-06-08
Ad-Hoc will only support wep encryption, if security is something you care about. Ad-Hoc is also sometimes not supported to 54M rates or on 11a channels.

For IP forwarding, I usually create a bridge, that way connected clients can use DHCP from the ISP if it's available, and address translation is not a problem.

---

### Post by DiamondX on 2006-06-08
Thanks for all the help. Im guessing I should ask in the Dell forums if my card (onboard actually) supports it. I dont really care about security, I live in the grid, but not too close to many people. I dont think my card could reach them, and even if it could, most of them dont care/know about anything like this. It would mainly be for my PSP (so many interesting homebrew that use Wifi), but if it works well, I will put a card in a desktop and be able to use my laptop around the house. Where the router is, it gets uncomfortably warm. Especially in the summer.

I just cant see myself buying a real AP, just for 1 laptop and ocasionally a PSP... Looks like this will work!

---

### Post by grsing on 2006-06-08
[QUOTE=Ivan Matveich]I'm actually not sure that his chipset supports master mode. Some drivers have issues with ad-hoc mode too, so it is not clear-cut which to recommend.

So, DiamondX, you can substitute "Ad-Hoc" for "Master" in your /etc/network/interfaces configuration, if that helps, and proceed just the same.[/QUOTE]

Right, I just meant in general.

---

