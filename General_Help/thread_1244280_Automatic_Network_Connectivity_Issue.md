---
title: "Automatic Network Connectivity Issue"
date: 2009-08-19
forum: General Help
---

### Post by krimzen85 on 2009-08-19
Hey All,

Well, I thought I had everything ironed out, but I've run into another problem. This one isn't crippling, it's just a little annoying.

After finding my ESSID and MAC address of my router from *iwlist wlan0 scan,* I populate the Wireless Tab under "System-Preference-Network Connections, and I connect without a problem.

However, if I shut down my laptop after I'm done, and then boot it back up next time I want to use it, I have to delete and re-create the wireless connection under Network Connections in Ubuntu for it to work.

I read some literature online and the general consensus was that *Most home networks broadcast in ESSID, which means it is hidden, and unless you plan to unhide your SSID (i.e. turn off SSID broadcasting on the router, you will pretty much have to do this every time*

I can tell you that my router does not like to work unless SSID broadcasting is enabled, so I guess my question is if I am going to have to re-create the entry every time I begin a new session, or if there is a way around it?

---

### Post by The Cog on 2009-08-19
You may prefer **wicd** which is an alternative network manager. I don't get that kind of run-around from wicd. You will have to uninstall the existing network manager first, but I think Synaptic will handle that for you. Reboot after making the change, to get the wicd daemon started. If you don't like wicd either, you can just reinstall the original again.

---

### Post by Thasaidon on 2009-09-17
I have a similar problem with Ubuntu 8.04 Gnome.
Each time I boot the system, I need to open the "Network Administration Tool" and re-enter my WPA key before Ubuntu connects to my wireless network.

Is this WICD tool also available for 8.04? because I can't find it in the package repository.

Thanx.

---

### Post by The Cog on 2009-09-17
I think that wicd waasn't included in the Ubuntu repositories until later. You will have to get a .deb from the wicd web site.

---

### Post by Thasaidon on 2009-09-18
> **The Cog said:**
> I think that wicd waasn't included in the Ubuntu repositories until later. You will have to get a .deb from the wicd web site.

Thanx!

---

### Post by speedwell68 on 2009-09-18
> **The Cog said:**
> You may prefer **wicd** which is an alternative network manager. I don't get that kind of run-around from wicd. You will have to uninstall the existing network manager first, but I think Synaptic will handle that for you. Reboot after making the change, to get the wicd daemon started. If you don't like wicd either, you can just reinstall the original again.

I am a big fan of WICD, in many ways it is far better than the default network manager.  As you have said it is included in the standard 9.04 Jaunty repositories.  If you simply install it in the Synaptic Package Manger it will automatically remove the default network manager for you.  The quick way of doing this would be in the terminal...

```
sudo apt-get install wicd
```

That command will also automatically replace the default network manager for you.  For people using earlier versions of Ubuntu a repository for WICD is available here...

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by Thasaidon on 2009-09-18
Thanx guys.
During the install via the package manager, I got an error saying it wasn't installed correctly, but when I tried to (re)install it via terminal, I got the message wicd was already installed.

After a reboot, all seems to work just fine! :)

Well, WICD seems to work like a charm! I can recommend it to everyone!

---

