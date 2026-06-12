---
title: "Startup script runnign before networkmanager - help"
date: 2009-08-04
forum: General Help
---

### Post by Blundey on 2009-08-04
Me again,

I have installed OpenVPN via a tarball. OpenVPN is not starting at boot time which I need to have working. 

Ive checked syslog and it seems its trying to bind to eth0 before network manager has initalised.

So i went into /etc/rc*.d and renamed K01openvpn to S20openvpn

For some reason openvpn is in every single rc.d folder and is usually before networkmanager so i went in each folder and renamed it so that its the last one loaded. I then rebooted and still openvpn is started before the network manager. Not sure what im doing wrong and why there are symbolic links in every rc.d folder.

Any help in this would be appriciated.

Regards

Blundey

---

### Post by Blundey on 2009-08-04
anyone?! :(

---

### Post by dcstar on 2009-08-05
Uninstall Network Manager, install the older tool that actually uses the /etc/network/interfaces file (**gnome-network-admin**) and your problem should be solved.

---

### Post by Blundey on 2009-08-05
must admit im a bit hestitant to start removing network manager on a production server!

Any other alternatives?

---

### Post by slakkie on 2009-08-05
You are aware that you renamed a STOP script to a START script.. 

K == kill
S == start

---

### Post by Blundey on 2009-08-05
oops. :) Ill rename it back. Still why are there instances of openvpn in every single rc.d folder?

---

### Post by slakkie on 2009-08-05
> **Blundey said:**
> oops. :) Ill rename it back. Still why are there instances of openvpn in every single rc.d folder?

Because of the various run levels.

[http://en.wikipedia.org/wiki/Runlevel](http://en.wikipedia.org/wiki/Runlevel)

---

