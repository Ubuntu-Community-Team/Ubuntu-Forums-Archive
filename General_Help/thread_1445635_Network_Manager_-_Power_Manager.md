---
title: "Network Manager - Power Manager"
date: 2010-04-02
forum: General Help
---

### Post by pheebs on 2010-04-02
This is a big question so bear with me. I'm on a iBook G3 PPC.
I've been working on an openbox install from a 9.10 cli install, and I'm almost there. The one thing I am really missing is a network configuration menu.  I'm a big fan of crunchbang (unfortunately they don't have a PPC release), so I went through their network packages, got them (along with nm-applet) and expected it to work. I've tried installing:
```
gnome-network-admin network-manager network-manager-gnome
```I can get the icon to load in stalonetray, but it doesn't identify that the network is active (seeing as I can browse the web).
Is this the correct way to go about it?

The second thing I tried was compiling NetworkManager by extracting, and doing ./configure 
I'm running into the problem where a package: gudev-1.0  cannot be found. I'm stumped on that, my udev is all up to date. 

I haven't got into Power Manager yet (i've installed the packages) but can't see a tray icon. 

Am I going about this wrong?  Is there an easier way?

UPDATE:  After installing some packages, I'm now seeing wireless networks!  But still i'm connected through ethernet and still see it disconnected.

---

### Post by prodigy_ on 2010-04-02
Why don't you remove network manager and use **/etc/network/interfaces** instead? From my personal experience, network manager is trash. It has never functioned reliably.

---

