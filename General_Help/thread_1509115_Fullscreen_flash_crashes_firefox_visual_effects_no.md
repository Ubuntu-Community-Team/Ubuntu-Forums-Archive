---
title: "Fullscreen flash crashes firefox/ visual effects not working"
date: 2010-06-13
forum: General Help
---

### Post by Jahe25 on 2010-06-13
I've included both cos they both occurred at about the same time, so I'm thinking they might be related. Anyway, when I click fullscreen in BBC iPlayer or youtube or whatever, the whole browser crashes instantly, no warning. 

And secondly my visual effects aren't working. When I go into Appearance and try and change from 'None' to 'Normal', it says 'Searching for available drivers' for about 20 seconds, and then says 'Desktop effects could not be enabled'.

Both visual effects and fullscreen flash worked fine until about lunchtime today, and I honestly can't think of anything I did that would've changed setting or messed something up, so I really don't know.

These two issues could be unrelated tbh, but they occurred at the same time so I thought I'd mention them both.

Cheers in advance

---

### Post by lovinglinux on 2010-06-13
Right-click on the flash video, select settings and untick "Enable hardware acceleration". See if that helps.

Also make sure you have the latest flash installed. Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by Jahe25 on 2010-06-13
De-enabling hardware acceleration did sort it :D What exactly does that mean?

And the thing you said I should paste:

File:  /usr/lib/flashplugin-installer/libflashplayer.soVersion:   Shockwave Flash 10.0 r45

---

### Post by lovinglinux on 2010-06-13
> **Jahe25 said:**
> De-enabling hardware acceleration did sort it :D What exactly does that mean?

Means flash won't try to use the GPU to process the video. The processing will be made by the CPU instead.

> **Jahe25 said:**
> And the thing you said I should paste:

File:  /usr/lib/flashplugin-installer/libflashplayer.soVersion:   Shockwave Flash 10.0 r45

That version of flash has a critical vulnerability. Make sure you update your system and check if flash gets updated to 10.1 r53.

---

### Post by reviver on 2010-08-07
I think I have this same problem, but am unable to disable hardware acceleration.  If I right click on a Flash video, Settings is greyed-out.  Is there another way I can disable it?

---

