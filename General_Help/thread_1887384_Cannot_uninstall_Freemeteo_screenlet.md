---
title: "Cannot uninstall Freemeteo screenlet"
date: 2011-11-26
forum: General Help
---

### Post by bep7987 on 2011-11-26
I have used the screenlet manager to uninstall the freemeteo (weather) screenlet, but it still starts everytime I boot my system.

When I highlight freemeteo in the screenlet manager, I do not have the option to uninstall the screenlet as I do with the other screenlets that I've installed.

Can someone tell me how to remove the screenlet?  I have tried uninstalling screenlets, but there seems to be a configuration file that does not get deleted.

---

### Post by raja.genupula on 2011-11-26
use this to delete completely 
```
sudo apt-get remove --purge screenlets
```

and then reinstall

---

### Post by bep7987 on 2011-11-26
Thanks, but purging doesn't work.  When I reinstall screenlets, freemeteo is still installed, so there must be a configuration file that is not getting deleted.

---

### Post by hansdown on 2011-11-26
Hi,bep7987.

If you right click the icon, you should be able to uncheck the box, that says,

```
load at startup
```

Sorry, I can't install it on this version, so I'm going from memory.

Edit:

I booted 10.04, and have a sceenshot.

---

### Post by bep7987 on 2011-12-04
Thank you, hansdown.  That worked.

Now, if I could only get ClearWeather to start automatically.  I select autostart on login, but for some reason, it doesn't save the setting for ClearWeather.

---

### Post by hansdown on 2011-12-04
> **bep7987 said:**
> Thank you, hansdown.  That worked.

Now, if I could only get ClearWeather to start automatically.  I select autostart on login, but for some reason, it doesn't save the setting for ClearWeather.

Glad you fixed the fist part,bep7987.

Not sure about the clearweather part.

Did you download it from gnome-look.org?

---

### Post by bep7987 on 2011-12-18
No, it's just one of the screenlets in the standard installation from the repository.

---

### Post by hansdown on 2011-12-18
> **bep7987 said:**
> No, it's just one of the screenlets in the standard installation from the repository.

You rock, bep7987.

I've had problems, with clearweather.

I ended up right clicking a blank space on the top bar>add to panel>weather applet.

It seems to work better, and looks more elegant.

---

