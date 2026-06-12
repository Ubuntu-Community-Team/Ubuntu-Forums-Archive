---
title: "Installing Listen Player, Get Python Error Message"
date: 2006-05-16
forum: General Help
---

### Post by fishmorg909 on 2006-05-16
I downloaded the deb for Listen player 4.3, and ran sudo dpkg -i -- when install started, I got this error:

> Selecting previously deselected package listen.
(Reading database ... 94220 files and directories currently installed.)
Unpacking listen (from listen_0.4.3-1_i386.deb) ...
dpkg: dependency problems prevent configuration of listen:
 listen depends on python-gst0.10; however:
  Package python-gst0.10 is not installed.
 listen depends on python2.4-pymad; however:
  Package python2.4-pymad is not installed.
 listen depends on python2.4-pysqlite2; however:
  Package python2.4-pysqlite2 is not installed.
 listen depends on python2.4-ctypes; however:
  Package python2.4-ctypes is not installed.
 listen depends on gstreamer0.10-plugins-base; however:
  Package gstreamer0.10-plugins-base is not installed.
 listen depends on gstreamer0.10-plugins-ugly; however:
  Package gstreamer0.10-plugins-ugly is not installed.
 listen depends on gstreamer0.10-plugins-good; however:
  Package gstreamer0.10-plugins-good is not installed.
dpkg: error processing listen (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 listen


I've been doing a search, but I can't find advice on what to do next. (I'm running Breezy.) Any leads?

---

### Post by fishmorg909 on 2006-05-16
Ah, never mind, searched some more and found news indicating it would be better to wait for Dapper to be released in a few weeks... because the Listen folks have put all their attention there. Oh well. :rolleyes:

---

