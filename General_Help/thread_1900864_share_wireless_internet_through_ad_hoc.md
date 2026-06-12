---
title: "share wireless internet through ad hoc?"
date: 2011-12-27
forum: General Help
---

### Post by qwertyjjj on 2011-12-27
I have a working mobile broadband connection but I cann't seem to start that and the ad hoc connection I setup.
How can I share the connected wireless broadband connection (USB) through my wireless card with ubuntu and have other users share it?

---

### Post by vangop on 2011-12-27
Did you try to google first?
Anyway, check this [guide]("https://help.ubuntu.com/community/Internet/ConnectionSharing").

---

### Post by qwertyjjj on 2011-12-27
> **vangop said:**
> Did you try to google first?
Anyway, check this [guide]("https://help.ubuntu.com/community/Internet/ConnectionSharing").

Yes, I even looked at that page you already have.,
All the tutorials are either for wired network sharing, none seem to to say how to run an ad hoc connection at the same time as a USB mobile connection.

---

### Post by vangop on 2011-12-27
But if you create an ad-hoc wifi net, it should by default share your existing internet connection over it when you choose "Shared to other computers" Method on the IPv4 tab. 
Did you try that?

---

### Post by qwertyjjj on 2011-12-27
> **vangop said:**
> But if you create an ad-hoc wifi net, it should by default share your existing internet connection over it when you choose "Shared to other computers" Method on the IPv4 tab. 
Did you try that?

But how do you start the ad hoc network?
When mobile internnet is on, you cannot start the ad hoc in the list without first disconnecting the usb internet?

---

### Post by qwertyjjj on 2011-12-27
right, the xp comp is connected but it is not being shared.
it has ip: 10.42.43.60
255 255 255 0
gateway 10 42 43 1

but no internet pages open on the xp computer.
firewalls turned off

---

### Post by vangop on 2011-12-27
Check the /var/log/syslog, also post ifconfig on the ubuntu and ipconfig on the xp.
This could be an issue on any of them, try to ping each other, try to ping some site by ip. For example, ping google on ubuntu, then ping the same ip on xp.

---

