---
title: "Your session only lasted less than 10 seconds."
date: 2009-10-14
forum: General Help
---

### Post by amarendra on 2009-10-14
I tried everything but no solution worked. It is such a widespread problem and Ubuntu doesn't have official solution page. I hope someone gets me a solution that will actually work in my case.

A pop-up window comes up with this message and when clicked "ok" or "closed" it just restarts the OS and same again. How can I get rid of this? Same if log into Failsafe.
It takes me to GNOME login screen again and again. When tried logging into GNOME Failsafe-once it logged into safely and I downloaded updates too but once I tried to login back normally same problem reoccured and then I can't login to failsafe even. It logs in but nothing works-no clicks no keys excpet ctrl+alt+F2 which takes me to commands only screen and I am left clueless there.

.xsession-errors file:

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_IN.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
** Message: Another GPG agent already running

GNOME_KEYRING_SOCKET=/tmp/keyring-QIuK6M/socket
SSH_AUTH_SOCK=/tmp/keyring-QIuK6M/socket.ssh

(gnome-settings-daemon:4682): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:4682): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_windows_backward"
Window manager warning: Failed to read saved session file /home/fakeer/.config/metacity/sessions/10ee8e7baf38dfc9c81255495597661500000045840037.ms: Failed to open file '/home/fakeer/.config/metacity/sessions/10ee8e7baf38dfc9c81255495597661500000045840037.ms': No such file or directory
** (gnome-panel:4688): DEBUG: Adding applet 0.
** (gnome-panel:4688): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:4688): DEBUG: Adding applet 1.
** (gnome-panel:4688): DEBUG: Adding applet 2.
** (gnome-panel:4688): DEBUG: Adding applet 3.
** (gnome-panel:4688): DEBUG: Adding applet 4.
** (gnome-panel:4688): DEBUG: Adding applet 5.
x-session-manager[4584]: GLib-CRITICAL: unquote_string_inplace: assertion `err == NULL || *err == NULL' failed
x-session-manager[4584]: WARNING: Could not launch application '.wine%22%20wine%20%22C:%5CProgram%20Files%5CWordWeb%5Cwweb32.exe%22%20.desktop': Unable to start application: Key file contains key 'Exec' which has value that cannot be interpreted.
** (gnome-panel:4688): DEBUG: Adding applet 6.
** (gnome-panel:4688): DEBUG: Adding applet 7.
** (gnome-panel:4688): DEBUG: Adding applet 8.
** (gnome-panel:4688): DEBUG: Adding applet 9.
** (gnome-panel:4688): DEBUG: Adding applet 10.
** (gnome-panel:4688): DEBUG: Adding applet 11.
** (gnome-panel:4688): DEBUG: Adding applet 12.
** (gnome-panel:4688): DEBUG: Adding applet 13.
** (gnome-panel:4688): DEBUG: Adding applet 14.
** (gnome-panel:4688): DEBUG: Adding applet 15.
** (gnome-panel:4688): DEBUG: Adding applet 16.
beagled will run in the background.
Use beagle-status to check progress of beagled.
For log files check /home/fakeer/.beagle/Log/current-Beagle.

** (gnome-panel:4688): DEBUG: Adding applet 17.
new binding F12
Got accel 65481, 0, 0
Got keycode 96
Got modmask 0
Warn: Inotify watches may be too low (8192) for some users!  Increase it to at least 65535 by setting fs.inotify.max_user_watches in /etc/sysctl.conf
Debug: Starting Inotify threads
Debug: Using utf8 encoding for filenames
Starting Dropbox...Initializing nautilus-dropbox 0.6.1
** (gnome-panel:4688): DEBUG: Adding applet 18.
Initializing nautilus-open-terminal extension
Got Event! 33, -1
** (gnome-panel:4688): DEBUG: Adding applet 19.

(gnome-panel:4688): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:4688): DEBUG: Adding applet 20.

** (nautilus:4690): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (nm-applet:4710): DEBUG: applet_common_device_state_changed
** (nm-applet:4710): DEBUG: applet_common_device_state_changed
** (nm-applet:4710): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:4710): DEBUG: foo_client_state_changed_cb
Done!
** (nm-applet:4710): DEBUG: applet_common_device_state_changed
** (nm-applet:4710): DEBUG: foo_client_state_changed_cb
** (update-notifier:4702): DEBUG: /usr/lib/update-notifier/apt-check returned 1 (security: 0)
** (update-notifier:4702): DEBUG: crashreport_check

The program 'dropbox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadIDChoice (invalid resource ID chosen for this connection)'.
  (Details: serial 699 error_code 14 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
dropbox: ../../src/xcb_io.c:242: process_responses: Assertion `(((long) (dpy->last_request_read) - (long) (dpy->request)) <= 0)' failed.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Registering '@mozilla.org/module-loader/python;1' (libpyloader.so)
Registering '@mozilla.org/network/protocol/about;1?what=python' (pyabout.py)
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


```

---

### Post by CharlesA on 2009-10-14
Any recent hardware or software changes?

---

### Post by amarendra on 2009-10-14
@Charles: 
Actually the problem is at least 4 months old as far as I can remember. Yes at that time I had recently installed Mac4Lin theme, was experimenting with Emerald, Compiz etc and had crashed my system a couple of times but this problem came after I had used Mac4Lin for a few 1-2 weeks.

Even now I got the error and clicked "ok" on error message pop-up -- went back to Gnome login screen -- logged in and hit "ok" again and so on.. after 4-5 attempts I was able to login successfully. I did this because this work around had worked once earlier too. But doesn't work always.

Sound is not there in my Ubuntu (but this problem was there long before this "10 sec session had come" ).

Mine is a laptop so no hardware change.

---

