---
title: "First time installing LTSP,  PXE-E53, need help please."
date: 2012-02-21
forum: General Help
---

### Post by Kissell on 2012-02-21
I downloaded the Ubuntu 11.10 64-bit alternative CD and pressed F4 at the beginning of the install to setup an LTSP server.  During installation I saw a screen saying it was installing LTSP.  

But after the install, I updated the server with apt-get and rebooted it..  then tried to connect a laptop via network boot (the laptop is wired, plugged into the same dlink switch as the server, no VLANs), and got this error:
> 
PXE-E53: No boot filename received


The DHCP server is not any of these devices, it's a router connected to the d-link switch and a DSL modem.

The server only has one network card.

I googled, came back to the server and thought maybe it didn't have the client installed and that's why I couldn't boot to it, so I tried:
```
sudo ltsp-build-client
```
but it said:
> NOTE: Root directory /opt/ltsp/amd64 already exists, this will lead to problems, please remove it before trying again. Exiting.
error: LTSP client installation ended abnormally


So it looks like the server is installed and ready, but I can't connect to it from the client...  is there some configuration I need to do after installing the server, or is it supposed to just be ready to go?  I've never done this before and have been wanting to do it for years, so finally did it, but it doesn't work. :(

---

