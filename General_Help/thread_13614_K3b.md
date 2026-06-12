---
title: "K3b ?"
date: 2005-02-01
forum: General Help
---

### Post by ThePainter on 2005-02-01
Hi,
A couple of weeks ago I installed UBUNTU and installed k3b.
I had to change my HD and so have just reinstalled ubuntu but I cant install k3b ?

I have tried from the deb link on the k3b page and I have tried from "alien" .rpm.
An old version installs but wont run and the new one wont install because of dependencies.
libid  &  libvorbis0
libid wont install without libvorbis0 and libvorbis0 is already installed ?

Anyone else having probs with this or have a solution ?

---

### Post by Quest-Master on 2005-02-01
Make sure you have universe enabled, and install k3b as you did previously.

However, **NEVER, NEVER, NEVER** sudo to get into k3b. **NEVER** do the following:

sudo k3b

**ALWAYS** do the following:

gksudo k3b

sudo causes k3b to screw your ICEAuthority file, and you won't be able to login to Gnome anymore. I am emphasizing the importance of using gksudo instead since I've had many friends make the mistake and have to reinstall.

Of course, they could've just done some permission changing, but.. let't not go into that.

---

