---
title: "System Settings for Proxy Username and Password?"
date: 2010-08-31
forum: General Help
---

### Post by o_swas on 2010-08-31
Hello,

I'm trying to use Kubuntu 10.04 in a corporate environment.  Our environment uses an internet proxy that requires a username and password.

Under Ubuntu 10.04, I can use the GUI to set the proxy host, port, username and password.  When I do this, all the web browsers work, Snyaptic works, etc.

However,  under Kubuntu 10.04, the GUI lets me specify a proxy host and port, but doesn't appear to save the username and password.  Because of this, I have to manually set the proxy information on my web browser, but the package managers don't work because they can't access the internet.  Apparently the ability to specify proxy username and password is either broken or unfinished.

Does anybody know when Kubuntu will allow complete proxy settings through the GUI?

Thank you!!

-Ryan

---

### Post by andrewthomas on 2010-08-31
```
apt-get install gnome-control-center
``` and launch with
```
 gnome-network-properties
```

---

### Post by o_swas on 2010-08-31
And this will work under Kubuntu (KDE)?  Just want to make sure.  Thanks for the tip!

Does anybody know when KDE/Kubuntu will nativel support proxy username and password?

---

### Post by o_swas on 2010-08-31
Oops, wait a second:  I don't think apt-get will work to install gnome control center because it won't be able to access the internet -- because of the proxy.  Can I get around that?

---

### Post by andrewthomas on 2010-08-31
Download from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and install with dpkg -i

---

