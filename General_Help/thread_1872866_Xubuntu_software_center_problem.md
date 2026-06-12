---
title: "Xubuntu software center problem"
date: 2011-10-31
forum: General Help
---

### Post by Python Jedi on 2011-10-31
I upgraded to 11.10 not too long ago, and I just found out that the ubuntu software center is not functioning. when "software-center" is run in the terminal:
```
ERROR:root:Could not find any typelib for Gtk
Traceback (most recent call last):
  File "/usr/bin/software-center", line 33, in <module>
    from gi.repository import Gtk
ImportError: cannot import name Gtk
```
I'm thinking this is because I run the xfce desktop and installed 11.04 xubuntu, therefore the update did not install the correct gtk packages...  any suggestions/alternate ideas?

---

### Post by Toz on 2011-10-31
Here is a related reference link: [http://askubuntu.com/questions/48663/software-sources-requires-gtk-2-and-wont-run-on-11-04]("http://askubuntu.com/questions/48663/software-sources-requires-gtk-2-and-wont-run-on-11-04"). 
It pertains to 11.04, but it might help troubleshoot. 

According to the link:
```
python -c 'from gi.repository import Gtk; print Gtk'
```
...should return the python gtk provider file. I get:
> <gi.module.DynamicModule 'Gtk' from '/usr/lib/girepository-1.0/Gtk-3.0.typelib'>

When I search for this file using apt-file search:
```
$ apt-file search /usr/lib/girepository-1.0/Gtk-3.0.typelib
```
...I get:
> gir1.2-gtk-3.0: /usr/lib/girepository-1.0/Gtk-3.0.typelib

Do you have **gir1.2-gtk-3.0** installed?
```
$ apt-cache policy gir1.2-gtk-3.0 
gir1.2-gtk-3.0:
  Installed: 3.2.0-0ubuntu3
  Candidate: 3.2.0-0ubuntu3
  Version table:
 *** 3.2.0-0ubuntu3 0
        500 http://ca.archive.ubuntu.com/ubuntu/ oneiric-updates/main i386 Packages
        100 /var/lib/dpkg/status
     3.2.0-0ubuntu2 0
        500 http://ca.archive.ubuntu.com/ubuntu/ oneiric/main i386 Packages

```

---

### Post by Python Jedi on 2011-10-31
The package is now installed, but I get the same error running 'software-center' or "python -c 'from gi.repository import Gtk; print Gtk'"  I installed gir1.2-gtk-3.0 and reinstalled gir1.2-gtk-2.0 (I have both now).  I found that deleting the usr/local/lib/girepository-1.0 gave me an error about GObject, even though it was there in /usr/lib/girepository I'm working on it now.

Running ```
python -c 'from gi.repository import Gtk; print Gtk'
``` still gives me the same error, even after reinstalling gir1.2-glib-2.0.  It would appear that deleting the /usr/local/lib/girepository-1.0 directory was a bad idea, probably should have copied the files from /usr/lib/girepository-1.0  going to see if there is a girepository-1.0 anywhere else...

Strangely, it would appear that ```
locate girepository-1.0
``` along with giving me a bunch of typelibs, says that/usr/local/lib/girepository-1.0 still exists, yet when I browse there in thunar, it is not there

upon executing 
```
$cd /usr/local/lib
$ls
```
girepository-1.0 is not there.  strange...

upon further study of "locate girepository-1.0", I found that gedit *also* has a girepository-1.0 directory.  Looking into it

/usr/lib/gedit/girepository-1.0 only has a typelib for gedit, so that cannot be overriding /usr/lib/girepository-1.0

I've installed a number of packages that deal with Gobject and Glib, installing them from source, possibly one of those has messed something up?  it's pygobject 3.0.0, glib 2.30.0, and gobject-introspection 1.30.0.  They are dependencies for LibRPG 0.5, a python module to help with creating RPGs, obviously

Not sure what to do, calling it for tonight.

---

### Post by Toz on 2011-11-01
> **Python Jedi said:**
> The package is now installed, but I get the same error running 'software-center' or "python -c 'from gi.repository import Gtk; print Gtk'"  I installed gir1.2-gtk-3.0 and reinstalled gir1.2-gtk-2.0 (I have both now).  I found that deleting the usr/local/lib/girepository-1.0 gave me an error about GObject, even though it was there in /usr/lib/girepository I'm working on it now.

Running ```
python -c 'from gi.repository import Gtk; print Gtk'
``` still gives me the same error, even after reinstalling gir1.2-glib-2.0.  It would appear that deleting the /usr/local/lib/girepository-1.0 directory was a bad idea, probably should have copied the files from /usr/lib/girepository-1.0  going to see if there is a girepository-1.0 anywhere else...
It would appear that /usr/local/lib/girepository-1.0 doesn't come from the default ubuntu repositories:
```
$ apt-file search /usr/local/lib/girepository-1.0

```
...returns nothing.

> Strangely, it would appear that ```
locate girepository-1.0
``` along with giving me a bunch of typelibs, says that/usr/local/lib/girepository-1.0 still exists, yet when I browse there in thunar, it is not there

upon executing 
```
$cd /usr/local/lib
$ls
```
girepository-1.0 is not there.  strange...
The locate command updates the contents of its database nightly I believe (see /etc/cron.daily/mlocate). You can run it manually to force an update via:
```
sudo /usr/bin/updatedb.mlocate
```

> upon further study of "locate girepository-1.0", I found that gedit *also* has a girepository-1.0 directory.  Looking into it

/usr/lib/gedit/girepository-1.0 only has a typelib for gedit, so that cannot be overriding /usr/lib/girepository-1.0

I've installed a number of packages that deal with Gobject and Glib, installing them from source, possibly one of those has messed something up?  it's pygobject 3.0.0, glib 2.30.0, and gobject-introspection 1.30.0.  They are dependencies for LibRPG 0.5, a python module to help with creating RPGs, obviously

Not sure what to do, calling it for tonight.
Here are software-center's dependencies. 
```
$ apt-cache depends software-center 
software-center
  Depends: python
  Depends: app-install-data
  Depends: aptdaemon
  Depends: humanity-icon-theme
  Depends: gir1.2-glib-2.0
  Depends: gir1.2-gtk-3.0
  Depends: gir1.2-gmenu-3.0
  Depends: gir1.2-webkit-3.0
  Depends: python-gobject
  Depends: python-gobject-cairo
  Depends: python-xapian
  Depends: python-apt
  Depends: python-aptdaemon
  Depends: python-aptdaemon.gtk3widgets
  Depends: python-dbus
  Depends: python-defer
  Depends: policykit-1
 |Depends: policykit-1-gnome
  Depends: <policykit-1-kde>
  Depends: python-xdg
  Depends: python-lazr.restfulclient
  Depends: ubuntu-sso-client
  Depends: python-piston-mini-client
  Depends: oneconf
  Recommends: lsb-release
  Recommends: gir1.2-launchpad-integration-3.0
  Recommends: apt-xapian-index
  Recommends: update-notifier
  Recommends: software-properties-gtk
  Recommends: sessioninstaller
  Recommends: zeitgeist-core
  Recommends: lzma
    xz-lzma
  Conflicts: <gnome-app-install>
  Conflicts: oneconf
  Replaces: <gnome-app-install>
    software-center

```
Maybe try manually re-install all packages with Depends: prefix?
```
apt-get install --reinstall <pkg>
```

---

### Post by Python Jedi on 2011-11-01
reinstalled all but '<policykit-1-kde>' as this seems to be missing from sources but still referred to (probably by software-center)...

upon reinstalling software-center itself, it seems that Gioand Gobject are missing typelibs, yet they're there, and that stops the install process. what could possibly be going on here...

---

### Post by Toz on 2011-11-01
python version?

```
$ ls -l `which python`
lrwxrwxrwx 1 root root 9 2011-10-08 12:50 /usr/bin/python -> python2.7

```

---

### Post by shakaran on 2011-11-10
Hi, 

I found this topic searching on Google with the same problem.

Apparently, all the typelibs are installed on /usr/lib/girepository-1.0, but on some moment they changed to /usr/local/lib/girepository-1.0

There is a bug filled on Debian with a complain of a developer:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=645391](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=645391)

So, my guess was create a symlink as temporal workaround:

```
sudo ln -s /usr/lib/girepository-1.0 /usr/local/lib
```

This seems a bug with the default prefix for autotools (/usr/local) for the package gobject-introspection

I am having the same issue with Gtreamer (Gst) for PyGObject (PyGi) trying to compile the new Gstreamer 0.11.1 that it still is not shipped with Ubuntu:

[http://lists.freedesktop.org/archives/gstreamer-devel/2011-November/033841.html](http://lists.freedesktop.org/archives/gstreamer-devel/2011-November/033841.html)
[http://www.mail-archive.com/pygtk@daa.com.au/msg20690.html](http://www.mail-archive.com/pygtk@daa.com.au/msg20690.html)

---

