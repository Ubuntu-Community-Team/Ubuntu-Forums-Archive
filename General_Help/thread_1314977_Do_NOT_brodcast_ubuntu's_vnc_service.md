---
title: "Do NOT brodcast ubuntu's vnc service"
date: 2009-11-04
forum: General Help
---

### Post by darthpenguin on 2009-11-04
Ubuntu 9.10

in /etc/avahi/service I have made two files afpd.service and vnc.service. this allows me to see my afp and vnc services running on ubuntu from the Finder on my Mac's. It works great. My problem is vino is still broadcasting as "user's remote desktop on ubuntu" as well. I have two instances of the same screen sharing service visible to my mac (and to ubuntu's Remote desktop viewer). for the sake of cleanliness, how do I stop avahi from broadcasting the "user's remote desktop on ubuntu" um.. thingy?

thx.

---

### Post by Gossar on 2010-03-12
I found a workaround listed under [gnome bug #561123]("https://bugzilla.gnome.org/show_bug.cgi?id=561123#c2").

---

### Post by darthpenguin on 2010-03-17
Great, I did as suggested and got the desired result. As I have found that VNC does not currently work as long as Compiz is enabled I have chosen to disable Ubuntu's VNC server for now. On another note, I find that both netatalk and avahi-daemon quit working after a period of time. I have to restart the services from the command line to get them to work (note: restarting the Ubuntu machine doesn't start up the services. :S). Could this be a result of the work around suggested above or a separate issue?

Thank.

---

