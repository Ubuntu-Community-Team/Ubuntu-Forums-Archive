---
title: "Help with offset desktop graphics"
date: 2011-06-30
forum: General Help
---

### Post by maxxjr on 2011-06-30
If I log out of my initial login session, the login w/ username+password screen is *sometimes* shifted to the right (so that the power icon on the bottom right is off-screen, and I have a black column on the left).

When I log back into an account, the same shift *sometimes* happens, independent of whether or not the login screen was shifted.

User switching *sometimes* results in the same behavior (it's not just logging in and out).

I have also logged in using a different desktop manager (openbox), and have had no issues (so far) with shifted graphics.  Logging back out from openbox, the login screen still *sometimes* has the shift.

Any suggestions on what the issue may be, things to check, etc.?

This is 64-bit Ubuntu, running the AMD graphics driver.

Thanks!

---

### Post by dino99 on 2011-06-30
seems to be a grahic driver issue. So if you have a xorg.conf, remove it as now kernel directly deal with X. Otherwise, purge then reinstall the driver from synaptic
and watch logs to find usefull errors

---

