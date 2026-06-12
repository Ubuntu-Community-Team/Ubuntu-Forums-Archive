---
title: "I know karmic is free but i am getting seriously cheesed off"
date: 2010-04-27
forum: General Help
---

### Post by myjess on 2010-04-27
knetworkmanager is the latest I am fighting with.
I cannot get knm to set a static for eth0, even if i have set it in the config. It always does an auto config which gives my lappy a DHCP addy.

I want knm cos it also sets up my wifi on the same lappy, and uses the IP I set in th config.

Also  LTSP, nautilus nas samba shares, there seems to be no end to the issues I face. 

Searching on google is rubbish too, cos there are that many results, but a lot of them are for previous ubuntu releases which have no bearing on karmic.

grumble, grumble!

---

### Post by ubuntu27 on 2010-04-27
Knetwork Manager is still in heavy development and not recommend for production purposes.

You could switch back to Gnome's [NetworkManager]("http://projects.gnome.org/NetworkManager/") or to [WICD]("http://wicd.sourceforge.net/").


You should try WICD, it is in the repositories. It works for any desktop environment.

---

### Post by myjess on 2010-04-27
> **ubuntu27 said:**
> Knetwork Manager is still in heavy development and not recommend for production purposes.

You could switch back to Gnome's [NetworkManager]("http://projects.gnome.org/NetworkManager/") or to [WICD]("http://wicd.sourceforge.net/").


You should try WICD, it is in the repositories. It works for any desktop environment.

How do i get the wicd-client to start in kdm automatically please?

---

### Post by ubuntu27 on 2010-04-28
There is a Control Module called "Autostart" in KDE.

Click on the Kickoff Application Launcher (The "start" button for KDE), and then type "Autostart".

Click on "Add program..." and select what program you want it to Autostart.

---

