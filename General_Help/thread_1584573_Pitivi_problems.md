---
title: "Pitivi problems"
date: 2010-09-29
forum: General Help
---

### Post by Billisnice on 2010-09-29
When i try to run pitivi i get the following message and it closes down. 

"Install a version of the GStreamer Python bindings greater or equal to 0.10.19" without the quotes.

What do I need to do? Where is the deb package for gstreamer needed?

Thanks

Ubuntu 10.04 user

---

### Post by andrewthomas on 2010-09-29
```
sudo apt-get install python-gst0.10
```
Info

```
aptitude show python-gst0.10
Package: python-gst0.10                  
State: installed
Automatically installed: no
Version: 0.10.19-2
Priority: optional
Section: python
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,163k
Depends: libc6 (>= 2.4), libglib2.0-0 (>= 2.24.0),
         libgstreamer-plugins-base0.10-0 (>= 0.10.30), libgstreamer0.10-0 (>=
         0.10.30), libpython2.6 (>= 2.6), libxml2 (>= 2.6.27), python (< 2.7),
         python (>= 2.6), python-central (>= 0.6.11), python-gobject (>=
         2.11.2), python-libxml2
Suggests: python-gst0.10-dev, python-gst0.10-dbg
Conflicts: python2.3-gst0.10, python2.4-gst0.10
Replaces: python2.3-gst0.10, python2.4-gst0.10
Provides: python2.6-gst0.10
Description: generic media-playing framework (Python bindings)
 GStreamer is a media processing framework with support for a wide variety of
 data sources, sinks, and formats through the use of dynamically loaded plugins.
 
 This package contains bindings to access GStreamer from Python.
Homepage: http://gstreamer.freedesktop.org

```

---

### Post by Billisnice on 2010-09-29
After :
sudo apt-get install python-gst0.10

I get the following

bn@bn-desktop:~$ sudo apt-get install python-gst0.10
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-gst0.10 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bn@bn-desktop:~$ 


[B]pitivi still does now work and the same error code pops up:
"Install a version of the GStreamer Python bindings greater or equal to 0.10.19" without the quotes.[/B]


Ty

---

### Post by andrewthomas on 2010-09-29
You probably have python-gst0.10 (0.10.18-1) & **are not using the version of ****pitivi ****from the lucid repo's since it only requires [python-gst0.10]("http://packages.ubuntu.com/lucid/python-gst0.10")      (>= 0.10.16)         **

post the output of ```
aptitude show python-gst0.10
```You could try to install it from maverick, **but I make no promises that you won't have some dependency issues.**

[http://packages.ubuntu.com/maverick/python-gst0.10](http://packages.ubuntu.com/maverick/python-gst0.10)

---

### Post by Billisnice on 2010-09-29
State: installed
Automatically installed: no
Version: 0.10.18-1
Priority: optional
Section: python
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 967k
Depends: libc6 (>= 2.4), libglib2.0-0 (>= 2.16.0),
         libgstreamer-plugins-base0.10-0 (>= 0.10.26), libgstreamer0.10-0 (>=
         0.10.26), libpython2.6 (>= 2.6), libxml2 (>= 2.6.27), python (< 2.7),
         python (>= 2.6), python-central (>= 0.6.11), python-gobject (>=
         2.11.2), python-libxml2
Suggests: python-gst0.10-dev, python-gst0.10-dbg
Conflicts: python2.3-gst0.10, python2.4-gst0.10
Replaces: python2.3-gst0.10, python2.4-gst0.10
Provides: python2.6-gst0.10
Description: generic media-playing framework (Python bindings)
 GStreamer is a media processing framework with support for a wide variety of
 data sources, sinks, and formats through the use of dynamically loaded plugins.
 
 This package contains bindings to access GStreamer from Python.
Homepage: [http://gstreamer.freedesktop.org](http://gstreamer.freedesktop.org)

---

### Post by andrewthomas on 2010-09-29
Where did you install pitivi from?

Is there a reason that you are not using the version from lucid?

[http://packages.ubuntu.com/lucid/pitivi](http://packages.ubuntu.com/lucid/pitivi)

pitivi (0.13.4-0ubuntu3)

---

### Post by Billisnice on 2010-09-29
no, how do I remove it? I tried uninstall and reinstalled and it is still there. thanks

---

### Post by andrewthomas on 2010-09-29
But now it should be the version from lucid (0.13.4-0ubuntu3)

```
aptitude show pitivi 
```

unless you have some funky ppa enabled.

---

### Post by Billisnice on 2010-09-29
bn@bn-desktop:~$ aptitude show pitivi
Package: pitivi
State: installed
Automatically installed: no
Version: 0.13.4.3-1ubuntu1~ppa2~lucid1
Priority: optional
Section: gnome
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 3,121k
Depends: python, python-central (>= 0.6.11), python-gtk2 (>= 2.14),
         python-gst0.10 (>= 0.10.18), gstreamer0.10-gnonlin (>= 0.10.15),
         python-cairo (>= 1.0.0), python-glade2, python-gconf, python-dbus,
         python-pkg-resources, python-zope.interface | python-zope-interface,
         libgstreamer0.10-0 (>= 0.10.28), libgstreamer-plugins-base0.10-0 (>=
         0.10.28), gstreamer0.10-plugins-base (>= 0.10.28),
         gstreamer0.10-plugins-good, gstreamer0.10-pulseaudio |
         gstreamer0.10-audiosink, gstreamer0.10-x | gstreamer0.10-videosink,
         gnome-icon-theme, python-pygoocanvas, python-launchpad-integration
Suggests: gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-bad, hal,
          gstreamer0.10-ffmpeg
Description: non-linear audio/video editor using GStreamer
 GStreamer is a streaming media framework, based on graphs of filters which
 operate on media data.  Applications using this library can do anything from
 real-time sound processing to playing videos, and just about anything else
 media-related.  Its plugin-based architecture means that new data types or
 processing capabilities can be added simply by installing new plug-ins. 
 
 PiTiVi allows users to easily edit audio/video projects based on the GStreamer
 framework.  PiTIVi provides several ways of creating and modifying a timeline.
 Ranging from a simple synopsis view (a-la iMovie) to the full-blown editing
 view (aka Complex View) which puts you in complete control of your editing.

---

### Post by andrewthomas on 2010-09-29
[B]0.13.4.3-1ubuntu1~ppa2~lucid1
[/B]

If you want pitivi to work I would get rid of that ppa that you are picking it up from.

It seems to be this one: [https://launchpad.net/~lucid-bleed/+archive/ppa]("https://launchpad.net/%7Elucid-bleed/+archive/ppa")

```
deb [http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu](http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu) lucid main 
 deb-src [http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu](http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu) lucid main
```

---

### Post by Billisnice on 2010-09-30
What do I type to get rid of it? I did not find anything in synaptic.

thanks

---

### Post by Irony on 2010-09-30
Synaptic > Settings > Repositories

Untick or delete the offending repository.

---

### Post by Billisnice on 2010-09-30
I unclicked an rebooted and it worked. Thanks for all the help!

---

