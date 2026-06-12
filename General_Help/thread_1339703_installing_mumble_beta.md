---
title: "installing mumble beta"
date: 2009-11-27
forum: General Help
---

### Post by fallen seraph on 2009-11-27
So I'm having a bit of trouble installing mumble beta 1.2.xxx

when I tried to install it from source using this guide [http://mumble.sourceforge.net/BuildingLinux#](http://mumble.sourceforge.net/BuildingLinux#)

I get the following error message upon using the make command: [http://dl.dropbox.com/u/1976943/whowouldhavethunkthatrunningabetaclientinlinuxwouldbegay.txt](http://dl.dropbox.com/u/1976943/whowouldhavethunkthatrunningabetaclientinlinuxwouldbegay.txt)

When I try to install it from PPA as per instructions here:
[https://launchpad.net/~slicer/+archive/ppa](https://launchpad.net/~slicer/+archive/ppa)

I go to synaptic and ask it to upgrade my mumble and it gives me:

mumble:
  Depends: libcelt0 (>=0.7.0) but 0.5.1-0ubuntu1 is to be installed
 Recommends: mumble-11x but it is not going to be installed


Any ideas?

---

### Post by Tagert on 2009-12-01
Grab the needed libcelt0 version at:
[http://packages.ubuntu.com/sv/lucid/libcelt0](http://packages.ubuntu.com/sv/lucid/libcelt0)

It should not require additional packages.
Worked for me. :)

Remember to run:
sudo dpkg-reconfigure mumble-server
after, it seems to require to run in root mode. Almost pulled my hair out trying to get it to run with my ordinary user but to no use :P

I'm running Ubuntu 9.04.

---

### Post by domagoj91 on 2009-12-01
wrong thread

---

