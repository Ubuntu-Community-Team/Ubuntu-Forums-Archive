---
title: "Ubuntu 10.04 boot screen..."
date: 2010-05-18
forum: General Help
---

### Post by brad1138 on 2010-05-18
The first few times I booted 10.04 (clean install) the final boot splash screen before the desktop was in the default res of my monitor (1680x1050) or very close to that. After a while (3-4 boots or so) it is now 640x480 at best and the rolling dots are blocky, basically it looks like crap. This isn't a real big deal, but I would like the nice clear boot graphics I had originally.

Any ideas?

Thanks,
Brad

---

### Post by Skywa&#8224;cher on 2010-05-18
I had this problem on my desktop PC after installing an NVidia driver. If I remember correctly, you can set the resolution manually: go to your /etc/default folder and open up the "grub" file in a text editor (or simply run the command "**sudo gedit /etc/default/grub**" from a terminal). Find the line that says "**GRUB_GFXMODE=1280x800**" (for me it's line 18 ) and set the resolution as you desire. Save the file and then rebuild grub by running "**sudo update-grub**" from a terminal. Reboot.

Otherwise...maybe try updating your video card drivers? I know that NVidia drivers at least are causing problems for a lot of people.

---

### Post by brad1138 on 2010-05-18
> **Skywa†cher said:**
> I had this problem on my desktop PC after installing an NVidia driver. If I remember correctly, you can set the resolution manually: go to your /etc/default folder and open up the "grub" file in a text editor (or simply run the command "**sudo gedit /etc/default/grub**" from a terminal). Find the line that says "**GRUB_GFXMODE=1280x800**" (for me it's line 18 ) and set the resolution as you desire. Save the file and then rebuild grub by running "**sudo update-grub**" from a terminal. Reboot.

Otherwise...maybe try updating your video card drivers? I know that NVidia drivers at least are causing problems for a lot of people.

I do run Nvidia, I'll try that.

Thanks

---

### Post by pcdave98 on 2010-05-18
You could try installing StartUp-Manager through Software Centre. That'll let you play with your boot resolutions.

---

### Post by brad1138 on 2010-05-18
> **pcdave98 said:**
> You could try installing StartUp-Manager through Software Centre. That'll let you play with your boot resolutions.


Well the other fix didn't work, so maybe I'll try this. I tried setting the res to 1680x1050 and 1280x1024, neither did anything different, thanks though.

Brad

---

### Post by brad1138 on 2010-05-18
Well that didn't work either, actually killed the splash screen entirely. Oh well, thanks anyway.

When 10.04 did work, I got about 20 secs of black/blank screen after grub, then ~5 secs of animated (640x480) splash, then desktop, then after 10+ secs I could use the desktop. In 9.10, the ~20 secs after grub had an Ubuntu logo, then ~5 secs of animated logo, then desktop ready to use.

I don't know how much of my 10.04s boot is "normal" or correct but 9.10 seemed to be better on 3 points (logo immediately after grub, working animated logo after that, desktop immediate ready to use), none that big of a deal though. 

Thanks again,
Brad

---

