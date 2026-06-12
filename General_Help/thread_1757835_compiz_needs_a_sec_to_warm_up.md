---
title: "compiz needs a sec to warm up"
date: 2011-05-13
forum: General Help
---

### Post by jeremz on 2011-05-13
For some reason, compiz effects such as cube rotation and the scale plugin are some what jerky and sluggish for less than a second when I first use them, but then super smooth afterwards. If I wait a while, and try again, it is the same story. I am overclocked, and strangely, this doesn't happen when I am not overclocked. cpu temps are low, gpu temp is ~40 celcius. Here is my relavant hardware/software:

Maverick 64 bit
i5 2500k quad core cpu clocked at 4.5GHz by MSI BIOS version 1.9
not overclocked = 3.3GHz
nvidia gtx 550 ti

nvidia driver 270.41.06

Does anyone have any idea what could cause this?

---

### Post by jeremz on 2011-05-29
On the off chance that anyone else ever has this issue. I finally figured it out. I had nvidia-settings' preferred mode for PowerMizer set to "Adaptive". Setting it to "Prefer Maximum Performance" solves this.

---

