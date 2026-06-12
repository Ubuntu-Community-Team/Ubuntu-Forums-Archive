---
title: "have to start services"
date: 2010-01-10
forum: General Help
---

### Post by foxy123 on 2010-01-10
I have a strange problem on my laptop. Something wrong with the services, which are supposed to start at boot. They just do not work. To be able printing I have to restart CUPS (sudo /etc/cups restart), to enable networking I have to restart samba (sudo /etc/samba restart). I have recently installed reniced, which is run on runlevels 3, 4 and 5 and have to restart it either to make it work. Any suggestion what might go wrong with my system?

---

### Post by foxy123 on 2010-01-10
I'd like also to add that nothing from /etc/rc.local runs on boot either.

---

### Post by foxy123 on 2010-01-12
Bump

---

### Post by john newbuntu on 2010-01-13
These kind of problems were reported about a month ago on this forum.  What we found at that time was that a package installation went bad (I think it was the upstart) and therefore, events weren't triggered properly and jobs suffered.

I suggest looking at your logs like /var/log/dpkg.log or /var/log/apt etc and see if you have a recent installation of upstart.  If so, reinstall it or revert it to an older version using synaptics.  Hopefully that should fix your problems.

---

