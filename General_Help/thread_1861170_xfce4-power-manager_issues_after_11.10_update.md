---
title: "xfce4-power-manager issues after 11.10 update"
date: 2011-10-15
forum: General Help
---

### Post by Jarm1 on 2011-10-15
I'm having an issue with xfce4-power-manager since I did the in place update from 11.04 to 11.10, where it basically seems as if it won't run.

Trying to open it via the Settings pane results in a dialog bog saying "Xfce4 Power Manager is not running, do you want to launch it now?" with the options of Run and No; neither have any impact. Of course the pane never appears and I'm left with essentially a blank preference window.

Trying to run it via a terminal, sudo or not, makes no difference either, giving no errors and still it appears that it had not started.

Re-installing xfce4-power-manager didn't make any difference.

Any tips for how I might get it working again?

Thanks!

---

### Post by Toz on 2011-10-15
When it try to run it from the command line, does anything show up in your ~/.xsession-errors file? Error messages of any kind?

---

### Post by Jarm1 on 2011-10-15
Nothing at all is added when I try to launch from the command line, whenever I use the GUI to try to launch it only one line appears and it is just a repeat of the text in the "Run" box:

"Xfce power manager is not running"

---

### Post by Toz on 2011-10-16
Do you have another power manager running (like gnome-power-manager)?

---

### Post by Jarm1 on 2011-10-16
Not as far as I know, any other would have had to been installed automatically during the update since this is just standard Xubuntu, and I run Xfce Session instead of Xubuntu Desktop (Or Session?-whichever the proper name is). Just checked specifically for gnome-power-manager, it is not installed.

---

### Post by Toz on 2011-10-16
Can you post back the contents of your ~/.xsession-errors file?

Also, try running it like this from the command line to see if it generates any error messages:
```
xfce4-power-manager --no-daemon
```

---

### Post by Jarm1 on 2011-10-16
After booting:

```
Running X session wrapper
Loading profile from /etc/profile
Loading profile from /home/mbpcolin/.profile
Loading resource: /etc/X11/Xresources/x11-common
Loading X session script /etc/X11/Xsession.d/20x11-common_process-args
Loading X session script /etc/X11/Xsession.d/30x11-common_xresources
Loading X session script /etc/X11/Xsession.d/40x11-common_xsessionrc
Loading X session script /etc/X11/Xsession.d/50x11-common_determine-startup
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/60x11-common_localhost
Loading X session script /etc/X11/Xsession.d/60x11-common_xdg_path
Loading X session script /etc/X11/Xsession.d/60xdg-user-dirs-update
Loading X session script /etc/X11/Xsession.d/70gconfd_path-on-session
Loading X session script /etc/X11/Xsession.d/75dbus_dbus-launch
Loading X session script /etc/X11/Xsession.d/80im-switch
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Loading X session script /etc/X11/Xsession.d/90consolekit
Loading X session script /etc/X11/Xsession.d/90x11-common_ssh-agent
Loading X session script /etc/X11/Xsession.d/99x11-common_start
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 13 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 14 overrides entry on line 7
ssh-agent is already running
xfdesktop[1702]: starting up

(xfce4-settings-helper:1706): xfce4-settings-helper-CRITICAL **: Stored Xfconf properties disable all outputs, aborting.
xfce4-settings-helper: Another instance is already running. Leaving...
GNOME_KEYRING_CONTROL=/tmp/keyring-qeGeGK
SSH_AUTH_SOCK=/tmp/keyring-qeGeGK/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-qeGeGK
SSH_AUTH_SOCK=/tmp/keyring-qeGeGK/ssh
GPG_AGENT_INFO=/tmp/keyring-qeGeGK/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-qeGeGK
SSH_AUTH_SOCK=/tmp/keyring-qeGeGK/ssh
GPG_AGENT_INFO=/tmp/keyring-qeGeGK/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-qeGeGK
SSH_AUTH_SOCK=/tmp/keyring-qeGeGK/ssh
GPG_AGENT_INFO=/tmp/keyring-qeGeGK/gpg:0:1

(polkit-gnome-authentication-agent-1:1758): polkit-gnome-1-WARNING **: Failed to register client: The name org.gnome.SessionManager was not provided by any .service files
(xfce4-mixer-plugin:1729): xfce4-mixer-plugin-DEBUG: mixer_plugin->track_label = 'Master'
** Message: applet now removed from the notification area
** (nm-applet:1739): DEBUG: old state indicates that this was not a disconnect 0
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/BasePlugin.py", line 65, in _load
    self.on_load(parent)
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/applet/PulseAudio.py", line 173, in on_load
    raise Exception("PulseAudio too old, required 0.9.15 or higher")
Exception: PulseAudio too old, required 0.9.15 or higher

```

After trying to select the Power Manager settings page:

```
Running X session wrapper
Loading profile from /etc/profile
Loading profile from /home/mbpcolin/.profile
Loading resource: /etc/X11/Xresources/x11-common
Loading X session script /etc/X11/Xsession.d/20x11-common_process-args
Loading X session script /etc/X11/Xsession.d/30x11-common_xresources
Loading X session script /etc/X11/Xsession.d/40x11-common_xsessionrc
Loading X session script /etc/X11/Xsession.d/50x11-common_determine-startup
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/60x11-common_localhost
Loading X session script /etc/X11/Xsession.d/60x11-common_xdg_path
Loading X session script /etc/X11/Xsession.d/60xdg-user-dirs-update
Loading X session script /etc/X11/Xsession.d/70gconfd_path-on-session
Loading X session script /etc/X11/Xsession.d/75dbus_dbus-launch
Loading X session script /etc/X11/Xsession.d/80im-switch
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Loading X session script /etc/X11/Xsession.d/90consolekit
Loading X session script /etc/X11/Xsession.d/90x11-common_ssh-agent
Loading X session script /etc/X11/Xsession.d/99x11-common_start
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 13 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 14 overrides entry on line 7
ssh-agent is already running
xfdesktop[1702]: starting up

(xfce4-settings-helper:1706): xfce4-settings-helper-CRITICAL **: Stored Xfconf properties disable all outputs, aborting.
xfce4-settings-helper: Another instance is already running. Leaving...
GNOME_KEYRING_CONTROL=/tmp/keyring-qeGeGK
SSH_AUTH_SOCK=/tmp/keyring-qeGeGK/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-qeGeGK
SSH_AUTH_SOCK=/tmp/keyring-qeGeGK/ssh
GPG_AGENT_INFO=/tmp/keyring-qeGeGK/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-qeGeGK
SSH_AUTH_SOCK=/tmp/keyring-qeGeGK/ssh
GPG_AGENT_INFO=/tmp/keyring-qeGeGK/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-qeGeGK
SSH_AUTH_SOCK=/tmp/keyring-qeGeGK/ssh
GPG_AGENT_INFO=/tmp/keyring-qeGeGK/gpg:0:1

(polkit-gnome-authentication-agent-1:1758): polkit-gnome-1-WARNING **: Failed to register client: The name org.gnome.SessionManager was not provided by any .service files
(xfce4-mixer-plugin:1729): xfce4-mixer-plugin-DEBUG: mixer_plugin->track_label = 'Master'
** Message: applet now removed from the notification area
** (nm-applet:1739): DEBUG: old state indicates that this was not a disconnect 0
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/BasePlugin.py", line 65, in _load
    self.on_load(parent)
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/applet/PulseAudio.py", line 173, in on_load
    raise Exception("PulseAudio too old, required 0.9.15 or higher")
Exception: PulseAudio too old, required 0.9.15 or higher
[3:3:139902625:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
[6:6:140214410:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
[9:9:140707963:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
[12:12:140744568:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
[13:13:140757363:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
[25:25:149748365:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
Xfce power manager is not running
[30:30:227412676:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied

```

It does appear now that I failed to notice something key in there while looking at it the 1st time around, that only shows up the 1st time. Sorry about that...

While it's there if there is something else I may be able to fix that shows in that file, I'm more than happy to have a go.

---

### Post by Atreus10 on 2011-10-16
I'm having the same problem.  Installed 11.10 earlier today, just installed the xfce4 metapackage along with the recommended extras.  I uninstalled nautilus (it was causing problems with xfce and it's file manager).  I wouldn't think that that would cause this problem, but it was a relatively large operation.

Running it with --no-daemon generate this:
```
(xfce4-power-manager:2391): xfce4-power-manager-WARNING **: could not map keysym 1008ffa8 to keycode

The program 'xfce4-power-manager' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadName (named color or font does not exist)'.
  (Details: serial 307 error_code 15 request_code 149 minor_code 11)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

On a whim, I ran apt-get check and update, nothing.

---

### Post by Toz on 2011-10-16
@Jarm1, do you get any error messages when you run:
```
xfce4-power-manager --no-daemon
```
on the command line?

---

### Post by Toz on 2011-10-16
@Atreus10, It looks like a bug. Please refer to the following links:

- [https://bugzilla.xfce.org/show_bug.cgi?id=7999]("https://bugzilla.xfce.org/show_bug.cgi?id=7999")
- [https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/821170]("https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/821170")
- [http://ubuntuforums.org/showthread.php?p=11327476]("http://ubuntuforums.org/showthread.php?p=11327476")

Perhaps you could add your information to the existing launchpad bug report.

---

### Post by Jarm1 on 2011-12-17
Just a quick update, I had uninstalled it once I realized that it was a bug, hoping it would be fixed eventually.

So although I'm not sure of exactly when, it has been fixed. I re-installed xfce4-power-manager after a major round of updates had come around and everything is working fine now.

---

