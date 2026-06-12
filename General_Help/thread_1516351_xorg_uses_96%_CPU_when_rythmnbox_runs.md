---
title: "xorg uses 96% CPU when rythmnbox runs"
date: 2010-06-23
forum: General Help
---

### Post by gatorbrit on 2010-06-23
When I start rythmnbox, Xorg goes up to 96-98% of CPU and stays there.  It goes back down to below 10 when rbox is minimized or closed.

Any ideas?

---

### Post by phildini on 2010-06-23
Are you running a visualizer? Or, if not, how is the audio being processed on your hardware? As in, what audio layer are you using?

---

### Post by gatorbrit on 2010-06-23
Checked the hardware drivers under system-admin-hardware drivers.
Needed to install the correct nvidia driver.
After doing so and rebooting, all is well.

Thanks

---

