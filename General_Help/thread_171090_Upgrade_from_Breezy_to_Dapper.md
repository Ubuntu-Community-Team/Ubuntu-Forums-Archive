---
title: "Upgrade from Breezy to Dapper"
date: 2006-05-05
forum: General Help
---

### Post by philetus on 2006-05-05
I did:
gksudo update-manager -d

and got

/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
/usr/lib/python2.4/site-packages/UpdateManager/MetaRelease.py:169: DeprecationWa rning: Class MetaRelease is already GObject-registered; Please note that classes  containing any of the attributes __gtype_name__, __gproperties__, or __gsignals __ are now automatically registered.
  gobject.type_register(MetaRelease)
xauth: /tmp/libgksu1.2-JHbAtB/.Xauthority
xauth_env: /tmp/.gdmhSxYwv
dir: /tmp/libgksu1.2-JHbAtB

Am I missing something?

---

### Post by Sef on 2006-05-05
Why did you do what you did instead of this:

sudo apt-get update

sudo apt-get dist-upgrade

Also did you change your sources list from Breezy to Dapper?

---

### Post by philetus on 2006-05-05
[QUOTE=Sef]Why did you do what you did instead of this:

sudo apt-get update

sudo apt-get dist-upgrade

Also did you change your sources list from Breezy to Dapper?[/QUOTE]

I did what I did from here:
[http://www.ubuntu.com/testing/dapperbeta](http://www.ubuntu.com/testing/dapperbeta)

Changed my sources list and got it. Thanks

---

