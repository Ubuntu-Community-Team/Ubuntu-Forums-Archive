---
title: "Ubuntu non-2D version broken"
date: 2011-12-24
forum: General Help
---

### Post by Irishpolyglot on 2011-12-24
I was trying to enable 3-D effects, such as the cube, through compiz and after doing so I have lost all useful access to the system. All that I have is a line at the top for File, Edit etc. specifically for navigating the home directory. There is no more left sidebar and the super key does not respond.

What can I do to disable the particular 3D effects I had enabled? At the moment the only way to access the computer at a useful way is within the 2D log in. From the 3D log on, I can't access anything, and have to press the power button to be able to shut down. Within the 2D log in they are disabled anyway, so I'm not sure what I can do from this set up other than perhaps create a shortcut that brings up the terminal? Ideas appreciated.

I'm on 11.10 and a Dell XPS M1730.

---

### Post by jim_deadlock on 2011-12-24
It's quite common for this to happen when messing around with ccsm. To fix it, log in to your 2D environment and open ccsm. Click the orange Preferences button and select the 'unity' profile (this is the default profile used for the main 3D environment). Hit the Back button and enable these bare minimum settings:

Desktop -> Ubuntu Unity Plugin (MOST IMPORTANT)
Effects -> Window Decoration
Window Management -> Move + Resize

You should now be able to get a working 3D environment, you can then try again with your cube etc. Always make sure your Unity plugin is enabled whenever you mess around with ccsm because enabling other plugins can often disable it without you realising.

Another ccsm tip: it's a good idea to export your unity profile and then import it as a named profile and use a specific profile for each of your users, that way you can keep the default unity profile as a fallback for emergencies.

---

### Post by jim_deadlock on 2011-12-24
Oh and another thing, after you update your unity profile, switch back to the Default profile (which it should have been on originally) before logging out of your 2D environment.

---

### Post by Irishpolyglot on 2011-12-24
That's done it! Yes, something I did had disabled the Unity plugin - obviously I wasn't aware of how important it was. Thanks for your help :)

---

