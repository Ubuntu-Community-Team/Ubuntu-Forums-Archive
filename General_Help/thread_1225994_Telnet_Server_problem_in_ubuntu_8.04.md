---
title: "Telnet Server problem in ubuntu 8.04"
date: 2009-07-29
forum: General Help
---

### Post by Bob Unitt on 2009-07-29
I'm trying to do the exercise 'TimeServer' in Chapter 17 of 'Teach yourself Java 6 in 21 days', which runs a Time-server intended to be accessible from Telnet port 4415. The code is listed at <http://workbench.cadenhead.org/book/java-6-21-days/source/chapter17/TimeServer.java>.

I'm on ubuntu 8.04. I've installed the telnet server using openbsd-inetd and telnetd, and run it with 'sudo /etc.init.d/openbsd-inetd restart'. It would appear to be running correctly as I can 'telnet 192.168.0.2' and start a terminal session from a remote pc.

When I run the program it displays 'TimeServer Running', as expected. However if I issue the terminal command 'telnet 192.168.0.2:4415' from the remote PC, or 'telnet localhost:4415' from the same pc, I always get the message 'could not resolve localhost:4415/telnet: Name or service not known' (or '192.168.0.2' instead of 'localhost').

I've tried running both the client and the server both with and without 'sudo', doesn't make any difference.

Can anyone help with this ?

Bob

---

