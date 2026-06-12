---
title: "What is DCOM-scm ( Firestarter alert ) ?"
date: 2009-07-02
forum: General Help
---

### Post by credobyte on 2009-07-02
Every 5-10 minutes I see my Firestarter alerting me about this event :
> Time: Jul  3 01:38:32 Source: 94.30.XXX.12 Destination: 94.30.XXX.129 In IF: eth0 Out IF:  Port: 135 Length: 64 ToS: 0x00 Protocol: TCP Service: DCOM-scm

What the hell is DCOM-scm ?

---

### Post by synapsys on 2009-07-02
> DCOM-scm is the DCOM interface to the Service Control Manager, which
allows for the starting, stopping, etc. of the background services on a
Windows system.  Unfortunately, Microsoft didn't get the security quite
right in this subsystem.

This is an attempt by a compromised Windows box to compromise your Linux
system by scanning the local blueyonder IP address range, hoping it will
find another open Windows system.

HTH
Taken from [http://mailman.lug.org.uk/pipermail/wolves/2005-August/016232.html](http://mailman.lug.org.uk/pipermail/wolves/2005-August/016232.html)

So.....block that first ip address completely.....

Unless it's a box you own.... then scan for viruses.....

---

### Post by credobyte on 2009-07-02
That's exactly what I found .. asked here in hope to get a bit more info :)
There's 1 thing I'm curious about - is it normal to have 400+ blocked connections in 1 hour ?

---

### Post by synapsys on 2009-07-02
No.... that means another computer is hammering away at yours, trying to break in. You need to blacklist the ip. 

You can also try turning off your router for about a minute or two and the turn it back on. This should reset your public ip address which will essentially give you a new identity on the internet.

---

### Post by credobyte on 2009-07-02
I've a static IP address and I'm not behind a router/modem. More or less, IP blocked .. let's see how it will turn out !

---

