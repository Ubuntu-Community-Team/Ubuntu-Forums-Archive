---
title: "Xubuntu 12.04 buggy interface?"
date: 2012-05-07
forum: General Help
---

### Post by FeraTech on 2012-05-07
Has anybody had issues with the Xubuntu interface in 12.04?

I switched from Ubuntu because I hate the Unity interface. It seriously has made every single thing more difficult to use. I tried Linux Mint in vain. Then moved to Xubuntu which the interface is so much better.

However, that being said I have had 2 strange bugs so far.

1. My network interface when clicked disappeared. It only had options to enable or disable interfaces. All other options are gone.

2. When I tried to reconnect my bluetooth mouse I realized all notification windows do not allow me to press any buttons. Nothing happens. I can close them out but clicking options like "allow" "deny" does nothing.

Is this a common issue?

I'm using Xubuntu 12.04 x64
I also installed the proprietary AMD drivers for "AMD Radeon HD 6310".

---

### Post by ve4cib on 2012-05-07
Yes, I am having this exact same issue and was wondering about it too.  The  buttons just don't seem to do anything.

My Bluetooth mouse was working fine under 11.04 (Gnome 2), but I cannot get it set up with XFCE 12.04

---

### Post by FeraTech on 2012-05-07
are you using the AMD Proprietary Drivers?

---

### Post by ve4cib on 2012-05-07
I'm not.  I do have the proprietary Nvidia drivers for my graphics card, but that's it.

---

### Post by Marzata on 2012-05-07
I have not noticed any of these problems in Xubuntu 12.04 (i386) after a dozen of installations.

---

### Post by mike555 on 2012-05-07
I think the problems often occur when people put Xubuntu on Ubuntu ,instead of a "clean" install, or they try to use an old /home folder ......... better to install clean with a new /home .

---

### Post by FeraTech on 2012-05-07
Mine is a completely clean install.

---

### Post by bob-linux-user on 2012-05-07
You might try going back to the gnome fallback session. It seems a bit improved over the 11.10 version and looks and feels like gnome 2 and xfce.

---

### Post by ve4cib on 2012-05-08
It seems slightly like overkill to change WMs/DEs to make something as simple as a bluetooth mouse to work.

Does anyone know what (if any) hidden folders in my home directory would contain stale configurations that could affect bluetooth?  My /home is on a separate partition so I do have a few older files lurking around on there.

---

### Post by izx on 2012-06-10
It's a bug in the xfce4-notifyd (Notification Daemon) shipped with Xubuntu 12.04. It has been fixed in upstream Debian as well as Quantal.

Please see [this AskUbuntu answer]("http://askubuntu.com/a/148829/58612") for more details and how to fix.

---

