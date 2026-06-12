---
title: "Slight Hanging"
date: 2010-05-02
forum: General Help
---

### Post by Fuel90 on 2010-05-02
I'm having a problem with some slight hanging in 10.04, sometimes when I open programs or click on things that are already open from the task bar- the system will freeze (still can move mouse) for ~2 to ~3 seconds. The "loading" mouse icon does stop spinning during this time also.

Any help would be awesome!

Thanks!

---

### Post by dino99 on 2010-05-02
need to look at .xsession-errors (/home , unhide file to see it, in top menu), and logs (system admin log viewer)

sudo dpkg --configure -a 
sudo apt-get install -f

---

### Post by Fuel90 on 2010-05-02
> **dino99 said:**
> need to look at .xsession-errors (/home , unhide file to see it, in top menu), and logs (system admin log viewer)

sudo dpkg --configure -a 
sudo apt-get install -f
Can you tell me exactly on how to get to what you need? I tried those terminal commands and they didn't do anything....but I don't know how to get to the ".xsession-errors".

Thanks for the quick reply!

---

### Post by Fuel90 on 2010-05-02
Bumpity Bump

---

### Post by dino99 on 2010-05-02
easy i'm not seating waiting for your comments only :P

on top panel, click on the second menu title (shortcuts or so), that will open the file browser (nautilus): here look at that hiden file .Xsession-errors ( unhide it into menu)

---

### Post by Fuel90 on 2010-05-02
> **dino99 said:**
> easy i'm not seating waiting for your comments only :P

on top panel, click on the second menu title (shortcuts or so), that will open the file browser (nautilus): here look at that hiden file .Xsession-errors ( unhide it into menu)

> /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-iubccE
SSH_AUTH_SOCK=/tmp/keyring-iubccE/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-iubccE
SSH_AUTH_SOCK=/tmp/keyring-iubccE/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-iubccE
SSH_AUTH_SOCK=/tmp/keyring-iubccE/ssh
** Message: adding killswitch idx 2 state 1
** Message: killswitch 2 is 1
** Message: killswitches state 1
gnome-session[1401]: WARNING: Could not launch application 'Screenlets%20Daemon.desktop': Unable to start application: Failed to execute child process "/usr/share/screenlets-manager/screenlets-daemon.py" (No such file or directory)
** (bluetooth-applet:1466): DEBUG: Unhandled UUID 0000111b-0000-1000-8000-00805f9b34fb (0x111b)
** Message: killswitch 2 is 1
** Message: killswitches state 1

(polkit-gnome-authentication-agent-1:1477): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1477): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

** (gsynaptics-init:1480): WARNING **: Using synclient

(gnome-power-manager:1470): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.0/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0xa01f448'
** (nm-applet:1485): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1485): DEBUG: foo_client_state_changed_cb
Initializing nautilus-gdu extension
Starting gtk-window-decorator
I/O warning : failed to load external entity "/home/brian/.compiz/session/102437db022eaef692127281441784382700000014010030"
/usr/bin/compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/blueman/plugins/AppletPlugin.py", line 105, in _load
    self.on_load(applet)
  File "/usr/lib/python2.6/dist-packages/blueman/plugins/applet/PulseAudio.py", line 115, in on_load
    if int(version.split(".")[2]) < 15:
ValueError: invalid literal for int() with base 10: '21-63-gd3efa-dirty'
[ERROR]: Option "edge_flip_pointer" already defined
[ERROR]: Option "edge_flip_window" already defined
[ERROR]: Option "edge_flip_dnd" already defined
[ERROR]: Option "flip_time" already defined
[ERROR]: Option "raise_on_rotate" already defined
[ERROR]: Option "initiate_button" already defined
[ERROR]: Option "rotate_left_key" already defined
[ERROR]: Option "rotate_left_button" already defined
[ERROR]: Option "rotate_right_key" already defined
[ERROR]: Option "rotate_right_button" already defined
[ERROR]: Option "rotate_left_window_key" already defined
[ERROR]: Option "rotate_left_window_button" already defined
[ERROR]: Option "rotate_right_window_key" already defined
[ERROR]: Option "rotate_right_window_button" already defined
[ERROR]: Option "rotate_to_key" already defined
[ERROR]: Option "rotate_window_key" already defined
[ERROR]: Option "rotate_flip_left_edge" already defined
[ERROR]: Option "rotate_flip_right_edge" already defined
[ERROR]: Option "rotate_to_1_key" already defined
[ERROR]: Option "rotate_to_2_key" already defined
[ERROR]: Option "rotate_to_3_key" already defined
[ERROR]: Option "rotate_to_4_key" already defined
[ERROR]: Option "rotate_to_5_key" already defined
[ERROR]: Option "rotate_to_6_key" already defined
[ERROR]: Option "rotate_to_7_key" already defined
[ERROR]: Option "rotate_to_8_key" already defined
[ERROR]: Option "rotate_to_9_key" already defined
[ERROR]: Option "rotate_to_10_key" already defined
[ERROR]: Option "rotate_to_11_key" already defined
[ERROR]: Option "rotate_to_12_key" already defined
[ERROR]: Option "rotate_to_1_window_key" already defined
[ERROR]: Option "rotate_to_2_window_key" already defined
[ERROR]: Option "rotate_to_3_window_key" already defined
[ERROR]: Option "rotate_to_4_window_key" already defined
[ERROR]: Option "rotate_to_5_window_key" already defined
[ERROR]: Option "rotate_to_6_window_key" already defined
[ERROR]: Option "rotate_to_7_window_key" already defined
[ERROR]: Option "rotate_to_8_window_key" already defined
[ERROR]: Option "rotate_to_9_window_key" already defined
[ERROR]: Option "rotate_to_10_window_key" already defined
[ERROR]: Option "rotate_to_11_window_key" already defined
[ERROR]: Option "rotate_to_12_window_key" already defined
[ERROR]: Option "invert_y" already defined
[ERROR]: Option "sensitivity" already defined
[ERROR]: Option "acceleration" already defined
[ERROR]: Option "snap_top" already defined
[ERROR]: Option "snap_bottom" already defined
[ERROR]: Option "speed" already defined
[ERROR]: Option "timestep" already defined
[ERROR]: Option "zoom" already defined
** (nm-applet:1485): DEBUG: foo_client_state_changed_cb
evolution-alarm-notify-Message: Setting timeout for 30346 1272844800 1272814454
evolution-alarm-notify-Message:  Sun May  2 20:00:00 2010

evolution-alarm-notify-Message:  Sun May  2 11:34:14 2010

Updating...
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'SSL connection timeout')
** (update-notifier:1946): DEBUG: Skipping reboot required
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'SSL connection timeout')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 45925 out of 119711 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'SSL connection timeout')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'SSL connection timeout')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'SSL connection timeout')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')

(gnome-terminal:2210): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'SSL connection timeout')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead
Loading configuration plugins
Using gconf config backend
Using gconf config backend

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1704): Gdk-WARNING **: XID collision, trouble ahead
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 41581 out of 119007 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'SSL connection timeout')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')

There ya go!

---

### Post by dino99 on 2010-05-02
so as you can see, there are some crappy apps pushing the mess there.

so remove/purge them first with synaptic : pulseaudio, gwibber, some applets (reread the logs), you will reinstall later when errors will have desappeared.

be sure you only have lucid genuine repo, no other third party or ppa

then update, and: sudo apt-get install -f

till apps flood logs with errors ( dont worry about "xid collision" at time), remove/purge them and reinstall them again.

you need to have logs with less errors (eliminate them one by one)

" application 'Screenlets%20Daemon.desktop " where this app come from ?

sudo dpkg-reconfigure gnome-session

---

### Post by Fuel90 on 2010-05-02
> **dino99 said:**
> so as you can see, there are some crappy apps pushing the mess there.

so remove/purge them first with synaptic : pulseaudio, gwibber, some applets (reread the logs), you will reinstall later when errors will have desappeared.

be sure you only have lucid genuine repo, no other third party or ppa

then update, and: sudo apt-get install -f

till apps flood logs with errors ( dont worry about "xid collision" at time), remove/purge them and reinstall them again.

you need to have logs with less errors (eliminate them one by one)

" application 'Screenlets%20Daemon.desktop " where this app come from ?

sudo dpkg-reconfigure gnome-session

Ok thanks, I'll get rid of them one by one.

---

### Post by Fuel90 on 2010-05-02
Cleaned up some stuff but I still get some hanging.

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-NIYI59
SSH_AUTH_SOCK=/tmp/keyring-NIYI59/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-NIYI59
SSH_AUTH_SOCK=/tmp/keyring-NIYI59/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-NIYI59
SSH_AUTH_SOCK=/tmp/keyring-NIYI59/ssh
gnome-session[1383]: WARNING: Could not launch application 'Screenlets%20Daemon.desktop': Unable to start application: Failed to execute child process "/usr/share/screenlets-manager/screenlets-daemon.py" (No such file or directory)
** Message: adding killswitch idx 2 state 1
** Message: killswitch 2 is 1
** Message: killswitches state 1

(polkit-gnome-authentication-agent-1:1457): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1457): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** (bluetooth-applet:1448): DEBUG: Unhandled UUID 0000111b-0000-1000-8000-00805f9b34fb (0x111b)
** Message: killswitch 2 is 1
** Message: killswitches state 1

** (gsynaptics-init:1459): WARNING **: Using synclient

(gnome-power-manager:1450): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.0/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x9d84390'
** (nm-applet:1463): DEBUG: old state indicates that this was not a disconnect 0
Starting gtk-window-decorator
Initializing nautilus-gdu extension
** (nm-applet:1463): DEBUG: foo_client_state_changed_cb
I/O warning : failed to load external entity "/home/brian/.compiz/session/10260ea20840f14ded127284463350466800000013830030"
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/blueman/plugins/AppletPlugin.py", line 105, in _load
    self.on_load(applet)
  File "/usr/lib/python2.6/dist-packages/blueman/plugins/applet/PulseAudio.py", line 115, in on_load
    if int(version.split(".")[2]) < 15:
ValueError: invalid literal for int() with base 10: '21-63-gd3efa-dirty'
/usr/bin/compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

(nm-applet:1463): Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
[ERROR]: Option "edge_flip_pointer" already defined
[ERROR]: Option "edge_flip_window" already defined
[ERROR]: Option "edge_flip_dnd" already defined
[ERROR]: Option "flip_time" already defined
[ERROR]: Option "raise_on_rotate" already defined
[ERROR]: Option "initiate_button" already defined
[ERROR]: Option "rotate_left_key" already defined
[ERROR]: Option "rotate_left_button" already defined
[ERROR]: Option "rotate_right_key" already defined
[ERROR]: Option "rotate_right_button" already defined
[ERROR]: Option "rotate_left_window_key" already defined
[ERROR]: Option "rotate_left_window_button" already defined
[ERROR]: Option "rotate_right_window_key" already defined
[ERROR]: Option "rotate_right_window_button" already defined
[ERROR]: Option "rotate_to_key" already defined
[ERROR]: Option "rotate_window_key" already defined
[ERROR]: Option "rotate_flip_left_edge" already defined
[ERROR]: Option "rotate_flip_right_edge" already defined
[ERROR]: Option "rotate_to_1_key" already defined
[ERROR]: Option "rotate_to_2_key" already defined
[ERROR]: Option "rotate_to_3_key" already defined
[ERROR]: Option "rotate_to_4_key" already defined
[ERROR]: Option "rotate_to_5_key" already defined
[ERROR]: Option "rotate_to_6_key" already defined
[ERROR]: Option "rotate_to_7_key" already defined
[ERROR]: Option "rotate_to_8_key" already defined
[ERROR]: Option "rotate_to_9_key" already defined
[ERROR]: Option "rotate_to_10_key" already defined
[ERROR]: Option "rotate_to_11_key" already defined
[ERROR]: Option "rotate_to_12_key" already defined
[ERROR]: Option "rotate_to_1_window_key" already defined
[ERROR]: Option "rotate_to_2_window_key" already defined
[ERROR]: Option "rotate_to_3_window_key" already defined
[ERROR]: Option "rotate_to_4_window_key" already defined
[ERROR]: Option "rotate_to_5_window_key" already defined
[ERROR]: Option "rotate_to_6_window_key" already defined
[ERROR]: Option "rotate_to_7_window_key" already defined
[ERROR]: Option "rotate_to_8_window_key" already defined
[ERROR]: Option "rotate_to_9_window_key" already defined
[ERROR]: Option "rotate_to_10_window_key" already defined
[ERROR]: Option "rotate_to_11_window_key" already defined
[ERROR]: Option "rotate_to_12_window_key" already defined
[ERROR]: Option "invert_y" already defined
[ERROR]: Option "sensitivity" already defined
[ERROR]: Option "acceleration" already defined
[ERROR]: Option "snap_top" already defined
[ERROR]: Option "snap_bottom" already defined
[ERROR]: Option "speed" already defined
[ERROR]: Option "timestep" already defined
[ERROR]: Option "zoom" already defined
** (nm-applet:1463): DEBUG: foo_client_state_changed_cb
evolution-alarm-notify-Message: Setting timeout for 133 1272844800 1272844667
evolution-alarm-notify-Message:  Sun May  2 20:00:00 2010

evolution-alarm-notify-Message:  Sun May  2 19:57:47 2010

Updating...
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
/usr/share/software-center/softwarecenter/apt/aptcache.py:40: GtkWarning: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
  gtk.main_iteration()
** (update-notifier:1968): DEBUG: Skipping reboot required
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1272844800
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86399 1272931200 1272844801
evolution-alarm-notify-Message:  Mon May  3 20:00:00 2010

evolution-alarm-notify-Message:  Sun May  2 20:00:01 2010

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')

(gnome-terminal:2201): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')

(gnome-terminal:2432): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (28, 'Operation timed out after 15000 milliseconds with 0 bytes received')
```

---

