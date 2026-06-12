---
title: "VNCClient Crashes the VNC server when I start an App in the client window"
date: 2011-05-18
forum: General Help
---

### Post by wdavro on 2011-05-18
I have 64bit Lucid and am having some trouble trying to get tightvncserver functional.  I type the following in a terminal window.

```
tightvncserver -geometry 1024x768 -depth 16 :1

```

and I get the following in response:

```
Found /usr/share/tightvnc-java for http connections.

New 'X' desktop is ubuntu:1

Starting applications specified in /home/dave/.vnc/xstartup
Log file is /home/dave/.vnc/ubuntu:1.log
```

I move to my XP Pro sp3 (also on my local network) and start TighVNC Viewer.  I enter ubuntu:1 and hit connect.  I enter my password and I get my ubuntu desktop with a terminal window open, and an error message box that says:

```
Error: XKB Extnesion is not enabled
```

There is only a "Close" button so I click it.

I click on the Application menu of ubuntu and the TightVNC client window simply disappears.

If I start TightVNC Viewer again and try to connect I get an error message:
```
Failed to connect to server (ubuntu:1)
```.

Following is the contents of my ubuntu:1.log file:
```
17/05/11 23:47:05 Xvnc version TightVNC-1.3.9
17/05/11 23:47:05 Copyright (C) 2000-2007 TightVNC Group
17/05/11 23:47:05 Copyright (C) 1999 AT&T Laboratories Cambridge
17/05/11 23:47:05 All Rights Reserved.
17/05/11 23:47:05 See http://www.tightvnc.com/ for information on TightVNC
17/05/11 23:47:05 Desktop name 'X' (ubuntu:1)
17/05/11 23:47:05 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
17/05/11 23:47:05 Listening for VNC connections on TCP port 5901
17/05/11 23:47:05 Listening for HTTP connections on TCP port 5801
17/05/11 23:47:05   URL http://ubuntu:5801
Option "--login" is no longer supported in this version of gnome-terminal; you might want to create a profile with the desired setting, and use the new '--profile' option
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".
gnome-session[2864]: WARNING: GSIdleMonitor: IDLETIME counter not found
GNOME_KEYRING_CONTROL=/tmp/keyring-uht1Ua
SSH_AUTH_SOCK=/tmp/keyring-uht1Ua/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-uht1Ua
SSH_AUTH_SOCK=/tmp/keyring-uht1Ua/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-uht1Ua
SSH_AUTH_SOCK=/tmp/keyring-uht1Ua/ssh
Xlib:  extension "RANDR" missing on display ":1.0".

** (gnome-settings-daemon:2880): WARNING **: Unable to start xrandr manager: RANDR extension is not present

** (gnome-settings-daemon:2880): WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings

** (gnome-settings-daemon:2880): WARNING **: XKB extension not available

** (gnome-settings-daemon:2880): WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
Unable to find a synaptics device.
Window manager warning: Failed to read saved session file /home/dave/.config/metacity/sessions/104d6e23b4bb1a8e10130570122643967800000028640032.ms: Failed to open file '/home/dave/.config/metacity/sessions/104d6e23b4bb1a8e10130570122643967800000028640032.ms': No such file or directory
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".
Window manager warning: Log level 32: could not find XKB extension.
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".
Found /usr/share/tightvnc-java for http connections.

(polkit-gnome-authentication-agent-1:2924): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2924): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

** (polkit-gnome-authentication-agent-1:2924): WARNING **: Unable to register authentication agent: Remote Exception invoking org.freedesktop.PolicyKit1.Authority.RegisterAuthenticationAgent() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session
Cannot register authentication agent: Remote Exception invoking org.freedesktop.PolicyKit1.Authority.RegisterAuthenticationAgent() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session
An instance of nm-applet is already running.

(gnome-power-manager:2929): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x1d49e60'
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".

** (gnome-power-manager:2929): WARNING **: No idle counter.
Xlib:  extension "DPMS" missing on display ":1.0".
Unable to open desktop file /usr/share/applications/xsane.desktop for panel launcher: No such file or directory
Initializing nautilus-gdu extension

New 'ubuntu-2' desktop is ubuntu:2

Starting applications specified in /home/dave/.vnc/xstartup
Log file is /home/dave/.vnc/ubuntu:2.log

17/05/2011 11:47:07 PM Autoprobing TCP port in (all) network interface
17/05/2011 11:47:07 PM Listening IPv{4,6}://*:5900
17/05/2011 11:47:07 PM Listening IPv4://0.0.0.0:5900
17/05/2011 11:47:07 PM Problems in NewSocketListenTCP(), sock=-1
17/05/2011 11:47:07 PM Listening IPv{4,6}://*:5901
17/05/2011 11:47:07 PM Listening IPv4://0.0.0.0:5901
17/05/2011 11:47:07 PM Problems in NewSocketListenTCP(), sock=-1
17/05/2011 11:47:07 PM Listening IPv{4,6}://*:5902
17/05/2011 11:47:07 PM Listening IPv4://0.0.0.0:5902
17/05/2011 11:47:07 PM Problems in NewSocketListenTCP(), sock=-1
17/05/2011 11:47:07 PM Listening IPv{4,6}://*:5903
17/05/2011 11:47:07 PM Autoprobing selected port 5903
17/05/2011 11:47:07 PM Advertising security type: 'TLS' (18)
17/05/2011 11:47:07 PM Advertising authentication type: 'VNC Authentication' (2)
17/05/2011 11:47:07 PM Advertising security type: 'VNC Authentication' (2)
Xlib:  extension "RANDR" missing on display ":1.0".
Failure: Module initalization failed
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".
** Message: secret service operation failed: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Xlib:  extension "RANDR" missing on display ":1.0".
** (update-notifier:3247): DEBUG: Skipping reboot required

17/05/11 23:49:18 Got connection from client 192.168.1.232
17/05/11 23:49:18 Using protocol version 3.8
17/05/11 23:49:18 Enabling TightVNC protocol extensions
17/05/11 23:49:54 Full-control authentication passed by 192.168.1.232
17/05/11 23:49:54 Pixel format for client 192.168.1.232:
17/05/11 23:49:54   16 bpp, depth 16, little endian
17/05/11 23:49:54   true colour: max r 31 g 63 b 31, shift r 11 g 5 b 0
17/05/11 23:49:54   no translation needed
17/05/11 23:49:54 Using tight encoding for client 192.168.1.232
17/05/11 23:49:54 rfbProcessClientNormalMessage: ignoring unknown encoding 8
17/05/11 23:49:54 Enabling X-style cursor updates for client 192.168.1.232
17/05/11 23:49:54 Enabling cursor position updates for client 192.168.1.232
17/05/11 23:49:54 Using image quality level 6 for client 192.168.1.232
17/05/11 23:49:54 Enabling LastRect protocol extension for client 192.168.1.232
17/05/11 23:49:54 rfbProcessClientNormalMessage: ignoring unknown encoding -223
gnome-terminal: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':1.0'.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
vino-server: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
gnome-volume-control-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
gnome-power-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
XOpenDisplay() failed
gnome-panel: Fatal IO error 88 (Socket operation on non-socket) on X server :1.0.

```

I could use some help.  Where do I start resolving all this?

TIA

---

