---
title: "Allow networking but not an internet connection."
date: 2009-12-06
forum: General Help
---

### Post by DarkRookie on 2009-12-06
I was wondering if there was a way to limit the computer to only networking and not allow it to connect to the Internet?

---

### Post by dcstar on 2009-12-06
> **DarkRookie said:**
> I was wondering if there was a way to limit the computer to only networking and not allow it to connect to the Internet?

There are many ways, firewall rules in the gateway, no default route etc.

---

### Post by DarkRookie on 2009-12-06
Any examples you can give?

---

### Post by dcstar on 2009-12-06
> **DarkRookie said:**
> Any examples you can give?

Set a fixed IP and set the default route to an invalid address.

---

### Post by Iowan on 2009-12-06
It'll be more bulletproof to block access on the router (or proxy server), but locally you could (probably) flush extermal nameservers from */etc/resolv.conf*. 
(I'd be going out a bit (too far) on a limb to suggest changing the default route to something like 127.0.0.1)

---

