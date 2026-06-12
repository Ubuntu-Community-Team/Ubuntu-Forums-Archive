---
title: "Ubuntu file server partially unresponsive after a few days"
date: 2010-03-09
forum: General Help
---

### Post by AncientPC on 2010-03-09
I have a home file server running Ubuntu Server 9.04.

Twice in the past week the system fails to respond to ssh.  I can get into the system and swap between the various terminals, but local login fails as well.

I can press the power button to attempt a soft shutdown and a few messages scroll on the screen, but it always fails and I end up having to do a hard reboot.

This has happened two times in the past week, whereas before I've had months and months of uptime.

I've checked kern.log and dmesg.log, but can't seem to find anything that would point to a problem or maybe I just don't know what to look for.  Any help is appreciated.

---

### Post by dcstar on 2010-03-09
> **AncientPC said:**
> I have a home file server running Ubuntu Server 9.04.

Twice in the past week the system fails to respond to ssh.  I can get into the system and swap between the various terminals, but local login fails as well.

I can press the power button to attempt a soft shutdown and a few messages scroll on the screen, but it always fails and I end up having to do a hard reboot.

This has happened two times in the past week, whereas before I've had months and months of uptime.

I've checked kern.log and dmesg.log, but can't seem to find anything that would point to a problem or maybe I just don't know what to look for.  Any help is appreciated.

How much free space is left on the system?

---

### Post by AncientPC on 2010-03-09
Every mount point is less than 30% use except for /home.

---

