---
title: "Command to load a specific GNOME session"
date: 2011-10-26
forum: General Help
---

### Post by tonysathre on 2011-10-26
I was just wondering what command I can use to start a specific desktop session.

My session file is 

/usr/share/gnome-session/sessions/cairo-dock.session

which contains:

```


[GNOME Session]
Name=Cairo-Dock Session
RequiredComponents=gnome-settings-daemon;
RequiredProviders=windowmanager;panel;
DefaultProvider-windowmanager=compiz
DefaultProvider-panel=cairo-dock
FallbackSession=cairo-dock-fallback
DesktopName=GNOME

```

Basically I'm looking for a command line way to start this specific GNOME session.

Thanks,

Tony

---

