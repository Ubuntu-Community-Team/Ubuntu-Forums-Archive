---
title: "Network-manager-gnome"
date: 2006-06-02
forum: General Help
---

### Post by Jingo on 2006-06-02
Just did a fresh install of the Final dapper.

I have installed network-manager

sudo aptitude install network-manager-gnome

Now, when I start up gnome its giving me this:
"The NetworkManager applet could not find some required resources.  It cannot continue."

What resources? What could be missing?

Network-manager is startet ok, only the applet won't start.

---

### Post by asimon on 2006-06-02
This problem is filed as [Bug #45609](https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/45609). Have a look at the comment of Jun Kobayashi, he posted a workaround. Maybe that works for you.

---

### Post by predator29 on 2006-06-02
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor

---

### Post by Jingo on 2006-06-02
thanks... works

---

### Post by predator29 on 2006-06-02
Ur welcome :) I hade the same problem...

---

### Post by tim-e on 2006-09-15
> **predator29 said:**
> sudo gtk-update-icon-cache -f /usr/share/icons/hicolorSweet, thanks!  (bump)

---

