---
title: "Compiz and 11.10 Trouble"
date: 2011-10-19
forum: General Help
---

### Post by JMT391 on 2011-10-19
I have Oneiric + CCSM Installed on both my desktop and netbook.  I broke unity (whoops) on the desktop.  I used gconftool-2 --recursive-unset /apps/compiz-1 and unity --reset to get everything back to defaults.  The gconftool command seemingly worked, but when opening CCSM again none of the settings were reset.  In addition, the unity --reset command never finishes successfully.  It hangs at "Initializing session options...done."  I tried this in a regular terminal and the tty terminal as both root and user.  Neither worked, left running for hours.  CCSM's "reset" button does not work either, just causes crashes or does nothing.  Logging in and out does nothing.  Unity 2D and Gnome3 work fine.  Running the ccsm reset stuff from Unity 2D or Gnome3 does not work.

Went to the netbook so I could export the default profile from CCSM.  Clicked on profiles, computer locked up.  The mouse would move but clicking did not register and keyboard shortcuts seized to work.  Hard reset, now unity is broken on the netbook.  Same issues with CCSM and terminal/tty terminal commands.  The only thing that displays on either desktop is the top bar, and it does not contain the system tray, just "File Edit View" etc...

Before I waste my time doing 2 full reinstalls, does anyone know what might be happening?  Are there known issues with compiz and Oneiric?

---

