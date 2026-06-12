---
title: "NVIDIA driver  problem"
date: 2012-08-07
forum: General Help
---

### Post by community on 2012-08-07
Hi
   I want to know whether the graphics drivers installed using *nvidia-current* for NVIDIA graphics card is proprietary or opensource? Is there any problem if proprietary drivers are installed for the graphics card? I heard that in some cases installing NVIDIA drivers cause the OS to crash.

---

### Post by Statia on 2012-08-07
nvidia-current is proprietary, made by Nvidia.
Yes, it can have bugs, yes that might cause lock-ups or crashes, but I haven't encountered this.
The open source Nouveau driver will have bugs as well and these might cause crashes and lock-ups as well, but I have no experience with this.

---

### Post by vexorian on 2012-08-07
> **community said:**
> Hi
   I want to know whether the graphics drivers installed using *nvidia-current* for NVIDIA graphics card is proprietary or opensource? Is there any problem if proprietary drivers are installed for the graphics card? I heard that in some cases installing NVIDIA drivers cause the OS to crash.
proprietary nvidia drivers currently have a security vulnerability that can allow programs running in your computer to gain root access to your whole system.

nouveau are a little more stable, but they are not as powerful. I don't remember the last time I had crashes with proprietary nvidia drivers though.

---

