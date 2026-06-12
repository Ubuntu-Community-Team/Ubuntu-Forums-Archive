---
title: "changed screen resolution and can't get back, help :("
date: 2009-10-18
forum: General Help
---

### Post by a cup of tea on 2009-10-18
omg I'm dumb. I fiddled with my screen resolution. Everything was fine before, and now the resolution's at 720x400. I can't see most of the box where I'm supposed to pick the resolution and set it back to normal. I can't click "apply" because it's off the screen, and there's no scrollbar. 

Is there some way to resize that box with the screen resolution options, or to scroll down it? Or, can someone show me what the bottom half looks like, or tell me how many times I need to hit tab to get to the apply button? I tried tabbing down and clicking enter at every stop along the way and I can close it, but can't seem to change the screen resolution. 

I tried looking for info on other ways to change my screen resolution. I went into a xorg configuration thing, picked some settings and probably messed more stuff up, and wasn't given the option to reset my screen resolution. 

I just want everything back to normal. :(

---

### Post by PorkyPie on 2009-10-18
Hi. Boot into Recovery Mode (accessable through GRUB) and run this command:

```
sudo dpkg-reconfigure xserver-xorg
```

This command should reset and reconfigure your screen properties, and get everything back to normal.

---

### Post by a cup of tea on 2009-10-18
After I hit reboot, suddenly everything looked normal, so I rebooted normally rather than going into recovery mode. I don't know why, I'd be a bit puzzled by this if I weren't happy that everything's fine now. 

Thank you for your help. :D

---

### Post by PorkyPie on 2009-10-18
> **a cup of tea said:**
> After I hit reboot, suddenly everything looked normal, so I rebooted normally rather than going into recovery mode. I don't know why, I'd be a bit puzzled by this if I weren't happy that everything's fine now. 

Thank you for your help. :D

You're welcome. If you can't ver get your system screen resolution back, you whould use the above command. Glad to help :)

---

