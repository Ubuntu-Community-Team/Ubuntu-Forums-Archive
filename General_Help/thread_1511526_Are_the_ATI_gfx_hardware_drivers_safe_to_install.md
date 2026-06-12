---
title: "Are the ATI gfx hardware drivers safe to install?"
date: 2010-06-16
forum: General Help
---

### Post by kittkatt on 2010-06-16
Hello everyone,

I was just wondering if its safe to install the ATI proprietary gfx drivers? I have a Radeon 4770. 

This is my first time trying 10.4, I had tried a previous version of Ubuntu but when I tried to install the proprietary gfx drivers for my videocard, it completely broke my system (on reboot I got a blank screen and couldn't even POST).

---

### Post by alphacrucis2 on 2010-06-16
> **kittkatt said:**
> Hello everyone,

I was just wondering if its safe to install the ATI proprietary gfx drivers? I have a Radeon 4770. 

This is my first time trying 10.4, I had tried a previous version of Ubuntu but when I tried to install the proprietary gfx drivers for my videocard, it completely broke my system (on reboot I got a blank screen and couldn't even POST).

Should be fine. You can install fglrx (catalyst 10.4) via System - Administration - Hardware Drivers. I find when it finishes, it is a good idea to issue the following command before rebooting:

```
sudo aticonfig --initial -f
```

If you want to install the latest binary driver (Catalyst 10.5) which isn't in the Ubuntu repos as yet, then follow this guide rather than the ATI instructions.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

Of course replacing any references to karmic with lucid in any of the commands and also the actual ATI installer name changes with each release.


Edit: I see that AMD have released catalyst 10.6 today. getting some good reports on the Phoronix forums.

---

