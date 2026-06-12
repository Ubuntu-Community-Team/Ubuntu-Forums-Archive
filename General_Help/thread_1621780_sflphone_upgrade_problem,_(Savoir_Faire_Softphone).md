---
title: "sflphone upgrade problem, (Savoir Faire Softphone)"
date: 2010-11-14
forum: General Help
---

### Post by Sun.Dial on 2010-11-14
Running Ubuntu Karmic 9.10, problem upgrading Savoir Faire Softphone
This is a softphone that will record calls, so very useful in that respect.

I noticed that upgrades for this application were available according to Update Manager, but the options to install them were greyed out. Having searched for the reason I followed the advice to uninstall the package completely, and then tried to install the new version.

Synaptic Package Manager showed two entries for this:
sflphone-client-gnome and sflphone-common

I checked the box to install sflphone-common and got the error:
Depends: libyaml-0-2 but is not installable
Depends: libcelt0-0  but is not installable

So I tried to install sflphone-client-gnome and got the error:
Depends: sflphone-common but is not going to be installed

This looks like a vicious circle and I am not sure how to proceed, so I wonder if anyone can help please?

I have this repository installed
[http://ppa.launchpad.net/savoirfairelinux/ppa/ubuntu](http://ppa.launchpad.net/savoirfairelinux/ppa/ubuntu)

Thank you
Sun

---

