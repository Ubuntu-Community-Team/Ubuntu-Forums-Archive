---
title: "nautilus-sendto and bluetooth plugin"
date: 2006-02-17
forum: General Help
---

### Post by cronholio on 2006-02-17
I set up Bluetooth and sending files from my mobile to the computer works. However, I have no way to do it the other way around. In older versions of gnome-bluetooth there used to be an entry in the Nautilus right-click menu.

In the changelog for gnome-bluetooth 0.6.0 it states that:

>  * Remove the nautilus extension, sending files over Bluetooth devices is now handled though nautilus-sendto (Bastien Nocera)

That doesn't seem to work in Breezy from the start. Only the Evolution and Gaim plugins are there. Did I miss something?

Or is it possible to do it by issuing a command from the terminal? In this case, I could use nautilus-actions to integrate it in the right-click menu.

Any help is appreciated.

---

### Post by cronholio on 2006-02-17
Okay, I'll just reply myself. There is apparently a bug:

[https://launchpad.net/distros/ubuntu/+source/nautilus-sendto/+bug/23217](https://launchpad.net/distros/ubuntu/+source/nautilus-sendto/+bug/23217)

Breezy ships with nautilus-sendto 0.4. The bug is fixed in 0.5. See here:

[http://mail.gnome.org/archives/gnome-announce-list/2005-December/msg00049.html](http://mail.gnome.org/archives/gnome-announce-list/2005-December/msg00049.html)

Unfortunately, 0.5 depends on Gnome 2.13.

There is a workaround though: I found out that you can send files to Bluetooth devices from the command line using "gnome-obex-send", which you can add to the nautilus-actions menu.

---

