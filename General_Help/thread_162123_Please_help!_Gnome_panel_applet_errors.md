---
title: "Please help! Gnome panel applet errors"
date: 2006-04-18
forum: General Help
---

### Post by ketsugi on 2006-04-18
Several of my gnome panel applets refuse to load, giving me an error dialog for each one. Here's the error output from the console:

```
ketsugi@Asahara:~$ gnome-panel

** (gnome-panel:7481): WARNING **: /build/buildd/gnome-panel-2.14.1/./gnome-panel/panel-applet-frame.c:1261: failed to load applet OAFIID:GNOME_ShowDesktopApplet:
Failed to resolve, or extend '!prefs_key=/apps/panel/applets/show_desktop_button_screen0/prefs;background=none:;orient=up;size=x-small;locked_down=false

** (gnome-panel:7481): WARNING **: /build/buildd/gnome-panel-2.14.1/./gnome-panel/panel-applet-frame.c:1261: failed to load applet OAFIID:GNOME_WindowListApplet:
Failed to resolve, or extend '!prefs_key=/apps/panel/applets/window_list_screen0/prefs;background=none:;orient=up;size=x-small;locked_down=false

** (gnome-panel:7481): WARNING **: /build/buildd/gnome-panel-2.14.1/./gnome-panel/panel-applet-frame.c:1261: failed to load applet OAFIID:GNOME_Panel_TrashApplet:
Failed to resolve, or extend '!prefs_key=/apps/panel/applets/trashapplet_screen0/prefs;background=none:;orient=up;size=x-small;locked_down=false

** (gnome-panel:7481): WARNING **: /build/buildd/gnome-panel-2.14.1/./gnome-panel/panel-applet-frame.c:1261: failed to load applet OAFIID:GNOME_WorkspaceSwitcherApplet:
Failed to resolve, or extend '!prefs_key=/apps/panel/applets/workspace_switcher_screen0/prefs;background=none:;orient=up;size=x-small;locked_down=false

** (gnome-panel:7481): WARNING **: /build/buildd/gnome-panel-2.14.1/./gnome-panel/panel-applet-frame.c:1261: failed to load applet OAFIID:GNOME_MixerApplet:
Failed to resolve, or extend '!prefs_key=/apps/panel/applets/mixer_screen0/prefs;background=none:;orient=down;size=x-small;locked_down=false

** (gnome-panel:7481): WARNING **: /build/buildd/gnome-panel-2.14.1/./gnome-panel/panel-applet-frame.c:1261: failed to load applet OAFIID:GNOME_BattstatApplet:
Failed to resolve, or extend '!prefs_key=/apps/panel/applets/battstat_screen0/prefs;background=none:;orient=down;size=x-small;locked_down=false

** (gnome-panel:7481): WARNING **: /build/buildd/gnome-panel-2.14.1/./gnome-panel/panel-applet-frame.c:1261: failed to load applet OAFIID:GNOME_Panel_WirelessApplet:
Failed to resolve, or extend '!prefs_key=/apps/panel/applets/wireless_screen0/prefs;background=none:;orient=down;size=x-small;locked_down=false
```

I've tried purging gnome-panel(-data) and gnome-applets(-data) and reinstalling, and removing all my .gnome* and .gconf* directories, and even creating a new account, but I still get all these errors. It's beginning to get difficult to get any work done with only alt-tab to switch between apps.

Note: I'm using Dapper Flight 6 dist-upgraded from a fresh Breezy install. I already tried [posting in the Dapper forum](http://www.ubuntuforums.org/showthread.php?t=161084) but wasn't able to get any useful help there so far, so I'm trying my luck here.

---

