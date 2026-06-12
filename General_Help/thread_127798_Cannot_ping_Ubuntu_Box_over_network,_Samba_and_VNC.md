---
title: "Cannot ping Ubuntu Box over network, Samba and VNC not accessible"
date: 2006-02-09
forum: General Help
---

### Post by curarine on 2006-02-09
I hope someone can help me with this. I have a machine with a Netgear WG311T network card happily connected to my router using the standard madwifi driver and the help of wpa_supplicant. I can connect to whatever I want to from the Ubuntu box, and ping other computers on my local network.

However, I cannot ping my Ubuntu machine from any other computer on my local network, or even from my wireless router. Additionally (and probably for the same reason), I cannot access Samba shares or my VNC server from any computer, though I can connect to VNC from the Ubuntu box using localhost. I've installed SWAT and xinetd, and they appear to be working correctly. I can connect to webmin, SWAT and CUPS through firefox as well, again on the localhost.

I have tried:

1. Installing Firestarter and configuring it to allow access for "everyone" to the SMB and VNC ports.

2. Disabling Firestarter and running without iptables policies set.
neither works.

Additionally, ifconfig shows that the vast majority of RX'd packets on my Ubuntu box are having frame errors. no other errors are reported.

I'm using Breezy 5.10, any updates available through the update service are applied. Not being able to access any shares on the machine is a bit of a drag, though, as this was formerly my Windows XP-based file and print server.

---

### Post by dickohead on 2006-02-09
Sounds like an issue with your wireless router, something to do with the way it connects the wireless network to the wired one.

Am I correct in assuming that your Ubuntu machine is wireless and everything else is wired?

---

### Post by curarine on 2006-02-09
nope. actually, almost all the machines are wireless.

---

### Post by curarine on 2006-02-09
and, of note, none of the other computers have any problems reaching the machine when I boot it back into windows.

Thanks for your quick reply, though...

---

### Post by dickohead on 2006-02-09
Awesome... that's me stuffed! I've yet to get wireless working with Linux, but if certain ports are blocked by your router could this have anything to do with it? Internally I don't think it would matter, but you never what machines have what firewall settings...

---

### Post by dickohead on 2006-02-09
Okay, so it's definately Linux related then. I'd check my port settings, remove all firewalls and security (as long as you have a router with a firewall your internal network will be fine from net based intrusions) and then try again.

Since ping doesn't work, that worries me a bit... how does your Ubuntu machine get an IP, you sure it's using DHCP?

The issue won't have anything to do with the services on your machine, getting the most basic communications working first should then enable everything else. So once we figure out what's wrong with your IP addressing/gateway settings/DHCP ping should work and then your services will operate as intended.

---

### Post by curarine on 2006-02-09
The ubuntu box gets its IP from the router via dhcp. this has never been a problem. the subnet, gateway and other information specified for the ath0 adapter are all correct, and the same as they would be in windows. and the network connection is working outbound from ubuntu to anywhere on the web or on my intranet, so i'm pretty sure this isn't the problem.

I've tried disabling the firewall and checking that the iptables policies are clear. Still no ping.

I agree with you, though. there's some basic connectivity issue here that's preventing packets from my other machines from getting in to the ubuntu box.

---

