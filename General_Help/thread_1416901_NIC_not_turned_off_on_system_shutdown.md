---
title: "NIC not turned off on system shutdown"
date: 2010-02-26
forum: General Help
---

### Post by Admiral_Payne on 2010-02-26
It appears I've got some strange driver problem.. When I shut down this computer, the NIC apparently doesn't go off. The LEDs next to the ethernet socket keep blinking, so does the LED on my ethernet switch.

I don't have this problem when using XP, only Karmic. That leads me to think that there's something wrong with the network driver. My NIC is on-board, the ASUS M3A32-MVP. According to System Info this is the Marvell 88E8056 PCI-E.
It seems like ASUS doesn't have the drivers on their website (anymore), because their website search returns empty handed. Also the motherboard product page doesn't appear to know it.

Anyone have any tips / ideas? I'm just unplugging the machine before turning it off now... as it appears to be disturbing the rest of my network :(

---

### Post by efflandt on 2010-02-26
Your BIOS may be set by default to "Wake on LAN".  Check your CMOS settings (whatever key you need to press from the BIOS splash screen before grub comes up).

---

### Post by Admiral_Payne on 2010-02-26
> **efflandt said:**
> Your BIOS may be set by default to "Wake on LAN".  Check your CMOS settings (whatever key you need to press from the BIOS splash screen before grub comes up).
Yeah I checked that too.., but it was switched off :(

---

### Post by doas777 on 2010-02-26
I know a perpetually powered nic is prequisite to getting WOL to work, but I'm not sure that the power managment is actually part of WOL (eg you may have to disable it elsewhere first).

---

### Post by Admiral_Payne on 2010-02-26
Hmmmm..., but where else than in the BIOS would this setting actually be? I've always had WOL off in the BIOS and it doesn't make a difference.

By the way, just now I've switched the Network Manager off and shutdown the system. The problem doesn't show up D: Possible bug in Network Manager?
I've totally forgot how to manually configure /etc/network/interfaces, but I'll try to get it up without Network Manager and see what happens.


Right. The following works.
Edit /etc/network/interfaces to:
```
auto eth0
iface eth0 inet static
address 192.168.1.50
gateway 192.168.1.254
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
```

Reboot networking:
```
sudo /etc/init.d/networking restart
```

Remove network-manager:
```
sudo apt-get remove network-manager network-manager-gnome
```

---

