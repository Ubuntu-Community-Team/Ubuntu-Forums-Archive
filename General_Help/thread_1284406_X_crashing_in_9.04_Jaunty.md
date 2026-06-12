---
title: "X crashing in 9.04 Jaunty"
date: 2009-10-06
forum: General Help
---

### Post by randiroo76073 on 2009-10-06
After updating this AM I keep getting random crashes of Xorg throwing me into re-login. Here's Xorg error file:
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
gnome-session[3644]: WARNING: Could not parse desktop file /home/randyb/.config/autostart/gshared.desktop: Key file does not have key 'Type'
gnome-session[3644]: WARNING: could not read /home/randyb/.config/autostart/gshared.desktop
GNOME_KEYRING_SOCKET=/tmp/keyring-UeIlWC/socket
SSH_AUTH_SOCK=/tmp/keyring-UeIlWC/socket.ssh
GNOME_KEYRING_PID=3786

(gnome-settings-daemon:3784): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
gnome-session[3644]: WARNING: Could not launch application '102b3d444a8942b88f125322982760906500000037320031.desktop': Unable to start application: Failed to execute child process "fast-user-switch-applet" (No such file or directory)
gnome-session[3644]: WARNING: Could not launch application 'nm-applet.desktop': Unable to start application: Failed to execute child process "nm-applet" (No such file or directory)
** (gnome-panel:3832): DEBUG: Adding applet 0.
** (gnome-panel:3832): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:3832): DEBUG: Adding applet 1.
** (gnome-panel:3832): DEBUG: Adding applet 2.
** (gnome-panel:3832): DEBUG: Adding applet 3.
** (gnome-panel:3832): DEBUG: Adding applet 4.
** (gnome-panel:3832): DEBUG: Adding applet 5.
** (gnome-panel:3832): DEBUG: Adding applet 6.
** (gnome-panel:3832): DEBUG: Adding applet 7.
** (gnome-panel:3832): DEBUG: Adding applet 8.
** (gnome-panel:3832): DEBUG: Adding applet 9.

(gnome-panel:3832): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:3832): DEBUG: Adding applet 10.
** (gnome-panel:3832): DEBUG: Adding applet 11.
** (gnome-panel:3832): DEBUG: Adding applet 12.
Initializing nautilus-open-terminal extension
** Message: Initializing gksu extension...

** (nautilus:3833): WARNING **: Unable to add monitor: Not supported
```

I don't know what to make of this as I have not run into it before, any help greatly appreciated.
Thanks

---

### Post by randiroo76073 on 2009-10-07
Updated, fixed problem with pulse-rt, but am still having problems with "fast-user-switch-applet" & 'nm-applet.desktop'
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
gnome-session[3634]: WARNING: Could not parse desktop file /home/randyb/.config/autostart/gshared.desktop: Key file does not have key 'Type'
gnome-session[3634]: WARNING: could not read /home/randyb/.config/autostart/gshared.desktop
GNOME_KEYRING_SOCKET=/tmp/keyring-eNBuJV/socket
SSH_AUTH_SOCK=/tmp/keyring-eNBuJV/socket.ssh
GNOME_KEYRING_PID=3774

(gnome-settings-daemon:3773): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
gnome-session[3634]: WARNING: Could not launch application '102b3d444a8942b88f125322982760906500000037320031.desktop': Unable to start application: Failed to execute child process "fast-user-switch-applet" (No such file or directory)
gnome-session[3634]: WARNING: Could not launch application 'nm-applet.desktop': Unable to start application: Failed to execute child process "nm-applet" (No such file or directory)
** (gnome-panel:3820): DEBUG: Adding applet 0.
** (gnome-panel:3820): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:3820): DEBUG: Adding applet 1.
** (gnome-panel:3820): DEBUG: Adding applet 2.
** (gnome-panel:3820): DEBUG: Adding applet 3.
** (gnome-panel:3820): DEBUG: Adding applet 4.
** (gnome-panel:3820): DEBUG: Adding applet 5.
** (gnome-panel:3820): DEBUG: Adding applet 6.
** (gnome-panel:3820): DEBUG: Adding applet 7.
** (gnome-panel:3820): DEBUG: Adding applet 8.
** (gnome-panel:3820): DEBUG: Adding applet 9.

(gnome-panel:3820): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:3820): DEBUG: Adding applet 10.
** (gnome-panel:3820): DEBUG: Adding applet 11.
** (gnome-panel:3820): DEBUG: Adding applet 12.
Initializing nautilus-open-terminal extension
** Message: Initializing gksu extension...

** (nautilus:3821): WARNING **: Unable to add monitor: Not supported
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
```

---

