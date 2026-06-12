---
title: "Cursor can only move within limited region via synergy during dual monitor"
date: 2011-01-24
forum: General Help
---

### Post by 130s on 2011-01-24
Hi all,

I'm using Mac as a main machine and Ubuntu Netbook as a secondary. Although synergy gives me a good control over Netbook when it works without external monitor, but when I activate VGA monitor, I can only move around the limited region (details are below). Anyone has an idea?

Phenomenon:
- Cursor can move in the external monitor's screen. No way to move cursor into the netbook's screen via synergy (it's possible from local touchpad/mouse)
- In the external monitor's screen, curosor moves only within limited region, which I'm guessing is as large as the size of netbook's screen.

Configuration:
-  Use dual screens (uncheck "Same image in all monitors" in the tool "Monitor" on Ubuntu)

Env:
- OS: Ubuntu 10.04 Netbook edition
- HW: Starling Netbook (star3)

Thanks!

Isaac

---

### Post by drewsus on 2011-01-24
Its because you connect with synergy on the netbook with, I am assuming resolution 1024x600, and then you activate a monitor with a higher resolution. Synergy still thinks it is controlling 1024x600 so that is all you get! You would need to restart the synergy server and client I believe.

---

### Post by 130s on 2011-01-30
Thanks a lot drewsus! That seems to be the cause and your work around works :p

# Next obstacle is what if activating/deactivating an external monitor happen so often though ...rebooting both server and client gets more tedious in that situation.

---

