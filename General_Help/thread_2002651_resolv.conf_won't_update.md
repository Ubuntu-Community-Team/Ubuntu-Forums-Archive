---
title: "resolv.conf won't update"
date: 2012-06-13
forum: General Help
---

### Post by bjfcom on 2012-06-13
I've had crashing issues with 12.04 apparently related to my nvidia video card.  After one of the crashes, while I was logged into my work through a vpn, my computer refuses to allow me to search the web or access any outside network, however, I am connected to my local network (computers in my house).

I have found that if I manually edit the resolv.conf to the network I am connected to, then I can connect to the web.  However, this is getting very annoying and would like to find a permanent solution.

Any help would be greatly appreciated!!!,
An lspci is attached as an image if helpful.

Best,
Bernard

---

### Post by dcstar on 2012-06-13
> **bjfcom said:**
> I've had crashing issues with 12.04 apparently related to my nvidia video card.  After one of the crashes, while I was logged into my work through a vpn, my computer refuses to allow me to search the web or access any outside network, however, I am connected to my local network (computers in my house).

I have found that if I manually edit the resolv.conf to the network I am connected to, then I can connect to the web.  However, this is getting very annoying and would like to find a permanent solution.
........

The VPN software resets the resolv.conf when it exits, since it did not exit it did not fix that file.

Delete your LAN connection and add it back again and it may fix things up.

LSPCI hardware dumps are useless, this is a software issue with the networking.

---

### Post by bjfcom on 2012-07-06
Thanks David,

I'll do that.

I guess I left the lspci dump because I am trying to figure out why my computer keeps crashing--that's the real problem.  I made another post regarding this issue to which I never got a response.

Thanks again!

---

