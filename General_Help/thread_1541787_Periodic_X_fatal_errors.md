---
title: "Periodic X fatal errors"
date: 2010-07-29
forum: General Help
---

### Post by violinuxer on 2010-07-29
Hello everyone!

Lately, I have been having problems with Xserver crashes (goes into low graphics mode). On inspection of my .xsession-errors file, I get X IO fatal errors 5, 11 and/or 104. Somehow my computer is losing its connection with the xserver (connection reset by peer) What is causing this? Should I post a report to launchpad? This happened before and after a clean install and more often when I opened a full screen game (SDL or OpenGL) Here is my xsession errors after my last crash:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-n6I1pR
GNOME_KEYRING_CONTROL=/tmp/keyring-n6I1pR
GNOME_KEYRING_CONTROL=/tmp/keyring-n6I1pR
SSH_AUTH_SOCK=/tmp/keyring-n6I1pR/ssh

(polkit-gnome-authentication-agent-1:1428): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1428): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:1440): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x83040f8'
** (nm-applet:1441): DEBUG: old state indicates that this was not a disconnect 0
Unable to find a synaptics device.
Initializing nautilus-gdu extension
** Message: Initializing gksu extension...
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
I/O warning : failed to load external entity "/home/*******/.compiz/session/10a6b301b86dc3b7f7128032276374161400000013670026"
/usr/bin/compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
evolution-alarm-notify-Message: Setting timeout for 53204 1280376000 1280322796
evolution-alarm-notify-Message:  Thu Jul 29 00:00:00 2010

evolution-alarm-notify-Message:  Wed Jul 28 09:13:16 2010

** (update-notifier:1637): DEBUG: Skipping reboot required
ERROR:dbus.proxies:Introspect error on :1.56:/com/ubuntu_tweak/daemon: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.55" (uid=1000 pid=1787 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.56" (uid=0 pid=1789 comm="/usr/bin/python))
/usr/bin/compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

(nautilus:1438): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported


(nautilus:1438): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported


(nautilus:1438): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported


(nautilus:1438): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported


(nautilus:1438): Nautilus-GDU-WARNING **: unable to query info: The specified location is not supported


(gnome-panel:1432): GLib-CRITICAL **: g_bookmark_file_load_from_data: assertion `length != 0' failed
/usr/bin/ubuntu-tweak:79: Warning: g_bookmark_file_load_from_data: assertion `length != 0' failed
  gtk.main()

(gnome-terminal:2001): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed
gnc.bin-Message: main: binreloc relocation support was disabled at configure time.


(gnome-terminal:6627): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed
Found Finance::Quote version 1.17
gwenhywfar-INFO: plugin.c:  574: Plugin type "ct" unregistered
gwenhywfar-INFO: plugin.c:  574: Plugin type "configmgr" unregistered
gwenhywfar-INFO: plugin.c:  574: Plugin type "dbio" unregistered
** (evolution:7540): DEBUG: mailto URL command: evolution %s
** (evolution:7540): DEBUG: mailto URL program: evolution
gnc.bin-Message: main: binreloc relocation support was disabled at configure time.

Found Finance::Quote version 1.17
gwenhywfar-INFO: plugin.c:  574: Plugin type "ct" unregistered
gwenhywfar-INFO: plugin.c:  574: Plugin type "configmgr" unregistered
gwenhywfar-INFO: plugin.c:  574: Plugin type "dbio" unregistered
gnc.bin-Message: main: binreloc relocation support was disabled at configure time.


** (gnome-settings-daemon:8193): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:8193): WARNING **: Could not acquire name
NOTE: child process received `Goodbye', closing down
gnc.bin-Message: main: binreloc relocation support was disabled at configure time.


** (evince:8117): WARNING **: Error setting file metadata: No such file or directory

** (evince:8117): WARNING **: Error setting file metadata: No such file or directory

** (evince:8117): WARNING **: Error setting file metadata: No such file or directory

** (evince:8117): WARNING **: Error setting file metadata: No such file or directory
Found Finance::Quote version 1.17
gwenhywfar-INFO: plugin.c:  574: Plugin type "ct" unregistered
gwenhywfar-INFO: plugin.c:  574: Plugin type "configmgr" unregistered
gwenhywfar-INFO: plugin.c:  574: Plugin type "dbio" unregistered
Found Finance::Quote version 1.17
gwenhywfar-INFO: plugin.c:  574: Plugin type "ct" unregistered
gwenhywfar-INFO: plugin.c:  574: Plugin type "configmgr" unregistered
gwenhywfar-INFO: plugin.c:  574: Plugin type "dbio" unregistered
gnc.bin-Message: main: binreloc relocation support was disabled at configure time.


(gnome-help:8351): Gtk-CRITICAL **: gtk_tool_button_new: assertion `icon_widget == NULL || GTK_IS_MISC (icon_widget)' failed

(gnome-help:8351): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-help:8351): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-help:8351): Gtk-CRITICAL **: gtk_toolbar_insert: assertion `GTK_IS_TOOL_ITEM (item)' failed

(gnome-help:8351): Gtk-CRITICAL **: gtk_tool_button_new: assertion `icon_widget == NULL || GTK_IS_MISC (icon_widget)' failed

(gnome-help:8351): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-help:8351): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-help:8351): Gtk-CRITICAL **: gtk_toolbar_insert: assertion `GTK_IS_TOOL_ITEM (item)' failed
/usr/share/software-center/softwarecenter/apt/aptcache.py:40: GtkWarning: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
  gtk.main_iteration()

(polkit-gnome-authentication-agent-1:1428): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(polkit-gnome-authentication-agent-1:1428): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
/usr/share/software-center/softwarecenter/view/appview.py:737: DeprecationWarning: integer argument expected, got float
  h)
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied

** (gnome-system-monitor:24312): WARNING **: SELinux was found but is not enabled.

debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
Found Finance::Quote version 1.17
gwenhywfar-INFO: plugin.c:  574: Plugin type "ct" unregistered
gwenhywfar-INFO: plugin.c:  574: Plugin type "configmgr" unregistered
gwenhywfar-INFO: plugin.c:  574: Plugin type "dbio" unregistered
NOTE: child process received `Goodbye', closing down
gnc.bin-Message: main: binreloc relocation support was disabled at configure time.

Info: Found gl-117 data directory /usr/share/games/gl-117 
Info: Startup gl-117, V1.3 ... 
Info: Loading /home/*******/.gl-117/conf 
Warning: Could not load /home/*******/.gl-117/conf
Info: No configuration file found. Testing...
Info: Using SDL and GLUT
Info: Saving /home/*******/.gl-117/conf 
Info: Loading /home/*******/.gl-117/conf.interface 
Warning: Could not load /home/*******/.gl-117/conf.interface
Info: Saving /home/*******/.gl-117/conf.interface 
Warning: Could not load saves/pilots
Warning: Could not load pilot
Info: Using SDL and GLUT
Info: Using SDL_mixer
Info: Joystick "Logitech Logitech Freedom 2.4" detected
Found Finance::Quote version 1.17
gwenhywfar-INFO: plugin.c:  574: Plugin type "ct" unregistered
gwenhywfar-INFO: plugin.c:  574: Plugin type "configmgr" unregistered
gwenhywfar-INFO: plugin.c:  574: Plugin type "dbio" unregistered
Info: Saving /home/*******/.gl-117/saveconf 
Info: Saving /home/*******/.gl-117/conf 
Info: Saving /home/*******/.gl-117/conf.interface 
Info: Pilots saved
No ID match for device smb://WORKGROUP/*******/Canon%20PIXMA%20iP4000:
  <manufacturer>Generic</manufacturer>
  <model>Printer</model>
  <description>Generic Printer</description>
  <commandset></commandset>
Using lsb/usr/cups-included/textonly.ppd (status: 3)
gnc.bin-Message: main: binreloc relocation support was disabled at configure time.

NOTE: child process received `Goodbye', closing down
Found Finance::Quote version 1.17
gwenhywfar-INFO: plugin.c:  574: Plugin type "ct" unregistered
gwenhywfar-INFO: plugin.c:  574: Plugin type "configmgr" unregistered
gwenhywfar-INFO: plugin.c:  574: Plugin type "dbio" unregistered
Info: Found gl-117 data directory /usr/share/games/gl-117 
Info: Startup gl-117, V1.3 ... 
Info: Loading /home/*******/.gl-117/conf 
Info: Saving /home/*******/.gl-117/conf 
Info: Loading /home/*******/.gl-117/conf.interface 
Info: Saving /home/*******/.gl-117/conf.interface 
Info: Using SDL and GLUT
Info: Using SDL_mixer
Info: Joystick "Logitech Logitech Freedom 2.4" detected
Info: Saving /home/*******/.gl-117/saveconf 
Info: Saving /home/*******/.gl-117/conf 
Info: Saving /home/*******/.gl-117/conf.interface 
Info: Pilots saved
Info: Found gl-117 data directory /usr/share/games/gl-117 
Info: Startup gl-117, V1.3 ... 
Info: Loading /home/*******/.gl-117/conf 
Info: Saving /home/*******/.gl-117/conf 
Info: Loading /home/*******/.gl-117/conf.interface 
Info: Saving /home/*******/.gl-117/conf.interface 
Info: Using SDL and GLUT
Info: Using SDL_mixer
Info: Joystick "Logitech Logitech Freedom 2.4" detected
Info: Saving /home/*******/.gl-117/saveconf 
Info: Saving /home/*******/.gl-117/conf 
Info: Saving /home/*******/.gl-117/conf.interface 
Info: Pilots saved
Info: Found gl-117 data directory /usr/share/games/gl-117 
Info: Startup gl-117, V1.3 ... 
Info: Loading /home/*******/.gl-117/conf 
Info: Saving /home/*******/.gl-117/conf 
Info: Loading /home/*******/.gl-117/conf.interface 
Info: Saving /home/*******/.gl-117/conf.interface 
Info: Using SDL and GLUT
Info: Using SDL_mixer
Info: Joystick "Logitech Logitech Freedom 2.4" detected
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Saving /home/*******/.gl-117/saveconf 
Info: Saving /home/*******/.gl-117/saveconf 
Info: Saving /home/*******/.gl-117/conf 
Info: Saving /home/*******/.gl-117/conf.interface 
Info: Pilots saved
Info: Found gl-117 data directory /usr/share/games/gl-117 
Info: Startup gl-117, V1.3 ... 
Info: Loading /home/*******/.gl-117/conf 
Info: Saving /home/*******/.gl-117/conf 
Info: Loading /home/*******/.gl-117/conf.interface 
Info: Saving /home/*******/.gl-117/conf.interface 
Info: Using SDL and GLUT
Info: Using SDL_mixer
Info: Joystick "Logitech Logitech Freedom 2.4" detected
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1280376000
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1280462400 1280376000
evolution-alarm-notify-Message:  Fri Jul 30 00:00:00 2010

evolution-alarm-notify-Message:  Thu Jul 29 00:00:00 2010

Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Initing new mission
Info: Saving /home/*******/.gl-117/saveconf 
Info: Saving /home/*******/.gl-117/conf 
Info: Saving /home/*******/.gl-117/conf.interface 
Info: Pilots saved

[COLOR=Blue]//This is where things fall apart[/COLOR]
[COLOR=Red](gnome-terminal:5690): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed
[COLOR=DarkOrange]../../intel/intel_bufmgr_gem.c:1152: Error setting memory domains 2 (00000040 00000000): Input/output error[/COLOR] .[COLOR=Black] [COLOR=Blue]//<-Whats this?[/COLOR][/COLOR]
firefox-bin: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-power-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XIO:  fatal IO error 5 (Input/output error) on X server ":0.0" 
      after 35696256 requests (35696254 known processed) with 1 events remaining. 
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
evolution-alarm-notify: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
<unknown>: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-terminal: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-panel: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
[/COLOR] 
(gnome-panel:1432): GLib-GObject-CRITICAL **: g_object_run_dispose: assertion `G_IS_OBJECT (object)' failed

(gnome-panel:1432): GLib-GObject-CRITICAL **: g_object_run_dispose: assertion `G_IS_OBJECT (object)' failed
```Thanks to everyone!!:D

violinuxer

---

### Post by violinuxer on 2010-09-01
Bump....

---

