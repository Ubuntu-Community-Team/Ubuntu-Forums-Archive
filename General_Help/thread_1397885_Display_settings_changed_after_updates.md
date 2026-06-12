---
title: "Display settings changed after updates"
date: 2010-02-03
forum: General Help
---

### Post by geovino on 2010-02-03
In the last day I did an update and now my display is not what it use to be. its 1028 x 768 instead of 1280 x 1024. I have Nvidia 6100 video. How do I get it back to the way it was? It won't let me change the resolution.

Why do these things happen?

---

### Post by drs305 on 2010-02-03
Have you checked System, Administration, Hardware Drivers? Make sure your Nvidia drivers are still installed and activated.

---

### Post by warfacegod on 2010-02-03
Did you install a video driver that was not in the repositories? One from nVidia's site perhaps. If you got a kernel update then your video driver would not have survived the update and you will need to reinstall that driver.

---

### Post by geovino on 2010-02-03
I just shutdown and rebooted and it now came back to 1280 x 1024. but lately I've noticed that the fonts have changed where they're not as smooth and sharp as before. I never change any of the settings. It changes on its own so it makes me think that its from an update. 

I've adjusted Fonts many times and I don't know what else to do. I use Mint also on another PC and it doesn't do this. What happens to change things?

---

### Post by drs305 on 2010-02-03
> **geovino said:**
> ...but lately I've noticed that the fonts have changed where they're not as smooth and sharp as before. I never change any of the settings. It changes on its own so it makes me think that its from an update. I've adjusted Fonts many times and I don't know what else to do. I use Mint also on another PC and it doesn't do this. What happens to change things?

You can tweak the Font settings a bit via System, Preferences, Appearance: Fonts tab. You can try various fonts, and for the clarity issue you might get better results by changing the setting in the bottom pane (Rendering) or in Details.

---

### Post by warfacegod on 2010-02-03
In Appearance> Fonts tab> Details button> under "Smoothing" select subpixel> under "Hinting" try the different levels of hinting to see if it fixes it.

---

### Post by warfacegod on 2010-02-03
You may also want to go to: System> Admin.> Hardware Drivers and activate the recommended video driver.

---

### Post by geovino on 2010-02-03
Thanks I'll give that a try. 

I still wonder why the resolution changed and then came back after a shutdown-reboot. what causes that?

Overall Ubuntu has been very good the past two versions. Its just strange that stuff happens like this.

---

### Post by warfacegod on 2010-02-03
> **geovino said:**
> Thanks I'll give that a try. 

I still wonder why the resolution changed and then came back after a shutdown-reboot. what causes that?

Overall Ubuntu has been very good the past two versions. Its just strange that stuff happens like this.

I don't have any specific explanation. I can only say that 9.10 has been having  quite a few medium to minor glitches.

---

