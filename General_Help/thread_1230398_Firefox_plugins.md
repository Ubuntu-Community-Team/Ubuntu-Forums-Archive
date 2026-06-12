---
title: "Firefox plugins?"
date: 2009-08-03
forum: General Help
---

### Post by Flexico on 2009-08-03
I'm trying to be able to watch Flash movies with Firefox, but the plugin that was installed when I clicked the box "install missing plugins" that came out of the top of the browsing window doesn't work very well. So, I installed the official Flash player from the Adobe website, but Firefox doesn't recognize it. And now I can't figure out how to get rid of the one that doesn't work right! I've gone into Tools>>Plugins, but there's only a "disable" option, not uninstall.

---

### Post by kellemes on 2009-08-03
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Flexico on 2009-08-03
> **kellemes said:**
> ```
sudo apt-get install flashplugin-nonfree
```

I already have that installed -- I need to UNinstall a different shockwave plugin before it will work.

---

### Post by grizzler on 2009-08-03
The Adobe plugin didn't want to install here either (seems a lot of people have that problem). So I disabled the old version in Firefox's Add-ons/Plug-ins window, copied the file (**libflashplayer.so**) to **~/.mozilla/plugins**, overwriting the old file that was there and restarted Firefox. That's all it took.

Oh, I did remove all the 'flashplugin' stuff before downloading Adobe's version, mainly because Synaptic still showed the old version (still does today).

---

### Post by jocampo on 2009-08-03
Hi Flexico:

Please do this to remove a package for good

```
apt-get --purge remove <package>
```

replace <package> for the one that is yours and you want to remove. Please be sure Firefox is not open before execute it.

---

### Post by bryncoles on 2009-08-03
when you're on a page which requires flash, do you see a little 'lego brick' icon in the bottom right of firefox? click it, and it'll bring up a menue for configuring plugins in use. i'll wager you're not yet using adobe's plug in. you should be able to click around and select the plug in here!

---

