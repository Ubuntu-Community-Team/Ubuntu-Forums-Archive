---
title: "Window frames gone Xubuntu 11.04"
date: 2011-07-06
forum: General Help
---

### Post by Mzwo on 2011-07-06
hi,

window frames went awol one boot to the next.

tried apt-get install -f and dpkg --configure -a as suggested elsewhere, but no joy.

help is very much appreciated.

Cheers,
Matt

---

### Post by Toz on 2011-07-06
Usually a symptom of when the window manager (xfwm4) crashes.

Either Alt-F2 (if it works) or open a terminal window (Accessories->Terminal Emulator) and type in:```
xfwm4 --replace
```

You may need to add it to your autostart (Settings->Settings Manager->Session and Startup->Application Autostart tab) to get it to run on every subsequent login.

---

### Post by Mzwo on 2011-07-07
thanks, will try this as soon as i'm back home.

quick question, though: reboots have no effect, neither do the above commands. doesn't this mean xfwm4 is broken and should be reinstalled or any such thing?

cheers,

matt

---

### Post by Toz on 2011-07-07
It could simply mean that at some point in time, xfwm4 crashed and is now not starting automatically. Try the command and see if it works. 

The commands from your original post are to fix apt - and may not be applicable here.

---

### Post by Mzwo on 2011-07-07
Thanks a bunch, that worked. 

I get a number of error messages, though:

```
mzwo@mzwo-laptop:~$ sudo xfwm4 --replace
[sudo] password for mzwo: 

(xfwm4:1876): GLib-CRITICAL **: g_str_has_prefix: assertion `prefix != NULL' failed

(xfwm4:1876): xfwm4-WARNING **: The property '/general/double_click_distance' of type int is not supported

(xfwm4:1876): xfwm4-WARNING **: Failed to connect to session manager: Failed to connect to the session manager: SESSION_MANAGER environment variable not defined


```

something I should look into?

oh, and how do I do the autostart thing?

Thanks,
Matt

---

### Post by Toz on 2011-07-07
First of all, try logging off and back in again. If the window borders are gone again, then you will have to create an autostart entry.

This time, to see about the error messages, try running the command as:
```
xfwm4 --display=:0.0 --replace
```

To create an autostart entry, From the Main Menu choose Settings, then Settings Manager, then Session and Startup, then click on the Application Autostart tab. Once there, click the "Add" button, then set the following:
- Name = xfwm4
- Description = xfwm4
- Command = xfwm4 --replace (or xfwm4 --display=:0.0 --replace)

---

### Post by Mzwo on 2011-07-08
thanks!

Logging on and off makes the borders go away, I'll add it to the autostart list.

Where do I find the log file for xfwm4?

Ta,

Matt

---

### Post by Toz on 2011-07-08
Should be posted to ~/.xsession-errors (hidden file in your home directory)

---

### Post by Mzwo on 2011-07-08
There seems to be quite a bot wrong.
What can I do?

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 13 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 14 overrides entry on line 7
ssh-agent is already running
xfdesktop[1431]: starting up
(xfce4-indicator-plugin:1438): xfce4-indicator-plugin-DEBUG: Looking at Module: libapplication.so
(xfce4-indicator-plugin:1438): xfce4-indicator-plugin-DEBUG: Loading Module: libapplication.so
(xfce4-indicator-plugin:1438): xfce4-indicator-plugin-DEBUG: Looking at Module: libsoundmenu.so
(xfce4-indicator-plugin:1438): xfce4-indicator-plugin-DEBUG: Loading Module: libsoundmenu.so
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.

(xfce4-indicator-plugin:1438): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
(xfce4-indicator-plugin:1438): xfce4-indicator-plugin-DEBUG: Looking at Module: libmessaging.so
(xfce4-indicator-plugin:1438): xfce4-indicator-plugin-DEBUG: Loading Module: libmessaging.so

(xfce4-indicator-plugin:1438): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:1438): libxfce4panel-CRITICAL **: IA__xfce_panel_plugin_add_action_widget: assertion `GTK_IS_WIDGET (widget)' failed
(xfce4-indicator-plugin:1438): Indicator-Application-DEBUG: Connected to Application Indicator Service.
(xfce4-indicator-plugin:1438): Indicator-Messages-DEBUG: new_application_item ("Pidgin Internet Messenger")
(xfce4-indicator-plugin:1438): Indicator-Application-DEBUG: Request current apps
(xfce4-indicator-plugin:1438): Indicator-Sound-DEBUG: indicator-sound: new_volume_slider_widget
(xfce4-indicator-plugin:1438): Indicator-Sound-DEBUG: indicator-sound: new_voip_slider_widget
(xfce4-indicator-plugin:1438): Indicator-Sound-DEBUG: new_title_widget ("gmusicbrowser")
(xfce4-indicator-plugin:1438): Indicator-Sound-DEBUG: indicator-sound: new_metadata_widget
(xfce4-indicator-plugin:1438): Indicator-Sound-DEBUG: indicator-sound: new_transport_bar() called 

(xfce4-indicator-plugin:1438): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed
Peer ID: -qB2690-
HTTP user agent is qBittorrent v2.6.9
GNOME_KEYRING_CONTROL=/tmp/keyring-Yb1YW9
SSH_AUTH_SOCK=/tmp/keyring-Yb1YW9/ssh
GPG_AGENT_INFO=/tmp/keyring-Yb1YW9/gpg:0:1
xfce4-settings-helper: Another instance is already running. Leaving...
GNOME_KEYRING_CONTROL=/tmp/keyring-Yb1YW9
SSH_AUTH_SOCK=/tmp/keyring-Yb1YW9/ssh
GPG_AGENT_INFO=/tmp/keyring-Yb1YW9/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-Yb1YW9
SSH_AUTH_SOCK=/tmp/keyring-Yb1YW9/ssh
GPG_AGENT_INFO=/tmp/keyring-Yb1YW9/gpg:0:1

(<unknown>:1432): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:1432): Gtk-WARNING **: Loading IM context type 'ibus' failed
env: firefox-bin: No such file or directory

(<unknown>:1432): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:1432): Gtk-WARNING **: Loading IM context type 'ibus' failed

(polkit-gnome-authentication-agent-1:1515): polkit-gnome-1-WARNING **: Failed to register client: The name org.gnome.SessionManager was not provided by any .service files

(<unknown>:1432): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:1432): Gtk-WARNING **: Loading IM context type 'ibus' failed

(xfwm4:1505): xfwm4-WARNING **: Unmanaged net_wm_state (window 0x2a00018, atom "_NET_WM_STATE_STAYS_ON_TOP")
** (nm-applet:1538): DEBUG: old state indicates that this was not a disconnect 0
(xfce4-indicator-plugin:1438): Indicator-Application-DEBUG: Building new application entry: :1.71  with icon: nm-no-connection at position 0

** (gnome-settings-daemon:1531): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:1531): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.

** (gnome-settings-daemon:1531): WARNING **: Grab failed for some keys, another application may already have access the them.

** (gnome-settings-daemon:1531): WARNING **: Clipboard manager is already running.

(gnome-settings-daemon:1531): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed
xfdesktop: Fatal IO error 0 (Success) on X server :0.0.
** (nm-applet:1538): DEBUG: foo_client_state_changed_cb
xfdesktop[1590]: starting up
xfce4-taskmanager-Message: Running as mzwo on mzwo-laptop
/usr/lib/python2.7/dist-packages/UpdateManager/SimpleGtkbuilderApp.py:35: GtkWarning: Ignoring the separator setting
  self.builder.add_from_file(path)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 18 (X_ChangeProperty)
  Resource id:  0x2a00290
** (nm-applet:1538): DEBUG: foo_client_state_changed_cb

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 49

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 50

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 51

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 52

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 53

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 54

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 55

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 56

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 57

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 58

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 59

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 60

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 61

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 74

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 75

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 76

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 77

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 78

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 81

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 82

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 83

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 84

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 85

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 86

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 87

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 62

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 63

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 64

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 65

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 66

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 67

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 68

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 69

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 70

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 71

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 72

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 73

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 79

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 80

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(<unknown>:1509): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:1509): Gtk-WARNING **: Loading IM context type 'ibus' failed

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 89

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 90

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 91

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 92

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 93

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 94

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 95

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 96

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 97

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 98

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 99

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 100

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 101

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 114

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 115

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 116

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 117

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 118

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 121

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 122

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 123

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 124

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 125

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 126

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 127

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(<unknown>:1509): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 102

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 103

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 104

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 105

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 106

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 107

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 108

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 109

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(<unknown>:1509): Gtk-WARNING **: Loading IM context type 'ibus' failed

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 110

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 111

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 112

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 113

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 119

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Generating properties error for: 120

(xfce4-indicator-plugin:1438): LIBDBUSMENU-GLIB-WARNING **: Error getting properties on a new menuitem: Error getting properties for ID

(<unknown>:1509): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:1509): Gtk-WARNING **: Loading IM context type 'ibus' failed
WARNING:root:timeout reached, exiting
Error: No running window found

```


Thanks,
matt

---

### Post by Mzwo on 2011-07-08
ok, this is after i changed the autostart entry from xfwm4 --replace to xfwm4 --display=:0.0 --replace.

seems better to the layman, but there still seem to be certain warnings ...

Cheers,
Matt

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 13 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 14 overrides entry on line 7
ssh-agent is already running
xfdesktop[1533]: starting up
(xfce4-indicator-plugin:1545): xfce4-indicator-plugin-DEBUG: Looking at Module: libapplication.so
(xfce4-indicator-plugin:1545): xfce4-indicator-plugin-DEBUG: Loading Module: libapplication.so
(xfce4-indicator-plugin:1545): xfce4-indicator-plugin-DEBUG: Looking at Module: libsoundmenu.so
(xfce4-indicator-plugin:1545): xfce4-indicator-plugin-DEBUG: Loading Module: libsoundmenu.so
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.

(xfce4-indicator-plugin:1545): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
(xfce4-indicator-plugin:1545): xfce4-indicator-plugin-DEBUG: Looking at Module: libmessaging.so
(xfce4-indicator-plugin:1545): xfce4-indicator-plugin-DEBUG: Loading Module: libmessaging.so

(xfce4-indicator-plugin:1545): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:1545): libxfce4panel-CRITICAL **: IA__xfce_panel_plugin_add_action_widget: assertion `GTK_IS_WIDGET (widget)' failed
(xfce4-indicator-plugin:1545): Indicator-Application-DEBUG: Connected to Application Indicator Service.
(xfce4-indicator-plugin:1545): Indicator-Application-DEBUG: Request current apps
(xfce4-indicator-plugin:1545): Indicator-Messages-DEBUG: new_application_item ("Pidgin Internet Messenger")
(xfce4-indicator-plugin:1545): Indicator-Sound-DEBUG: indicator-sound: new_volume_slider_widget
(xfce4-indicator-plugin:1545): Indicator-Sound-DEBUG: indicator-sound: new_voip_slider_widget
(xfce4-indicator-plugin:1545): Indicator-Sound-DEBUG: new_title_widget ("gmusicbrowser")
(xfce4-indicator-plugin:1545): Indicator-Sound-DEBUG: indicator-sound: new_metadata_widget
(xfce4-indicator-plugin:1545): Indicator-Sound-DEBUG: indicator-sound: new_transport_bar() called 

(xfce4-indicator-plugin:1545): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(xfwm4:1512): xfwm4-WARNING **: Unmanaged net_wm_state (window 0x2800018, atom "_NET_WM_STATE_STAYS_ON_TOP")
Peer ID: -qB2690-
HTTP user agent is qBittorrent v2.6.9
GNOME_KEYRING_CONTROL=/tmp/keyring-hI3fUP
SSH_AUTH_SOCK=/tmp/keyring-hI3fUP/ssh
GPG_AGENT_INFO=/tmp/keyring-hI3fUP/gpg:0:1
xfce4-settings-helper: Another instance is already running. Leaving...
GNOME_KEYRING_CONTROL=/tmp/keyring-hI3fUP
SSH_AUTH_SOCK=/tmp/keyring-hI3fUP/ssh
GPG_AGENT_INFO=/tmp/keyring-hI3fUP/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-hI3fUP
SSH_AUTH_SOCK=/tmp/keyring-hI3fUP/ssh
GPG_AGENT_INFO=/tmp/keyring-hI3fUP/gpg:0:1
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode: 2 (X_ChangeWindowAttributes)
  Resource id:  0x2800221
env: firefox-bin: No such file or directory

(polkit-gnome-authentication-agent-1:1613): polkit-gnome-1-WARNING **: Failed to register client: The name org.gnome.SessionManager was not provided by any .service files

(<unknown>:1539): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:1539): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:1539): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:1539): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:1539): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:1539): Gtk-WARNING **: Loading IM context type 'ibus' failed
** (nm-applet:1637): DEBUG: old state indicates that this was not a disconnect 0
(xfce4-indicator-plugin:1545): Indicator-Application-DEBUG: Building new application entry: :1.71  with icon: nm-no-connection at position 0

** (gnome-settings-daemon:1640): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:1640): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.
** (nm-applet:1637): DEBUG: foo_client_state_changed_cb

** (gnome-settings-daemon:1640): WARNING **: Grab failed for some keys, another application may already have access the them.

** (gnome-settings-daemon:1640): WARNING **: Clipboard manager is already running.

(gnome-settings-daemon:1640): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed
The application 'xfdesktop' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
xfce4-taskmanager-Message: Running as mzwo on mzwo-laptop
xfdesktop[1678]: starting up
** (nm-applet:1637): DEBUG: foo_client_state_changed_cb

```

---

### Post by Toz on 2011-07-08
The majority of them are warning or debug messages - nothing to worry about. I think the xfdesktop message is related to you restarting xfwm4. If everything is fine now, I wouldn't worry about it.

---

### Post by Mzwo on 2011-07-11
Thanks, everything appears to be in order.

Cheers,
Matt

---

