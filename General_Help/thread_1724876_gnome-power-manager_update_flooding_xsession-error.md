---
title: "gnome-power-manager update flooding xsession-errors"
date: 2011-04-08
forum: General Help
---

### Post by M4570D0N on 2011-04-08
I had a few updates show up today in synaptic. Among them, was an update for gnome-power-manager. Here's the updates from synaptic's history:

Upgraded the following packages:
gnome-power-manager (2.32.0-0ubuntu1) to 2.32.0-0ubuntu1.1
python-cupshelpers (1.2.3+20100723-0ubuntu8.1) to 1.2.3+20100723-0ubuntu8.2
python-gnomeapplet (2.30.0-1ubuntu5) to 2.30.0-1ubuntu5.1
python-gnomedesktop (2.30.0-1ubuntu5) to 2.30.0-1ubuntu5.1
python-gnomekeyring (2.30.0-1ubuntu5) to 2.30.0-1ubuntu5.1
python-gtop (2.30.0-1ubuntu5) to 2.30.0-1ubuntu5.1
python-rsvg (2.30.0-1ubuntu5) to 2.30.0-1ubuntu5.1
python-wnck (2.30.0-1ubuntu5) to 2.30.0-1ubuntu5.1
system-config-printer-common (1.2.3+20100723-0ubuntu8.1) to 1.2.3+20100723-0ubuntu8.2
system-config-printer-gnome (1.2.3+20100723-0ubuntu8.1) to 1.2.3+20100723-0ubuntu8.2
system-config-printer-udev (1.2.3+20100723-0ubuntu8.1) to 1.2.3+20100723-0ubuntu8.2
update-manager (1:0.142.22) to 1:0.142.23
update-manager-core (1:0.142.22) to 1:0.142.23
w3m (0.5.2-6) to 0.5.2-6ubuntu1

Following these updates I now have 
```
(gnome-power-manager:2437): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
```flooding my xsession-errors file, repeating that entry every few seconds. What might be causing this?

---

### Post by scottku on 2011-04-09
I'm seeing the same thing.  But, I'm not 100% certain that I didn't get these messages before the update.

They recently fixed a bug (that I reported about 1 year ago) in gnome-power-manager.  So, perhaps these new messages are a result of that fix:
[https://bugs.launchpad.net/ubuntu/+source/indicator-application/+bug/569273?comments=all](https://bugs.launchpad.net/ubuntu/+source/indicator-application/+bug/569273?comments=all)

---

### Post by lorneboone on 2011-05-06
Bump....

I'm getting the same message in my .xsession-errors log. The file grew to over 60 gigs before I noticed it. Anyone have any ideas?

---

### Post by demilord on 2011-05-10
yes me too I filed it at launchpad sigh..

---

### Post by demilord on 2011-05-10
if anyone knows a work around please let us know..

---

### Post by zephyr707 on 2011-06-29
I just discovered this problem today when a notification popped up saying I had <2gb left on my file system.  found a 12gb .xsession-errors file.  Any solution to this one?  I just rm'd the file, but it'd be great if someone has found a fix for this or maybe it is just sitting in bug purgatory...  

demilord, thanks for filing the bug, I'm going to include it in this post so that it is part of the thread:

[http://bugs.launchpad.net/ubuntu/+source/indicator-application/+bug/780755](http://bugs.launchpad.net/ubuntu/+source/indicator-application/+bug/780755)

thanks
z

---

