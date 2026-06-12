---
title: "Xserver crashes suddenly"
date: 2010-04-10
forum: General Help
---

### Post by emanuel.b on 2010-04-10
Hi everyone,

Just wondering if you could help me out. Every once and a while (maybe once or twice a day) my Xserver crashes (usually when I'm connecting to a wireless network or when I'm on the internet) and all i see is a brown screen, with black lines running down, and distortion where the mouse pointer was. Does anyone know why this is happening?

---

### Post by ubunterooster on 2010-04-10
No, but look for an error log in your home folder

---

### Post by emanuel.b on 2010-04-10
> **ubunterooster said:**
> No, but look for an error log in your home folder

Ok, I found a file called xsession-errors hidden in my home folder. It's kinda big, so here it is:

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_SOCKET=/tmp/keyring-UA4sLI/socket
SSH_AUTH_SOCK=/tmp/keyring-UA4sLI/socket.ssh

(gnome-settings-daemon:1608): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:1608): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Window manager warning: Failed to read saved session file /home/emanuel/.config/metacity/sessions/107c0bfa9233ba39dd12709251133148600000015420023.ms: Failed to open file '/home/emanuel/.config/metacity/sessions/107c0bfa9233ba39dd12709251133148600000015420023.ms': No such file or directory
** (gnome-panel:1639): DEBUG: Adding applet 0.
** (gnome-panel:1639): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:1639): DEBUG: Adding applet 1.
** (gnome-panel:1639): DEBUG: Adding applet 2.
** (gnome-panel:1639): DEBUG: Adding applet 3.

(polkit-gnome-authentication-agent-1:1663): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1663): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** Message: killswitches state 3

(nautilus:1640): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
** (gnome-panel:1639): DEBUG: Adding applet 4.
** (gnome-panel:1639): DEBUG: Adding applet 5.
** (gnome-panel:1639): DEBUG: Adding applet 6.

(gnome-panel:1639): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24
** (gnome-panel:1639): DEBUG: Adding applet 7.
** (gnome-panel:1639): DEBUG: Adding applet 8.
** (gnome-panel:1639): DEBUG: Adding applet 9.
Initializing nautilus-gdu extension

** (nautilus:1640): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1640): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1640): WARNING **: No marshaller for signature of signal 'ShareCreateError'
** (gnome-panel:1639): DEBUG: Adding applet 10.
** (gnome-panel:1639): DEBUG: Adding applet 11.
** (gnome-panel:1639): DEBUG: Adding applet 12.
** (gnome-panel:1639): DEBUG: Adding applet 13.

(gnome-panel:1639): Gdk-WARNING **: /build/buildd/gtk+2.0-2.18.3/gdk/x11/gdkdrawable-x11.c:952 drawable is not a pixmap or window
** (gnome-panel:1639): DEBUG: Adding applet 14.
Apache CouchDB has started, time to relax.
** Message: RFKILL event: idx 0 type 1 op 0 soft 0 hard 0

** Message: RFKILL event: idx 0 type 1 op 2 soft 0 hard 0

** (nm-applet:1650): DEBUG: foo_client_state_changed_cb
** (nm-applet:1650): DEBUG: foo_client_state_changed_cb
evolution-alarm-notify-Message: Setting timeout for 44054 1270969200 1270925146
evolution-alarm-notify-Message:  Sun Apr 11 00:00:00 2010

evolution-alarm-notify-Message:  Sat Apr 10 11:45:46 2010


(firefox-bin:1983): GLib-WARNING **: g_set_prgname() called multiple times

** (nm-connection-editor:2007): WARNING **: nm_connection_list_new: failed to load VPN plugins: Couldn't read VPN .name files directory /etc/NetworkManager/VPN.

(nm-connection-editor:2007): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(nm-connection-editor:2007): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(nm-connection-editor:2007): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(nm-connection-editor:2007): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2a00003 (Authentica)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2a00003 (Authentica)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
** (evolution:2070): DEBUG: mailto URL command: evolution --component=mail %s
** (evolution:2070): DEBUG: mailto URL program: evolution

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: New Indicator: emanuel.b@nwtechforums.com imap://emanuel.b+nwtechforums.com@mail.nwtechforums.com/
** (evolution:2070): DEBUG: New account: emanuel.b@nwtechforums.com (imap://emanuel.b+nwtechforums.com@mail.nwtechforums.com/)
** (evolution:2070): DEBUG: Number of email accounts: 1
** (evolution:2070): DEBUG: EI: SHELL STARTUP

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: EI: mail_read_notify
** (evolution:2070): DEBUG: Setting emanuel.b@nwtechforums.com to 0 unread messages

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: Evolution is focused

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(evolution:2070): camel-WARNING **: camel_exception_get_id called with NULL parameter.

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: EI: mail_read_notify
** (evolution:2070): DEBUG: Setting emanuel.b@nwtechforums.com to 0 unread messages

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(evolution:2070): GLib-WARNING **: g_set_prgname() called multiple times

** (gnome-help:2172): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (gnome-help:2172): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
OMF category 'Applications|Other' not recognised, ignoring.
OMF category 'Applications|Other' not recognised, ignoring.
OMF category 'Applications|Other' not recognised, ignoring.

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
EI: MAIL PREFS
** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: New Indicator: emanuel.b@nwtechforums.com imap://emanuel.b+nwtechforums.com@mail.nwtechforums.com/
** (evolution:2070): DEBUG: New account: emanuel.b@nwtechforums.com (imap://emanuel.b+nwtechforums.com@mail.nwtechforums.com/)
** (evolution:2070): DEBUG: Number of email accounts: 1

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: EI: mail_read_notify
** (evolution:2070): DEBUG: Setting emanuel.b@nwtechforums.com to 0 unread messages

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: EI: mail_read_notify
** (evolution:2070): DEBUG: Setting emanuel.b@nwtechforums.com to 0 unread messages

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: EI: mail_read_notify
** (evolution:2070): DEBUG: Setting emanuel.b@nwtechforums.com to 0 unread messages

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: Evolution is focused

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (gnome-help:2236): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (gnome-help:2236): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
OMF category 'Applications|Other' not recognised, ignoring.
OMF category 'Applications|Other' not recognised, ignoring.
OMF category 'Applications|Other' not recognised, ignoring.

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: EI: mail_read_notify
** (evolution:2070): DEBUG: Setting emanuel.b@nwtechforums.com to 0 unread messages

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(evolution:2070): evolution-mail-WARNING **: em_utils_in_addressbook: Can't get contacts: EBookStatus returned 20

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (gnome-help:2236): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (gnome-help:2236): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (gnome-help:2236): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (gnome-help:2236): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: EI:mail_new_notify: imap://emanuel.b+nwtechforums.com@mail.nwtechforums.com/INBOX

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: EI: mail_read_notify
** (evolution:2070): DEBUG: Setting emanuel.b@nwtechforums.com to 0 unread messages

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(evolution:2070): evolution-mail-WARNING **: em_utils_in_addressbook: Can't get contacts: EBookStatus returned 20
EI: MAIL PREFSWindow manager warning: Invalid WM_TRANSIENT_FOR window 0x420dd47 specified for 0x420e1c2 (Delete acc).

** (evolution:2070): WARNING **: Unable to determine number of accounts, defaulting to '1' (unknown)
** (evolution:2070): DEBUG: Number of email accounts: 1

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: New Indicator: Inbox pop:
** (evolution:2070): DEBUG: New Inbox inidicator
** (evolution:2070): DEBUG: Number of email accounts: 1
** Message: Unable to load host id information, assuming unset
** Message: No pilot userid/username information located
** Message: Unable to load pilot id/username, assuming unset
** Message: No pilot cradle information located
** Message: Unable to load pilot cradle info, assuming unset
gpilotd-Message: Activating object OAFIID:GNOME_Pilot_Daemon
** Message: Unable to load host id information, assuming unset
** Message: No pilot userid/username information located
** Message: Unable to load pilot id/username, assuming unset
** Message: No pilot cradle information located
** Message: Unable to load pilot cradle info, assuming unset

(gpilotd-control-applet:2311): libglade-WARNING **: could not find glade file 'gpilotd-capplet.glade'
** Message: Unable to load host id information, assuming unset
** Message: No pilot userid/username information located
** Message: Unable to load pilot id/username, assuming unset
** Message: No pilot cradle information located
** Message: Unable to load pilot cradle info, assuming unset

(gpilotd-control-applet:2311): libglade-WARNING **: could not find glade file 'gpilotd-capplet.glade'

(gpilotd-control-applet:2311): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gpilotd-control-applet:2311): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
** Message: No pilot userid/username information located
** Message: Unable to load pilot id/username, assuming unset
** Message: No pilot cradle information located
** Message: Unable to load pilot cradle info, assuming unset
EI: MAIL PREFS
** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
EI: MAIL PREFS** (evolution:2070): DEBUG: Number of email accounts: 1

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: EI: mail_read_notify
** (evolution:2070): DEBUG: Setting Inbox to 0 unread messages

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: EI: mail_read_notify
** (evolution:2070): DEBUG: Setting Inbox to 0 unread messages

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: EI: mail_read_notify
** (evolution:2070): DEBUG: Setting Inbox to 0 unread messages

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: EI: mail_read_notify
** (evolution:2070): DEBUG: Setting Inbox to 0 unread messages

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: EI: mail_read_notify
** (evolution:2070): DEBUG: Setting Inbox to 0 unread messages

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: EI: mail_read_notify
** (evolution:2070): DEBUG: Setting Inbox to 0 unread messages

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x40064a7 (OpenDNS > ); these messages lack timestamps and therefore suck.

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x40064a7 (OpenDNS > ); these messages lack timestamps and therefore suck.
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x40064a7 (OpenDNS > ); these messages lack timestamps and therefore suck.

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x400002c (Ubuntu For); these messages lack timestamps and therefore suck.

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(nautilus:2604): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
** (evolution:2070): DEBUG: Number of email accounts: 1

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: Number of email accounts: 1
** (evolution:2070): DEBUG: Number of email accounts: 1
** (evolution:2070): DEBUG: Number of email accounts: 1

** (evolution:2070): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2070): DEBUG: Number of email accounts: 1
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x400002c (Thank you ); these messages lack timestamps and therefore suck.
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x400002c (Thank you ); these messages lack timestamps and therefore suck.
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
** (gnome-panel:1639): DEBUG: Removing applet 14.
** (gnome-panel:1639): DEBUG: Removing applet 13.
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x67 specified for 0x3e0661f (Wrong cert).
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 9D2C2E0A3C88DD807EC787D74874D3686E80C6B7
gpg: requesting key 6E80C6B7 from hkp server keyserver.ubuntu.com
gpg: key 6E80C6B7: public key "Launchpad PPA for Banshee Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

(nautilus:2849): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 9D2C2E0A3C88DD807EC787D74874D3686E80C6B7
gpg: requesting key 6E80C6B7 from hkp server keyserver.ubuntu.com
gpg: key 6E80C6B7: "Launchpad PPA for Banshee Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package openoffice.org-java-common
is installed.
If it is already installed then try removing ~/.openoffice.org/3/user/config/javasettings_Linux_*.xml
javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package openoffice.org-java-common
is installed.
If it is already installed then try removing ~/.openoffice.org/3/user/config/javasettings_Linux_*.xml
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x67 specified for 0x3e83cac (Authentica).
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x67 specified for 0x3e90ed5 (Authentica).

(firefox-bin:3489): GLib-WARNING **: g_set_prgname() called multiple times

(nautilus:3540): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:3591): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(nautilus:1640): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed

** (nautilus:1640): CRITICAL **: dbus_g_proxy_begin_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

```

---

