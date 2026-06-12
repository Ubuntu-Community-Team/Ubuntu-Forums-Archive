---
title: "tightvncserver: root and user"
date: 2012-07-25
forum: General Help
---

### Post by dustinr on 2012-07-25
Hello Forum

I am running tightvncserver and x11vnc server. This way I can have a real desktop (x11vnc) to view and control, and I can have a virtual desktop (tightvncserver) to run apps with out disturbing the real desktop.

One problem is, the virtual desktop runs as root. Because of this I can't run apps as users. For example when I try to open google-chrome I get, "Google Chrome can not be run as root. Please start Google Chrome as a normal user. ..." 

Another issue I have ( might be related ) when I try to open "Monitors" inside system/preferences it gives me the error, "Could not get screen information. RANDR extension is not present."

Overall I was expecting a fully functioning virtual desktop. Can anyone help me out? Maybe I expect too much haha.


I am running ubuntu 10.10

Thanks!

---

### Post by steeldriver on 2012-07-25
How are you invoking the tightvnc server? if you start it as user then it runs as user surely?

---

### Post by dustinr on 2012-07-25
Thanks for your response.

I was starting it as user. 

Strange note... I work on multiple machines, so i copy and pasted the vnc scripts from computer A and put them on computer B. I tried very hard to use the same steps with installing the servers. I know for a fact that they are initialized in the same manor. BUT Computer B works as I would expect. I can run chrome, im logged in as user, etc.

So, the original post does not apply to computer B, only computer A. As long as from here on out when I put this on future machines it continues to act as I expect, the thread is solved. I will keep it open for now until I am sure this wont repeat.

HOWEVER! I do have another issue with tightvncserver...

I try to start tightvncserver at boot and it seems like it dosent fully start? It loads a terminal ( my script tells it to) but the desktop is grey. A warning or error message pops up saying "Could not acquire name on session bus".

This is my non-appended log from boot when this happens.
```
25/07/12 11:25:38 Xvnc version TightVNC-1.3.9
25/07/12 11:25:38 Copyright (C) 2000-2007 TightVNC Group
25/07/12 11:25:38 Copyright (C) 1999 AT&T Laboratories Cambridge
25/07/12 11:25:38 All Rights Reserved.
25/07/12 11:25:38 See http://www.tightvnc.com/ for information on TightVNC
25/07/12 11:25:38 Desktop name 'X' (DML-0004:1)
25/07/12 11:25:38 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
25/07/12 11:25:38 Listening for VNC connections on TCP port 5901
Option "--login" is no longer supported in this version of gnome-terminal; you might want to create a profile with the desired setting, and use the new '--profile' option
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".
gnome-session[2040]: WARNING: Failed to acquire org.gnome.SessionManager

25/07/12 11:25:52 Got connection from client 192.168.1.115
25/07/12 11:25:52 Using protocol version 3.8
25/07/12 11:25:54 Full-control authentication passed by 192.168.1.115
25/07/12 11:25:54 Pixel format for client 192.168.1.115:
25/07/12 11:25:54   8 bpp, depth 8
25/07/12 11:25:54   true colour: max r 7 g 7 b 3, shift r 0 g 3 b 6
25/07/12 11:25:54 Using tight encoding for client 192.168.1.115
25/07/12 11:25:54 rfbProcessClientNormalMessage: ignoring unknown encoding 16
25/07/12 11:25:54 rfbProcessClientNormalMessage: ignoring unknown encoding 9
25/07/12 11:25:54 rfbProcessClientNormalMessage: ignoring unknown encoding -65527
25/07/12 11:25:54 Using compression level 9 for client 192.168.1.115
25/07/12 11:25:54 Using image quality level 0 for client 192.168.1.115
25/07/12 11:25:54 Enabling X-style cursor updates for client 192.168.1.115
25/07/12 11:25:54 Enabling cursor position updates for client 192.168.1.115
25/07/12 11:25:54 rfbProcessClientNormalMessage: ignoring unknown encoding -131072
25/07/12 11:25:54 rfbProcessClientNormalMessage: ignoring unknown encoding -223
25/07/12 11:25:54 Enabling LastRect protocol extension for client 192.168.1.115
25/07/12 11:25:54 rfbProcessClientNormalMessage: ignoring unknown encoding -131071
25/07/12 11:25:54 rfbProcessClientNormalMessage: ignoring unknown encoding -131070

```

With this being said. I CAN kill that virtual desktop and start it again using the SAME command, and everything works great.

Note: When I start it manually, I get warnings 
```
xauth: /home/kiosk/.Xauthority not writeable, changes will be ignored
xauth: error in locking authority file /home/kiosk/.Xauthority

```

and my log file when this happens is:
```

25/07/12 11:31:52 Xvnc version TightVNC-1.3.9
25/07/12 11:31:52 Copyright (C) 2000-2007 TightVNC Group
25/07/12 11:31:52 Copyright (C) 1999 AT&T Laboratories Cambridge
25/07/12 11:31:52 All Rights Reserved.
25/07/12 11:31:52 See http://www.tightvnc.com/ for information on TightVNC
25/07/12 11:31:52 Desktop name 'X' (DML-0004:1)
25/07/12 11:31:52 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
25/07/12 11:31:52 Listening for VNC connections on TCP port 5901
Option "--login" is no longer supported in this version of gnome-terminal; you might want to create a profile with the d
esired setting, and use the new '--profile' option
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".
gnome-session[17520]: WARNING: GSIdleMonitor: IDLETIME counter not found
Xlib:  extension "RANDR" missing on display ":1.0".
GNOME_KEYRING_CONTROL=/tmp/keyring-RxAoMb
GNOME_KEYRING_PID=17553
GNOME_KEYRING_CONTROL=/tmp/keyring-RxAoMb
SSH_AUTH_SOCK=/tmp/keyring-RxAoMb/ssh
Xlib:  extension "RANDR" missing on display ":1.0".
GNOME_KEYRING_CONTROL=/tmp/keyring-RxAoMb
SSH_AUTH_SOCK=/tmp/keyring-RxAoMb/ssh
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".

** (gnome-settings-daemon:17556): WARNING **: Unable to start xrandr manager: RANDR extension is not present

** (gnome-power-manager:17550): WARNING **: No idle counter.
The program 'gnome-power-manager' received an X Window System error.
This probably reflects a bug in the program.
The error was 'XSyncBadCounter'.
  (Details: serial 99 error_code 129 request_code 133 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
gnome-session[17520]: WARNING: Could not launch application 'caffeine.desktop': Unable to start application: Failed to e
xecute child process "/usr/bin/caffeine" (No such file or directory)
xscreensaver: 11:31:54: logging to file /var/log/TpScreenSaver.log
Xlib:  extension "RANDR" missing on display ":1.0".

(polkit-gnome-authentication-agent-1:17597): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:17597): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0'
failed
Xlib:  extension "RANDR" missing on display ":1.0".

** (gnome-settings-daemon:17556): WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings

** (gnome-settings-daemon:17556): WARNING **: XKB extension not available

** (gnome-settings-daemon:17556): WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
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
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".
An instance of nm-applet is already running.
Window manager warning: Log level 32: could not find XKB extension.
Initializing nautilus-gdu extension

(nautilus:17604): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:17604): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed
A VNC server is already running as :1
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: ca
nnot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Failure: Module initalization failed
Xlib:  extension "RANDR" missing on display ":1.0".

(nautilus:17604): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

(nautilus:17604): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed
Xlib:  extension "RANDR" missing on display ":1.0".

(nautilus:17604): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

(nautilus:17604): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

(nautilus:17604): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed
exec: 1: jockey-gtk: not found

(nautilus:17604): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

(nautilus:17604): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

(nautilus:17604): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

(nautilus:17604): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

(nautilus:17604): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

(nautilus:17604): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

(nautilus:17604): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

(nautilus:17604): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

(nautilus:17604): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

(nautilus:17604): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed


```


Any ideas?

Thanks!

---

### Post by steeldriver on 2012-07-25
I don't know - what session are you trying to start? there are for sure some problems with the default tightvnc ~/.vnc/xstartup if you are using Unity/compiz - see this thread

[http://kb.realvnc.com/questions/196/VNC+Server+in+Virtual+Mode+does+not+start+correctly+on+Ubuntu+12.04](http://kb.realvnc.com/questions/196/VNC+Server+in+Virtual+Mode+does+not+start+correctly+on+Ubuntu+12.04)

---

### Post by dustinr on 2012-07-25
I guess I did leave that part out.

I use Gnome-session

here are my scripts I use.

/home/user/.vnc/xstartup
```

#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
 x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
# x-window-manager &
gnome-session &
#su user

```

/usr/local/bin/vnc
```

#!/bin/sh

sudo x11vnc -notruecolor -nap -bg -forever -shared -rfbauth ~/.vnc/passwd -rfbport 5900 -desktop "VNC ${USER}@${HOSTNAME}" -auth guess -oa /home/user/.vnc/x11vnc.log
tightvncserver :1

```

Thanks!

---

### Post by dustinr on 2012-07-25
WOO!

I found this link:
[https://bugs.launchpad.net/unity-2d/+bug/822234]("https://bugs.launchpad.net/unity-2d/+bug/822234")

They suggested adding 
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession
to my xstartup script.

Now when I boot up it launches normally, log file looks clean and small :) . I can even kill it and launch it manually and it still works like a charm.

I guess I should have researched more. Thanks steeldriver for your help. 

I will mark this as solved shortly :)

---

### Post by steeldriver on 2012-07-25
OK glad you got it fixed

Why are you running the x11vnc process as sudo though? I would think that's a recipe for trouble

---

### Post by dustinr on 2012-07-25
Good question. I dont know why I did that, I guess I get sudo happy sometimes. I took the sudo off of my x11vnc and everything still works, thanks for pointing that out.

btw my xstartup looks like this now

```
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#Added the following to get GNOME to work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession

```

For anyone that is using tightvncserver with gnome.

---

### Post by dustinr on 2012-07-25
OK I will mark this solved. For future reference, the issue I had with 'Computer A' not being able to log in as user, and it only ran as root was because of permissions. 

I would receive and error when trying to start thightvncserver about permission denied. Carelessly I ran it with a sudo to take care of the pesky permissions. 

These are the correct permissions for inside of the .vnc/ dir.

```

-rwxr-xr-x  1 kiosk kiosk 2462458 2012-07-25 15:12 x11vnc.log
-rw-r--r--  1 kiosk kiosk     552 2012-07-25 15:12 DML-0004:1.log
drwxr-xr-x 55 kiosk kiosk   12288 2012-07-25 15:12 ..
drwxr-xr-x  2 kiosk kiosk    4096 2012-07-25 15:12 .
-rw-r--r--  1 kiosk kiosk       5 2012-07-25 15:12 DML-0004:1.pid
-rwxr-xr-x  1 kiosk kiosk     145 2012-07-25 12:36 xstartup
-rw-------  1 kiosk kiosk       8 2012-07-25 10:57 tightpasswd
-rw-------  1 kiosk kiosk       8 2012-07-25 10:56 passwd
-rw-r--r--  1 kiosk kiosk       5 2012-07-25 10:44 port.txt

```

More specifically the passwd files need to be chmod 600, and the x11vnc.log needs to be like the above. 

I hope someone can benefit from my mistakes.

Enjoy ubuntu!

---

