---
title: "4th Time is a Charm"
date: 2006-03-17
forum: General Help
---

### Post by haze03 on 2006-03-17
Last Couple of times I have gotten no response and since it has been ~6months and I can't get on-line, hopefully I can get some help this time.

Having trouble with wireless like many, so went through the troubleshhoting guide. Here is what I got on first step. Where am I screwing up?

description: Wireless interface
product: Ralink RT2500 802.11 Cardbus Reference Card
vendor: RaLink
physical id: c
bus info: pci@00:0c.0
logical name: ra0
version: 01
serial: 00:0e:2e:5d:59:04
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rt2500 multicast=yes wireless=RT2500 Wireless
resources: iomemory:dc000000-dc001fff irq:11

I use WEP. I typed it in the network settings as ASCII. After running iwconfig I get this:

lo no wireless extension

eth0 no wireless extensions.

ra0 RT2500 Wireless ESSID: “2WIRE356”
Mode- Managed Frequency- 2.437 GHz Access Point- 00:0D:72:85:8A;A1E
Bit Rate- 11 Mb/s
RTS thrff Fragment thr- off
Link Quality=70/100 Signal level=-53 dBm Noise level=-193 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
haze03 is online now Edit/Delete Message

here is my readout from ifconfig:

lo
link encap:local loopback
inet addr:127.0.0.1 Mask:2555.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:12266240 errors:0 dropped:0 overruns:0 frame:0
TX packets:12266240 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txquelan:0
RX bytes:918820813 (876.2 MiB) TX bytes:918820813 (876.2 MiB)

ra0
link encap:Ethernet HWaddr: 00:0E:2E:5D:59:04
inet6 addr: fe80::20e:2eff:fe5d:5904/64 Scope:Link
UP BROADCAST RUNNING MUKTICAST MTU:1500 Metric:1
RX packets:313497 errors:0 dropped:0 overruns:0 frame:0
TX packets:180339 errors:10 dropped:0 overruns:0 carrier:0
collisions:1288 txquelan:1000
RX bytes:28312045 (27.0 MiB) TX bytes:1320563 (12.5 MiB)
Interrupt:11

i tried checking dhcp and got No DHCOOFFERS received and No working leases in persistent database - sleeping.

the guy i rent from has som funky 2wire router/modem/switch something from the dsl company. i don't know much about it and he is techno dunce. he can turn a computer on and vheck fantasy football and that is about it.

---

### Post by DJ Scribblinni on 2006-03-17
Your situation seems like it is mostly the routers fault.  Either DHCP isn't operating, no more addresses are available, or it's just not working like it should.  Everything seems fine in the code you wrote out.  I would suggest finding a way to find more information on that "funky 2wire router/modem/switch something"  Maybe a static IP can help...

---

### Post by Jason_25 on 2006-03-17
The problem is most likely with your wep key.  For it to show your key, you need to type 
```

sudo iwconfig

```
Sometimes the graphical tool doesn't correctly set the key.
Try 
```

sudo iwconfig ra0 key insertkeyhere

```

---

