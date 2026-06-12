---
title: "icon themes disappearing in Maverick"
date: 2010-10-21
forum: General Help
---

### Post by robhamm on 2010-10-21
Just did a clean install of Maverick 64-bit on an Acer Travelmate 5720. Along with my explanation, I attached a screen shot of the problem to this post.

After installing a few border, application, and icon themes from the Gnome Art site, all folder icons system-wide reset to the default Gnome grey ones, and the icon thumbnails in Appearance Preferences all showed grey rectangles with question marks in them--including those that shipped with Ubuntu, like Mono, etc. 

I reinstalled the normal Ubuntu icons with Synaptic--and they work--but most of the icon thumbnails in Appearance Preferences--again, including the normal Ubuntu icons that I just reinstalled--still show the grey rectangle with the question mark. (See attached image.) My concern is that this may be indicative of a deeper problem.

The Appearance Preferences installer threw me errors on a couple of the themes, but since they were along the lines of "Installation failed," I just assumed, "Oh, well. Guess something is screwed in that package," and moved on. Could that have hosed things the way I describe above?

So... Ideas, anyone? Thanks in advance.

---

### Post by farbror_ace on 2010-10-21
Similar problem for me, on fresh install I had the default theme applied and all looked good. Then suddenly it reverted to to the greyish, sharpedged 1980's look and now the only thing that applies to other applications from the appearance dialog is changing window border. Controls/Icons/Colors are ignored.

Something is broken.
Attaching screenshot of appearance dialog and nautilus.

---

### Post by farbror_ace on 2010-10-22
Anyone?
No matter what I do top panel, application panel and all menues/buttons are just unskinned.
The only thing that gets skinned when I select a new theme i System->Appearance is the windows top list and minimize/maximize/close buttons.

Can I see logs somewhere of what happens when Ubuntu tries to apply a skin?

---

### Post by farbror_ace on 2010-10-22
Ok so after reading some other threads Ive found a workaround but I would really like to understand the rootcause.

Workaround:
Kill all gnome-settings-daemon processes
Start gnome-settings-daemon manually

Then the only application that still doesnt respect the theme is nautilus. Solution here:
[http://wwww.ubuntuforums.org/showpost.php?p=9307380&postcount=4](http://wwww.ubuntuforums.org/showpost.php?p=9307380&postcount=4)

Can anyone point me to where I should be looking for the real problem here?

---

### Post by farbror_ace on 2010-10-22
Also seeing that my problem might not be the same as robhamm's maybe a mod can split this thread?

---

### Post by robhamm on 2010-10-22
Just in case anyone ends up attempting to address this, I have additional information: When I created another user, everything showed up as normal. I reinstalled, though, figuring that I must have somehow hosed something beyond my meager abilities to fix. The wise thing would have been to do a backup BEFORE installing a bunch of stuff, but I am apparently not that wise.
;-)

So while I no longer have the issue, I also still have no idea what happened, since I fixed it by reinstalling.

---

