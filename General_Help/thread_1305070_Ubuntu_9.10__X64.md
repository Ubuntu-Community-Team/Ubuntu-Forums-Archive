---
title: "Ubuntu 9.10  X64"
date: 2009-10-29
forum: General Help
---

### Post by hotmail@yahoo.com on 2009-10-29
Hi everyone,

                 I want to install Ubuntu 9.10 in my new machine. Before I install it I just want to know if my system will be compatible with the x64 version.


Below is my machine specification. Let me know if I will encounter any compatibility issue. Many Thanks.

AMD Phenom II Quad Core 3.3 GHz processor
ASUS M4A78T-E AM3 AMD 790GX HDMI  Motherboard
SAPPHIRE GHDMI Radeon HD 4850 1GB 256-bit GDDR3
CORSAIR XMS3 DHX 6 GB GDDR3 1600 MHZ RAM
SAMSUNG Spinpoint F1 HD103UJ 1TB HD
OCZ ModXStream Pro OCZ600MXSP 600W ATX12V PSU

Also I already have Win 7 and Win XP in my system as dual boot. Is it possible to do triple boot? If so is there a tutorial about it?

---

### Post by TwiStEr55 on 2009-10-29
If you can run a 64bit system depends entirely on your CPU!

Your CPU has the 64bit instructions, so yes you will be able to run an 64bit system. In fact it is recommended to do that, since you have more than 4GB of RAM. A 32bit system can only address 4GB and you will end up with 3.2-3.5GB ... with 64bit all your RAM will be used.

It is possible to triple boot, but be careful when you tamper with boot sectors. I dont have a guide handy, but by just installing grub2 with karmic it should detect the other 2 Os's.

If you dont know exactly what your doing, its always advisable to backup all your important data!

---

### Post by ljrmorgan on 2009-10-29
> **hotmail@yahoo.com said:**
> Hi everyone,

                 I want to install Ubuntu 9.10 in my new machine. Before I install it I just want to know if my system will be compatible with the x64 version.


Below is my machine specification. Let me know if I will encounter any compatibility issue. Many Thanks.

AMD Phenom II Quad Core 3.3 GHz processor
ASUS M4A78T-E AM3 AMD 790GX HDMI  Motherboard
SAPPHIRE GHDMI Radeon HD 4850 1GB 256-bit GDDR3
CORSAIR XMS3 DHX 6 GB GDDR3 1600 MHZ RAM
SAMSUNG Spinpoint F1 HD103UJ 1TB HD
OCZ ModXStream Pro OCZ600MXSP 600W ATX12V PSU

Also I already have Win 7 and Win XP in my system as dual boot. Is it possible to do triple boot? If so is there a tutorial about it?

Firstly, download the Live CD (which I think is just the installer CD) - it's basically just a version of Ubuntu that runs off the CD and lets you install ubuntu properly. If it works, then Ubuntu will work!

Triple booting etc. is fine - ubuntu will take care of it all.

---

### Post by hotmail@yahoo.com on 2009-10-29
> **TwiStEr55 said:**
> If you can run a 64bit system depends entirely on your CPU!

Your CPU has the 64bit instructions, so yes you will be able to run an 64bit system. In fact it is recommended to do that, since you have more than 4GB of RAM. A 32bit system can only address 4GB and you will end up with 3.2-3.5GB ... with 64bit all your RAM will be used.

It is possible to triple boot, but be careful when you tamper with boot sectors. I dont have a guide handy, but by just installing grub2 with karmic it should detect the other 2 Os's.

If you don't know exactly what your doing, its always advisable to backup all your important data!

Thanks for the insight on my CPU and and explanation on 64bit architecture. I build the system myself :) and I have x64 win7 and xp running.

Can you give me the link for the guide? Also my major concern is about driver support. Are there drivers for made specifically for my hardware? If so where should I check that?

You mentioned you have the tutorial, please provide links. Thanks.

---

