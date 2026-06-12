---
title: "Boatloads of issues, BT, obex, boot - Lucid 10.04"
date: 2010-06-13
forum: General Help
---

### Post by keithspg on 2010-06-13
Guys, what is going on? I get an update today and now I cannot browse my phone (obex/gvfs/dbus error)?!? Also, Blueman now (as of an update) will allow my iphone to connect (tethering via BT) but network manager cannot see it nor recognizes that it is connected though the phone shows connected. ifconfig shows bnep0, but it has no ip address and no connectivity. USB tethering works fine with ipeth-utils, so I am still good via wire.

```
[   19.987194] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.987198] Bluetooth: BNEP filters: protocol multicast
...
[  813.568233] bnep0: no IPv6 routers present
...
bnep0     Link encap:Ethernet  HWaddr 00:15:83:15:a3:10  
          inet6 addr: fe80::215:83ff:fe15:a310/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:53 (53.0 B)  TX bytes:172 (172.0 B)

```It is still not resolved on bootup (grub2/plymouth/uvesa) I have the work around, but, really why is this not the default? 

Lucid does not work well on my Dell D630 laptop on suspend. It comes back and sound is no longer available, the BT dongle does not come back, all requiring a reboot. 

if I connect my iphone as ipeth, I have to remove the phone USB cable, shut down rhythmbox, restart rhythmbox then plug in the phone, then I can transfer music again...

I also do not understand why gnome-bluetooth is the default BT manager. Blueman at least tells you what it is doing and why and gives you better visual cues and menu options. 

Karmic got to be pretty decent by January or so. Lucid still has a ways  to go. My guess is that by October it should be pretty solid. 

Sorry for the rant, but it was getting better then, today, I get updates that break things...

Keith

---

