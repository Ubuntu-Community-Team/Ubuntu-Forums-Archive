---
title: "how can i delete a desktop such as lxde?"
date: 2010-10-08
forum: General Help
---

### Post by enhu on 2010-10-08
how can i delete a desktop such as lxde?
i've already installed gnome and i'm saving space :D

---

### Post by HermanAB on 2010-10-08
Howdy,

Uninstalling anything is like unscrambling an egg.  This is especially true with desktop systems, since they are extremely complex.  So to be quite frank, I would not even try.  Your best bet is to re-install the system from scratch, but don't format your /home partition. You do have a /home partition right?  If not, now you know why you should.

---

### Post by 3Miro on 2010-10-08
This can take some time, but here is how to do it without reinstalling.

Find the lxde environment package and check out what it depends on. Synaptic can do that for you (on the package properties). Then remove those package one by one. This may not remove the entire DE, but it should cover most of it.

For LXDE the large things will be: lxde panel, openbox, pcfman, leafpad. I don't think it has much more, maybe some dependencies as libraries, but those are probably common to all gtk.

---

### Post by enhu on 2010-10-08
if for example i delete a package will it also delete a common lib?

---

### Post by Spice Weasel on 2010-10-08
sudo aptitude purge lxsession lxappearance lxpanel pcmanfm

---

### Post by enhu on 2010-10-08
thanks all
thanks Spice Weasel

finally saved space. and get rid of leafpad :P

---

