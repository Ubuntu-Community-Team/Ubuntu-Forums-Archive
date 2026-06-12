---
title: "Azureus errors"
date: 2006-04-26
forum: General Help
---

### Post by spaceghoti on 2006-04-26
I've been using Azureus for a while, because I prefer using the SafePeer plugin rather than the standalone Peer Guardian tool (I find it has a huge memory leak).  However, since switching to Kubuntu 5.10 and the latest stable build of Fluxbox (0.9.14) I've discovered that Azureus is filling my .xsession-errors file with GB worth of errors.  They all go like this:

```
DEBUG::Wed Apr 26 12:57:33 CDT 2006::org.gudy.azureus2.ui.swt.StartServer::pollForConnectionsSupport::167:
  java.lang.NullPointerException
        at org.gudy.azureus2.ui.swt.StartServer.pollForConnectionsSupport(StartServer.java:121)
        at org.gudy.azureus2.ui.swt.StartServer.access$000(StartServer.java:45)
        at org.gudy.azureus2.ui.swt.StartServer$2.runSupport(StartServer.java:104)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
```

Can anyone help me figure out what's wrong and what I need to do to fix it?  I'd be content with just getting it to stop filling my error logs.

Thank you.

---

### Post by debian-user on 2007-08-22
Hello
I'm a debian-user.
I'm using the software of "guarddog".
I have had the same error.
I changed the setting of this one like below.

Firewall Configration
Protocol tab
Internet
Network Protocol
File Transfer
BitTorrent Peer : protocol is blocked -> protocol is permitted.
BitTorrent Tracker : protocol is blocked -> protocol is permitted.

This error is't apper after that.

---

