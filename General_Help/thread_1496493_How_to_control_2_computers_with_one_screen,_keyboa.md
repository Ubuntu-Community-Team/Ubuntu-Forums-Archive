---
title: "How to control 2 computers with one screen, keyboard and mouse?"
date: 2010-05-29
forum: General Help
---

### Post by Muscar on 2010-05-29
I have 2 computers running Ubuntu 10.04, One of them have a screen, keyboard and mouse connected (all wired)

I want to control the other computer in some way, like a virtual PC in a window, via my network or a cable.

Any tutorials on how to do this? (sorry if this is the wrong section)

---

### Post by Darkness Des on 2010-05-29
Have you considered purchasing a KVM Switch? Just tap a button and control is switched to the other computer. There are also virtual KVM Switches that are entirely free and cross platform.

---

### Post by SoFl W on 2010-05-29
Perhaps you just want to use the remote desktop feature of Ubuntu?

---

### Post by HermanAB on 2010-05-29
Howdy,

The standard way to control another machine is with SSH:
$ ssh -C -c blowfish -X user@serveripaddress 'gnome-panel'

SSH is secure and it is very powerful.  It has many more features beyond mere X forwarding.

VNC is a totally insecure way to do it that works, but which will get your machine hacked if you are behind a P&P router (any home router), since it very conveniently opens it up to the wild wild world.  So this one is only good if you are a masochist, or enjoy re-installing your machine at inconvenient and irregular intervals.

---

### Post by SoFl W on 2010-05-29
> **HermanAB said:**
> VNC is a totally insecure way to do it that works, but which will get your machine hacked if you are behind a P&P router (any home router), since it very conveniently opens it up to the wild wild world.  So this one is only good if you are a masochist, or enjoy re-installing your machine at inconvenient and irregular intervals.

If you don't allow incoming connections on your router the local network is safe from the outside world.

---

