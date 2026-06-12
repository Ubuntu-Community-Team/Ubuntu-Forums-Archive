---
title: "Startup applications won't load on boot of Ubuntu 9.10 karmic"
date: 2010-09-03
forum: General Help
---

### Post by Nemo_bis on 2010-09-03
Since several months ago (I think when I upgraded to Karmic), whatever program I add to session startup won't load on boot, and no icon appears at the top-right of the screen, only clock and shutdown button (no audio etc.). [https://help.ubuntu.com/community/AddingProgramToSessionStartup](https://help.ubuntu.com/community/AddingProgramToSessionStartup) didn't help, nor did searching in forums and bugs.
I've enabled debug to /etc/gdm/custom.conf, and this is my .xsession-errors first part: 
```

Unable to create /home/name/.dbus/session-bus

(gnome-settings-daemon:1957): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:1957): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Avviso del window manager: Lettura del file della sessione /home/name/.config/metacity/sessions/10202b25c953eedbf3128344035910216700000019440001.ms non riuscita: Apertura del file "/home/name/.config/metacity/sessions/10202b25c953eedbf3128344035910216700000019440001.ms" non riuscita: Nessun file o directory
Unable to find a synaptics device.

(nautilus:1997): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
** (gnome-panel:1986): DEBUG: Adding applet 0.
** (gnome-panel:1986): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:1986): DEBUG: Adding applet 1.
** (gnome-panel:1986): DEBUG: Adding applet 2.

(gnome-panel:1986): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/name/.recently-used.xbel', but the parser failed: Errore nel leggere il file "/home/name/.recently-used.xbel": È una directory.
** (gnome-panel:1986): DEBUG: Adding applet 3.
** (gnome-panel:1986): DEBUG: Adding applet 4.
** (gnome-panel:1986): DEBUG: Adding applet 5.
** (gnome-panel:1986): DEBUG: Adding applet 6.
** (gnome-panel:1986): DEBUG: Adding applet 7.
** (gnome-panel:1986): DEBUG: Adding applet 8.
Initializing nautilus-gdu extension
Initializing nautilus-dropbox 0.6.1
** (gnome-panel:1986): DEBUG: Adding applet 9.
** (gnome-panel:1986): DEBUG: Adding applet 10.
** (gnome-panel:1986): DEBUG: Adding applet 11.
** (gnome-panel:1986): DEBUG: Adding applet 12.
** (gnome-panel:1986): DEBUG: Adding applet 13.

** (nautilus:1997): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1997): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1997): WARNING **: No marshaller for signature of signal 'ShareCreateError'

(nautilus:2047): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
sys:1: GtkWarning: Attempting to read the recently used resources file at `/home/name/.recently-used.xbel', but the parser failed: Errore nel leggere il file "/home/name/.recently-used.xbel": È una directory.

```

Following some suggestions on this forum I removed .recently-used.xbel to avoid recently opened files to be logged, so this explains part of these errors. 
I would like to fix this now because I had disabled gnome-screensaver but now I would need it to automate screen lock and looks like dbus may be the problem. My .dbus directory is empty.

---

### Post by Nemo_bis on 2010-09-03
Reinstalling gnome-screensaver was enough to make it work; I've also made myself owner of my .dbus directory (was root), and now a session-bus sub-directory (last modified on May 2009! owned by root) has appeared, while I'm pretty sure that there wasn't before.

---

