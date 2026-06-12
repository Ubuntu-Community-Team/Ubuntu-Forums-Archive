---
title: "NTP on laptops?"
date: 2011-11-20
forum: General Help
---

### Post by Palmstroem on 2011-11-20
Hello friends,

I learned that ntp lets you synchronize your PC time with UTC via internet - which is certainly important on servers. However, nowadays you notice that ntp is quite often also running on desktop computers, even on laptops with WLAN etc.

Is this a good idea? After all, laptops are not online all the time, they get connected to many different networks of (sometimes) low bandwidth or less stability...

---

### Post by Lars Noodén on 2011-11-20
NTP works fine on laptops.  If you are disconnected from the net when it tries to sync, then it will just log an error that the remote clock was unreachable.  No big deal.  

It's only a few packets now and then so it's nothing that will consume bandwidth, if that's what you are worried about.  If you are worried about the quality of the connection, latency, etc, that's part of the protocol to figure out and compensate for that.

---

### Post by Palmstroem on 2011-11-20
Thanks, Lars, you made it very clear.

And yes, increasing local traffic by NTP was my main concern.

---

### Post by Lars Noodén on 2011-11-20
If you are curious you can watch it on port 123 with Wireshark or tcpdump.  It really is only a few packets every once in a while.

---

