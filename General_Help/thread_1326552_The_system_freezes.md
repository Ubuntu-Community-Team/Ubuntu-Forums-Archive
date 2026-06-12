---
title: "The system freezes"
date: 2009-11-14
forum: General Help
---

### Post by cursebg on 2009-11-14
I've just installed the new Ubuntu 9.10 and it hangs at a random moment, it just freezes. I've tried using the magic keys (Alt +SysRq + K/R/E/I/S/U/B ) but it doesn't respond... I am not using a swap partition, it's a swap file that is equal to the RAM. The first time I installed it the root filesystem was ext4, but I reinstalled it with ext3 and it keeps freezing and thus it's not a FS problem... 

The laptop:
Asus F5SL
RAM: 2GB
HDD: 120 GB Hitachi
Video: ATI Radeon Mobility 3470 HD
CPU: Intel Celeron M 550 @ 2 GHz
Wi-Fi adapter: Atheros AR 5008

---

### Post by Tsquad on 2009-11-14
im having this problem as well. Only i can still move my mouse. My keyboard and desktop are frozen and wont respond, but my mouse does.

---

### Post by jeb800e on 2009-11-14
You don't have to use "K" in REISUB.

---

### Post by jeb800e on 2009-11-14
ext4 has much more problems than ext3. For most home computers today, I would recommend ext3.

---

### Post by cursebg on 2009-11-14
Yeah, but in my case neighter the mouse, nor magic keys work... It isn't even a kernel panic, because the lock light are not flashing. Does anybody have an idea how can I view the main system logs? :-k

---

### Post by jeb800e on 2009-11-14
Go to System < Administration < System Log

---

### Post by jeb800e on 2009-11-14
You may want to reinstall Ubuntu, as something may have been messed up after you installed it, and I can infer you probably finally had to unplug the system.

---

### Post by cursebg on 2009-11-14
> **jeb800e said:**
> You may want to reinstall Ubuntu, as something may have been messed up after you installed it, and I can infer you probably finally had to unplug the system.

Reinstalled it, no change :/ CD image hashes and checksums are OK... I have no other ideas ):

---

### Post by MaxIBoy on 2009-11-14
Intermittent problems like this can often be caused by overheating. I think that is likely to be the problem. 

When was the last time you opened your computer's case and blew all the dust out? Or if you have a laptop, when was the last time you put some compressed air through the vents? Is your computer in a well-ventilated spot with plenty of airflow and nothing covering the vents? 

For laptops, the absolute worst place for them is your lap, a bed, or any soft cushy surface that it will "sink into." This chokes off the vents and causes overheating. ALWAYS use a laptop on a hard flat desk, or at least keep the vents in open air by tilting it! 

For desktops, the absolute worst place is some little cubbyhole (like the ones built into a lot of modern furniture for that purpose,) stowed away under your desk, or in some closet somewhere. You should keep your computer in open air, ideally right near an open window. A good rule of thumb for desktops is: if it's not a blatantly-visible eyesore, it's not getting enough air!

---

### Post by mahdif62 on 2009-11-20
I have the same problem. I'm using the latest nvidia drivers from the nvidia-vdpau ppa repositiry. My mainboard is ASUS P5B.

---

### Post by deepaktmimt on 2009-11-20
i have installed ubuntu 9.10 on my system and i found the same the problem of freezing up the system as the boots up. I was using the previous version of ubuntu that works fine but i found the problem with the new version.I am using core 2 duo with 1 gb of ram and 1 gb of swap space.. Don't no how to tackle the problem .Is there anyone who can help me over this issue..

---

