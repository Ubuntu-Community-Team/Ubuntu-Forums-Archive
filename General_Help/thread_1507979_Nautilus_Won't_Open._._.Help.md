---
title: "Nautilus Won't Open. . .Help?"
date: 2010-06-12
forum: General Help
---

### Post by Amaterasu80 on 2010-06-12
Hi ^^ So, I've just been changing some of my icons in /usr/share/applications with the "gksu nautilus" command and now Nautilus won't open at all.

If click any of the options in 'Places' my PC just hangs then does nothing. If I try to open nautilus from the terminal I get the following output:

```
(nautilus:2284): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.24.1/gobject/gtype.c:2706: You forgot to call g_type_init()

(nautilus:2284): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(nautilus:2284): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
Segmentation fault
```

Any ideas?

---

### Post by dino99 on 2010-06-12
sudo dpkg-reconfigure nautilus

or with synaptic: remove purge nautilus (right click) then reinstall

---

### Post by Amaterasu80 on 2010-06-12
Thank's dino99 for your quick reply, worked like a charm! :D

---

### Post by dino99 on 2010-06-12
glad to help you ):P

---

### Post by jmw86069 on 2010-07-20
Just wanted to add one possibility (**sshfs**) since it happened to me just now, and I thought it may help somebody out there.

I frequently use sshfs to mount local network drives into my directory structure, makes it easier to copy things around, and it runs over SSH and all that.

Sometimes sshfs gets stalled somehow, either the network hiccups, or something else, I don't know. Normally I can unmount the sshfs with a command like
```
fusermount -u /mounted_directory
```
But just now when I couldn't get Nautilus to open, I tried the dpkg-reconfigure suggestion above, and I tried killing bonobo-activation-server (from another thread), both to no avail. Then when I tried to "fusermount", the commandline hung. (Ctrl-C didn't kill it.)

So I opened a new terminal prompt and killed the sshfs process with this command:
```
sudo killall -KILL sshfs
```

All of a sudden like 15 Nautiluses opened up! I guess they were all "hung" waiting for the sshfs process too. Anyway, hope this helps someone.

---

