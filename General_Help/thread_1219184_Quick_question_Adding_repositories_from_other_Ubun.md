---
title: "Quick question: Adding repositories from other Ubuntu versions"
date: 2009-07-21
forum: General Help
---

### Post by hokuem on 2009-07-21
Hi,

I have Ubuntu 8.04 and want to install libapache-mod-security. However, it has been removed from the packages list after some licensing problems and never been put back. ([http://packages.ubuntu.com/hardy/web](http://packages.ubuntu.com/hardy/web))

But if you look at the 9.04 packages it's there, and my friend successfully installed it on his 9.04 server with apt-get. ([http://packages.ubuntu.com/jaunty/web/libapache-mod-security](http://packages.ubuntu.com/jaunty/web/libapache-mod-security))

[B]Question:
Am I gonna have problems if I add repositories from Ubuntu 9.04 to my sources.list to install libapache-mod-security?[/B]

Thanks. :)

---

### Post by michy99 on 2009-07-21
I'm not sure if that would work or not. However, you can download the .deb from here:

[http://packages.ubuntu.com/jaunty/web/libapache-mod-security](http://packages.ubuntu.com/jaunty/web/libapache-mod-security)

You will also need these to satisfy the dependencies:

[http://packages.ubuntu.com/jaunty/libpcre3](http://packages.ubuntu.com/jaunty/libpcre3)
[http://packages.ubuntu.com/jaunty/mod-security-common](http://packages.ubuntu.com/jaunty/mod-security-common)

The other dependencies should be satisfiable from the Hardy repositories.

---

