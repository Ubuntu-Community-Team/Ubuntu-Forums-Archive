---
title: "Blurry screen after login"
date: 2009-09-02
forum: General Help
---

### Post by thor.bj on 2009-09-02
Hi

When I used my Ubuntu laptop with a video projector, my screen suddenly became blurry.
I tried to autorepair xorg. That made the boot-screen and logon-screen look sharp and crisp again, but when I log in the screen becomes blurry.

I have a resolution of 1440x900, on a Dell Inspiron 6400 laptop running Ubuntu 9.04.
The screen has a sync rate of 60hz.

I Run the latest Intel driver from Synaptic.

Anyone have any ideas what this could be?

Thank!

---

### Post by thor.bj on 2009-09-02
Never mind, I found the solution for my problem.
Quite simple, actually :P

Before I repaired xorg, I tried all possible resolutions I had on my computer. But now, after I repaired xorg, I got even more choices in the resolution drop-down, so I found the resolution I needed to get it crisp and sharp again :D

---

### Post by egalvan on 2009-09-02
> **thor.bj said:**
> Never mind,.
Quite simple, actually :P
 I found the resolution I needed to get it crisp and sharp again :D

Would you mind sharing this information with us?
It may help others.

---

### Post by thor.bj on 2009-09-02
> **egalvan said:**
> Would you mind sharing this information with us?
It may help others.

Offcourse :)

It could look like the Xorg.conf file had changed when I connected the video projector. This resulted in issues where my display settings didn't show all possible resolutions anymore.

What I did, which I think fixed it, was to boot my computer in recovery mode (press esc when prompted during boot, and choose the linux kernel with "(recovery mode)" at the end, or something like that). When it entered the recovery console, I chose the option for auto-repairing the display settings (all down at the bottom). When it was done repairing, I chose the top option, to continue booting.

When my computer was finished booting, I logged in and opened the display settings for my computer. There I found all the possible resolution settings that's supposed to be there. I chose 1680x1050 (16:10), which is the resolution I prefer on my screen. :)

Thats it :)

---

