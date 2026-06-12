---
title: "X server periodacally crashing?"
date: 2011-06-19
forum: General Help
---

### Post by mvmacd on 2011-06-19
I'm on Ubuntu 11.04, upgraded from Ubuntu 10[.x, I forget which version] by the Package Manager.

Lately I've noticed my X server crashing every once in a while. Sometimes when I come out of Sleep, I can see my mouse, but the background looks like the boot log [you know, the messages when it's booting up].  It just crashed and here are the contents of ~/.xsession-errors:
```


/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
gnome-session[15944]: WARNING: Could not parse desktop file /home/matt/.config/autostart/xfconf-migration-4.6.desktop: Key file does not have key 'Name'
gnome-session[15944]: WARNING: could not read /home/matt/.config/autostart/xfconf-migration-4.6.desktop
gnome-session[15944]: WARNING: Could not parse desktop file /home/matt/.config/autostart/xfce4-settings-helper-autostart.desktop: Key file does not have key 'Name'
gnome-session[15944]: WARNING: could not read /home/matt/.config/autostart/xfce4-settings-helper-autostart.desktop
GNOME_KEYRING_CONTROL=/tmp/keyring-AAR7QQ
SSH_AUTH_SOCK=/tmp/keyring-AAR7QQ/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-AAR7QQ
SSH_AUTH_SOCK=/tmp/keyring-AAR7QQ/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-AAR7QQ
SSH_AUTH_SOCK=/tmp/keyring-AAR7QQ/ssh
** (<unknown>:15992): DEBUG: Client registered with session manager: /org/gnome/SessionManager/Client2
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing move options...done
Initializing resize options...done
Initializing grid options...done
Initializing commands options...done
gnome-session[15944]: WARNING: Could not launch application 'gnome-screensaver.desktop': Unable to start application: Failed to execute child process "xscreensaver" (No such file or directory)
/home/matt/.boot: line 4: s: command not found
Initializing gnomecompat options...done
/home/matt/.boot: line 7: s: command not found
Initializing place options...done
tput: No value for $TERM and no -T specified
tput: No value for $TERM and no -T specified
Initializing animation options...done
tput: No value for $TERM and no -T specified
Initializing screenshot options...done
Initializing annotate options...done
I/O warning : failed to load external entity "/home/matt/.compiz/session/10e2318c97b880e7c13085037227025400000159440045"
Initializing session options...done
Initializing vpswitch options...done
Initializing workarounds options...done
Initializing mousepoll options...done
Initializing wall options...done
Initializing wobbly options...done
Initializing expo options...done
Initializing ezoom options...done
Initializing staticswitcher options...done
Initializing fade options...done
Initializing scale options...done
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension
Starting unity-window-decorator

(nautilus:16033): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Failed to play sound: File or data not found
Setting Update "texture_filter"
Setting Update "opacity"
Setting Update "command0"
Setting Update "command1"
Setting Update "command2"
Setting Update "run_command0_key"
Setting Update "run_command1_key"
Setting Update "run_command2_key"
Setting Update "run_key"
Setting Update "directory"
Setting Update "launch_app"
Setting Update "clear_key"
Setting Update "fill_color"
Setting Update "stroke_color"
Setting Update "shiver"
Setting Update "friction"
Setting Update "spring_k"
Setting Update "expo_key"
Setting Update "next_all_key"
Setting Update "prev_all_key"
[16202:16276:107278814939:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[16202:16276:107278815420:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[16202:16276:107278817671:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[16202:16276:107278817743:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[16202:16275:107279113459:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[16202:16268:107279121450:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[16202:16268:107279121566:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[16202:16268:107279121587:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[16202:16274:107279131832:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[16202:16267:107279132892:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[16202:16267:107279133984:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[16202:16267:107279134008:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[16202:16269:107279254937:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[16202:16288:107279787855:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[16202:16288:107279788729:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[16202:16288:107279799946:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[16202:16288:107279800252:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[16202:16256:107280866266:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
Gtk-Message: Failed to load module "atk-bridge"
Gtk-Message: Failed to load module "atk-bridge"
Gtk-Message: Failed to load module "gail-gnome"
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
Loading plugin Twitter version 1.0
Loading plugin Identi.ca version 1.1
Loading plugin Facebook version 1.1
sh: dropbox: not found
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

```
and here is ~/.xsession-errors.old
```


/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
gnome-session[14954]: WARNING: Could not parse desktop file /home/matt/.config/autostart/xfconf-migration-4.6.desktop: Key file does not have key 'Name'
gnome-session[14954]: WARNING: could not read /home/matt/.config/autostart/xfconf-migration-4.6.desktop
gnome-session[14954]: WARNING: Could not parse desktop file /home/matt/.config/autostart/xfce4-settings-helper-autostart.desktop: Key file does not have key 'Name'
gnome-session[14954]: WARNING: could not read /home/matt/.config/autostart/xfce4-settings-helper-autostart.desktop
GNOME_KEYRING_CONTROL=/tmp/keyring-d9gcbz
SSH_AUTH_SOCK=/tmp/keyring-d9gcbz/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-d9gcbz
SSH_AUTH_SOCK=/tmp/keyring-d9gcbz/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-d9gcbz
SSH_AUTH_SOCK=/tmp/keyring-d9gcbz/ssh
** (<unknown>:15003): DEBUG: Client registered with session manager: /org/gnome/SessionManager/Client2
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
gnome-session[14954]: WARNING: Could not launch application 'gnome-screensaver.desktop': Unable to start application: Failed to execute child process "xscreensaver" (No such file or directory)
/home/matt/.boot: line 4: s: command not found
/home/matt/.boot: line 7: s: command not found
tput: No value for $TERM and no -T specified
tput: No value for $TERM and no -T specified
tput: No value for $TERM and no -T specified
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
** (process:15051): DEBUG: zeitgeist-datahub.vala:174: Inserting 7 events
Failed to play sound: File or data not found
Initializing move options...done
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension
Initializing resize options...done
Initializing grid options...done
Initializing commands options...done
Initializing gnomecompat options...done
Initializing place options...done
Initializing animation options...done
Initializing screenshot options...done
Initializing annotate options...done
I/O warning : failed to load external entity "/home/matt/.compiz/session/107a2e0eb11785b912130850344823963000000149540045"
Initializing session options...done
Initializing vpswitch options...done
Initializing workarounds options...done
Initializing mousepoll options...done
Initializing wall options...done
Initializing wobbly options...done
Initializing expo options...done
Initializing ezoom options...done
Initializing staticswitcher options...done
Initializing fade options...done
Initializing scale options...done
Starting unity-window-decorator
Setting Update "texture_filter"
Setting Update "opacity"
Setting Update "command0"
Setting Update "command1"
Setting Update "command2"
Setting Update "run_command0_key"
Setting Update "run_command1_key"
Setting Update "run_command2_key"
Setting Update "run_key"
Setting Update "directory"
Setting Update "launch_app"
Setting Update "clear_key"
Setting Update "fill_color"
Setting Update "stroke_color"
Setting Update "shiver"
Setting Update "friction"
Setting Update "spring_k"
Setting Update "expo_key"
Setting Update "next_all_key"
Setting Update "prev_all_key"

(nautilus:15046): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15046): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15046): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15046): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15046): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15046): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Loading plugin Twitter version 1.0
Loading plugin Identi.ca version 1.1
Loading plugin Facebook version 1.1
sh: dropbox: not found

** (gnome-settings-daemon:15446): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:15446): WARNING **: Could not acquire name

(polkit-gnome-authentication-agent-1:15050): Gtk-CRITICAL **: IA__gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
Gtk-Message: Failed to load module "atk-bridge"
Gtk-Message: Failed to load module "atk-bridge"
Gtk-Message: Failed to load module "gail-gnome"
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
      after 42309 requests (42309 known processed) with 0 events remaining.
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
<unknown>: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
The application 'gnome-session' lost its connection to the display :0;
most likely the X server was shut down or you killed/destroyed
the application.
gnome-settings-daemon: Fatal IO error 104 (Connection reset by peer) on X server :0.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 11 requests (11 known processed) with 0 events remaining.
unity-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
unity-window-decorator: Fatal IO error 104 (Connection reset by peer) on X server :0.
[15707:15707:107262825051:ERROR:x11_util.cc(66)] X IO Error detected
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
update-notifier: Fatal IO error 2 (No such file or directory) on X server :0.
npviewer.bin: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-panel: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
The application 'gnome-panel' lost its connection to the display :0;
most likely the X server was shut down or you killed/destroyed
the application.
gnome-power-manager: Fatal IO error 104 (Connection reset by peer) on X server :0.

** (gnome-power-manager:15049): WARNING **: Failed to send buffer

** (gnome-power-manager:15049): WARNING **: Failed to send buffer
The application 'gnome-power-manager' lost its connection to the display :0;
most likely the X server was shut down or you killed/destroyed
the application.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
The application 'gdu-notification-daemon' lost its connection to the display :0;
most likely the X server was shut down or you killed/destroyed
the application.
[15463:15463:107262846144:ERROR:browser_main_gtk.cc(75)] X IO Error detected
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
The application 'polkit-gnome-authentication-agent-1' lost its connection to the display :0;
most likely the X server was shut down or you killed/destroyed
the application.
wicd-client.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
The application 'wicd-client.py' lost its connection to the display :0;
most likely the X server was shut down or you killed/destroyed
the application.
Has notifications support True
rename failed
Loading...
Connecting to daemon...
Connected.
displaytray True
Done loading.
checkgmail: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
The application 'checkgmail' lost its connection to the display :0;
most likely the X server was shut down or you killed/destroyed
the application.
gwibber-service: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
gwibber-service: Fatal IO error 2 (No such file or directory) on X server :0.
nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
The application 'nautilus' lost its connection to the display :0;
most likely the X server was shut down or you killed/destroyed
the application.
** (process:15051): DEBUG: zeitgeist-datahub.vala:58: Zeitgeist-daemon disappeared from the bus, exitting...

** (process:15051): WARNING **: zeitgeist-datahub.vala:218: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

```

Anyone have any ideas?

~Matt

---

