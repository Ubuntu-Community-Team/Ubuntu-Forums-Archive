---
title: "Installing NX"
date: 2010-09-15
forum: General Help
---

### Post by KolakCC on 2010-09-15
Hi,
I get this error when trying to install nxserver:
NX> 701 Updating: server at: Wed Sep 15 19:50:33 2010.
NX> 701 Autodetected system: debian.
NX> 701 Update log is: /usr/NX/var/log/update.
NX> 701 Checking NX server configuration using /usr/NX/etc/server.cfg file.
NX> 701 ERROR: Output: chown: invalid user: `nx:root'.
NX> 701 ERROR: Cannot set ownership attributes for '/usr/NX/etc' to 'nx:root'.
dpkg: error processing nxserver (--install):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:

I am at the end of my rope here.. help!

---

### Post by Baked- on 2010-09-15
I had major issues with nxserver.   I eventually gave up and used neatx from google.  Info here:

[http://code.google.com/p/neatx/](http://code.google.com/p/neatx/)

---

### Post by CharlesA on 2010-09-15
How are you installing it? From a deb?

---

### Post by KolakCC on 2010-09-15
> **CharlesA said:**
> How are you installing it? From a deb?
Yes.

---

### Post by KolakCC on 2010-09-15
> **Baked- said:**
> I had major issues with nxserver.   I eventually gave up and used neatx from google.  Info here:

[http://code.google.com/p/neatx/](http://code.google.com/p/neatx/)
Heh.. Trying to install this though. It's dependant on nx server though.

---

### Post by Baked- on 2010-09-15
just install it from the google ubuntu repo it will pull in all of the dependencies.   it will use some of the libraries from the other nx projects, but i had a much easier time getting it to work than freenx in 10.04.

I have had freenx working before on 9.04 and a gentoo system, but neatx on 10.04 was by far the easiest to setup and make work properly.

---

### Post by KolakCC on 2010-09-15
> **Baked- said:**
> just install it from the google ubuntu repo it will pull in all of the dependencies.   it will use some of the libraries from the other nx projects, but i had a much easier time getting it to work than freenx in 10.04.

I have had freenx working before on 9.04 and a gentoo system, but neatx on 10.04 was by far the easiest to setup and make work properly.
Sorry, I'm kinda new to ubuntu. The INSTALL says:
  sudo apt-get install make openssh-server python python-pexpect \
       python-simplejson python-gtk2 python-gobject gcc autoconf automake \
       python-docutils netcat xauth x11-xserver-utils
to which i get:
Setting up nxserver (3.4.0-14) ...
NX> 701 Updating: server at: Wed Sep 15 20:44:29 2010.
NX> 701 Autodetected system: debian.
NX> 701 Update log is: /usr/NX/var/log/update.
NX> 701 Checking NX server configuration using /usr/NX/etc/server.cfg file.
NX> 701 ERROR: Output: chown: cannot access `/usr/NX/etc/passwords.db': No such file or directory.
NX> 701 ERROR: Cannot set ownership attributes for '/usr/NX/etc/passwords.db' to 'nx:root'.

---

### Post by Baked- on 2010-09-15
Ok try this:

remove the nx server you have installed previously

then type these command in a terminal

sudo apt-get install python-software-properties && sudo add-apt-repository ppa:freenx-team
sudo apt-get update
sudo apt-get install neatx-server


that should get you up and running.

---

