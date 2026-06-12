---
title: "Lucid Can`t login to Gnome"
date: 2010-07-03
forum: General Help
---

### Post by tretiy3 on 2010-07-03
After installing updates, a can`t login to Gnome. I see only purple screen. I was googling for it for several hours, but nothing helps me. 
pressing ctl-alt-f1 just before login, i can start gnone-panel as root. this brings me full functionallity, but only as root :( (and login screen is still there - on the desctop)

Things i`ve allready tried :

[LIST]
[*]reinstall gnome-panel, gnome-session
[*]*killall gnome*-keyring-manager just after login
[*]have enough disk space
[*]use noapic acpi-off splash quiet etc in grub command line
[*]remove intel_drv.so from the system
[*]all files in ~/ has owned by `user`, not by root
[/LIST]
Can suppose only the problems with video driver.
May be something else?
Thanks

---

### Post by quixote on 2010-07-06
Have you already tried this: boot into recovery mode, select "root shell with networking" (have an ethernet cable attached to the computer), and then, once you're at the command prompt, type 
```
dpkg --configure -a
``` (You don't need "sudo" because that's already a root shell.) That should fix broken packages.  Although sometimes it doesn't.  If it's still messed up, come back with what the new errors or error messages are.

---

### Post by tretiy3 on 2010-07-06
Thanks for your message.
No, it does not work :(
here are some logs:
**~/.xsession-errors**
[I]/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
gnome-session[1773]: WARNING: No required applications specified
GNOME_KEYRING_CONTROL=/tmp/keyring-ya5T65
SSH_AUTH_SOCK=/tmp/keyring-ya5T65/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-ya5T65
SSH_AUTH_SOCK=/tmp/keyring-ya5T65/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-ya5T65
SSH_AUTH_SOCK=/tmp/keyring-ya5T65/ssh

(polkit-gnome-authentication-agent-1:1824): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1824): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:1823): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x90082b8'
Traceback (most recent call last):
  File "/usr/share/system-config-printer/applet.py", line 20, in <module>
    import cups
ImportError: No module named cups
evolution-alarm-notify-Message: Setting timeout for 10898 1278460800 1278449902
evolution-alarm-notify-Message:  Wed Jul  7 03:00:00 2010

evolution-alarm-notify-Message:  Tue Jul  6 23:58:22 2010

gnome-session[1773]: WARNING: Could not launch application 'update-notifier.desktop': Unable to start application: Failed to execute child process "update-notifier" (No such file or directory)
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-power-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.


[/I][B]
/var/log/gdm/:0-freeter.log[/B][I]


`value != NULL' failed

(metacity:1117): GConf-CRITICAL **: gconf_value_get_string: assertion `value != NULL' failed

(metacity:1117): GConf-CRITICAL **: gconf_value_get_string: assertion `value != NULL' failed

(metacity:1117): GConf-CRITICAL **: gconf_value_get_string: assertion `value != NULL' failed

(metacity:1117): GConf-CRITICAL **: gconf_value_get_string: assertion `value != NULL' failed

(metacity:1117): GConf-CRITICAL **: gconf_value_get_string: assertion `value != NULL' failed

(metacity:1117): GConf-CRITICAL **: gconf_value_get_string: assertion `value != NULL' failed

(metacity:1117): GConf-CRITICAL **: gconf_value_get_string: assertion `value != NULL' failed

(metacity:1117): GConf-CRITICAL **: gconf_value_get_string: assertion `value != NULL' failed

(metacity:1117): GConf-CRITICAL **: gconf_value_get_string: assertion `value != NULL' failed

(metacity:1117): GConf-CRITICAL **: gconf_value_get_string: assertion `value != NULL' failed
Window manager warning: Failed to read saved session file /var/lib/gdm/.config/metacity/sessions/10470900f14f3d436412784495818196000000010530006.ms: Failed to open file '/var/lib/gdm/.config/metacity/sessions/10470900f14f3d436412784495818196000000010530006.ms': No such file or directory
** (process:1119): DEBUG: Greeter session pid=1119 display=:0.0 xauthority=/var/run/gdm/auth-for-gdm-0pFgdb/database

(gnome-power-manager:1118): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x94c9f30'

** (gnome-power-manager:1118): WARNING **: Either HAL or DBUS are not working!

** (gnome-power-manager:1118): WARNING **: proxy failed

** (gnome-power-manager:1118): WARNING **: failed to get Computer root object

** (gnome-power-manager:1118): WARNING **: proxy NULL!!
gdm-simple-greeter[1119]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1400046 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1400046 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

** (ck-history:1239): WARNING **: Unable to parse session added event: sea1278449511.183 type=SEAT_ADDED : seat-id='Seat1' seat-kind=0

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1400046 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

(gnome-power-manager:1118): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!

[/I][B]/var/log/gdm/:0.log

[/B][I](II) AIGLX: Resuming AIGLX clients after VT switch
(EE) intel(0): Couldn't create pixmap for fbcon
(II) intel(0): EDID vendor "SNY", prod id 9216
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) A4Tech PS/2+USB Mouse: Device reopened after 1 attempts.
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) AIGLX: Resuming AIGLX clients after VT switch
(EE) intel(0): Couldn't create pixmap for fbcon
(II) intel(0): EDID vendor "SNY", prod id 9216
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) A4Tech PS/2+USB Mouse: Device reopened after 1 attempts.
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) AIGLX: Suspending AIGLX clients for VT switch[/I][B]

/var/log/syslog

[/B][I]Jul  6 23:58:35 aganzha-desktop acpid: client 898[0:0] has disconnected
Jul  6 23:58:35 aganzha-desktop kernel: [  350.713348] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Jul  6 23:58:35 aganzha-desktop acpid: client connected from 898[0:0]
Jul  6 23:58:35 aganzha-desktop acpid: 1 client rule loaded
Jul  6 23:58:50 aganzha-desktop gnome-session[1773]: WARNING: Could not launch application 'update-notifier.desktop': Unable to start application: Failed to execute child process "update-notifier" (No such file or directory)
Jul  6 23:59:42 aganzha-desktop acpid: client 898[0:0] has disconnected
Jul  6 23:59:42 aganzha-desktop kernel: [  417.197508] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Jul  6 23:59:42 aganzha-desktop acpid: client connected from 898[0:0]
Jul  6 23:59:42 aganzha-desktop acpid: 1 client rule loaded
Jul  6 23:59:43 aganzha-desktop anacron[950]: Job `cron.daily' terminated
Jul  6 23:59:43 aganzha-desktop anacron[950]: Normal exit (1 job run)

[/I]I have no any idea :(
As i say before, prior to login, a can start gnome-panel from shell as root, and all damn things are work! May be some file became owned by root???

---

### Post by quixote on 2010-07-06
Yikes!  :shock:  That looks like gnome is pretty well stuffed for that user.  I have no more idea than you do about how to really fix this.  The only thing I could do, if it was me, is try two different reinstalls.  One: just gnome and Two: the whole operating system.  Fair warning: I'm just guessing here.  I haven't had to do this for myself

You could back up your data first by booting from a livecd, finding the directories you're interested in, and copying them to removable media.  You could also do it when you're root, of course, but then all the copied files will be owned by root, and you probably don't want that.  If you use Thunderbird, mozilla keeps your mail directories by default under .mozilla-thunderbird, and your firefox bookmarks and settings under .mozilla, so you'd probably want those two as well.

1) Try to get a fresh gnome:  Create a new user. System > Administration > Users & Groups, or, command line: ```
sudo useradd *newuser*
sudo passwd *newuser*
```and the prompt will then ask for a new password for that user.  Then try logging in as that newuser, and see if that gets you a normal graphical login.  If yes, you could try removing the three gnome directories in your olduser, and copying in the three new ones from newuser:```
rm -rf /home/olduser/.gnome*
cp -a /home/newuser/.gnome /home/olduser/.gnome
cp -a /home/newuser/.gnome2 /home/olduser/.gnome2
cp -a /home/newuser/.gnome2_private /home/olduser/.gnome2_private
```Without any gnome directories, I'm pretty sure you won't be able to log in, so make sure you've replaced the directories with new ones before leaving the computer!  Then logout and login as olduser (or reboot) and see whether it now works.  

Alternatively, you could copy the directories you care about to newuser's home and use that login instead. If you did that, then for sudo to work, newuser would have to be added to the admin group: ```
sudo usermod -G admin -a 'newuser'
```

There may be other or much better things you could try before reinstalling.  For me, if that didn't work, all I'd know to do next is just reinstall. :(

---

### Post by tretiy3 on 2010-07-10
thanks for your help anyway.
i found some "solution" - here [http://ubuntuforums.org/showthread.php?t=1456605](http://ubuntuforums.org/showthread.php?t=1456605)
when my machine stuck after login? i switch to terminal and type metacity --replace
sfter, switch to 1 more terminal and type gnome-panel
my system is working, but appearance is little bit ugly :(
better than nothing.
i still have no desktop. it all right with the ~/Descktop but nothing appears on the screen (no any icons)

---

### Post by quixote on 2010-07-10
Sounds like the workaround is just barely adequate. The linked thread implies that this is some kind of bug in Lucid.  It sounds pretty serious, so presumably they'll fix it.  (Although I was one of the people caught by the 64-bit bug in jaunty which corrupted the filesystem and caused data loss, and for something that earth-shattering (as far as I was concerned) they calmly waited till Karmic to fix it!) 

 Did you try applying the fix with the compiz.real link like the one commenter recommended?  That is supposed to be the bug workaround, so if it doesn't work, you may want to get on that thread and mention it.

---

