---
title: "lost power during lucid lynx installation unfortunately"
date: 2010-05-01
forum: General Help
---

### Post by princeofnam on 2010-05-01
While leaving my laptop to install the upgrades, I hadn't noticed how the power cord had slipped loose. When I came back my computer must have shut off due to battery loss. When I booted up my computer again, I couldn't boot up Ubuntu under any of the kernels, -20,-19, etc. I get cryptic messages such as "unable to enumerate USB device on port 2," device not accepting messages," and "device descriptor read." does anyone have any suggestions for what i should do? i definitely intend to recover my data.

I had been upgrading from 9.10 to the latest version of lucid lynx.

---

### Post by Smart Viking on 2010-05-01
Boot with a live cd, and recover your files. Then install it again.

---

### Post by Ryan Dwyer on 2010-05-01
Download a live CD, boot from it, copy your data elsewhere, then do a fresh install from the CD and copy your data back.

---

### Post by princeofnam on 2010-05-01
when you say recover my files, you mean i have to temporarily back them up on an external hard drive? 
 
i found a way to dpkg "repair broken packages" during recovery mode, but i'm not sure what that means or if it'd help

---

### Post by Ryan Dwyer on 2010-05-01
> **princeofnam said:**
> when you say recover my files, you mean i have to temporarily back them up on an external hard drive?
 
Yes.

> **princeofnam said:**
> i found a way to dpkg "repair broken packages" during recovery mode, but i'm not sure what that means or if it'd help

No.

---

### Post by princeofnam on 2010-05-01
is there no way to repair my current copy of ubuntu?

---

### Post by Ryan Dwyer on 2010-05-01
No. Your system is in a completely unstable state and needs to be reinstalled.

---

