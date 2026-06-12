---
title: "X11 issues"
date: 2009-12-22
forum: General Help
---

### Post by Neezer on 2009-12-22
So,

I have my ssh working and i'm using an rsa key. I have been monitoring my port 2222 and it seems like nothing is going on there.

I am trying to use port forwarding to see my desktop of my server machine.

here is what I have done.

```

nathan@lappy:~$ ssh -X -C 75.70.164.50
Linux server 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

Last login: Tue Dec 22 08:52:41 2009 from 192.168.1.1
nathan@server:~$ ls
Checkip  Documents  ipaddress  Pictures  Templates
Desktop  Downloads  Music      Public    Videos
nathan@server:~$ who
nathan   pts/0        2009-12-22 08:55 (192.168.1.1)
nathan   tty7         2009-12-22 08:44 (:0)
nathan@server:~$ cd /etc/ssh
nathan@server:/etc/ssh$ ls
moduli      sshd_config   ssh_host_dsa_key      ssh_host_rsa_key
ssh_config  sshd_config~  ssh_host_dsa_key.pub  ssh_host_rsa_key.pub
nathan@server:/etc/ssh$ sudo gedit sshd_config
[sudo] password for nathan: 
nathan@server:/etc/ssh$ exit
logout

```

The big part is that when I used the exit comnmand I get the logout response and then nothing. I have to close the terminal window. It won't go back to a regular command prompt.

Also, if I try gnome-desktop to see the desktop of my server, I get all kinds of errors.

---

### Post by Neezer on 2009-12-22
well, I fixed the exit problem....

I used logout instead and it works just fine.

When I try the gnome-session command I get all kinds of errors

```

nathan@lappy:~$ ssh -X  -C 75.70.164.50
Linux server 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

Last login: Tue Dec 22 09:11:40 2009 from 192.168.1.1
nathan@server:~$ gnome-session
GNOME_KEYRING_SOCKET=/tmp/keyring-aNdb6z/socket
SSH_AUTH_SOCK=/tmp/keyring-aNdb6z/socket.ssh
GNOME_KEYRING_PID=3586

(gnome-settings-daemon:3585): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:3585): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

** (gnome-settings-daemon:3585): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:3585): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.

** (gnome-settings-daemon:3585): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:3585): WARNING **: Failed to connect context: Connection refused
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1366x768) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
** (gnome-panel:3684): DEBUG: Adding applet 0.
** (gnome-panel:3684): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:3684): DEBUG: Adding applet 1.
** (gnome-panel:3684): DEBUG: Adding applet 2.

(nautilus:3685): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:3685): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3685): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3685): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension

** (bluetooth-applet:3696): WARNING **: Could not open RFKILL control device, please verify your installation

** (update-notifier:3708): WARNING **: already running?


(polkit-gnome-authentication-agent-1:3704): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:3704): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
Failed to play sound: Not available
** Message: killswitches state 3
** (gnome-panel:3684): DEBUG: Adding applet 3.
** (gnome-panel:3684): DEBUG: Adding applet 4.

** (gnome-volume-control-applet:3706): WARNING **: Connection failed, reconnecting...

** (gnome-volume-control-applet:3706): WARNING **: Failed to connect context: Connection refused
Shutting down nautilus-gdu extension

(nautilus:3685): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (gnome-panel:3684): DEBUG: Adding applet 5.
The program 'gnome-settings-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 1383 error_code 8 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
** (gnome-panel:3684): DEBUG: Adding applet 6.
** (gnome-panel:3684): DEBUG: Adding applet 7.
** (gnome-panel:3684): DEBUG: Adding applet 8.
** (gnome-panel:3684): DEBUG: Adding applet 9.
** (gnome-panel:3684): DEBUG: Adding applet 10.

** (gnome-volume-control-applet:3706): WARNING **: Connection failed, reconnecting...

** (gnome-volume-control-applet:3706): WARNING **: Failed to connect context: Connection refused
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
I/O warning : failed to load external entity "/home/nathan/.compiz/session/10ec941b7f4894f3b0126149837728083400000035720022"


```

not really sure what is going on with that.

---

### Post by Neezer on 2009-12-23
A bump to the front for this afternoon...still trying to get remote desktop to work.

---

