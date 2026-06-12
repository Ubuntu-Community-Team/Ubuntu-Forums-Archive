---
title: "Traffic to 555.555.555.555"
date: 2011-10-17
forum: General Help
---

### Post by AlexBooton on 2011-10-17
Hi,

Three clients on my LAN (out of 10 or so) are attempting traffic to 255.255.255.255.  This happens about every 30 seconds.

Here's a log entry:
Oct 17 15:16:02 pti-server kernel: [2435961.812885] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0f:fe:fd:d0:c1:08:00 SRC=192.168.0.62 DST=255.255.255.255 LEN=137 TOS=0x00 PREC=0x00 TTL=128 ID=33828 PROTO=UDP SPT=17500 DPT=17500 LEN=117 

What is this about?  Is there some piece of software that does this?

Thanks

---

### Post by gsmanners on 2011-10-17
That's some kind of UDP on 17500. Might be dropbox doing that.

---

### Post by AlexBooton on 2011-10-17
> **gsmanners said:**
> That's some kind of UDP on 17500. Might be dropbox doing that.

Thanks!  I think that may be it.

---

