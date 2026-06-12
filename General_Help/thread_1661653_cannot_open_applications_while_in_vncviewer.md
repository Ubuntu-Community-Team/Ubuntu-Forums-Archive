---
title: "cannot open applications while in vncviewer"
date: 2011-01-07
forum: General Help
---

### Post by thedaynos on 2011-01-07
hi all, i'm frustrated as hell. i've tried different vncservers and with all of them, when i use vncviewer, i'm unable to open some applications.  for instance, i can open firefox and terminal. but other programs are giving me problems, like google chrome or the disk manager, which will open for a split second and then disappear. i am so mad i've looked all over the place for a couple days and ready to pull my hair out. i've installed vnc4server, tightvncserver, and a couple others i can't think of right now.  all are giving me the same problem.  anybody???

thanks in advance

---

### Post by thedaynos on 2011-01-08
bump biggity bump

---

### Post by jm23 on 2012-02-17
I am seeing the same thing in 11.10.   It seems that the VNCserver is terminating.
This is the log from ~/.vnc/


17/02/12 20:17:43 See [http://www.tightvnc.com/](http://www.tightvnc.com/) for information on TightVNC
17/02/12 20:17:43 Desktop name 'X' (dragon:2)
17/02/12 20:17:43 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
17/02/12 20:17:43 Listening for VNC connections on TCP port 5902
Font directory '/usr/share/fonts/X11/75dpi/' not found - ignoring
Font directory '/usr/share/fonts/X11/100dpi/' not found - ignoring
No VNC extension on display :2
Xlib:  extension "RANDR" missing on display ":2".
Option "-ry '/usr/share/fonts/X11/75dpi/' not found - ignoring
Font directory '/usr/share/fonts/X11/100dpi/' not found - ignoring
No VNC extension on display :2
Xlib:  extension "RANDR" missing on display ":2".
Option "--login" is no longer supported in this version of gnome-terminal; you might want to create a profile with the desired setting, and use the new '--profile' option
gnome-session[4986]: WARNING: GSIdleMonitor: IDLETIME counter not found
gnome-session[4986]: WARNING: Session 'ubuntu' runnable check failed: Exited with code 1
GNOME_KEYRING_CONTROL=/tmp/keyring-RRHusM
SSH_AUTH_SOCK=/tmp/keyring-RRHusM/ssh
GNOME_KEYRING_PID=5013
GNOME_KEYRING_CONTROL=/tmp/keyring-RRHusM
SSH_AUTH_SOCK=/tmp/keyring-RRHusM/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-RRHusM
SSH_AUTH_SOCK=/tmp/keyring-RRHusM/ssh
GPG_AGENT_INFO=/tmp/keyring-RRHusM/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-RRHusM
SSH_AUTH_SOCK=/tmp/keyring-RRHusM/ssh
GPG_AGENT_INFO=/tmp/keyring-RRHusM/gpg:0:1

(gnome-settings-daemon:5012): color-plugin-WARNING **: Unable to start color manager: RANDR extension is not present

(gnome-settings-daemon:5012): power-plugin-WARNING **: No idle counter

(gnome-settings-daemon:5012): power-plugin-WARNING **: Unable to start power manager: RANDR extension is not present

(gnome-settings-daemon:5012): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-settings-daemon:5012): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-settings-daemon:5012): xrandr-plugin-WARNING **: Unable to start xrandr manager: RANDR extension is not present
Xlib:  extension "RANDR" missing on display ":2".

(gnome-settings-daemon:5012): keyboard-plugin-WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings
ogin" is no longer supported in this version of gnome-terminal; you might want to create a profile with the desired setting, and use the new '--profile' option

---

