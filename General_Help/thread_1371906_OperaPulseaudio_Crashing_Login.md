---
title: "Opera/Pulseaudio Crashing Login"
date: 2010-01-03
forum: General Help
---

### Post by Saiko Berry on 2010-01-03
Okay well here is what I notice in the syslog

Jan  3 23:52:38 Sai kernel: [ 3914.806177] __ratelimit: 3 callbacks suppressed
Jan  3 23:52:38 Sai kernel: [ 3914.806183] compiz.real[1908]: segfault at 11 ip 08055c2d sp bfccbb70 error 4 in compiz.real[8048000+34000]
Jan  3 23:52:38 Sai kernel: [ 3914.866575] operapluginwrap[2169]: segfault at b66a5030 ip 003cbd1d sp bff5e5d4 error 4 in libpthread-2.10.1.so[3c4000+15000]
Jan  3 23:52:39 Sai console-kit-daemon[750]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `<invalid>'
Jan  3 23:52:39 Sai console-kit-daemon[750]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Jan  3 23:52:39 Sai console-kit-daemon[750]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Jan  3 23:52:39 Sai pulseaudio[4815]: pid.c: Stale PID file, overwriting.
Jan  3 23:52:39 Sai acpid: client 1224[0:0] has disconnected
Jan  3 23:52:39 Sai acpid: client 1224[0:0] has disconnected
Jan  3 23:52:39 Sai acpid: client connected from 4816[0:0]
Jan  3 23:52:40 Sai pulseaudio[4815]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-Xk8Kw1lFSe: Connection refused
Jan  3 23:52:40 Sai pulseaudio[4824]: pid.c: Daemon already running.

These are various other errors Im getting when I log back in.

Jan  3 23:52:58 Sai pulseaudio[4815]: module-x11-xsmp.c: Failed to open connection to session manager: Could not open network socket
Jan  3 23:52:58 Sai pulseaudio[4815]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Jan  3 23:17:02 Sai CRON[3281]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  3 22:47:51 Sai udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan  3 22:47:51 Sai udev-configure-printer: add /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2:1.0
Jan  3 22:47:51 Sai udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.1/usb1/1-2
Jan  3 22:47:51 Sai udev-configure-printer: Device vendor/product is 0409:005A
Jan  3 22:47:51 Sai udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan  3 22:47:51 Sai console-kit-daemon[750]: WARNING: Couldn't read /proc/746/environ: Failed to open file '/proc/746/environ': No such file or directory
Jan  3 22:47:48 Sai bonobo-activation-server (root-1127): could not associate with desktop session: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.
Jan  3 22:47:48 Sai init: kdm main process (1152) terminated with status 1
Jan  3 22:47:48 Sai init: kdm main process ended, respawning
Jan  3 22:47:48 Sai init: kdm main process (1158 ) terminated with status 1
Jan  3 22:47:48 Sai init: kdm main process ended, respawning
Jan  3 22:47:48 Sai init: kdm main process (1160) terminated with status 1
Jan  3 22:47:48 Sai init: kdm main process ended, respawning
Jan  3 22:47:48 Sai init: kdm main process (1164) terminated with status 1
Jan  3 22:47:48 Sai init: kdm main process ended, respawning
Jan  3 22:47:48 Sai init: kdm main process (1166) terminated with status 1
Jan  3 22:47:48 Sai init: kdm main process ended, respawning
Jan  3 22:47:48 Sai init: kdm main process (1168 ) terminated with status 1
Jan  3 22:47:48 Sai init: kdm main process ended, respawning
Jan  3 22:47:48 Sai init: kdm main process (1170) terminated with status 1
Jan  3 22:47:48 Sai init: kdm main process ended, respawning
Jan  3 22:47:48 Sai init: kdm main process (1172) terminated with status 1
Jan  3 22:47:48 Sai init: kdm main process ended, respawning
Jan  3 22:47:48 Sai init: kdm main process (1174) terminated with status 1
Jan  3 22:47:48 Sai init: kdm main process ended, respawning
Jan  3 22:47:48 Sai init: kdm main process (1176) terminated with status 1
Jan  3 22:47:48 Sai init: kdm main process ended, respawning
Jan  3 22:47:48 Sai init: kdm main process (1178 ) terminated with status 1
Jan  3 22:47:48 Sai init: kdm respawning too fast, stopped
Jan  3 22:47:48 Sai gdm-binary[1151]: WARNING: Unable to find users: no seat-id found

It seems starting up gives a ton of errors I can't really isolate. The above boot errors are in no order. I just pasted them all together.

What happens is randomly when Im browsing through videos on youtube, it crashes back to the login screen. Im guessing this has something to do with Opera's plugin/Sound/Pulse Audio. Can anyone tell me how to fix this?

Running Ubuntu Karmic 9.10

---

### Post by Saiko Berry on 2010-01-03
Repduced:

Jan  4 00:38:13 Sai kernel: [ 6649.856474] operapluginwrap[7643]: segfault at b673f030 ip 00148d1d sp bfa06db4 error 4 in libpthread-2.10.1.so[141000+15000]
Jan  4 00:38:13 Sai console-kit-daemon[750]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `(null)'
Jan  4 00:38:13 Sai console-kit-daemon[750]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Jan  4 00:38:13 Sai console-kit-daemon[750]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Jan  4 00:38:13 Sai acpid: client 7147[0:0] has disconnected
Jan  4 00:38:13 Sai acpid: client 7147[0:0] has disconnected
Jan  4 00:38:13 Sai acpid: client connected from 7709[0:0]
Jan  4 00:38:14 Sai acpid: client connected from 7709[0:0]
Jan  4 00:38:22 Sai pulseaudio[7872]: pid.c: Stale PID file, overwriting.
Jan  4 00:38:24 Sai pulseaudio[7872]: module-x11-xsmp.c: X11 session manager not running.
Jan  4 00:38:24 Sai pulseaudio[7872]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Jan  4 00:38:24 Sai kernel: [ 6661.140082] opera[7554]: segfault at 0 ip (null) sp bff7d310 error 4 in libSM.so.6.0.0[110000+7000]

Thats the exact everything that happens when I crash. Its always while watching Youtube or switching to a site with flash sound.

---

### Post by Marrkk on 2010-01-04
Bad news .. seems you're not the only one having this problem.
Pulseaudio is broken in Ubuntu 9.10.
maybe try going to system preferences>sound> (see screenshot)
[http://www.ngohaibac.com/wp-content/uploads/2009/05/sound-preferences.png]("http://www.ngohaibac.com/wp-content/uploads/2009/05/sound-preferences.png")
and testing with the output on any other setting <alsa?> than pulseaudio 

do you get a crash with firefox/knqueror /

---

### Post by Saiko Berry on 2010-01-04
I don't even have that window in my system preferences. I can't find where Pulseaudio is selected for my audio handler.

What sound gui I have in there are;
- Default Sound Card (/usr/bin/asoundconf-gtk)
- Pulse Audio Preferences
- Volume Control

All of which have no selections like you have there.

Testing Firefox crash now.

---

### Post by Marrkk on 2010-01-04
are you using Gnome ? the GUI is there somewhere everytime i try Gnome.
very strange.  the 'default sound card' is the first thing i would change..
to ALSA  .. sorry i'm not much help, i dont use Gnome much

---

### Post by Saiko Berry on 2010-01-04
Gnome is one of the first mistakes im fixing. Its so primative. Guh..
I'm just scared to touch anything about Gnome while using gnome at the same time. xD Otherwise Id use something else.

---

### Post by Saiko Berry on 2010-01-04
I can't seem to duplicate the error using Konqueror, but I want to use Opera because of its ability to block any and all popups so any related fix to the opera flash plugin would be nice.

Edit: Duplicated on Firefox by browsing the Themes section of the add-ons page.

Jan  4 09:03:51 Sai acpid: client 7709[0:0] has disconnected
Jan  4 09:03:51 Sai acpid: client 7709[0:0] has disconnected
Jan  4 09:03:51 Sai acpid: client connected from 2990[0:0]
Jan  4 09:03:52 Sai acpid: client connected from 2990[0:0]
Jan  4 09:04:02 Sai pulseaudio[3156]: pid.c: Stale PID file, overwriting.
Jan  4 09:04:06 Sai pulseaudio[3156]: module-x11-xsmp.c: X11 session manager not running.
Jan  4 09:04:06 Sai pulseaudio[3156]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

I ran a manual lxsession over an existing x11 session just to see if any of the un-initiateable processes could be restored and here is the hash;
```
saiko@Sai:~$ lxsession

** (update-notifier:8389): WARNING **: already running?

Failure: Module initalization failed

(polkit-gnome-authentication-agent-1:8385): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:8385): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

** (polkit-gnome-authentication-agent-1:8385): WARNING **: Unable to register authentication agent: Remote Exception invoking org.freedesktop.PolicyKit1.Authority.RegisterAuthenticationAgent() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session
Cannot register authentication agent: Remote Exception invoking org.freedesktop.PolicyKit1.Authority.RegisterAuthenticationAgent() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session
Has notifications support True
Loading...
Connecting to daemon...
Connected.
Done loading.
no daemon yet
ScreenletsDaemon running ...
CachingBackend: Loading instances from cache
CachingBackend: Loading <RingSensors1>
Creating new entry for RingSensorsScreenlet in /tmp/screenlets/screenlets.saiko.running
ScreenletsDaemon: registered RingSensorsScreenlet
Loading instances in: /home/saiko/.config/Screenlets/RingSensors/default/
File: RingSensors1.ini
/home/saiko/.config/Screenlets/RingSensors/default/RingSensors1
Can't open /proc/acpi/ibm/thermal
Can't open /proc/acpi/ibm/fan
None
Can't open /proc/acpi/ibm/thermal
Can't open /proc/acpi/ibm/fan
LOAD NEW THEME: default
FOUND: /usr/share/screenlets/RingSensors/themes/default
/usr/lib/pymodules/python2.6/screenlets/__init__.py:289: DeprecationWarning: use copy pango.FontDescription.set_family instead
  self.p_fdesc.set_family_static(font)
Set options in RingSensorsScreenlet
LOAD NEW THEME: default
FOUND: /usr/share/screenlets/RingSensors/themes/default
Restored instances from session 'default' ...
CachingBackend: <#RingSensors1> removed!
Removing last instance from session
TODO: remove self.path: /home/saiko/.config/Screenlets/RingSensors/default/
Queue-element <RingSensors1> not found (already removed?)!
screenletsDaemon: unregistered RingSensorsScreenlet
No more screenlets running.
Deleting global tempfile /tmp/screenlets/screenlets.saiko.running

```And this was in syslog

Jan  4 09:39:47 Sai bonobo-activation-server (root-7714): could not associate with desktop session: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.
Jan  4 09:50:41 Sai pulseaudio[4705]: module-x11-xsmp.c: X11 session manager not running.
Jan  4 09:50:41 Sai pulseaudio[4705]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

Its definately a problem with pulseaudio.. hopefully a fix or some light can be shined on this soon.

---

### Post by Saiko Berry on 2010-01-04
I'm starting to think with all these pulseaudio problems, and I wonder why Ubuntu doesnt just use ALSA and completely drop Pulseaudio. I cant seem to find a solution for this anywhere, the only solution it seems is to run all flash anythings through Konqueror. Opera and Firefox both error and crash xsession/x11 it seems..

---

### Post by woodmaster on 2010-01-04
IDK about Opera as I don't use it but I purged pulse audio by:

Originally posted by: nullrend

Here is what I did to remove pulse audio in Karmic:

Code:
$ sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
Code:
$ sudo apt-get autoremove
Code:
$ sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui
Code:
$ sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer
restart your computer!

Notes:
-run gstreamer-properties in terminal to set defaults to alsa (the old system/preferences/sound in jaunty)
This means:
Code:
$ gstreamer-properties
-remove gstreamer0.10-pulseaudio to get sound in totem.
The above commands should have taken care of that, but it never hurts to be sure when talking about the hydra that is PulseAudio.
-gnome-alsamixer is for changing the volume, not an applet but better that nothing
This means you are left without a panel applet to control volume across the board, thanks to the thoughtful efforts of Canonical to shove PulseAudio down our throats. So you need to have something to control audio with:
Code:
$ sudo apt-get install gnome-alsamixer
And something to keep gnome-alsamixer within easy reach, provided by AllTray:
Code:
$ sudo apt-get install alltray
Now, one last word of advice. Usually the best solution is to use aptitude or synaptic to do these moves, but you'll run headfirst into their dependency resolution efforts, which command them to put PulseAudio back in your system when reinstalling gnome-alsamixer. So either you use apt-get or you reconfigure aptitude/synaptic dependency resolution to work the way you want.


PulseAudio is an invasive Hydra...All my sound works fine now and no more pulseaudio errors in my log files

---

### Post by Saiko Berry on 2010-01-04
I think I love you. Fixed, no errors. X11 no longer erroring and Ive yet to get a crash from Opera or Firefux. I'l post here if there are any further problems. Pulseaudio sucks, that is all. :D

---

### Post by jamesisin on 2010-01-04
PA sucks if you don't have it set up correctly.  Like driving a Porsche with knobby ties.

This guide will help you configure PA correctly (if that interests you):

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I am successfully running Opera and PA under 8.04, 8.10, 9.04, and 9.10.  I'm even running sound out through USB to a Decco Pre-Amp.

---

### Post by Saiko Berry on 2010-01-04
No PA just sucks.

Anyways, Opera crashed again. It didnt seem to log anything though..

Jan  4 17:39:54 Sai kernel: [ 3863.853219] __ratelimit: 3 callbacks suppressed
Jan  4 17:39:54 Sai kernel: [ 3863.853225] operapluginwrap[2551]: **segfault** at b6d70030 ip 00490d1d sp bfb605d4 error 4 in libpthread-2.10.1.so[489000+15000]
Jan  4 17:39:54 Sai console-kit-daemon[830]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `<invalid>'
Jan  4 17:39:54 Sai console-kit-daemon[830]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Jan  4 17:39:54 Sai console-kit-daemon[830]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Jan  4 17:39:55 Sai acpid: client 1212[0:0] has disconnected
Jan  4 17:39:55 Sai acpid: client 1212[0:0] has disconnected
Jan  4 17:39:55 Sai acpid: client connected from 6443[0:0]
Jan  4 17:39:55 Sai acpid: client connected from 6443[0:0]

---

### Post by jamesisin on 2010-01-04
Funny, works perfectly here.  And Opera isn't crashing for me.

---

