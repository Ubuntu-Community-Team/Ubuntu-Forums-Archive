---
title: "Dual Monitor Random Blanking"
date: 2012-06-06
forum: General Help
---

### Post by Mashepherd on 2012-06-06
Hey i've got what i assume to be a simple problem, well it seems simple on the face of it...

I'm running a Ubuntu 12.04 Dual Monitor (Nvidia-settings) setup and my 'secondary' suffers from random blanking. That is, it goes black for 2 or 3 seconds maybe then returns to normal. This isn't a problem native to 12.04 but has been occuring since 11.04.

Any help would be gratefully recieved.

---

### Post by idoitprone on 2012-06-06
> **Mashepherd said:**
> Hey i've got what i assume to be a simple problem, well it seems simple on the face of it...

I'm running a Ubuntu 12.04 Dual Monitor (Nvidia-settings) setup and my 'secondary' suffers from random blanking. That is, it goes black for 2 or 3 seconds maybe then returns to normal. This isn't a problem native to 12.04 but has been occuring since 11.04.

Any help would be gratefully recieved.


sound like a nvidia driver bug

what is nvidia card?
you can search it on google with the keyword ubuntu to find if other people is having the same issue
i guess check if the monitor is configure properly

i wonder if you should post it to the bugzilla to ensure it is your hardware that is causing the problem

then beg nvidia to fix their drivers


or else
you did not configure the refresh rate properly with your secondary monitor

---

### Post by Mashepherd on 2012-06-07
May have fixed an issue, only just tried testing this one but so far so good, no random screen blanking.

All I did was to untick the 'Allow Flipping' tick box under OpenGL Settings within NVIDIA X Server Settings

Cheers

---

### Post by bl8n8r on 2013-02-12
This didn't work for me. Still getting the random blanking.  Using nvidia 304.64 on Kubuntu 12.04 and dual Viewsonic LCD panels. Random blanking of secondary monitor lasting 1-3 seconds. Sometimes monitor goes completely offline saying "unsupported video mode"

---

