---
title: "Help! My account is &quot;not working with X11&quot;"
date: 2011-10-22
forum: General Help
---

### Post by spng453 on 2011-10-22
Hi!

So, I decided to see what user defined session was, after about 3 failed attempts at installing E, so after I logged out, I tried to log into my account. When I did, the screen went black for about 10 seconds, then brought me back to the login screen with no errors. I then made a password for root, and it worked just fine. (except for a weird black frozen screen with random noise in one spot, lol)

I am running a copy of Ubuntu 11.10.

Here is my .xsession-errors file

```
Running X session wrapper
Loading profile from /etc/profile
Loading profile from /home/tyler/.profile
Loading resource: /etc/X11/Xresources/x11-common
Loading X session script /etc/X11/Xsession.d/00_handle_guest_session
Loading X session script /etc/X11/Xsession.d/20x11-common_process-args
Loading X session script /etc/X11/Xsession.d/30x11-common_xresources
Loading X session script /etc/X11/Xsession.d/40x11-common_xsessionrc
Loading X session script /etc/X11/Xsession.d/50_check_unity_support
Loading X session script /etc/X11/Xsession.d/50x11-common_determine-startup
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/55gnome-session_gnomerc
Loading X session script /etc/X11/Xsession.d/60x11-common_localhost
Loading X session script /etc/X11/Xsession.d/60x11-common_xdg_path
Loading X session script /etc/X11/Xsession.d/60xdg-user-dirs-update
Loading X session script /etc/X11/Xsession.d/65compiz_profile-on-session
Loading X session script /etc/X11/Xsession.d/70gconfd_path-on-session
Loading X session script /etc/X11/Xsession.d/75dbus_dbus-launch
Loading X session script /etc/X11/Xsession.d/80appmenu
Loading X session script /etc/X11/Xsession.d/80appmenu-gtk3
Loading X session script /etc/X11/Xsession.d/80im-switch
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Loading X session script /etc/X11/Xsession.d/90consolekit
Loading X session script /etc/X11/Xsession.d/90qt-a11y
Loading X session script /etc/X11/Xsession.d/90x11-common_ssh-agent
Loading X session script /etc/X11/Xsession.d/99x11-common_start
GNOME_KEYRING_CONTROL=/tmp/keyring-2GaIAA
GNOME_KEYRING_CONTROL=/tmp/keyring-2GaIAA
SSH_AUTH_SOCK=/tmp/keyring-2GaIAA/ssh
GPG_AGENT_INFO=/tmp/keyring-2GaIAA/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-2GaIAA
SSH_AUTH_SOCK=/tmp/keyring-2GaIAA/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-2GaIAA
SSH_AUTH_SOCK=/tmp/keyring-2GaIAA/ssh
GPG_AGENT_INFO=/tmp/keyring-2GaIAA/gpg:0:1

(gnome-settings-daemon:1854): color-plugin-WARNING **: failed to get edid: unable to get EDID for output
common-plugin-Message: checking whether we have a device for 4: yes
common-plugin-Message: checking whether we have a device for 5: yes
common-plugin-Message: checking whether we have a device for 6: yes
common-plugin-Message: checking whether we have a device for 7: yes
common-plugin-Message: checking whether we have a device for 8: yes
common-plugin-Message: checking whether we have a device for 9: yes
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
x-session-manager[1792]: WARNING: Application 'compiz.desktop' failed to register before timeout
x-session-manager[1792]: CRITICAL: We failed, but the fail whale is dead. Sorry....
** (gnome-fallback-mount-helper:1926): DEBUG: Starting automounting manager

(bluetooth-applet:1925): Bluetooth-WARNING **: Could not open RFKILL control device, please verify your installation
Initializing nautilus-gdu extension
** (gnome-fallback-mount-helper:1926): DEBUG: Found ConsoleKit session at path /org/freedesktop/ConsoleKit/Session2
** (gnome-fallback-mount-helper:1926): DEBUG: ScreenSaver name appeared
** (gnome-fallback-mount-helper:1926): DEBUG: ScreenSaver proxy ready
** (gnome-fallback-mount-helper:1926): DEBUG: ConsoleKit session is active 0
** (gnome-fallback-mount-helper:1926): DEBUG: Screensaver GetActive() returned 0
Failed to play sound: Invalid state
** Message: applet now removed from the notification area
** (nm-applet:1930): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1930): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1930): DEBUG: foo_client_state_changed_cb
** Message: using fallback from indicator to GtkStatusIcon

(nautilus:1927): Gtk-CRITICAL **: gtk_action_set_visible: assertion `GTK_IS_ACTION (action)' failed

(nautilus:1927): Gtk-CRITICAL **: gtk_action_set_visible: assertion `GTK_IS_ACTION (action)' failed

(nautilus:1927): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1927): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1927): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1927): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1927): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1927): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1927): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1927): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1927): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1927): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1927): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1927): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1927): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1927): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1927): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1927): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1927): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1927): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (process:2226): DEBUG: Telepathy Indicator started
** (nm-applet:1930): DEBUG: old state indicates that this was not a disconnect 20
** (nm-applet:1930): DEBUG: foo_client_state_changed_cb
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (nm-applet:1930): DEBUG: foo_client_state_changed_cb
** (nm-applet:1930): DEBUG: going for offline with icon: notification-network-wireless-disconnected
** (nm-applet:1930): DEBUG: old state indicates that this was not a disconnect 20
** (nm-applet:1930): DEBUG: foo_client_state_changed_cb
** (nm-applet:1930): DEBUG: going for offline with icon: notification-network-wireless-disconnected
** (nm-applet:1930): DEBUG: foo_client_state_changed_cb
** (nm-applet:1930): DEBUG: going for offline with icon: notification-network-wireless-disconnected
** (nm-applet:1930): DEBUG: going for offline with icon: notification-network-wireless-disconnected

** (process:2452): WARNING **: recent-manager-provider.vala:125: Desktop file for xine was not found
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
I/O warning : failed to load external entity "/home/tyler/.compiz/session/101a22e72081d424cc131929848277996200000017920039"
Initializing session options...done
compiz (core) - Warn: no exact match for ConfigureNotify on 0x1200109!
compiz (core) - Warn: expected the following changes:
compiz (core) - Warn: sibling: 0x427e66
compiz (core) - Warn: instead got:
compiz (core) - Warn: x: 0
compiz (core) - Warn: y: 0
compiz (core) - Warn: width: 1920
compiz (core) - Warn: height: 1080
compiz (core) - Warn: above: 0
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
Starting unity-window-decorator
Initializing annotate options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing cube options...done
Initializing debugspew options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing mag options...done
Initializing neg options...done
Initializing obs options...done
Initializing opacify options...done
Initializing put options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scaleaddon options...done
Initializing screenshot options...done
Initializing shift options...done
Initializing switcher options...done
Initializing thumbnail options...done
Initializing unitymtgrabhandles options...done
Initializing unityshell options...done
Initializing water options...done
Initializing winrules options...done
Initializing wobbly options...done
Initializing zoom options...done
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
Setting Update "autoraise"
Setting Update "autoraise_delay"
Setting Update "maximize_window_key"
Setting Update "minimize_window_key"
Setting Update "show_desktop_key"
Setting Update "toggle_window_maximized_key"
Setting Update "toggle_window_shaded_key"
Setting Update "fullscreen_visual_bell"
Setting Update "run_command_terminal_key"
** (nautilus:1927): DEBUG: Got notification of SyncDaemon startup in NameOwnerChanged
x-session-manager[1792]: Gdk-WARNING: x-session-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gnome-settings-daemon:1854): Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(compiz:1872): Gdk-WARNING **: compiz: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(bluetooth-applet:1925): Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gnome-fallback-mount-helper:1926): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(nautilus:1927): Gdk-WARNING **: nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(nm-applet:1930): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

(gdu-notification-daemon:2406): Gdk-WARNING **: gdu-notification-daemon: Fatal IO error 104 (Connection reset by peer) on X server :0.

unity-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

(evolution-alarm-notify:2489): Gdk-WARNING **: evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
** (process:2452): DEBUG: zeitgeist-datahub.vala:58: Zeitgeist-daemon disappeared from the bus, exitting...

** (process:2452): WARNING **: zeitgeist-datahub.vala:218: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
```Sorry, upload didn't work ;)

EDIT: Wait, the fail whale? What. The. Heck.

---

