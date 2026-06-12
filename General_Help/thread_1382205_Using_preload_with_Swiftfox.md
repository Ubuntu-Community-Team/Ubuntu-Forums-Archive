---
title: "Using preload with Swiftfox"
date: 2010-01-15
forum: General Help
---

### Post by agrh on 2010-01-15
I recently started using the preload daemon, and it seems to work fine, but it doesn't preload Swiftfox which is mostly why I use it. There seems to be no developer support and no real documentation other than the thesis paper available, but they list speed improvements for Firefox. Is it possible Swiftfox is somehow un-preloadable? I'm using the stock /etc/preload.conf, any help would be appreciated.

---

### Post by warfacegod on 2010-01-15
> **agrh said:**
> I recently started using the preload daemon, and it seems to work fine, but it doesn't preload Swiftfox which is mostly why I use it. There seems to be no developer support and no real documentation other than the thesis paper available, but they list speed improvements for Firefox. Is it possible Swiftfox is somehow un-preloadable? I'm using the stock /etc/preload.conf, any help would be appreciated.

I don't see how one could be preloadable and not the other. They're basically the same thing just different name and about:config settings.

---

### Post by agrh on 2010-01-15
```
[Fri Jan 15 16:31:16 2010] state updating begin
[Fri Jan 15 16:31:16 2010] state updating end
[Fri Jan 15 16:31:26 2010] state scanning begin
[Fri Jan 15 16:31:26 2010] state log dump requested
persistent state stats:
preload time = 33580
num exes = 65
num bad exes = 1
num maps = 1669
runtime state stats:
num running exes = 58
[Fri Jan 15 16:31:26 2010] state log dump done
[Fri Jan 15 16:31:26 2010] state scanning end
[Fri Jan 15 16:31:26 2010] state predicting begin
ln(prob(~EXE)) =     -0.0261939390    /usr/lib/totem/totem-plugin-viewer
ln(prob(~EXE)) =     -0.0020695872    /usr/bin/sudo
ln(prob(~EXE)) =     -0.0041759983    /usr/bin/gksu
ln(prob(~EXE)) =     -0.0000907714    /usr/lib/gnome-panel/gnome-clock-applet-mechanism
ln(prob(~EXE)) =     -0.0028237163    /usr/bin/evince
ln(prob(~EXE)) =     -0.0064860531    /usr/lib/telepathy/mission-control-5
ln(prob(~EXE)) =     -0.0064860531    /usr/bin/empathy
ln(prob(~EXE)) =     -0.0111700606    /usr/bin/gcalctool
ln(prob(~EXE)) =     -0.0061831630    /usr/bin/gedit
ln(prob(~EXE)) =     -0.1332035178    /usr/bin/gnome-session-properties
[Fri Jan 15 16:31:26 2010] 366720kb available for preloading, using 49488kb of it

```

This is my debug output and you can see it preloading all sorts of things, some that I rarely use and even the mozilla totem plugin, but no Swiftfox. It occurs to me that Swiftfox might statically link the binaries and debs they release, could that affect preload?

---

### Post by warfacegod on 2010-01-15
From what I understand, Swiftfox uses the Firefox install and sort of lays itself on top if it. When I add a theme, for instance, to either, the other displays the correct theme. Same with bookmarks and any of the add-ons I install. I think Swiftfox is being preloaded, it's just being read as Firefox in your output.

---

