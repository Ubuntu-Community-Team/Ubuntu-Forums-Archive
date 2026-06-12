---
title: "Appereance Preference: &quot;Unable to show http://art.gnome.org/themes/&quot;"
date: 2009-11-18
forum: General Help
---

### Post by manolomanolo on 2009-11-18
Hi to all.

The Appereance Preference application is unable to open Firefox.
In fact, executing **gnome-appearance-properties** from terminal and trying to click on "Get more themes online" I get:

[INDENT]*(gnome-appearance-properties:3106): Gtk-WARNING **: Unable to show 'http://art.gnome.org/themes/': Failed to execute child process "/usr/bin/firefox-3.6" (No such file or directory)*[/INDENT]

Actually I have no more firefox-3.6 installed but I suppose Ubuntu still searches for it as "default browser" or something. I suppose other applications suffer the same problem too when trying to open a web browser.

Is there any way to discover which (configuration?) file points to firefox-3.6? 
Any other suggestion to solve this problem?

Thanks.

---

### Post by manolomanolo on 2009-11-18
Tha problem has been solved just setting the proper paramether in

System-> Preferences -> Preferred Applications -> Internet -> Web Browser

In my case, it was set to "custom" and firefox-3.6 was specified.
Since I just have an official version of firefox, I unset the "custom" option and just set "Firefox" from the window menu.

---

