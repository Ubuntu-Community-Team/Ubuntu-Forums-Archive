---
title: "Port forwarding not working"
date: 2009-12-02
forum: General Help
---

### Post by Warthaug on 2009-12-02
This is driving me crazy.

I am trying to setup port forwarding for transmission on my wifes computer.  I went into my routers configuration, set a static IP for my wifes computer, then opened a port for TCP/UDP traffic.  I then opened transmission and entered that as the port - no love; transmission see's the port as closed.

So I figure something must have gotten buggered up, so I repeated the above procedure, picked a different port/IP addy, and got the same result.  The real odd thing is that [open port checker]("http://www.yougetsignal.com/tools/open-ports/") sees the port as OPEN!

To make things even more confusing, the exact same procedure (different IP address and port) worked perfectly on my laptop, which is running the exact same ubuntu (9.10, 64bit) as my wifes computer.

I don't think this is a transmission issue - deluge also sees the port as closed.

Any ideas?

Bryan

---

### Post by lovinglinux on 2009-12-02
Both Deluge and Transmission needs to contact a remote server to test if the port is open. If the remote server is down, they will say the port is closed. For instance, Deluge site changed address recently, so the port checking functionality is not working at all. I don't know about transmission, but it's probably the same issue.

Checking the port with third-party services like Open Port Check Tool or CanYouSeeMe is a better option.

Anyway, check the [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923) for some tips and for troubleshooting BitTorrent stuff.

---

### Post by Warthaug on 2009-12-04
Thanx for the reply.

The problem sorted itself out - left the computer off for a day, turned it back on, and the port has magically forwarded itself...

---

