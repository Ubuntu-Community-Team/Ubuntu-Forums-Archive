---
title: "vncviewer and UltraVNC incompatibility"
date: 2010-06-18
forum: General Help
---

### Post by axonxorz on 2010-06-18
I've been trying to set-up a helpdesk-esque service for personal clients.
I've tried UltraVNC's single-click builder utility to make a one-touch executable for help.

From the helpdesk machine, I run
```
# vncviewer -listen
```
which starts listening on port 550

When I use the One-touch executable on any windows machine, it will connect to my listening VNC client and get hung up. The vncviewer outputs:
```
Fri Jun 18 13:30:41 2010
 CConn:       Accepted connection from 127.0.0.1::47265
 CConnection: reading protocol version
 CConnection: Server supports RFB protocol version 3.16
 CConnection: Using RFB protocol version 3.8
 CConnection: processing security types message
```

It gets hung up at 'processing security types message' and does not go any further.

More research has led me to a one-click solution using TightVNC on the windows end. This solution works. I'm just worried that there's some incompatibility between UltraVNC and Ubuntu's stock VNC viewer (based on RealVNC)

Note: I've tried this with a fresh installation from the repos on ubuntu Hardy, Intrepid and Lucid, as well with a fresh compile-from-source of the latest version of the viewer from the RealVNC website.

Any insight?

---

