---
title: "Additional drivers (jockey-text and jockey-gtk) crashes"
date: 2012-05-12
forum: General Help
---

### Post by callampen on 2012-05-12
Hi, trying to install new drivers for my wireless card on ubuntu 12.04. Additional drivers, in all its forms, are crashing on me. 

The first time I ran additional drivers, the "searching for additional drivers" popup appeared, and took a long time. I finally left and came back in 30 minutes, and it was gone, with no listing of drivers. When clicking on the launch icon, it didn't work.

A bit of googling to learn the comman, jockey-gtk, and the command line version, jockey-text. I ran both, which give a similar error message. The error for 
Additional drivers showed its "searching for drivers" .

The error for jockey-gtk is:\
> 
$ sudo jockey-gtk                     

(jockey-gtk:2671): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed

(jockey-gtk:2671): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed
ERROR:dbus.proxies:Introspect error on :1.73:/DeviceDriver: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 418, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 468, in run
    self.ui_show_main()
  File "/usr/bin/jockey-gtk", line 94, in ui_show_main
    self.update_tree_model()
  File "/usr/bin/jockey-gtk", line 274, in update_tree_model
    for h_id in self.get_displayed_handlers():
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 819, in get_displayed_handlers
    return self.backend().available(self.argv_options.mode)
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 130, in backend
    self._check_repositories()
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 842, in _check_repositories
    if self._dbus_iface.has_repositories():
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.Any idea why this would happen? I've found postings on ask ubuntu that looks like the same error: [Ask ubuntu post]("http://askubuntu.com/questions/134354/additional-drivers-application-does-not-work") , but there are no answers :-(.

Other, probably unrelated, things:

[LIST]
[*]the wireless card I'm trying to update is WN311B. When enabling wireless, the computer slows until it freezes. I have wireless disabled via the drop-down menu as I'm running these programs.
[*]Running from Z-shell.
[*]I had 11.10, and upgraded. I don't recall if I ever ran additional drivers in 11.10, and if this is an inherited issue.
[*]I'm running on a desktop (i.e. not a laptop)
[/LIST]
Thanks for any help.

---

### Post by concretewallflower on 2012-07-09
Hi Callampen.  Did you ever figure this out?  I'm having the same issue!  Or - can anyone else help out here?
Thanks!

---

### Post by callampen on 2012-07-09
No I didn't, sorry. I just am using the a hard connection. Its annoying, so  I'd love to hear if there is another solution.

---

### Post by uconvert on 2012-12-01
I have the same problem - admittedly with a legacy nvidia (173). Just an FYI, this occurs on Xubuntu also, but not on Lubuntu. I am just about done with Canonical, they seem less willing to fix bugs on the LTS versions than when I first converted to Ubuntu 6.06 LTS. This 6 month release cycle combined with the Unity/Gnome 3 fiasco has had me searching the Distrowatch for alternates. I am currently remastering the Gnome Shell Remix as a "retro" ubuntu similar to Jaunty. Getting rid of that purple splash is no small feat! Anyhow, good luck with a fix, no one seems to care about these kinds of bugs anymore.:(

---

### Post by miquelb on 2013-01-07
Hi all, I had then same problem. I solved it this way:
1. Open Synaptics
2. From there remove completely jockey-gtk and jockey-common
3. Re-install from synaptics both packages

Hope that solves your problem as well

---

### Post by umity on 2013-06-27
Thanks, this also solved my problem :)

> **miquelb said:**
> Hi all, I had then same problem. I solved it this way:
1. Open Synaptics
2. From there remove completely jockey-gtk and jockey-common
3. Re-install from synaptics both packages

Hope that solves your problem as well

---

### Post by Handssolow on 2014-04-06
As far I'm concerned jockey-gtk here hasn't worked for many months on my son's PC. It's running 12.04 LTS and my guess it's unlikely it will ever be fixed. As far as the developers are concerned, the caravan has moved on, jockey has been superseded by software-properties, leaving behind those still using 12.04 and jockey-gtk in System Tools>System Settings>Additional Drivers.

...so much for the promise of long term support.

[http://ubuntuforums.org/showthread.php?t=2178677](http://ubuntuforums.org/showthread.php?t=2178677)

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/946973](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/946973)

---

