---
title: "Dual Monitor issue w/ 12.04 LTS"
date: 2012-09-28
forum: General Help
---

### Post by leavesofgreen on 2012-09-28
Hi I'm kinda new to ubuntu and am just learning all the ins and outs. So please bear with me if I have some trouble with answers.

I recently did an update (maybe a couple of weeks ago) and after I restarted my system the second monitor didn't come on. I went under the display settings to try and figure this out. Instead of calling it a ViewSonic it was labled "laptop". When I boot from an older version (can't exactly remember which at the moment) it works just fine. I am using GeForce 9500 GT as my video card. Can some one please help me out?

---

### Post by meanmrmustard on 2012-09-28
> **leavesofgreen said:**
> Hi I'm kinda new to ubuntu and am just learning all the ins and outs. So please bear with me if I have some trouble with answers.

I recently did an update (maybe a couple of weeks ago) and after I restarted my system the second monitor didn't come on. I went under the display settings to try and figure this out. Instead of calling it a ViewSonic it was labled "laptop". When I boot from an older version (can't exactly remember which at the moment) it works just fine. I am using GeForce 9500 GT as my video card. Can some one please help me out?

Not sure why it would be reported as laptop but I'd start by installing the Nvidia driver - unless you refuse to use proprietary software.

---

### Post by mips on 2012-09-28
> **leavesofgreen said:**
> Hi I'm kinda new to ubuntu and am just learning all the ins and outs. So please bear with me if I have some trouble with answers.

I recently did an update (maybe a couple of weeks ago) and after I restarted my system the second monitor didn't come on. I went under the display settings to try and figure this out. Instead of calling it a ViewSonic it was labled "laptop". When I boot from an older version (can't exactly remember which at the moment) it works just fine. I am using GeForce 9500 GT as my video card. Can some one please help me out?

Install nvidia-current & nvidia-settings and afterwards use nvidia-settings to configure twinview for your displays.

---

