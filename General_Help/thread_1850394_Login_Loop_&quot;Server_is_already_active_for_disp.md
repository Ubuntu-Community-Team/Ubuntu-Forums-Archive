---
title: "Login Loop: &quot;Server is already active for display 0&quot;"
date: 2011-09-26
forum: General Help
---

### Post by hypergeek14 on 2011-09-26
The full error is: 

```
Fatal server error:
Server is already active for display 0
 If this server is no longer running, remove /tmp/.X0-lock
 and start again.
```

I followed the directions from [this ErrorFAQ]("http://wiki.x.org/wiki/FAQErrorMessages#Ikeepgettingthemessage.3A.22Serverisalreadyactivefordisplay0.22"), which told me to delete /tmp/.X0-lock, which didn't help.  I have, however, had success logging in with ```
startx -- :1
```, though I don't want to have to go through the CLI every time I turn my computer on.  Plus I am unable to mount USB hard drives, which another post suggested was because I was using a different display.  

Thanks in advance!
Keith

---

### Post by beardedman on 2011-10-19
Does anyone have a solutions for this? I have the exact same issue. I'm using 64 bit Ubuntu 11.10.

I'm pretty sure my issue started directly after installing tight vnc (same day as distro upgrade), I had to mess with some x configuration files and after rebooting I have OP's issue.

---

### Post by MeduZa on 2011-10-19
control alt F[6-9] and find it!

---

### Post by beardedman on 2011-10-19
Do you have any more in depth suggestions? That's where I've been playing around in and I've already done quite a bit including:

uninstalling and reinstalling xserver-xorg, xserver-xorg-core, ubuntu-desktop, unity

plus about 20 other things from last night that I can't fully remember. I do have a log file...I believe it's the x-service log:

                                                                     
                                                                     
                                                                     
                                             
Running X session wrapper
Loading profile from /etc/profile
Loading profile from /home/mozart/.profile
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
Loading X session script /etc/X11/Xsession.d/80kubuntu-xmodmap
Loading X session script /etc/X11/Xsession.d/80qtgraphicssystem
Loading X session script /etc/X11/Xsession.d/90consolekit
Loading X session script /etc/X11/Xsession.d/90gpg-agent
Loading X session script /etc/X11/Xsession.d/90qt-a11y
Loading X session script /etc/X11/Xsession.d/90x11-common_ssh-agent
Loading X session script /etc/X11/Xsession.d/99x11-common_start
gnome-session[1465]: WARNING: Session 'ubuntu' runnable check failed: Exited with code 1
GNOME_KEYRING_CONTROL=/tmp/keyring-lobqL1
SSH_AUTH_SOCK=/tmp/keyring-lobqL1/ssh
GNOME_KEYRING_PID=1554
GNOME_KEYRING_CONTROL=/tmp/keyring-lobqL1
SSH_AUTH_SOCK=/tmp/keyring-lobqL1/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-lobqL1
SSH_AUTH_SOCK=/tmp/keyring-lobqL1/ssh
GPG_AGENT_INFO=/tmp/keyring-lobqL1/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-lobqL1
SSH_AUTH_SOCK=/tmp/keyring-lobqL1/ssh
GPG_AGENT_INFO=/tmp/keyring-lobqL1/gpg:0:1
=== auto configure Configuration ===
  Clone: false
  Output: Unknown attached to default
     status: on
     width: 1024
     height: 768
     rate: 60
     primary: false
     position: 0 0
=== Applying Configuration Configuration ===
  Clone: false
  Output: Unknown attached to default
     status: on
     width: 1024
     height: 768
     rate: 60
     primary: true
     position: 0 0
common-plugin-Message: checking whether we have a device for 4: yes
common-plugin-Message: checking whether we have a device for 5: yes
common-plugin-Message: checking whether we have a device for 6: yes
common-plugin-Message: checking whether we have a device for 7: yes
common-plugin-Message: checking whether we have a device for 8: yes
common-plugin-Message: checking whether we have a device for 9: yes
unity-2d-panel: [DEBUG] Scanning panel plugin directory "/usr/lib/unity-2d/plugins/panel" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appindicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appname.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-homebutton.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-indicator.so" 
gnome-session[1465]: WARNING: Unable to parse command from  'file:///etc/xdg/autostart/synaptiks_init_config.desktop': Key file contains key 'Terminal' which has value that cannot be interpreted.
gnome-session[1465]: WARNING: Failed to start app: Unable to start application: Key file contains key 'Terminal' which has value that cannot be interpreted.
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-legacytray.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-separator.so" 
unity-2d-panel: [DEBUG] Configured plugins list is: ("appname", "!legacytray", "indicator") 
** (nautilus:1689): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Initializing nautilus-gdu extension
unity-2d-launcher: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core pointer 
unity-2d-launcher: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core keyboard 
** (gnome-fallbac: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F1" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F2" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+0" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+0" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+1" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+1" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+2" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+2" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+3" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+3" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+4" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+4" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+5" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+5" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+6" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+6" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+7" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+7" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+8" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+8" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+9" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+9" 
unity-2d-launcher: [DEBUG] static void WindowImageProvider::activateComposite(): Server supports the Composite extension (ver 0.4)

(gnome-settings-daemon:1553): color-plugin-WARNING **: failed to get edid: unable to get EDID for output
unity-panel-service: no process found
** Message: applet now removed from the notification area
** (nm-applet:1693): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1693): DEBUG: old state indicates that this was not a disconnect 0
** Message: using fallback from indicator to GtkStatusIcon
** (gnome-fallback-mount-helper:1696): DEBUG: Found ConsoleKit session at path /org/freedesktop/ConsoleKit/Session1
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+S" 
** (gnome-fallback-mount-helper:1696): DEBUG: ScreenSaver name appeared
** (gnome-fallback-mount-helper:1696): DEBUG: ScreenSaver proxy ready
** (gnome-fallback-mount-helper:1696): DEBUG: ConsoleKit session is active 1
** (gnome-fallback-mount-helper:1696): DEBUG: Screensaver GetActive() returned 0
unity-2d-panel: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "F10" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+T" 

(nautilus:1689): Gtk-CRITICAL **: gtk_action_set_visible: assertion `GTK_IS_ACTION (action)' failed

(nautilus:1689): Gtk-CRITICAL **: gtk_action_set_visible: assertion `GTK_IS_ACTION (action)' failed
** Message: moving back from GtkStatusIcon to indicator
unity-2d-launcher: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 18 (X_ChangeProperty)
  Resource id:  0x0

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: info_fn: file /var/lib/samba/usershares/torrents.done is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/mediacentral is not a well formed usershare file.
info_fn: Error was Path is not a directory.

** (process:1874): DEBUG: Telepathy Indicator started
unity-2d-launcher: [WARNING] void LauncherApplicationsList::onRemoteEntryUpdated(QString, QMap<QString, QVariant>): Application sent an update but we don't seem to have it in the launcher: "application://empathy.desktop" 
unity-2d-launcher: [WARNING] void LauncherApplicationsList::onRemoteEntryUpdated(QString, QMap<QString, QVariant>): Application sent an update but we don't seem to have it in the launcher: "application://empathy.desktop" 
** (nautilus:1689): DEBUG: Got notification of SyncDaemon startup in NameOwnerChanged
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Xids" with signature "" on interface "org.ayatana.bamf.application" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "IsRunning" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
** (process:2511): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
2011-10-18 14:05:21,135 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2011-10-18 14:05:23,240 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2011-10-18 14:05:23,382 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for ambiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
2011-10-18 14:05:27,290 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Xids" with signature "" on interface "org.ayatana.bamf.application" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "IsRunning" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
gpg: /tmp/tmptoisQM/trustdb.gpg: trustdb created
gpg: /tmp/tmpKEQatt/trustdb.gpg: trustdb created
/usr/lib/python2.7/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:336: Warning: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2335: instance `0x1fc23d0' has no handler with id `682'
  widget.handler_block(handler)
/usr/lib/python2.7/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:336: Warning: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2335: instance `0x2fa03d0' has no handler with id `682'
  widget.handler_block(handler)
/usr/lib/python2.7/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:340: Warning: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2377: instance `0x2fa03d0' has no handler with id `682'
  widget.handler_unblock(handler)
/usr/lib/python2.7/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:340: Warning: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2377: instance `0x1fc23d0' has no handler with id `682'
  widget.handler_unblock(handler)
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [CRITICAL] GLib-GObject: g_object_weak_ref: assertion `G_IS_OBJECT (object)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [CRITICAL] GLib-GObject: g_object_weak_unref: assertion `G_IS_OBJECT (object)' failed
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Xids" with signature "" on interface "org.ayatana.bamf.application" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "IsRunning" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Xids" with signature "" on interface "org.ayatana.bamf.application" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "IsRunning" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
** (deja-dup-monitor:3340): DEBUG: monitor.vala:221: Automatic backups disabled.  Not scheduling a backup.
** (process:2511): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
[3:3:303818444:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
[7:7:333738012:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Xids" with signature "" on interface "org.ayatana.bamf.application" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "IsRunning" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
gpg: /tmp/tmpqCcA_6/trustdb.gpg: trustdb created
/usr/lib/python2.7/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:336: Warning: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2335: instance `0x28a63d0' has no handler with id `682'
  widget.handler_block(handler)
/usr/lib/python2.7/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:340: Warning: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2377: instance `0x28a63d0' has no handler with id `682'
  widget.handler_unblock(handler)
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Xids" with signature "" on interface "org.ayatana.bamf.application" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "IsRunning" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
Window manager warning: Attempt to perform window operation 1 on window 0x3e00003 (System Set) when operation 1 on 0x3e00003 (System Set) already in effect
[12:12:556390926:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
[16:16:564373070:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
gpg: /tmp/tmpqVDbSH/trustdb.gpg: trustdb created
/usr/lib/python2.7/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:336: Warning: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2335: instance `0x1e7d3d0' has no handler with id `682'
  widget.handler_block(handler)
/usr/lib/python2.7/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:340: Warning: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2377: instance `0x1e7d3d0' has no handler with id `682'
  widget.handler_unblock(handler)
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2000003 (Authentica)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2000003 (Authentica)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
unity-2d-launcher: [WARNING] libindicator: Unable to load keyfile from file '': No such file or directory
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "IsRunning" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Xids" with signature "" on interface "org.ayatana.bamf.application" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "IsRunning" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
gpg: /tmp/tmpPq6W_m/trustdb.gpg: trustdb created
/usr/lib/python2.7/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:336: Warning: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2335: instance `0x34923d0' has no handler with id `682'
  widget.handler_block(handler)
/usr/lib/python2.7/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:340: Warning: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2377: instance `0x34923d0' has no handler with id `682'
  widget.handler_unblock(handler)
gpg: /tmp/tmp9YeqAW/trustdb.gpg: trustdb created
/usr/lib/python2.7/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:336: Warning: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2335: instance `0x1ab93d0' has no handler with id `682'
  widget.handler_block(handler)
/usr/lib/python2.7/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:340: Warning: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2377: instance `0x1ab93d0' has no handler with id `682'
  widget.handler_unblock(handler)
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [CRITICAL] GLib-GObject: g_object_weak_ref: assertion `G_IS_OBJECT (object)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [WARNING] GLib-GObject: invalid (NULL) pointer instance
unity-2d-panel: [CRITICAL] GLib-GObject: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
unity-2d-panel: [CRITICAL] GLib-GObject: g_object_weak_unref: assertion `G_IS_OBJECT (object)' failed
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Xids" with signature "" on interface "org.ayatana.bamf.application" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "IsRunning" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 

(gnome-control-center:3955): GLib-CRITICAL **: g_sequence_remove: assertion `iter != NULL' failed

(gnome-control-center:3955): GLib-CRITICAL **: g_sequence_remove: assertion `iter != NULL' failed

(gnome-control-center:3955): GLib-CRITICAL **: g_sequence_remove: assertion `iter != NULL' failed

(gnome-control-center:3955): GLib-CRITICAL **: g_sequence_remove: assertion `iter != NULL' failed
[21:21:777024921:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
[25:25:787793121:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied

(gnome-control-center:3955): GLib-CRITICAL **: g_sequence_remove: assertion `iter != NULL' failed

(gnome-control-center:3955): GLib-CRITICAL **: g_sequence_remove: assertion `iter != NULL' failed

(gnome-control-center:3955): GLib-CRITICAL **: g_sequence_remove: assertion `iter != NULL' failed

(gnome-control-center:3955): GLib-CRITICAL **: g_sequence_remove: assertion `iter != NULL' failed
unity-panel-service: no process found
** Message: using fallback from indicator to GtkStatusIcon
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x2200007
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x3c00005
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x3c00008
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x3c0000b
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x3c0000e
** Message: moving back from GtkStatusIcon to indicator
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Xids" with signature "" on interface "org.ayatana.bamf.application" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "Method "IsRunning" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
") 
unity-2d-launcher: [DEBUG] void GnomeSessionClient::queryEndSession(): 
unity-2d-launcher: [DEBUG] bool GnomeSessionClientPrivate::sendEndSessionResponse(): 
unity-2d-panel: [DEBUG] void GnomeSessionClient::waitForEndSession(): Application is about to quit, waiting for gnome-session to call us back 
unity-2d-panel: [DEBUG] void GnomeSessionClient::queryEndSession(): 
unity-2d-panel: [DEBUG] bool GnomeSessionClientPrivate::sendEndSessionResponse(): 
unity-2d-launcher: [DEBUG] void GnomeSessionClient::waitForEndSession(): Application is about to quit, waiting for gnome-session to call us back 
unity-2d-launcher: [DEBUG] void GnomeSessionClient::endSession(): 
unity-2d-launcher: [DEBUG] bool GnomeSessionClientPrivate::sendEndSessionResponse(): 
unity-2d-panel: [DEBUG] void GnomeSessionClient::endSession(): 
unity-2d-panel: [DEBUG] bool GnomeSessionClientPrivate::sendEndSessionResponse(): 
process 1687: arguments to dbus_message_unref() were incorrect, assertion "message != NULL" failed in file ../../dbus/dbus-message.c line 1554.
This is normally a bug in some application using the D-Bus library.
process 2692: arguments to dbus_message_unref() were incorrect, assertion "message != NULL" failed in file ../../dbus/dbus-message.c line 1554.
This is normally a bug in some application using the D-Bus library.
process 2692: arguments to dbus_message_unref() were incorrect, assertion "message != NULL" failed in file ../../dbus/dbus-message.c line 1554.
This is normally a bug in some application using the D-Bus library.
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!
process 1553: arguments to dbus_message_unref() were incorrect, assertion "message != NULL" failed in file ../../dbus/dbus-message.c line 1554.
This is normally a bug in some application using the D-Bus library.

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(gnome-settings-daemon:1553): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
[1318961071,000,xklavier.c:xkl_engine_start_listen/] 	The backend does not require manual layout management - but it is provided by the application

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

** (gnome-control-center:3955): WARNING **: Could not find icon

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

** (gnome-control-center:3955): WARNING **: Could not find icon

** (gnome-control-center:3955): WARNING **: Could not find icon

** (gnome-control-center:3955): WARNING **: Could not find icon

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

** (gnome-control-center:3955): WARNING **: Could not find icon

** (gnome-control-center:3955): WARNING **: Could not find icon

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

** (gnome-control-center:3955): WARNING **: Could not find icon

(nautilus:1689): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

** (gnome-control-center:3955): WARNING **: Could not find icon

** (gnome-control-center:3955): WARNING **: Could not find icon

** (gnome-control-center:3955): WARNING **: Could not find icon

** (gnome-control-center:3955): WARNING **: Could not find icon
gnome-session[1465]: WARNING: Unable to restart system: Authorization is required
** (gnome-fallback-mount-helper:1696): DEBUG: ConsoleKit session is active 0

(nautilus:1689): Gdk-WARNING **: nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(bluetooth-applet:1690): Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(nm-applet:1693): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gnome-fallback-mount-helper:1696): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gdu-notification-daemon:2008): Gdk-WARNING **: gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(evolution-alarm-notify:2623): Gdk-WARNING **: evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

unity-2d-launcher: [WARNING] Gdk: unity-2d-launcher: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

(gnome-control-center:3955): Gdk-WARNING **: gnome-control-center: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(update-notifier:3283): Gdk-WARNING **: update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

[3743:3743:1094837257:ERROR:browser_main_gtk.cc(75)] X IO Error detected
[4693:4693:1094847323:ERROR:x11_util.cc(67)] X IO Error detected
npviewer.bin: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
** (process:2511): DEBUG: zeitgeist-datahub.vala:58: Zeitgeist-daemon disappeared from the bus, exitting...

** (process:2511): WARNING **: zeitgeist-datahub.vala:218: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.


Any further suggestions are appreciated :)

---

