---
title: "openvpn/networking change = kernel panic"
date: 2009-12-20
forum: General Help
---

### Post by guvnr on 2009-12-20
WHAT I DID .. installed openvpn/bridge-utils, rejigged my interfaces file to allow for br0.  Reboot.  

RESULT .. "Kernel panic - not syncing: Attempted to kill init!"

I know this is to do with the changed networking file because when I go back in and revert that (via another OS) this kernel boots fine.

OTHERWISE .. 9.10 Desktop, fairly uncomplicated system, tho it does have ndiswrapper and I installed NFS to it quite recently*.

*would it be better to install that after openVPN?

---

### Post by guvnr on 2009-12-21
anyone?  really could do with a hand on this, would be most grateful.

some more background I should have mentioned, that may be somehow at fault ..

the original /etc/network/interfaces file read:-

auto lo
iface lo inet loopback

and, changed to allow for the bridge (bridging via ra0):-

auto lo br0
iface lo inet loopback
[FONT=monospace]
[/FONT]iface br0 inet static [FONT=monospace]
[/FONT]   address 192.168.1.10 [FONT=monospace]
  [/FONT]netmask 255.255.255.0[FONT=monospace][/FONT]
   gateway 192.168.1.1[FONT=monospace]
  [/FONT]bridge_ports ra0
iface ra0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  up ip link set $IFACE promisc on
  down ip link set $IFACE promisc off
  down ifconfig $IFACE down ... so when I make the above change, I get the "kernel panic".  then, if I revert to the original interfaces file, login is normal .. but I am no further forward setting up openVPN.

---

### Post by guvnr on 2009-12-23
er, anyone?

---

