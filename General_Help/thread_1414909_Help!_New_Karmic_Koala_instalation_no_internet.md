---
title: "Help! New Karmic Koala instalation no internet"
date: 2010-02-24
forum: General Help
---

### Post by mjmj177 on 2010-02-24
Hi all.

I have a Dell Latitude D620 which came with Windows XP. I have just installed Ubuntu 9.10 on the laptop so it can dual boot but I can't connect to the internet.

I have a dynamic IP allocated by my broadband service provider which I access by a wired Netgear DM111P router (not cable). It still works fine when booting up windows.

I've read through lots of posts by others trying to find a solution as the 9.10 install has just been done and I've not changed anything.

My tentative assessment is the laptop, when running Ubuntu, is not communicating with the router as there seems to be no IP address allocated by the router.

Can anyone suggest anything as i want to be free of MS! :(

---

### Post by mjmj177 on 2010-02-24
A bit more info...

ifconfig eth0 up comes back permission denied

lspci -v shows Ubuntu recognising the ethernet controller as a Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02) although the capabilities shows <access denied>

Pinging the router on 192.168.0.1 gets no response

The two lights when the ethernet cable plugs into the laptop show one as unlit and the other orange rather than green

When trying to display Connection information after right clicking the internet icon (top rightish of screen) shows No Active Connections Found

Looking at the detail in Network connections I have one named 'Ifupdown (eth0)' which shows as last used never and does allow me to edit

Another is called 'Wired Connection 1', has a blank MAC address screen and MTU set to automatic. Connect Automatically is checked and the IPv4 Settings are set to Automatic (DCHP) with a blank DHCP client ID. IPv6 Setting are set to Ignore

---

### Post by mjmj177 on 2010-02-24
I have also tried sudo pppoeconf which said I had 3 ethernet devices
eth0
eth0:avahi
wlan0

After the wizard ran it still didn't work returning the message

Sorry I scanned 3 interfaces, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem

This message came back with the laptop connected to the router and the same with it not connected. I'm sure its not the router / cable / broadband connection as these work fine on the laptop I'm using to post this and also on the Dual boot laptop when in windows.

Grrrrrrrrrrrrr........!

---

### Post by mjmj177 on 2010-02-24
Solved it, apparently I needed to reset the router by switching it on an off before switching between laptops...:)

---

### Post by Iowan on 2010-02-24
I know some modems will "lock onto" a specific MAC address, and must be reset when connecting a different machine, but I'm surprised that a router would require it... Does that happen even if you use different ports for the laptops - or is that something you can try?

---

