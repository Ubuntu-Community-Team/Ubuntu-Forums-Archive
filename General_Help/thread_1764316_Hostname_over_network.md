---
title: "Hostname over network"
date: 2011-05-21
forum: General Help
---

### Post by CloudedVision on 2011-05-21
I recently installed Ubuntu Server on an old netbook I had lying around to use as a home server.  I installed OpenSSH server.  I can SSH in using the local IP address (192.168.2.101) but not using the hostname (superintendent).  It gives me the following error when I try:

```
ssh: Could not resolve hostname superintendent: Name or service not known
```

I can't use IP address since my router doesn't support DHCP reservation, so the server's IP will be changing.  How can I get the hostname to work?

---

### Post by CloudedVision on 2011-05-21
Nevermind, it appears to be a router problem, not a server problem.

---

