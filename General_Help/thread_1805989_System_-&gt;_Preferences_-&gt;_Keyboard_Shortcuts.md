---
title: "System -&gt; Preferences -&gt; Keyboard Shortcuts"
date: 2011-07-16
forum: General Help
---

### Post by I Am Legend on 2011-07-16
Just curious, is there a command line version of the above?

---

### Post by I Am Legend on 2011-07-22
So, no way to configure these in a post-install script?

---

### Post by Frogs Hair on 2011-07-22
Keyboard shortcuts is one of the functions of the gnome-settings-daemon , so I'm not sure how you go about starting that one particular function. This is what the GSD controls .  

 * Keyboard: layout, accessibility options, shortcuts, media keys
 * Clipboard management
 * Theming: background, icons, GTK+ applications
 * Cleanup of unused files
 * Mouse: cursors, speed, accessibility options
 * Startup of other daemons: screensaver, sound daemon
 * Typing break

It also sets various application settings through X resources and
freedesktop.org XSETTINGS.

---

