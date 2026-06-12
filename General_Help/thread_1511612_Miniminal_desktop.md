---
title: "Miniminal desktop"
date: 2010-06-17
forum: General Help
---

### Post by rdejager on 2010-06-17
Hi, I'm working on a kiosk-type system. What it needs to do is boot, auto login as a specific user, display only the Gnome desktop (no icons, etc), and auto start an application.
 
Is this possible (I'm sure it is)? If so, can this be scripted, i.e. without having to use graphical tools like Sabayon.
 
Thanks.

---

### Post by wojox on 2010-06-17
Sure, just download the minimal iso [here]("https://help.ubuntu.com/community/Installation/MinimalCD")

After you've installed it this should give you a basic lightweight desktop

```

sudo apt-get update && sudo apt-get install 
gdm xorg gnome-core gnome-codec-install 
indicator-session-applet update-manager 
firefox-3.5-gnome-support gnome-themes 
network-manager gdebi

```

---

### Post by rdejager on 2010-06-18
Thanks

---

