---
title: "Help needed: Unable to log in with Gnome GUI session"
date: 2011-06-22
forum: General Help
---

### Post by sohelmk on 2011-06-22
Hi,
Can some please help to troubleshoot this issue. Its on Ubuntu 10.04 on dell vostro laptop.
Suddenly i cannot login, it returns to login screen again. There is just one user with which I can login. I even tried creating new users, the same issue. Attached are all xorg and gdm logs. Only one change i remember making is adding a screen resolution for external lcd screen. But it was working fine for some days.

Here are some errors from log:

XORG:

(gnome-power-manager:2967): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x8ad6870'
Initializing nautilus-gdu extension
WARNING: [Do.Banshee,1.0] Could not load some add-in assemblies: File '/usr/lib/banshee-1/Banshee.CollectionIndexer.dll' not found.
ERROR: Errors found in add-in '/usr/lib/gnome-do/plugins/Banshee.dll:
ERROR: The file '/usr/lib/banshee-1/Banshee.CollectionIndexer.dll' referenced in the manifest could not be found.
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator

** (gnome-screensaver:3069): WARNING **: Cannot open display: 
gnome-session[2893]: WARNING: Detected that screensaver has left the bus
gnome-session: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
gnome-settings-daemon: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0" 
      after 39 requests (38 known processed) with 0 events remaining. 
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
canberra-gtk-play: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-power-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0" 
      after 2004 requests (2002 known processed) with 6 events remaining. 
Do: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
nautilus: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
monajat-applet: Fatal IO error 104 (Connection reset by peer) on X server :0.0.

(gtk-window-decorator:3065): Gtk-WARNING **: cannot open display: :0.0
The application 'gnome-panel' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

GDM:
Window manager warning: Failed to read saved session file /var/lib/gdm/.config/metacity/sessions/10f52ae1a4f3c7d2de130875111740458300000017380004.ms: Failed to open file '/var/lib/gdm/.config/metacity/sessions/10f52ae1a4f3c7d2de130875111740458300000017380004.ms': No such file or directory
** (process:1750): DEBUG: Greeter session pid=1750 display=:0.0 xauthority=/var/run/gdm/auth-for-gdm-6fzhjE/database

(gnome-power-manager:1748): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x9f1c2c8'
gdm-simple-greeter[1750]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow

Thanks a lot,
Sohel.

---

