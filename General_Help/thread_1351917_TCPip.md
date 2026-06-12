---
title: "TCPip"
date: 2009-12-11
forum: General Help
---

### Post by kennethtb on 2009-12-11
Hi Ask a silly question I have Ubuntu 9.10 full hard disk installed  no other partitions. My question being .. is there any software available similar to PC Pitstop Optimize? which I used to use to improve my internet speed on Windows XP - this program adjusted many parameters within my PC and really did improve my internet reception. I understand that Ubuntu has no registry but I am still suffering from poor internet broadband (300-500KB) continually going up and down - this being due to living in an area of Spain that still has "Flintstone" technology. I hesitate to press the submit button but here goes....

---

### Post by undecim on 2009-12-11
The program you are talking about probably just adjusted your settings on windows to give you your full bandwidth (windows restricts you to 80% of your bandwidth by default)

Ubuntu, however, allows 100% bandwidth by default. I highly doubt that you were getting any better speed in windows.

A few tips you might find useful though:

in firefox, type "about:config" in your browser bar, and in the "filter" bar, type "pipelining", and change these values:
"network.http.pipelining" to true
"network.http.proxy.pipelining" to true
"network.http.pipelining.maxrequests" to 10.

then, right click anywhere on the page and select New->Integer. Name it "nglayout.initialpaint.delay" and set it to 0

And finally, restart Firefox.

You can also try out Google Chrome. Google just recently released a Linux version, but it's still in beta, so it can be a bit buggy at times.

---

### Post by kennethtb on 2009-12-11
Thanks a bunch for your advice ... I have downloaded the Debian package for Google-chrome-unstable and for the moment it seems very positive and much quicker in loading web pages so for the moment I have made this my default browser.

---

