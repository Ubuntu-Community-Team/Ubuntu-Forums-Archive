---
title: "Fix &quot;Unknown&quot; on Netgear Router?"
date: 2011-11-03
forum: General Help
---

### Post by Jose Catre-Vandis on 2011-11-03
This is a minor annoyance but could be having a wider impact when looking for computers by name on my network.

I dual boot my Xubuntu 11.10 PC with Windows 7. When on W7 if I log on to my router and check "Attached Devices" the router shows my IP address and Computer name (as seen in Computer > Properties). When I boot into Xubuntu and make the same check I see the IP address but the name is "UNKNOWN".

I have been through /etc/hosts and /etc/hostname, and also tried edits in /etc/dhcp/dhcp.conf (no dhcp3.conf on my machine) but to no avail.

My server (10.04.2 server) is named correctly by the router.

Unless I specifically name my PC on other PCs (in /etc/hosts) I cannot find it on the network from other machines.

So where is the setting needed or is this broken in Oneiric?

---

### Post by gsmanners on 2011-11-03
Might be an IPv6 thing.

---

### Post by Jose Catre-Vandis on 2011-11-04
Worth a try, but ipv6 is disabled :(

---

### Post by Jose Catre-Vandis on 2011-11-09
bump ?

---

### Post by Jose Catre-Vandis on 2011-11-12
OK, sorted - it's a problem with the router, only sees netbios names, so I had to install samba (will work on this so only nmbd is running and not smbd too). You need to put:
```
netbios name = yourpcname
``` in the [global] section of /etc/samba/smb.conf and restart smbd ```
sudo service smbd restart
```

There is another program called **[lisa]("http://lisa.sourceforge.net/")** that should allow the issue of a netbios name but I could not get it to compile (after installing automake 1.7 as a dependency). If anyone has had success installing **lisa** please let me know how.

---

