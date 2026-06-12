---
title: "Deluge torrent client issue"
date: 2011-01-04
forum: General Help
---

### Post by WiReIs on 2011-01-04
Hello, first of all apologies if this is in the wrong section.. i wasn't too sure on which section this topic fell in to..

anyway i am having a bit of difficulty regarding my Deluge torrent client on my Ubuntu 10.10 setup, i have been using Ubuntu for about 2 years now and i have always used Deluge as my torrent client, however i have just got a new computer and installed Deluge via Ubuntu software center and everything was fine for a while but for some reason now every time i open Deluge client and it connects as normal to Peers, any computer (except mine) on my network gets disconnected from the network WLAN or LAN and internet connection runs very slow, at first i thought this was me hogging all of our bandwidth but my torrent speeds are merely reaching 100kb/s most of the time, i checked deluge ports (Edit > Preferences > Test Active Port) and i receive a red exclamation mark symbol

heres my setup(default);

Network settings;

Incoming Ports

Use random ports(checked)
From:6881 to 6891

Outgoing Ports

Use random ports(checked)

From 0 to 0

Interface: eth1

Peer TOS Byte: 0x00

Network Extras;
UPnP(checked) NAT-PMP(checked) Peer Exchange (checked)
LSD(checked) DHT(checked)

Encryption:
Inbound:Enabled Outbound:Enabled
Level:Either
Encrypt entire stream(checked)

I haven't changed any of the settings from Default..

Has anybody else experienced this problem? i've tried google but i cant seem to find anything relating to my issue specifically. 

would i benefit from port forwarding??

Many thanks in advance :)

---

### Post by lithopsian on 2011-01-04
It is probably swamping your router with connections, probably not even fully open connections.  Deluge seems to be particularly bad for this for some reason.

There are several solutions.  Ideally you can configure your router to time out UDP requests more quickly so they don't build up to ridiculous numbers.  These should be fleeting things but for some reason routers hold onto them for hours.  Not all routers can be configured to time out bad connections more quickly, but have a look.

Then you can reduce several settings in Deluge.  First, drop your total connections to a low number, maybe 50.  Then drop the half-open connections to 2, and the maximum connection attempts per second to 2.  If these very low settings solve your problem then at least you know you're on the right track.  Increase them to higher levels until you see problems again.  Note that problems will take a while to appear when you are nearly at safe settings.

A few other things to try are turning off PnP, which sometimes just gets all tangled up, and turning off DHT which throws out a lot of requests very quickly.

---

### Post by lithopsian on 2011-01-04
I just noticed you asked about port forwarding.  It is generally considered a better solution than PnP for providing ports, but obviously it means you have to do some work yourself.  Since you know the ports you want to use then I recommend forwarding them and switching off the PnP.

Make sure no other application needs ports before you switch of PnP completely!  The obvious ports should all be open automatically but games use weird ports, as do many other internet applications that aren't email or web.  Ideally open ports for each one and don't let your router do PnP.

---

### Post by WiReIs on 2011-01-04
Thankyou for the information and for your advice lithopsian

I may just go ahead with the port forwarding on my router

Thanks

---

### Post by Vermind on 2011-01-04
Deluge, Transmission, Azureus or any other BitTorrent client should work fine even if behind a NAT. I don't have a direct answer for you, but if you have a lot of connections to peers (like hundreds) you may clog the whole upload bandwidth with connection handling and a few uploads to those peers. Perhaps you can limit the number of peers set for Deluge?

Also, I like to keep my torrent down/up rates below those reported by an Internet speed test website. Check your connection bandwidth from: [http://www.speedtest.net/](http://www.speedtest.net/)

---

### Post by Cas07 on 2011-01-16
> Interface: eth1

FYI: I doubt it is causing your issues but this should be an IP address. The use of the word Interface is a little misleading here :)

---

### Post by Cas07 on 2011-01-16
> Interface: eth1

FYI: I doubt it is causing your issues but this should be an IP address. The use of the word Interface is a little misleading here :)

---

### Post by piquat on 2011-01-17
> **WiReIs said:**
> 
Use random ports(checked)

From 0 to 0


Using a random port that rests between 0 and 0 could be the problem, if you really have it set up this way.

---

### Post by Cas07 on 2011-01-17
> **piquat said:**
> Using a random port that rests between 0 and 0 could be the problem, if you really have it set up this way.

That is not a problem. Deluge does not use those port numbers for its random port selection. This is reflected by the fact that when 'random ports' is ticked, the port number boxes are greyed out.

---

