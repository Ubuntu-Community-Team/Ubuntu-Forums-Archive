---
title: "input issues, no right click, focus issues"
date: 2010-06-28
forum: General Help
---

### Post by HamletDRC on 2010-06-28
After an update a few days ago and eventually a reboot yesterday, I started experience issues with my mouse track pad and windows. 

I have no right click. My Dell laptop has two ways to right click and neither works. Left click sometimes works. But then it will stop working. If a native Text Field gets focus then all is lost and the mouse doesn't work at all... I can move the pointer but no focus/selection available. Periodically ALT+Tab quits working as well. 

I tried some "mouse issue" solutions from other threads but so far nothing worked. 

Please help, I have a big presentation to give tonight :(

---

### Post by dino99 on 2010-06-28
some ways to follow:

- search for usefull errors logged into .xsession-errors (/home, unhide with ctrl+h) and into: system admin logviewer

- check driver activation: system admin hardware driver

- google around about your Dell model+ubuntu/lucid/or-else+mouse/trackball

- search into synaptic about "dell", you will find several packages you might need (firmware-addon-dell, ...)

---

### Post by HamletDRC on 2010-06-28
Huh, this is in my log, any idea what it means? 


** (mousetweaks:1802): CRITICAL **: cspi_object_unref: assertion `accessible->ref_count > 0' failed


and a bunch of stuff that looks unrelated: 
** (mousetweaks:1802): CRITICAL **: cspi_object_unref: assertion `accessible->ref_count > 0' failed
/usr/bin/checkbox-gtk: line 18:  2066 Killed                  python $CHECKBOX_SHARE/run "$@" $CHECKBOX_SHARE/configs/$(basename $0).ini
** (nm-applet:1763): DEBUG: foo_client_state_changed_cb
** (nm-applet:1763): DEBUG: going for offline with icon: notification-network-ethernet-disconnected
** (nm-applet:1763): DEBUG: going for offline with icon: notification-network-ethernet-disconnected

(nautilus:1772): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

** (nautilus:1772): CRITICAL **: atk_object_initialize: assertion `ATK_IS_OBJECT (accessible)' failed
** (nm-applet:1763): DEBUG: foo_client_state_changed_cb
** (nm-applet:1763): DEBUG: foo_client_state_changed_cb

** (mousetweaks:1802): CRITICAL **: cspi_object_unref: assertion `accessible->ref_count > 0' failed

(gnome-terminal:2533): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x740002f ([ubuntu] i); these messages lack timestamps and therefore suck.



and there are a whole bunch of these: 



(nautilus:1772): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(nautilus:1772): atk-bridge-WARNING **: IOR not set.

(nautilus:1772): atk-bridge-WARNING **: Could not locate registry


This stuff is meaningless to me.

---

### Post by dino99 on 2010-06-28
which ubuntu is used ? (lucid ?)

which desktop ? (gnome, kde, else ?)

is it a fresh install or a dist-upgrade ?

into a console:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo dpkg-reconfigure network-manager
sudo dpkg-reconfigure mousetweaks
sudo dpkg-reconfigure nautilus
sudo dpkg-reconfigure at-spi

---

### Post by HamletDRC on 2010-06-28
I'm on Lucid from a fresh install. worked fine for about 2 weeks. GNome desktop. I didn't do much special.

I ran the commands but they did nothing. 
It is weird, some widgets in windows I can click, and others I cannot. The GNome windows seem to be the worst and require keyboard navigation while Google Chrome seems better and some widgets can be clicked. 

Sorry to vent, but I am on vacation in Prague, with a 1 hour presentation and live coding session to give tonight, and it looks like I'm going to spend the day reinstalling Linux. I am about to cry. :(

---

### Post by dino99 on 2010-06-28
Prague is a nice city, your are lucky ):P

if you google around Dell+ubuntu/lucid you will find a lot of users troubles, so the important things to know are: which model and which graphic card (hope you dont have a ssd in)

---

