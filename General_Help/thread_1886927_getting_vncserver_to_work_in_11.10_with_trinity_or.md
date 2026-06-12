---
title: "getting vncserver to work in 11.10 with trinity or anything else"
date: 2011-11-25
forum: General Help
---

### Post by duindain on 2011-11-25
Hi everyone,
I'm having an issue getting vncserver to work with trinity or any desktop system almost fluxbox works but it wont render vms in vmworkstation so i cant keep using it ;(

Configured with trinity it currently runs i can connect it prompts for password i enter password i get a desktop if i open anything it immediately closes the vnc window and crashes vncserver I can navigate menus but as soon as i click any application the crash occurs

I am temporarily using this command to start vnc
su -c 'vncserver :1 -geometry 1280x1024' myUserName
xstartup file
#!/bin/sh
exec dbus-launch $HOME/.vnc/startvnc.sh

startvnc.sh
#!/bin/sh
autocutsel -fork
export XKL_XMODMAP_DISABLE=1
exec ck-launch-session /opt/trinity/bin/startkde &

when i try running gnome-session instead of trinity i get a error message on connection to vnc clients Failed to load session "ubuntu"
I think these are the errors from the vncserver log file relevant to that issue
```

gnome-session[8679]: WARNING: GSIdleMonitor: IDLETIME counter not found
gnome-session[8679]: WARNING: Session 'ubuntu' runnable check failed: Exited with code 1
gnome-session[8679]: WARNING: Unable to find default provider 'unity-2d-launcher' of required provider 'launcher'

```vnc log file for trinity sessions

```
26/11/11 08:51:57 Xvnc version TightVNC-1.3.9
26/11/11 08:51:57 Copyright (C) 2000-2007 TightVNC Group
26/11/11 08:51:57 Copyright (C) 1999 AT&T Laboratories Cambridge
26/11/11 08:51:57 All Rights Reserved.
26/11/11 08:51:57 See http://www.tightvnc.com/ for information on TightVNC
26/11/11 08:51:57 Desktop name 'X' (ServerName:1)
26/11/11 08:51:57 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
26/11/11 08:51:57 Listening for VNC connections on TCP port 5901
/home/myUserName/.vnc/startvnc.sh: 2: autocutsel: not found
[startkde] Starting startkde.
[startkde] KDEHOME is not set.
[startkde] Set KDEHOME to /home/myUserName/.trinity.
[startkde] kdehome: /home/myUserName/.trinity
[startkde] KDEDIR: /opt/trinity/
[startkde] KDEDIRS: /opt/trinity/:/usr/:/opt/trinity/:/usr/
[startkde] kdedirs_first: /opt/trinity/
[startkde] Reading from /opt/trinity//share/kgtk/preload
[startkde] Starting Trinity...
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
kdeinit: Launched DCOPServer, pid = 7827 result = 0
kdeinit: Launched KLauncher, pid = 7832 result = 0
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
kdeinit: opened connection to :1
kdeinit: Launched KDED, pid = 7833 result = 0
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
kdeinit: Got EXT_EXEC 'kbuildsycoca' from launcher.
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
kbuildsycoca running...
DCOP Cleaning up dead connections.
kdeinit: PID 7835 terminated.
kdeinit: Got EXEC_NEW 'kconf_update' from launcher.
kdeinit: PID 7836 terminated.
kdeinit: PID 7833 terminated.
reading '/home/myUserName/.kompmgr.pid' as kompmgr pidfile

[startkde] TDE_FULL_SESSION: true
[startkde] KDE_SESSION_UID:
kdeinit: Shutting down running client.
kdeinit: Killing kdeinit/klauncher.
kdeinit: Launched DCOPServer, pid = 7843 result = 0
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/myUserName/.DCOPserver_ServerName__1
and start dcopserver again.
---------------------------------

kdeinit: Launched KLauncher, pid = 7844 result = 0
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
kdeinit: opened connection to :1
kdeinit: Launched KDED, pid = 7845 result = 0
KDE Daemon (kded) already running.
kdeinit: Got EXT_EXEC 'kbuildsycoca' from launcher.
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
kbuildsycoca running...
Reusing existing ksycoca
DCOP Cleaning up dead connections.
kdeinit: PID 7847 terminated.
kdeinit: PID 7845 terminated.
kdeinit: Launched 'kcminit_startup', pid = 7848 result = 0
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
kdeinit: Got SETENV 'KDE_MULTIHEAD=false' from klauncher.
kdeinit: PID 7848 terminated.
[startkde] kdeinit started successfully.
kdeinit: Got KWRAPPER 'ksmserver' from socket.
kdeinit: PID 7851 terminated.
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
kdeinit: Got SETENV 'SESSION_MANAGER=local/ServerName:@/tmp/.ICE-unix/7852,unix/ServerName:/tmp/.ICE-unix/7852,inet6/ServerName:45301,inet/ServerName:59085' from klauncher.
kdeinit: Got EXEC_NEW 'kwin' from launcher.
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
kdeinit: Got EXEC_NEW 'kdesktop' from launcher.
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
kdeinit: PID 7855 terminated.
kdeinit: Got EXEC_NEW 'kicker' from launcher.
Cannot connect socket '/var/run/xdmctl/dmctl-:1/socket'.
kdeinit detected
^Mkdeinit: Got EXEC_NEW 'kio_file' from launcher.
kdeinit: Got EXEC_NEW 'kio_file' from launcher.
kdeinit: Got EXEC_NEW 'kio_media' from launcher.
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
kdeinit: PID 7858 terminated.
kdeinit: Got EXT_EXEC 'kio_uiserver' from launcher.
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
kdeinit: PID 7865 terminated.
kdeinit: Got EXEC_NEW 'kio_system' from launcher.
kdeinit: Got EXEC_NEW 'kio_trash' from launcher.
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
kdeinit: Got SETENV 'XCURSOR_THEME=DMZ-White' from klauncher.
server does not have extension for "r rate" option
xrdb: colon missing on line 359, ignoring line
kdeinit: Got SETENV 'GTK_RC_FILES=/etc/gtk/gtkrc:/home/myUserName/.gtkrc:/home/myUserName/.trinity/share/config/gtkrc' from klauncher.
kdeinit: Got SETENV 'GTK2_RC_FILES=/home/myUserName/.gtkrc-2.0-kde4:/home/myUserName/.trinity/share/config/gtkrc-2.0' from klauncher.
kdeinit: Got EXEC_NEW 'nspluginscan' from launcher.
Could not load library! Trying exec....
kdeinit: Got EXEC_NEW 'artswrapper' from launcher.
Could not load library! Trying exec....
kdeinit: Got EXEC_NEW 'kaccess' from launcher.
kdeinit: Got EXEC_NEW 'notification-daemon-tde' from launcher.
Could not load library! Trying exec....
kdeinit: Got EXEC_NEW 'kmixctrl' from launcher.
kdeinit: Got EXEC_NEW 'kmix' from launcher.
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
DCOP aborting call from 'anonymous-7876' to 'kaccess'
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
kdeinit: PID 7876 terminated.
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
kdeinit: Got EXEC_NEW 'katapult' from launcher.
Could not load library! Trying exec....
kdeinit: PID 7879 terminated.
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
kdeinit: Got EXEC_NEW 'su-to-root' from launcher.
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
Could not load library! Trying exec....
Server has no DPMS extension
kdeinit: Got EXEC_NEW '/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1' from launcher.
Could not load library! Trying exec....
kdeinit: Got EXT_EXEC 'knotify' from launcher.
kdeinit: Got EXEC_NEW 'start-pulseaudio-kde' from launcher.
Could not load library! Trying exec....
kdeinit: Got EXEC_NEW '/bin/sh' from launcher.
Could not load library! Trying exec....
kdeinit: Got EXEC_NEW 'zeitgeist-datahub' from launcher.
Failure: Module initalisation failed
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
ERROR: ld.so: object '/opt/trinity/$LIB/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/opt/trinity/$LIB/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
Could not load library! Trying exec....
kdeinit: PID 7928 terminated.
kdeinit: PID 7930 terminated.
kdeinit: Got EXEC_NEW 'konqueror' from launcher.
Xlib:  extension "RANDR" missing on display ":1".
Ignored duplicate item: IBus
Ignored duplicate item: Kontact
Ignored duplicate item: KMail
Ignored duplicate item: Brasero
Ignored duplicate item: Kontact
Ignored duplicate item: KArm
Ignored duplicate item: KMail
Ignored duplicate item: Evolution
Ignored duplicate item: LibreOffice Draw
Ignored duplicate item: KNotes
Ignored duplicate item: Onboard Settings
Ignored duplicate item: Startup Disk Creator
Ignored duplicate item: System Testing
Xlib:  extension "XInputExtension" missing on display ":1".
Ignored duplicate item: Computer Janitor
Failed to get list of devices
Ignored duplicate item: Firestarter
Ignored duplicate item: Storage Device Manager
Ignored duplicate item: Disk Utility
Ignored duplicate item: Ubuntu Software Center
Ignored duplicate item: Update Manager
Ignored duplicate item: Users and Groups
Ignored duplicate item: Network Tools
kdeinit: Got EXEC_NEW 'guidance-power-manager' from launcher.
Ignored duplicate item: Mines
Could not load library! Trying exec....
/opt/trinity/bin/guidance-power-manager: 2: /usr/share/python-support/kde-guidance-powermanager-trinity/guidance-power-manager.py: not found
kdeinit: PID 7946 terminated.
kdeinit: Got EXEC_NEW '/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1' from launcher.
Could not load library! Trying exec....
kdeinit: PID 7911 terminated.
kdeinit: Got EXEC_NEW 'start-pulseaudio-kde' from launcher.
Could not load library! Trying exec....
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
kdeinit: Got EXEC_NEW '/bin/sh' from launcher.
Could not load library! Trying exec....
kdeinit: Got EXEC_NEW 'zeitgeist-datahub' from launcher.
Could not load library! Trying exec....
kdeinit: Got EXEC_NEW 'adept_notifier' from launcher.
Could not load library! Trying exec....
kdeinit: PID 7954 terminated.
kdeinit: Got EXEC_NEW 'klipper' from launcher.
Failure: Module initalisation failed

** (process:7958): WARNING **: zeitgeist-datahub.vala:218: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
kdeinit: PID 7952 terminated.
Xlib:  extension "RANDR" missing on display ":1".
kdeinit: Got EXEC_NEW 'krandrtray' from launcher.
Could not load library! Trying exec....
kdeinit: PID 7958 terminated.
kdeinit: Got EXEC_NEW 'adept_notifier' from launcher.
Could not load library! Trying exec....
kdeinit: Got EXEC_NEW 'konqueror' from launcher.
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices

(polkit-gnome-authentication-agent-1:7949): polkit-gnome-1-WARNING **: Failed to register client: The name org.gnome.SessionManager was not provided by any .service files
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
Xlib:  extension "RANDR" missing on display ":1".

** (polkit-gnome-authentication-agent-1:7907): WARNING **: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
Cannot register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
ERROR: ld.so: object '/opt/trinity/$LIB/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/opt/trinity/$LIB/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
kdeinit: PID 7907 terminated.
kdeinit: PID 7874 terminated.
kdeinit: Got EXT_EXEC 'kbuildsycoca' from launcher.
kdeinit: PID 7966 terminated.
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
kbuildsycoca running...
Reusing existing ksycoca

(gksu:7926): Gtk-CRITICAL **: IA__gtk_widget_grab_default: assertion `GTK_IS_WIDGET (widget)' failed
kdeinit: PID 7974 terminated.
kdeinit: PID 7880 terminated.
DCOP Cleaning up dead connections.
kdeinit: PID 8015 terminated.
kdeinit: PID 7960 terminated.
kdeinit: PID 7975 terminated.

(process:7931): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (process:7931): DEBUG: zeitgeist-datahub.vala:58: Zeitgeist-daemon disappeared from the bus, exitting...
kdeinit: PID 7931 terminated.

26/11/11 08:52:06 Got connection from client 132.44.173.143
26/11/11 08:52:06 Using protocol version 3.8
26/11/11 08:52:08 Full-control authentication passed by 132.44.173.143
26/11/11 08:52:08 Pixel format for client 132.44.173.143:
26/11/11 08:52:08   32 bpp, depth 24, little endian
26/11/11 08:52:08   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
26/11/11 08:52:08   no translation needed
26/11/11 08:52:08 rfbProcessClientNormalMessage: ignoring unknown encoding 16
26/11/11 08:52:08 rfbProcessClientNormalMessage: ignoring unknown encoding 17
26/11/11 08:52:08 rfbProcessClientNormalMessage: ignoring unknown encoding 10
26/11/11 08:52:08 rfbProcessClientNormalMessage: ignoring unknown encoding 9
26/11/11 08:52:08 rfbProcessClientNormalMessage: ignoring unknown encoding 8
26/11/11 08:52:08 Using tight encoding for client 132.44.173.143
26/11/11 08:52:08 Using compression level 6 for client 132.44.173.143
26/11/11 08:52:08 Enabling X-style cursor updates for client 132.44.173.143
26/11/11 08:52:08 Enabling cursor position updates for client 132.44.173.143
26/11/11 08:52:08 Using image quality level 6 for client 132.44.173.143
26/11/11 08:52:08 rfbProcessClientNormalMessage: ignoring unknown encoding -65530
26/11/11 08:52:08 Enabling LastRect protocol extension for client 132.44.173.143
26/11/11 08:52:08 rfbProcessClientNormalMessage: ignoring unknown encoding -223
26/11/11 08:52:08 rfbProcessClientNormalMessage: ignoring unknown encoding -65535
26/11/11 08:52:08 rfbProcessClientNormalMessage: ignoring unknown encoding -32768
26/11/11 08:52:08 rfbProcessClientNormalMessage: ignoring unknown encoding -32767
26/11/11 08:52:08 rfbProcessClientNormalMessage: ignoring unknown encoding -32766
26/11/11 08:52:08 rfbProcessClientNormalMessage: ignoring unknown encoding -32765
26/11/11 08:52:08 rfbProcessClientNormalMessage: ignoring unknown encoding -1063131698
kdeinit: PID 7906 terminated.
kdeinit: Got EXEC_NEW 'kio_thumbnail' from launcher.
Xlib:  extension "XInputExtension" missing on display ":1".
Failed to get list of devices
QImage::smoothScale: Image is a null image
kdeinit: Got EXT_EXEC 'kate' from launcher.
knotify: Fatal IO error: client killed
ksmserver: Fatal IO error: client killed
kwin: Fatal IO error: client killed
kded: Fatal IO error: client killed
kio_uiserver: Fatal IO error: client killed
kmix: Fatal IO error: client killed
notification-daemon-tde: Fatal IO error: client killed
konqueror: Fatal IO error: client killed
konqueror: Fatal IO error: client killed
reading '/home/myUserName/.kompmgr.pid' as kompmgr pidfile

katapult: Fatal IO error: client killed
kicker: Fatal IO error: client killed
kdialogd3: Fatal IO error: client killed
klipper: Fatal IO error: client killed
krandrtray: Fatal IO error: client killed
adept_notifier: Fatal IO error: client killed
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
kdeinit: PID 7854 terminated.
kdeinit: PID 7878 terminated.
klauncher: Fatal IO error: client killed
kdeinit: PID 7887 terminated.
kdeinit: PID 7936 terminated.
kdeinit: PID 7949 terminated.
kdeinit: PID 7978 terminated.
kdeinit: Fatal IO error: client killed
kdeinit: sending SIGHUP to children.
klauncher: Exiting on signal 1
klauncher: Fatal IO error: client killed
*** kdesktop got signal 1 (Exiting)
kdeinit: sending SIGTERM to children.
kdeinit: Exit.
DCOP aborting (delayed) call from 'kdesktop' to 'klauncher'
[startkde] Shutting down Trinity...
[trinity kinit] Warning: connect() failed: : No such file or directory
[trinity kinit] Error: Can't contact kdeinit!
[startkde] Running Trinity shutdown scripts...
xprop:  unable to open display ':1'
[startkde] Trinity shutdown complete.
```I just need a decent desktop that works well enough to show virtual machines from vmworkstation if anyone knows how to resolve issues with trinity or fluxbox that would be ideal or i guess how to get gnome working that could work too

Thanks anyone for taking the time to read
;)

---

### Post by duindain on 2011-11-30
anyone?

---

