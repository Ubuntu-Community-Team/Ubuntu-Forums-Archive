---
title: "Exteremely high RAM usage on extremely light system at boot. What gives?"
date: 2009-11-30
forum: General Help
---

### Post by DarkED on 2009-11-30
Hi all. I am running my own heavily-modified flavor of Ubuntu 9.10. It could be thought of as similar to Crunchbang -- just the Ubuntu base packages with Openbox on top.

I have uninstalled everything that is not relevant, including Gnome. I have also disabled any non-relevant services and startup apps. If you haven't figured it out, I'm trying to run as light as possible ;)

And now to the problem. Half the time, after the system boots to desktop, it is using about 98mb of RAM. This is about right considering what I have running (almost nothing.) However, half the time it will boot to desktop and be using almost 400mb of RAM for no explainable reason. The same stuff is running in htop as what should be. There's just a lot more RAM being used. This is a problem considering that I only have 512mb of RAM. When it boots up with the extra usage the system is also slow and more sluggish, i.e. it's not just filesystem cache, that RAM is actually being used by something!

I have tried and tried to find the answer for this. I never see anything running in htop that shouldn't be there. Could this be some kind of massive memory leak, and if so, how can I find it? Does anyone have any other ideas?

If I can't eventually figure it out I have considered just compiling my own distro from scratch. But I don't want to have to do that, so please help me :D

---

### Post by doas777 on 2009-11-30
are you hibernating/suspending/resuming?

---

### Post by DarkED on 2009-11-30
> **doas777 said:**
> are you hibernating/suspending/resuming?

Never. It's always a fresh boot.

---

### Post by mkvnmtr on 2009-11-30
I have had a problem with the window manager using a lot of resources after start up for a few minutes when I have a lot of pictures stored. I have a more or less regular Ubuntu installed. Look for that in Htop.

---

