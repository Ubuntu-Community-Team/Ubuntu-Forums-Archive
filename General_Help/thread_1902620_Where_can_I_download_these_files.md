---
title: "Where can I download these files?"
date: 2011-12-31
forum: General Help
---

### Post by IanBorn on 2011-12-31
QT requires  these files for Phonon backend libs. I can not find them using sudo or software center.

libgstreamer0.10_0.10 The GStreamer base library.

libgstreamer0.10_0.10-devel  Contains files for developing applications with GStreamer.

libgstreamer-plugins-base0.10  Contains the basic plugins for audio and video playback, and will enable support for ogg files.

libgstreamer-plugins-base0.10-devel Makes it possible to develop applications using the base plugins.

---

### Post by howefield on 2011-12-31
What Ubuntu version are you using ?

In 11.10 you'll find 

libgstreamer0.10.0
libgstreamer0.10-dev
libgstreamer-plugins-base0.10-0
libgstreamer-plugins-base0.10-dev

---

### Post by muteXe on 2011-12-31
this website:
[http://developer.qt.nokia.com/doc/qt-4.8/phonon-overview.html](http://developer.qt.nokia.com/doc/qt-4.8/phonon-overview.html)

says this:
> 
The package names may vary between Linux distributions; on Mandriva, they have the following names:

which probably means they wont be called that on an ubuntu box. Just type "libgstreamer" into the quick search into synaptic and get the packages that are the closest names to the files you mentioned and see if that works.

For example, you list "libgstreamer-plugins-base0.10-devel", and in synaptic there's a package called "libgstreamer-plugins-base0.10-dev".  Doesn't take an Einstein to work out that this might be one of the packages you are after??

---

### Post by IanBorn on 2011-12-31
Thanks. It works.

---

### Post by IanBorn on 2011-12-31
I try to download them on another Notebook with Kubuntu(32 bits old version). I found the package using KPackageKit, it try to download them, 
but it failed by asking me to check my network connectivity.
How can it complain about my network if I can run Firefox and download emacs-24-4a.tar,gz without any problem.

---

### Post by 2F4U on 2011-12-31
What version are you running? Could it be that it is no longer supported with packages? If it is still supported, you could try a different mirror since mirrors are sometimes not reachable.

---

