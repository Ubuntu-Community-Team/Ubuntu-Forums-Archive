---
title: "changing ip address?"
date: 2011-02-04
forum: General Help
---

### Post by musendrophilus on 2011-02-04
I don't have a dynamic IP address. Is there a way I can change the IP address assigned to me by my internet provider (comcast) to something different with ifconfig et al?

Or is this where I call ISP tech support to have them reset it?

---

### Post by YesWeCan on 2011-02-04
The latter.

---

### Post by stderr on 2011-02-04
Assuming you're on a LAN, you can likely change your PC's *LAN IP address* (192.168.x.x, 10.x.x.x, etc) with ifconfig depending on how the gateway is configured, but this won't affect the fact that the gateway uses NAT to provide a different set of IP address on your local network compared to the **one** static external IP assigned to you by your ISP, which is what your packets will contain when they're sent out over the Internet.

If you're not using NAT, then you simply have that one static IP anyway - nothing you can do.

So, the long and short of it is

> **YesWeCan said:**
> The latter.

---

### Post by Iowan on 2011-02-04
Is there a particular reason you dislike the address you've been assigned? Most of us never know what our address will be.

---

### Post by dcstar on 2011-02-05
> **YesWeCan said:**
> The latter.

+1 - all other posts here do not answer the OPs basic question but this one.

---

