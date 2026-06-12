---
title: "Ubuntu 10.04 and Google Earth"
date: 2011-02-10
forum: General Help
---

### Post by Charlie Tame on 2011-02-10
Problem was GE reported it could not contact login server(s)

sudo gedit /etc/resolv.conf and change first DNS to 8.8.8.8

Save file. (8.8.8.8 and 8.8.4.4 are Google DNS servers!)

Try again and it should work.

My DHCP kept putting back the Qwest wireless router (Actiontec) as the default DNS resolver and for whatever reason it could not get to the GE servers. Who knows why?

This will likely change on reboot, so if this worked for you but after reboot GE fails again change your Network settings to DHCP addresses only and set the above DNS servers... and make sure the conf file is changed back. You will need to change both wireless and wired settings for this to remain working apparently.

---

