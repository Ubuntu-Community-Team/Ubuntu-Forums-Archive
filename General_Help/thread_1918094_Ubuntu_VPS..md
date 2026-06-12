---
title: "Ubuntu VPS."
date: 2012-01-31
forum: General Help
---

### Post by iiNitro360 on 2012-01-31
Hello, I've never used a Virtual Private Server on Ubuntu, however, I have used it on my desktop in  the past.

Basically, how do I install it so I can view a proper desktop, and use programs and such on it? As-if I was actually there at the computer. So from using this command line, can someone tell me how to install a 'GUI' I guess? and what program to view it in.

---

### Post by btindie on 2012-01-31
Take a look at KVM+SPICE which gives better performance over the more traditional VNC connection.
[http://spice-space.org/support.html](http://spice-space.org/support.html)
[http://docs.cslabs.clarkson.edu/wiki/SPICE](http://docs.cslabs.clarkson.edu/wiki/SPICE)
[http://bderzhavets.wordpress.com/2011/07/05/implementation-spice-on-ubuntu-11-10-kvm-server/](http://bderzhavets.wordpress.com/2011/07/05/implementation-spice-on-ubuntu-11-10-kvm-server/)
[http://www.linux-kvm.com/content/spice-ubuntu-wiki-available](http://www.linux-kvm.com/content/spice-ubuntu-wiki-available)

It's relatively new but pre-built packages are available for Ubuntu Precise so you could try it out with the Alpha1 of that [http://cdimage.ubuntu.com/releases/precise/alpha-1/](http://cdimage.ubuntu.com/releases/precise/alpha-1/)

---

