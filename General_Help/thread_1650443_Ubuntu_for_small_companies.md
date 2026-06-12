---
title: "Ubuntu for small companies"
date: 2010-12-21
forum: General Help
---

### Post by peterlauri on 2010-12-21
Hi,

We will be using Ubuntu as our OS on our laptops. The company will have 15 people working to start with. However, can Ubuntu provide some corporate network solutions out of the box?

What I'm interested is if there is any well integrated VPN provider and proxy server setup that you can recommend?

/Peter

---

### Post by davidmohammed on 2010-12-21
the solution really depends obviously on what your network looks like - what interfaces you require etc.

NFS and SAMBA come as standard - I presume you will have some-sort of server such as ubuntu server?  If so, use NFS. Windows server? - use SAMBA.  Peer-to-Peer?  SAMBA is your best bet.  Out of the box, ubuntu will see other computers on the same network.

[OpenVPN]("https://www.openvpn.net") has some good tutorials and examples - pricing is very cheap.

---

