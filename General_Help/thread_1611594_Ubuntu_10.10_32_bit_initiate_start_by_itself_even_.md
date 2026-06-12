---
title: "Ubuntu 10.10 32 bit initiate start by itself even when the power is off"
date: 2010-11-02
forum: General Help
---

### Post by arapaho on 2010-11-02
Ubuntu 10.10 32 bit and Mint 10 Julia 64-bit initiate start by itself! When I shutdown computer and the power is off and the Internet cable is connected, it stops working, but after about 30 seconds system initiate start by itself, I mean the power is on.
It doesn't happen when the Internet cable is off.

Linux 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux
Motherboard Gigabyte 945P-DS3

---

### Post by dcstar on 2010-11-02
> **arapaho said:**
> Ubuntu 10.10 32 bit and Mint 10 Julia 64-bit initiate start by itself! When I shutdown computer and the power is off and the Internet cable is connected, it stops working, but after about 30 seconds system initiate start by itself, I mean the power is on.
It doesn't happen when the Internet cable is off.

Linux 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux
Motherboard Gigabyte 945P-DS3

Turn off the Wake On LAN setting in your BIOS.

---

### Post by arapaho on 2010-11-02
Thank you. I had PME Event Wake Up option enabled. I did it accidentally and I thought I was under attack or that there is something wrong with my new system installation. 
Now it is fine.

---

