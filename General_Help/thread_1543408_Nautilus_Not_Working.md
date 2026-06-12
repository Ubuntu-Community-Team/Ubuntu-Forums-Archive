---
title: "Nautilus Not Working"
date: 2010-08-01
forum: General Help
---

### Post by maniacss on 2010-08-01
Hello. Suddenly nautilus stopped working on my Ubuntu 10.04 64bit. I can't left/right click on the desktop nor open any folder from the 'Places' menu. When I try running nautilus from the terminal here's what I get:

```
 (nautilus:1574): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.24.1/gobject/gtype.c:2706: You forgot to call g_type_init()

(nautilus:1574): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(nautilus:1574): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
Segmentation fault 
```I've already tried deleting all the gnome settings and it didn't help at all:
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity 
```Also, I've tried creating a new user but the problem remains. Right now I've no clue what to do next, I really don't want to reinstall. Any help would be very much appreciated. Thanks.

---

### Post by dino99 on 2010-08-01
as you can see into the first error line: glib2 is broken

so reinstall it with synaptic; you can reinstall nautilus too

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

*** note: be sure to only use genuine ubuntu repo (look into synaptic repo tab, and desactivate non trusted ppa and non Lucid repo if any)

---

### Post by maniacss on 2010-08-01
Thank you. What I actually did yesterday was 
```
 sudo apt-get install --reinstall nautilus 
```After which I did a reboot and Ubuntu started in terminal only mode for some reason. So I did
```
 sudo apt-get install ubuntu-desktop 
```There we're 3 packages missing, so after installing it I did another reboot and everything is working right now :) . 
Also, I've figured out what caused the problem - I was changing the default application icons in /usr/share/applications and after I changed Nautilus's icon with a custom one, everything crashed. Thanks again dino99 for your help. :)

---

