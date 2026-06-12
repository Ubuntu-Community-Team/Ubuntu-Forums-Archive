---
title: "excessive login time in Gnome - Ubuntu 10.04"
date: 2010-05-02
forum: General Help
---

### Post by andremalo on 2010-05-02
Hi guys, first of all thanks for your support and greetings to all.
I've update to ubuntu 10.04, it's a new installation from the cd dafter formatting the hard disk.
I've no problem with the os, it's stable and performing as i expected, but it spent almost a minute to log me in Gnome after i've inserted username & password in GDM.
I've tried different solutions, from switching windowm manager to changing  network manager but problem still persists.
Here is my bootchart, i'm not able to get useful informations from it.
Thanks in advance

[http://img709.imageshack.us/img709/815/andrelucid201005021.png](http://img709.imageshack.us/img709/815/andrelucid201005021.png)

EDIT: here is my .xsession-errors

> /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=it_IT.
Start IM through /home/andre/.xinput.d/it_IT linked to /etc/X11/xinit/xinput.d/none.
GNOME_KEYRING_CONTROL=/tmp/keyring-oY6IDc
GNOME_KEYRING_CONTROL=/tmp/keyring-oY6IDc
SSH_AUTH_SOCK=/tmp/keyring-oY6IDc/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-oY6IDc
SSH_AUTH_SOCK=/tmp/keyring-oY6IDc/ssh
gnome-session[2038]: WARNING: Could not launch application 'nm-applet.desktop': Unable to start application: Esecuzione del processo figlio "nm-applet" non riuscita (Nessun file o directory)

(polkit-gnome-authentication-agent-1:2100): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2100): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: Initializing gksu extension...

(gnome-panel:2105): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/andre/.recently-used.xbel', but the parser failed: Errore nel leggere il file "/home/andre/.recently-used.xbel": Argomento non valido.
Initializing nautilus-image-converter extension
Initializing nautilus-open-terminal extension
Initializing nautilus-gdu extension
Unable to find a synaptics device.
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
I/O warning : failed to load external entity "/home/andre/.compiz/session/10b68dfc78d502037b127283160116176300000020380038"
/usr/bin/compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
Updating...

(gnome-terminal:7296): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

(firefox-bin:3750): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3750): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3750): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3750): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3750): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3750): Gdk-WARNING **: XID collision, trouble ahead

(gnome-terminal:17411): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

(firefox-bin:3750): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3750): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3750): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:3750): Gdk-WARNING **: XID collision, trouble ahead

(gnome-terminal:20296): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

(firefox-bin:3750): Gdk-WARNING **: XID collision, trouble ahead

---

### Post by andremalo on 2010-05-04
i'm working on it...this is my new boothchart and xsession.
Suggestions?

[http://img243.imageshack.us/img243/5153/andrelucid201005042.png](http://img243.imageshack.us/img243/5153/andrelucid201005042.png)

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=it_IT.
Start IM through /home/andre/.xinput.d/it_IT linked to /etc/X11/xinit/xinput.d/none.
GNOME_KEYRING_CONTROL=/tmp/keyring-4wkE3f
SSH_AUTH_SOCK=/tmp/keyring-4wkE3f/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-4wkE3f
SSH_AUTH_SOCK=/tmp/keyring-4wkE3f/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-4wkE3f
SSH_AUTH_SOCK=/tmp/keyring-4wkE3f/ssh

(polkit-gnome-authentication-agent-1:2107): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2107): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: Initializing gksu extension...
Initializing nautilus-image-converter extension
Initializing nautilus-open-terminal extension
Initializing nautilus-gdu extension
Unable to find a synaptics device.
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
I/O warning : failed to load external entity "/home/andre/.compiz/session/10b731f5731a83e0db127296422317250600000020460039"
/usr/lib/python2.6/dist-packages/FusionIcon/interface_gtk/main.py:213: GtkWarning: gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
  gtk.main()
/usr/bin/compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
```

---

### Post by lurreluck on 2010-05-16
I have the same problem. It takes about 20 seconds for me.

EDIT: Check this out; [http://ubuntuforums.org/showthread.php?t=1472384](http://ubuntuforums.org/showthread.php?t=1472384)

---

### Post by michy99 on 2010-05-16
ureadahead caused massive slowdowns for me every time it had to re-profile. After removing it, I'm happy as a clam.

---

