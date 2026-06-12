---
title: "Ubuntu on old computers?"
date: 2009-09-14
forum: General Help
---

### Post by Janjiss on 2009-09-14
Hello dear Ubuntu comunity!

Recently I installed Ubuntu on few old boxes - With AMD sempron 1.8Ghz And AMD athlon 2.0. I have ATI AGP 128mb Video Card and 512 ddr400 ram. It runs preforms very poorly on those computers and i don't understand what is the problem. Browsers preform poorly and procesor is loaded on 100%... Thats mine experience with old computers with Ubuntu on it :( Somone has ran in same problem?

---

### Post by Vaphell on 2009-09-14
512MB ram is not that much nowadays, you could try some lighter environment
also gfx drivers can be bad so video card doesn't take over the visual stuff and CPU has to do everything.

run **top** in terminal and see what app is the biggest offender. It may give some clues how to resolve the issue.

---

### Post by james.exe on 2009-09-14
Have you tried running xubuntu instead?

---

### Post by LowSky on 2009-09-14
Most likely your issue is with the graphics while using the browser, go to restricted drivers under sytem and enable the driver that might help things.

---

### Post by P4man on 2009-09-14
> **LowSky said:**
> Most likely your issue is with the graphics while using the browser, go to restricted drivers under sytem and enable the driver that might help things.

I agree it probably the video driver, but his (i suspect somewhat old) ATI card is probably no longer supported by ATI. Hence, he is stuck with the opensource drivers, unless he downgrades to ubuntu 8.10

---

