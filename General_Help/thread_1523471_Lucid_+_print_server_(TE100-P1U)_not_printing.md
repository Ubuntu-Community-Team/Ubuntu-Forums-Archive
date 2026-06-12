---
title: "Lucid + print server (TE100-P1U) not printing"
date: 2010-07-03
forum: General Help
---

### Post by MrKimi on 2010-07-03
I'm struggling with getting my print server working since my Lucid upgrade. I have a TrendNet TE100-P1U attached to my LAN. I've noticed other people have trouble with similar setups because of network issues. But my problem seems to be different. The Trendnet box has a fixed IP address (192.168.123.10) and I can browse to that and check the status consistently. It tells me the box has detected the printer (HP 880C) and that it is on line. So far so good.

I configured the printer like this:
```

<Printer HP-Deskjet-880c>
Info HP Deskjet 880c
MakeModel HP Deskjet 880c hpijs, 3.10.2
DeviceURI lpd://192.168.123.10/U1
State Idle
StateTime 1277720564
Type 8425484
Filter application/vnd.cups-raw 0 -
Filter application/vnd.cups-postscript 100 foomatic-rip
Filter application/vnd.cups-pdf 0 foomatic-rip
Accepting Yes
Shared No
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
```which roughly matches what I once had working on Hardy a while back (I hardly ever actually print anything and I've changed printers since then, but the TrendNet box is the same).

With that setup when I print a test page it seems to launch okay, and the TrendNet box reports that it is 'printing' rather than 'online'. But nothing actually happens to the printer, and Lucid shows the job as 50% done, and it never progresses from there.

The printer works fine when I plug it directly into the USB and I'm using the same printer driver in both configurations. I'm a little suspicious of the driver, but I've tried several others and so far none are working.

I'm also suspicious of the device URI. I've used lpd://192.168.123.10/U1 but under Hardy I know I left the U1 out, and reading other posts on this suggest other people use different values. Possibly this doesn't matter, possibly whether it matters or not has changed, though the box is the same so I don't see why.

Any help is much appreciated.

---

