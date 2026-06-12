---
title: "No WM or Nautilus at startup"
date: 2009-12-06
forum: General Help
---

### Post by wolterh on 2009-12-06
Hi, I've been having this problem since a couple of days. I don't think I have changed any mattering configurations. Here is my .xsession-errors anyway:

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_SOCKET=/tmp/keyring-6BhzoF/socket
SSH_AUTH_SOCK=/tmp/keyring-6BhzoF/socket.ssh

(gnome-settings-daemon:2054): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(polkit-gnome-authentication-agent-1:2088): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2088): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** Message: killswitches state 3
06/12/2009 07:04:53 PM Listening for VNC connections on TCP port 7060 in (all) network interface
06/12/2009 07:04:53 PM Listening IPv{4,6}://*:7060
06/12/2009 07:04:53 PM Listening IPv4://0.0.0.0:7060
06/12/2009 07:04:53 PM Problems in NewSocketListenTCP(), sock=-1
06/12/2009 07:04:53 PM ListenOnTCPPort: Address already in use
06/12/2009 07:04:53 PM Advertising security type: 'TLS' (18)
06/12/2009 07:04:53 PM Advertising authentication type: 'No Authentication' (1)
06/12/2009 07:04:53 PM Advertising security type: 'No Authentication' (1)
** (gnome-panel:2082): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:2082): DEBUG: Adding applet 0.
** (gnome-panel:2082): DEBUG: Adding applet 1.
** (gnome-panel:2082): DEBUG: Adding applet 2.
** (gnome-panel:2082): DEBUG: Adding applet 3.

** (nm-applet:2103): WARNING **: Invalid connection /system/networking/connections/25: 'NMSettingWirelessSecurity' / 'pairwise' invalid: 1
** (nm-applet:2103): DEBUG: foo_client_state_changed_cb
** (gnome-panel:2082): DEBUG: Adding applet 4.
** (gnome-panel:2082): DEBUG: Adding applet 5.
** (gnome-panel:2082): DEBUG: Adding applet 6.
** (gnome-panel:2082): DEBUG: Adding applet 7.
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
** (gnome-panel:2082): DEBUG: Adding applet 8.
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

(gnome-panel:2082): Gdk-WARNING **: /build/buildd/gtk+2.0-2.18.3/gdk/x11/gdkdrawable-x11.c:952 drawable is not a pixmap or window
** (gnome-panel:2082): DEBUG: Adding applet 9.
** (nm-applet:2103): DEBUG: foo_client_state_changed_cb

(Do:2307): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

Apache CouchDB has started, time to relax.
Could not locate Tomboy on D-Bus. Perhaps it's not running?
Conky: forked to background, pid is 2431

Conky: desktop window (13c) is root window
Conky: window type - override
Conky: drawing to created window (0x400001)
Conky: drawing to double buffer
evolution-alarm-notify-Message: Setting timeout for 17681 1260165600 1260147919
evolution-alarm-notify-Message:  Mon Dec  7 00:00:00 2009

evolution-alarm-notify-Message:  Sun Dec  6 19:05:19 2009

e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-PAS - Undécimo B'
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
[Error 19:05:22.528] [ItemsService] Could not add custom item with id: Type to begin searching: Type to start searching. (Do.Interface.Widgets.DefaultLabelBoxItem)
Starting gtk-window-decorator
/usr/bin/compiz.real (animation) - Error: Option value missing in "magic_lamp_max_waves"
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

(nautilus:2538): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-open-terminal extension

** (nautilus:2538): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2538): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2538): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Conky: received SIGINT or SIGTERM to terminate. bye!
Conky: forked to background, pid is 2585

Conky: desktop window (44000b0) is subwindow of root window (13c)
Conky: window type - override
Conky: drawing to created window (0x400001)
Conky: drawing to double buffer
** (evolution:2596): DEBUG: mailto URL command: evolution %s
** (evolution:2596): DEBUG: mailto URL program: evolution

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2596): DEBUG: New account: Google Mail (pop://wolterh6@pop.gmail.com/)
** (evolution:2596): DEBUG: New account: Live Mail (pop://wolterh%40live.com@pop3.live.com/)
** (evolution:2596): DEBUG: Number of email accounts: 2
** (evolution:2596): DEBUG: EI: SHELL STARTUP

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2596): DEBUG: EI: mail_read_notify
** (evolution:2596): DEBUG: Setting Google Mail to 0 unread messages
** (evolution:2596): DEBUG: Setting Live Mail to 0 unread messages

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
LoadPlugin: failed to initialize shared library /home/wolter/.mozilla/firefox/362rssgq.default/extensions/quakeliveplugin@idsoftware.com/plugins/npquakelive.i386.so [/home/wolter/.mozilla/firefox/362rssgq.default/extensions/quakeliveplugin@idsoftware.com/plugins/npquakelive.i386.so: wrong ELF class: ELFCLASS32]
Could not locate Tomboy on D-Bus. Perhaps it's not running?

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Could not locate Tomboy on D-Bus. Perhaps it's not running?
Could not locate Tomboy on D-Bus. Perhaps it's not running?

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Could not locate Tomboy on D-Bus. Perhaps it's not running?

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Could not locate Tomboy on D-Bus. Perhaps it's not running?

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Could not locate Tomboy on D-Bus. Perhaps it's not running?

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Could not locate Tomboy on D-Bus. Perhaps it's not running?

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Could not locate Tomboy on D-Bus. Perhaps it's not running?

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Could not locate Tomboy on D-Bus. Perhaps it's not running?

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Could not locate Tomboy on D-Bus. Perhaps it's not running?

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2596): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Could not locate Tomboy on D-Bus. Perhaps it's not running?

(nautilus:3822): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

```

---

### Post by wolterh on 2009-12-18
Ok, I discovered this is due to gnome using [gnome-wm] as a tool to start the window manager, whichever the user uses. Now, in the case of we the people who use [compiz], [gnome-wm] attempts to run [compiz.real]--which seems to be a abort-if-fail kind of compiz-starter.

So, temporary solution:
Trick [gnome-wm] into calling [compiz] and not [compiz.real] with the following steps
```

# mv /usr/bin/compiz.real /usr/bin/compiz.real_original
# ln -s /usr/bin/compiz /usr/bin/compiz.real

```

My guess is that after running [compiz], [gnome-wm] tries to run nautilus, so I don't get either a window manager or a desktop manager.

NOTE: Most of the things I've said are subject to my experience and beliefs

---

### Post by wolterh on 2009-12-18
(This post read about a solution I had found, but turns out it didn't work on the long run, I don't even think the previous post's solution works)

---

### Post by wolterh on 2009-12-28
Solution finally found. I discovered the problem was home-dir related by making a new user and logging in (everything was fine there). 
So, I sorted through all the .folders (most logical thing) and after a lot of attempts found out that some files at my [~/.local/share/applications/] where causing the problem. These files were [compiz.desktop], [metacity.desktop], [gnome-wm.desktop]. If you have this same problem, your case may vary. All I did to find these was [$ grep -ril "Autostart" .] on the directory, to find all the files with "Autostart" in them somewhere.

---

