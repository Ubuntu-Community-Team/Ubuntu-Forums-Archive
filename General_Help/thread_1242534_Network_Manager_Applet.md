---
title: "Network Manager Applet"
date: 2009-08-17
forum: General Help
---

### Post by CarlosinFL on 2009-08-17
Let me first say I have no problem connecting to the Internet. My  Ubuntu machine is connecting perfectly to the web. I am making this post from my PC now however in the upper right hand corner of Gnome, I have an icon that shows me when I am connected to the LAN (wired) and it is not working for whatever reason.

My PC has two identical PCI NIC's installed...

```
7.199282] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
[    7.199328] e1000 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.463402] e1000: 0000:03:00.0: e1000_probe: (PCI:33MHz:32-bit) 00:1b:21:07:8b:71

```

I know they are recognized however the Network Manager Applet in Gnome is not recognizing my NIC or connection info for some reason...I don't understand why it doesn't see my active eth0 wired connection? In CLI I can do a ifconfig eth0 and I properly see my static wired IP configuration I determined during install.

Anyone know what the deal is?

---

### Post by signseeker on 2009-08-17
You could try disabling the port you arent using via bios?

---

### Post by CarlosinFL on 2009-08-17
I plan on using both eventually via NIC bonding but I don't understand why the applet wont see eth0, just eth1.

---

