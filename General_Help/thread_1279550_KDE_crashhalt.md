---
title: "KDE crash/halt"
date: 2009-09-30
forum: General Help
---

### Post by toejamfootball on 2009-09-30
I recently installed KDE by sudo apt-get install kde-core, It loads up fine, but if I try and do anything for example open an application or change settings it freezes. The mouse still moves but cannot click anything, Ctr-Alt-Del does not logout.

xsession errors...

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_AU.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.

(gnome-settings-daemon:3772): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:3772): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
GNOME_KEYRING_SOCKET=/tmp/keyring-2iW5rb/socket
SSH_AUTH_SOCK=/tmp/keyring-2iW5rb/socket.ssh
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1600x900) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
[Info  13:51:35.141] Running Banshee 1.4.3: [Ubuntu jaunty (development branch) (linux-gnu, i486) @ 2009-03-22 18:04:14 UTC]
** (gnome-panel:3840): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:3840): DEBUG: Adding applet 0.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
[Info  13:51:37.015] All services are started 1.692617s

** (nautilus:3841): WARNING **: Unable to add monitor: Not supported
I/O warning : failed to load external entity "/home/james/.compiz/session/101444b27b9670b79125436909257000400000036780022"
Starting gtk-window-decorator

(gnome-panel:3840): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
[Info  13:51:37.649] GNOME screensaver service not found
** (gnome-panel:3840): DEBUG: Adding applet 1.
** (gnome-panel:3840): DEBUG: Adding applet 2.
** (gnome-panel:3840): DEBUG: Adding applet 3.
[Info  13:51:38.092] nereid Client Started
exec: 1: /usr/lib/evolution/2.26/evolution-alarm-notify: not found
** (update-notifier:3861): DEBUG: /usr/lib/update-notifier/apt-check returned 9 (security: 0)
** (update-notifier:3861): DEBUG: crashreport_check


** (gnome-search-tool:3966): WARNING **: Throbber animation not found

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (gnome-settings-daemon:3991): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:3991): WARNING **: Could not acquire name
```

Any Idea what is causing this? Thanks.

---

### Post by toejamfootball on 2009-10-25
Thought I could bump this one up :)

---

