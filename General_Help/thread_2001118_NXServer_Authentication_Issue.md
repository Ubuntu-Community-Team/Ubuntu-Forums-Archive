---
title: "NXServer Authentication Issue"
date: 2012-06-10
forum: General Help
---

### Post by digioz on 2012-06-10
Hello All,

I am having trouble connecting to a Linux Server using NX Client for Windows 7. It gives the following error:

> NX> 203 NXSSH running with pid: 7124
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.149 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.followed by this:

> The NX service is not available or the NX access was disabled on host 192.168.1.149.When I run the "nxserver -- status" command I get the following:

> NX> 100 NXSERVER - Version 1.5.0-61
NX> 900 Connecting to server ..
NX> 204 Authentication to NX server failed.
NX> 110 NX Server is stopped
NX> 999 ByeBut when I try to start it, it says the service is already running!

> NX> 100 NXSERVER - Version 1.5.0-61
NX> 500 ERROR: Service already running
NX> 999 ByeThis doesn't make a lot of sense. :confused: The two computers on the same local network. I used the following instructions when setting up the NXServer:

[http://wiki.centos.org/HowTos/FreeNX](http://wiki.centos.org/HowTos/FreeNX)

Anyone know what the problem may be?

Thanks,
Pete

---

### Post by digioz on 2012-06-11
Anyone have any suggestions? I really need to get this going. :(

Pete

---

### Post by digioz on 2012-06-25
Still no reply after 2 weeks! Doesn't anyone know the answer to this??

---

