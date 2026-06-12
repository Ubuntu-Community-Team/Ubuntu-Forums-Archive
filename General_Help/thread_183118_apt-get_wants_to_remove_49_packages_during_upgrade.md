---
title: "apt-get wants to remove 49 packages during upgrade to dapper?"
date: 2006-05-27
forum: General Help
---

### Post by stodge on 2006-05-27
I changed all instances of breezy to dapper in my sources list and typed:

sudo apt-get dist-upgrade

However, apt-get tells me it wants to remove 49 packages as part of the upgrade:

The following packages will be REMOVED:
  akode akode-mpeg amarok amarok-gstreamer base-config busybox-cvs-initramfs
  cupsys-driver-gimpprint-data dbus gstreamer0.8-jack hal hotplug hplip-base
  ifrename ivman k3b k3blibs kaffeine-gstreamer kdelibs4c2 language-support-en
  libarts1c2 libid3-3.8.3c2 libjack0.80.0-0 libkcal2a libkdepim1
  libkleopatra0a libmimelib1a libopenexr2c2 libtag1c2 libtunepimp2c2 libwpd8c2
  mysql-common-4.1 openoffice.org2 openoffice.org2-base openoffice.org2-calc
  openoffice.org2-common openoffice.org2-core openoffice.org2-draw
  openoffice.org2-help-en-us openoffice.org2-impress openoffice.org2-kde
  openoffice.org2-l10n-en-us openoffice.org2-math openoffice.org2-writer
  python-uno sanekonsole x-common xmkmf xorg-common xserver-common


Is this correct?

Thanks

---

### Post by aysiu on 2006-05-27
First, you may have certain conflicting (at least from a Dapper point of view) repositories.

So you may want to get a clean list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Second, you should make sure before you do a *dist-upgrade* that you have the proper metapackages installed.

For more details, go here:
[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

---

