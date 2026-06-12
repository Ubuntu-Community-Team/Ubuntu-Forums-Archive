---
title: "Cannot login after removing zeitgeist"
date: 2012-09-02
forum: General Help
---

### Post by wojtalik on 2012-09-02
I removed zeitgeist (in the way it was advised here: [http://linuxaria.com/howto/how-to-remove-zeitgeist-in-ubuntu-and-why](http://linuxaria.com/howto/how-to-remove-zeitgeist-in-ubuntu-and-why)) and after that I cannot login graphically to my Ubuntu 12.04 anymore. 

The problem is the same for all users, including Guest user. After I type a password and hit "Enter", screen goes black for approx. 1 second and login screen apperas again. 

There is no problem with command line login. 

Here is a result of tail -30 .xsession-errors for user 1:

```
(gnome-fallback-mount-helper:2258): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Zasoby chwilowo niedost&#281;pne) on X server :0.


(nautilus:2261): Gdk-WARNING **: nautilus: Fatal IO error 11 (Zasoby chwilowo niedost&#281;pne) on X server :0.


(gdu-notification-daemon:2356): Gdk-WARNING **: gdu-notification-daemon: Fatal IO error 11 (Zasoby chwilowo niedost&#281;pne) on X server :0.

gtk-window-decorator: Fatal IO error 11 (Zasoby chwilowo niedost&#281;pne) on X server :0.0.

(telepathy-indicator:2477): Gdk-WARNING **: telepathy-indicator: Fatal IO error 11 (Zasoby chwilowo niedost&#281;pne) on X server :0.


(gnome-screensaver:2511): Gdk-WARNING **: gnome-screensaver: Fatal IO error 11 (Zasoby chwilowo niedost&#281;pne) on X server :0.


(update-notifier:2899): Gdk-WARNING **: update-notifier: Fatal IO error 11 (Zasoby chwilowo niedost&#281;pne) on X server :0.

kdeinit4: Fatal IO error: client killed
klauncher: Exiting on signal 15
kdeinit4: Fatal IO error: client killed

(bluetooth-applet:2255): Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Zasoby chwilowo niedost&#281;pne) on X server :0.

kdeinit4: kded4 [kdeinit]: Fatal IO error 11 (Zasoby chwilowo niedost&#281;pne) on X server :0.

(nm-applet:2247): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Zasoby chwilowo niedost&#281;pne) on X server :0.


** (zeitgeist-datahub:2510): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
```

-----------------

Here is a result of tail -30 .xsession-errors for another user:


```
(evolution-alarm-notify:28144): evolution-alarm-notify-WARNING **: alarm.c:260: Requested removal of nonexistent alarm!
Failed to open VDPAU backend libvdpau_nvidia.so: nie mo&#380;na otworzy&#263; pliku obiektu dzielonego: Nie ma takiego pliku ani katalogu
Failed to open VDPAU backend libvdpau_nvidia.so: nie mo&#380;na otworzy&#263; pliku obiektu dzielonego: Nie ma takiego pliku ani katalogu
Failed to open VDPAU backend libvdpau_nvidia.so: nie mo&#380;na otworzy&#263; pliku obiektu dzielonego: Nie ma takiego pliku ani katalogu
Failed to open VDPAU backend libvdpau_nvidia.so: nie mo&#380;na otworzy&#263; pliku obiektu dzielonego: Nie ma takiego pliku ani katalogu
Failed to open VDPAU backend libvdpau_nvidia.so: nie mo&#380;na otworzy&#263; pliku obiektu dzielonego: Nie ma takiego pliku ani katalogu

(gnome-settings-daemon:27758): print-notifications-plugin-CRITICAL **: gsd_print_notifications_plugin_finalize: assertion `plugin->priv != NULL' failed

(gnome-settings-daemon:27758): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-settings-daemon:27758): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
gnome-session[27676]: WARNING: Unable to stop system: Authorization is required

(nm-applet:27799): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Zasoby chwilowo niedost&#281;pne) on X server :1.


** (zeitgeist-datahub:28068): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!

(evolution-alarm-notify:28144): GConf-WARNING **: Got Disconnected from DBus.


(deja-dup-monitor:28818): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.36 of volume monitor org.gtk.Private.GduVolumeMonitor disconnected from the bus; removing drives/volumes/mounts
gtk-window-decorator: Fatal IO error 11 (Zasoby chwilowo niedost&#281;pne) on X server :1.0.
Terminated

(evolution:11980): Gdk-WARNING **: evolution: Fatal IO error 11 (Zasoby chwilowo niedost&#281;pne) on X server :1.

Terminated
```

Please help!

---

### Post by 2F4U on 2012-09-02
The zeitgeist daemon is needed in Ubuntu. The person in the article you are referring to is running Xubuntu, not Ubuntu. In Xubuntu zeitgeist is not even installed by default, but in Ubuntu it is necessary for several things to work. If you can get to a virtual console (Ctrl-Alt-F1) and login, you could try to re-install zeitgeist and see if this helps.

---

### Post by wojtalik on 2012-09-02
Thanks for reply and for pointing to the difference between Ubuntu and Xubuntu.

Yes, I installed zeitgeist again but it did not help! I reinstalled every single package that was uninstalled before but I still cannot login. Any idea why?

---

### Post by 2F4U on 2012-09-02
Are you sure that you installed everything that got removed? Zeitgeist has a couple of dependencies that probably got removed. It may also be worth to run unity --reset to get Unity back to its default settings, but you would lose all your settings.

---

