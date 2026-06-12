---
title: "eth1 recieving plz need help"
date: 2006-01-29
forum: General Help
---

### Post by njzillest on 2006-01-29
i got my eth1 working (wired) but now all i do is recieve. I use DHCP broad cast to obtain my ipadress. It sais its connected but all i do is recieve signals, i dont send any out. Im not able to load any internet pages...

---

### Post by dcstar on 2006-01-29
[QUOTE=njzillest]i got my eth1 working (wired) but now all i do is recieve. I use DHCP broad cast to obtain my ipadress. It sais its connected but all i do is recieve signals, i dont send any out. Im not able to load any internet pages...[/QUOTE]
What does "sudo ifconfig" show?

---

### Post by rudeboyskunk on 2006-01-29
i have the same problem; i posted about this too.  here is what my ifconfig says:

eth1      Link encap:UNSPEC   HWaddr  00-40-96-40-9D-1E-00-00-00-00-00-00-00-00-00-00
             UP BROADCAST  RUNNING  MULTICAST     MTU:2312    Metric:1
             RX packets:89  errors:29558  dropped:0  overruns:0  frame:29558
             TX packets:0  errors:0  dropped:0  overruns:0  carrier:0
             collisions:0  txqueuelen:100
             RX bytes:8524  (8.3 KiB)    TX bytes:954  (954.0 b)
             Interrupt:3  Base address:0x100


and then all the lo stuff.


anybody else having this problem?  it's with Breezy.

---

### Post by dcstar on 2006-01-29
[QUOTE=rudeboyskunk]i have the same problem; i posted about this too.  here is what my ifconfig says:

eth1      **Link encap:UNSPEC**   HWaddr  00-40-96-40-9D-1E-00-00-00-00-00-00-00-00-00-00
             UP BROADCAST  RUNNING  MULTICAST     MTU:2312    Metric:1
             RX packets:89  errors:29558  dropped:0  overruns:0  frame:29558
             TX packets:0  errors:0  dropped:0  overruns:0  carrier:0
             collisions:0  txqueuelen:100
             RX bytes:8524  (8.3 KiB)    TX bytes:954  (954.0 b)
             **Interrupt:3  Base address:0x100**

and then all the lo stuff.

anybody else having this problem?  it's with Breezy.[/QUOTE]
There is no IP address assigned to the card, as an example, here is my data:

eth0      Link encap:Ethernet  HWaddr 00:0D:61:22:B6:60
          **inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0**
          UP BROADCAST RUNNING MULTICAST  MTU:1472  Metric:1
          RX packets:16705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11067537 (10.5 MiB)  TX bytes:1400567 (1.3 MiB)
          Interrupt:18 Base address:0xe400

Either it is not communicating with a DHCP server, or there is another problem.

Try manually assigning an IP address and see if that gets you anywhere.

BTW, last time I looked, IRQ3 was used for PC Serial ports, you may want to check your PC's BIOS to see why it allocated that IRQ to a LAN card - there could be a clash that is causing a problem.

---

### Post by rudeboyskunk on 2006-01-29
yeah i tried the manual assignment, didn't get me anywhere.  i tried switching to no WEP on my router, didn't do anything.

it's strange because under Hoary it worked fine.  I think I may just reinstall Hoary, see if it works then, then just upgrade from there rather than do a complete overinstall of Breezy.

---

### Post by rudeboyskunk on 2006-01-29
i also just noticed something very odd.  the laptop i install on shows up on the dhcp clients table in my router DURING INSTALL, but not after.

---

