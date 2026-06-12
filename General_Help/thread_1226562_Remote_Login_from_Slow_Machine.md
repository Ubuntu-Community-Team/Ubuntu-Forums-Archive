---
title: "Remote Login from Slow Machine"
date: 2009-07-29
forum: General Help
---

### Post by unperson on 2009-07-29
I have a slow old machine (Celeron 400 MHz) that I'd like to use as a client to do work on a faster remote machine.  What I want is almost a thin client, meaning that most of the time I'd like as much as possible running on the faster server, but the client will have a hard drive and ideally I'd like to retain the ability to login to the local system occasionally.  Also, I don't have a special NIC I can boot from in the client.

What are my best options?

Currently, the server is running Ubuntu Hardy (8.04 LTS) and the client is running Xubuntu Jaunty (9.04).  The two machines are on the same 100 Mbps LAN.  Both have public (i.e., routable) IP addresses and are not behind a firewall, so I don't want to open anything terribly insecure.  I have the ability to change the settings on both machines.

I'm familiar with X Forwarding, which would allow me to connect via SSH and have individual applications on the remote machine forwarded to the local machine's X server.  But since I'd be working essentially entirely on the remote machine, it would be preferable to be using an entirely remote desktop.  Also, the more computational work that can be off-loaded onto the remote machine the better.

Should I look into some sort of VNC software or XDMCP?  Which of these is relatively secure (or can be easily made secure with the use of SSH tunnels)?  I would also like something that doesn't require me to already be logged in on the remote machine.

---

