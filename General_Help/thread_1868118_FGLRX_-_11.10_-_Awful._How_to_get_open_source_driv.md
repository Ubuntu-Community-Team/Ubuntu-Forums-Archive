---
title: "FGLRX - 11.10 - Awful. How to get open source drivers back?"
date: 2011-10-23
forum: General Help
---

### Post by Roasted on 2011-10-23
I have a laptop with an HD 6250 running 11.10. I was having great success with it and decided to test out the HDMI to the TV. So I hook it up and nothing happens. I ultimately decided I should check for video drivers and sure enough, FGLRX was listed. I haven't used ATI in years with Linux but FGLRX had sounded familiar, so I installed it and rebooted. When it came up I logged in to Gnome Shell and things looked horrible. Absolutely horrible. Asking in the #gnome IRC chat suggested:

```
Those are bugs in the driver, they don't show up in unity because it uses different opengl stuff than gnome-shell does and so does not expose these bugs.
```

Okay. So that explains why Unity was working for me and Gnome Shell was not. Even still, I have my preferences, and using Unity was far from a solution.

At this point I decided, ehh let's just get the laptop back in working order the way it was. Problem is when I uninstalled the FGLRX drivers I rebooted and logged back in. I had read that if the proprietary drivers weren't present, the system used open source drivers. That being said, I thought uninstalling the proprietary driver, rebooting, and coming back would thereby use the open source drivers. Sure enough, both Gnome Shell and Unity 3D fall back to their alternatives (gnome classic and unity 2d).

So clearly, I don't have a graphics driver installed.

So my questions are this:

1 - How do I mirror my display using the open source driver so I can have a video feed on the TV from my laptop via HDMI?

2 - I've uninstalled the proprietary drivers. Now what? How do I get the open source drivers back?



EDIT - Well, we're warmer now. I ended up running:

sudo apt-get remove fglrx*
sudo apt-get purge fglrx*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-video-radeon xserver-xorg-core

Rebooted and I was back in Gnome Shell without issue. I fired up "Additional Drivers" and both options listed were not activated, further indicating I was using the open source drivers. Okay, great. But can I get HDMI working with the open source drivers?

---

### Post by Roasted on 2011-10-26
BUMP - How do I get HDMI working with open source drivers? I want to shoot a 720 or 1080 resolution image (I forget what this particular TV is) via HDMI out on this laptop. Again, running an HD 6250.

Has anybody caught any wind in terms of bugs with these ATI drivers (FGLRX)?? I'm trying to dig up info but all I keep hearing is "ATI and Nvidia both had some bugs, but Nvidia fixed their's right away - ATI is still in progress."

Does anybody know anything or have a source I can check to get notified when the fix comes about?

---

### Post by Roasted on 2011-11-08
Any new info to add? On a hunch I updated to the newest driver within the additional drivers menu, but even still it tanked on me, giving me gnome classic fallback mode.

Likewise, does anybody have any information about being able to mirror diaplsy via HDMI and send audio through HDMI as well using the free open source drivers? 

Thanks!
-J

---

### Post by Roasted on 2011-11-11
upppppp. :confused::confused:

---

### Post by Roasted on 2011-11-14
So is there uh... no way to mirror HDMI out on open source drivers?

---

### Post by Mark Phelps on 2011-11-14
I'm using the open-source AMD drivers but have a DVI connection, not HDMI.  Did a quick search on all the documentation I could find about the open-source drivers, and NONE of them even include "HDMI".

So, my guess is that, Like TV OUT, the drivers do not support HDMI.

---

### Post by Roasted on 2011-11-14
> **Mark Phelps said:**
> I'm using the open-source AMD drivers but have a DVI connection, not HDMI.  Did a quick search on all the documentation I could find about the open-source drivers, and NONE of them even include "HDMI".

So, my guess is that, Like TV OUT, the drivers do not support HDMI.

Oh. Well that's awesome. If only ATI wasn't so bad with drivers I could be enjoying HDMI output at the moment.

Mental note: Nvidia or bust.

---

### Post by Roasted on 2011-12-11
Just bumping this up - has anybody successfully ran the open source ATI drivers on an Ubuntu 11.10 laptop with HDMI out?

---

