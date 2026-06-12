---
title: "Solitaire"
date: 2009-07-15
forum: General Help
---

### Post by Trekky0623 on 2009-07-15
A couple of problems.

In AisleRiot Solitaire, the variant "Klondike" is not listed in the list of games.

Also I cannot start PyChess, I get this when I try to run it.

```
Exception in thread Thread-2:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.6/dist-packages/pychess/System/tsqlite.py", line 34, in run
    con = sqlite.connect(self.path)
OperationalError: unable to open database file

/usr/lib/python2.6/dist-packages/pychess/Players/engineNest.py:3: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import os, md5, imp

(pychess:16274): libglade-WARNING **: could not find glade file '/usr/lib/python2.6/glade/tipoftheday.glade'
Traceback (most recent call last):
  File "/usr/games/pychess", line 87, in <module>
    import pychess.Main
  File "/usr/lib/python2.6/dist-packages/pychess/Main.py", line 20, in <module>
    from pychess.widgets import tipOfTheDay
  File "/usr/lib/python2.6/dist-packages/pychess/widgets/tipOfTheDay.py", line 7, in <module>
    widgets = GladeWidgets("tipoftheday.glade")
  File "/usr/lib/python2.6/dist-packages/pychess/System/uistuff.py", line 198, in __init__
    self.widgets = gtk.glade.XML(addDataPrefix("glade/%s" % filename))
RuntimeError: could not create GladeXML object

```

Any help would be appreciated.

---

### Post by Trekky0623 on 2009-07-21
bump

---

### Post by fiddler616 on 2009-07-21
Maybe try reinstalling AisleRiot?

---

