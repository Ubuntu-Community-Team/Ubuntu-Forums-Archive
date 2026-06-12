---
title: "Ubuntu logs out each time I use Emacs (X11)"
date: 2011-05-03
forum: General Help
---

### Post by _glook on 2011-05-03
I recently clean installed Ubuntu 10.10 and copied over my last home directory from 11.04, after having upgraded from 10.10. Maybe something went wrong in this transition which is making this happen.

Basically, I have a macbook pro with Ubuntu 10.10 64 bit and have the latest nvidia driver. I'm sshing using -X and -A. I try "emacs &" and Ubuntu logs me out immediately. Occasionally, it will simply log me out on startup although I haven't seen this happen in the last few logins.

I also just tried running kdiff3. It starts to load the window and it does the same as emacs: it logs me out of Ubuntu.

Does anyone have any suggestions?

---

### Post by _glook on 2011-05-03
Additional information: I just tried opening Firefox (not ssh'd) and it logged me out as well. This is odd since it didn't do that the first time.

Edit: It seems it only logs me out for locally installed programs when I launch them from Launchy. The ssh programs are naturally still an issue.

---

### Post by _glook on 2011-05-03
I just found out about .xsession_errors.old, so I'm going to post it below:

```
[COLOR=#351c75][FONT=Arial]/etc/gdm/Xsession: Beginning session setup...[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Setting IM through im-switch for locale=en_US.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]GNOME_KEYRING_CONTROL=/tmp/keyring-FzMDiL[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]GNOME_KEYRING_CONTROL=/tmp/keyring-FzMDiL[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]SSH_AUTH_SOCK=/tmp/keyring-FzMDiL/ssh[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]GNOME_KEYRING_CONTROL=/tmp/keyring-FzMDiL[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]SSH_AUTH_SOCK=/tmp/keyring-FzMDiL/ssh[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial][/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]** (gnome-settings-daemon:6874): WARNING **: Unable to start xrandr manager: RANDR extension is not present[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial][/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial](polkit-gnome-authentication-agent-1:6896): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial][/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial](polkit-gnome-authentication-agent-1:6896): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]gnome-session[6828]:  WARNING: Could not launch application 'xchat-gnome.desktop': Unable to  start application: Failed to execute child process "xchat-gnome" (No  such file or directory)[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]** Message: applet now removed from the notification area[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]** (nm-applet:6902): DEBUG: old state indicates that this was not a disconnect 0[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Loading settings in installed mode from /home/echung[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QKeySequence("Meta+Space") true[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Initializing nautilus-gdu extension[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial][/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial](nautilus:6904): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]** Message: applet now embedded in the notification area[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2a00043 (Buddy List)[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]** (update-notifier:7129): DEBUG: aptdaemon on bus: 0[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]** (update-notifier:7129): DEBUG: Skipping reboot required[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Xlib:  extension "RANDR" missing on display ":0.0".[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4800003 (Archive Ma)[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Window manager warning: Invalid WM_TRANSIENT_FOR window 0x2600030 specified for 0x260002e (Launchy).[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Searching catalog for "l"[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Setting output text to "Launchy"[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Searching history for ""[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Searching catalog for "t"[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Setting output text to "Terminal"[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Searching catalog for "te"[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Setting output text to "Terminal"[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Searching catalog for "ter"[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Setting output text to "Terminal"[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Searching catalog for "term"[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Setting output text to "Terminal"[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]QPixmap: It is not safe to use pixmaps outside the GUI thread[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Launching "Terminal" : "/usr/bin/gnome-terminal "[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Failed to parse arguments: Cannot open display:[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]gnome-power-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial][/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]** (gnome-settings-daemon:6874): WARNING **: Connection failed, reconnecting...[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Window manager warning: Fatal IO error 104 (Connection reset by peer) on display ':0.0'.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]      after 1477 requests (1476 known processed) with 0 events remaining.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]<unknown>: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]gnome-panel: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]xchat: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]Pidgin: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.[/FONT][/COLOR]
[COLOR=#351c75][FONT=Arial]firefox-bin: Fatal IO error 104 (Connection reset by peer) on X server :0.0.[/FONT][/COLOR]
```

---

### Post by _glook on 2011-05-03
Okay, so I forgot to fully upgrade my system, including adding the repository for macbook 6,2. After a few sudo apt-get installs, updates, and upgrades and going into the update manager a few times, the issue seems to have resolved itself.

---

