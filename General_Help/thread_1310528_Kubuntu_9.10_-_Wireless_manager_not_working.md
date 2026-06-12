---
title: "Kubuntu 9.10 - Wireless manager not working"
date: 2009-11-01
forum: General Help
---

### Post by Slaskie on 2009-11-01
I upgraded to Kubuntu 9.10, I was using wicd network manager earlier with 9.04, now that I have installed Kubuntu 9.10 I am back to the default terrible network manager, which now isn't even working. I click on my the wireless network to connect, and nothing happens - back in 9.04 it would bring up the box where I would put in my wireless security key, now I click it and nothing happens, like the app is dead. Please help me to achieve wireless functionality so I can begin setting up my new system. Thank you.

---

### Post by Slaskie on 2009-11-01
bump :(

---

### Post by luisito on 2009-11-13
The same thing happened to me after switching to Kubuntu 9.10. The applet looks dead but it is not. If I plug the ethernet cable it connects well and it is reflected in the icon of knetworkmanager. If I click to connect to the wireless network nothing happens, as if it wasn't even a button.

This started happening after switching to 9.10 (I did a fresh install, I also switched from 32bits to 64bits). After a few days it fixed itself magically, and now it is happening again. I killed knetworkmanager and restarted it from a console and it is working now. There is some bug there, but I can't say what it is.

---

### Post by brandonsh on 2009-11-13
I hear about this a lot. KDE doesn't have wireless implemented too well. Maybe you should look for a third-party connection program or something.

---

### Post by GameManK on 2009-11-14
As a workaround you can use the gnome applet:
```
sudo aptitude install -R network-manager-gnome
nm-applet
```
If you can characterize when this problem happens, we'd love to hear about it: [https://bugs.launchpad.net/ubuntu/+source/plasma-widget-networkmanagement](https://bugs.launchpad.net/ubuntu/+source/plasma-widget-networkmanagement)

---

