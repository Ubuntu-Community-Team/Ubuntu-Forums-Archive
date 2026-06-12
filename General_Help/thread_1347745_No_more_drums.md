---
title: "No more drums"
date: 2009-12-06
forum: General Help
---

### Post by majest on 2009-12-06
Please can someone tell me how to remove the drum sound entirely from Ubuntu. It plays on startup and it plays in Firefox whenever there's a confirmation dialog. It's irritating and don't want to hear this sound ever again for any reason :)

---

### Post by Sam on 2009-12-06
System > Preferences > Sound

Sound theme: No sounds

---

### Post by LuisGMarine on 2009-12-06
> **Sam said:**
> System > Preferences > Sound

Sound theme: No sounds

That will just get rid of every sound on your system.  If you just want to get rid of the drum roll, run this command:

```
sudo -u gdm gconftool-2 --set /desktop/gnome/sound/event_sounds --type bool false
```

I learned this the hard way from a previous post [http://ubuntuforums.org/showthread.php?t=1346211]("http://ubuntuforums.org/showthread.php?t=1346211")

Hope this works! :popcorn:

---

