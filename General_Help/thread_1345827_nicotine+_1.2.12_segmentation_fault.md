---
title: "nicotine+ 1.2.12 segmentation fault"
date: 2009-12-04
forum: General Help
---

### Post by febo on 2009-12-04
nicotine+ doesn't start-up since a couple of weeks ago, after a routine update on jaunty.
 i didn't save the terminal output, but it sounded more or less like this:

DeprecationWarning: the md5 module is deprecated; use hashlib instead
import md5

now i switched to karmic, and the issue remains, but the output is quite different:

Fri 13:29 Nicotine supports "psyco", an inline optimizer for python code, you
          can get it at [http://sourceforge.net/projects/psyco/](http://sourceforge.net/projects/psyco/)
ven 13:29 Nicotine supports a country code blocker but that requires a (GPL'ed)
          library called GeoIP. You can find it here:  C library:
          [http://www.maxmind.com/app/c](http://www.maxmind.com/app/c)  Python bindings:
          [http://www.maxmind.com/app/python](http://www.maxmind.com/app/python)  (the python bindings require the C
          library)
/usr/lib/pymodules/python2.6/pynicotine/gtkgui/frame.py:346: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips = gtk.Tooltips()
/usr/lib/pymodules/python2.6/pynicotine/gtkgui/frame.py:347: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips.enable()
/usr/lib/pymodules/python2.6/pynicotine/gtkgui/frame.py:2432: DeprecationWarning: Use the new widget gtk.Tooltip
  tips.enable()
Segmentation fault

i run nicotine+1.2.12 on karmic
kernel 2.6.31-15
processor intel pentium 4 CPU 2.53 GHz
ram 1,2 GiB

can anybody help me? i searched on the forum and google but couldn't find an answer.
thanks!

---

