---
title: "Can't start nautilus anymore"
date: 2010-10-16
forum: General Help
---

### Post by geoffjay on 2010-10-16
I may have tweaked one too many settings on a new install of 10.10, as the title suggests I can no longer start nautilus. It happened shortly after enabling RGBA support, I've got the following PPAs enabled that might have something to do with my problem:

deb [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) maverick main
deb [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) maverick main
deb [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu) maverick main
deb [http://ppa.launchpad.net/elementaryart/ppa/ubuntu](http://ppa.launchpad.net/elementaryart/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/elementaryart/ppa/ubuntu](http://ppa.launchpad.net/elementaryart/ppa/ubuntu) maverick main
deb [http://ppa.launchpad.net/erik-b-andersen/rgba-gtk/ubuntu](http://ppa.launchpad.net/erik-b-andersen/rgba-gtk/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/erik-b-andersen/rgba-gtk/ubuntu](http://ppa.launchpad.net/erik-b-andersen/rgba-gtk/ubuntu) maverick main

When I try to start it from a terminal I get:

$ nautilus
(nautilus:1935): Unique-DBus-WARNING **: Error while sending message: Message did not receive a reply (timeout by message bus)

$ dbus-launch nautilus
Initializing nautilus-open-terminal extension
Initializing nautilus-gdu extension

(nautilus:2060): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed
...
...
** (nautilus:2060): CRITICAL **: nautilus_view_factory_lookup: assertion `id != NULL' failed
Segmentation fault

I've seen this problem in launchpad but not for the last couple of releases, if anyone's fixed this or knows how to dig deeper I'd appreciate the help. Thanks.

---

### Post by hhh on 2010-10-16
> **geoffjay said:**
> It happened shortly after enabling RGBA support
I bet it happened immediately after. I have RGBA running on Lucid, but the instructions I've seen on WebUpd8 and maybe OMGUbuntu (and I think on these forums too) aren't quite accurate.

What worked for me was to have Nautilus Elementary working and fully updated before trying to enable RGBA. Try removing RGBA support, then upgrading Nautilus, then reinstalling the RGBA PPA. You can download PCManFM to manage files until you have Nautilus running again (it's in Synaptic Package Manager).

Instructions for removing RGBA are part of the post at WebUpd8 (near the end under Revert All Changes)...
[http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html](http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html)

Remove your Elementary PPA as well, then install the latest Elementary...
[http://www.webupd8.org/2010/09/install-nautilus-elementary-in-ubuntu.html](http://www.webupd8.org/2010/09/install-nautilus-elementary-in-ubuntu.html)

Then reinstall the RGBA PPA and other files. Hope it works out for you.

-edit- Oh yeah... Number One in the hood, G.

---

### Post by geoffjay on 2010-10-17
Yep, doing a ppa-purge on the RGBA PPA fixed it. Thanks.

---

