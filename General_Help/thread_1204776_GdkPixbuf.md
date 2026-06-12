---
title: "GdkPixbuf?"
date: 2009-07-05
forum: General Help
---

### Post by Mark76 on 2009-07-05
Everytime I try to run ROX menu I get an error message about gdkpixbuf.

Can anyone fathom out this bug report and tell me why?

Traceback (most recent call last):
  File "/home/mark/.roxpanel-applets/Menu-005/AppletRun", line 34, in <module>
    rox.report_exception()
  File "/home/mark/.cache/0install.net/implementations/sha1new=9c116df3689d60df58925a7c634064ac2394f696/ROX-Lib2/python/rox/__init__.py", line 184, in report_exception
    _excepthook(type, value, tb)
  File "/home/mark/.cache/0install.net/implementations/sha1new=9c116df3689d60df58925a7c634064ac2394f696/ROX-Lib2/python/rox/__init__.py", line 191, in _excepthook
    debug.show_exception(ex_type, value, tb)
  File "/home/mark/.cache/0install.net/implementations/sha1new=9c116df3689d60df58925a7c634064ac2394f696/ROX-Lib2/python/rox/debug.py", line 55, in show_exception
    traceback.format_tb(tb) +
  File "/home/mark/.roxpanel-applets/Menu-005/AppletRun", line 29, in <module>
    main = rmenu.RoxMenu(long(sys.argv[1]))
  File "/home/mark/.roxpanel-applets/Menu-005/rmenu.py", line 139, in __init__
    self.refresh_menu()
  File "/home/mark/.roxpanel-applets/Menu-005/rmenu.py", line 311, in refresh_menu
    self.load_icon(e.stock, join(self.root, e.stock))
  File "/home/mark/.roxpanel-applets/Menu-005/rmenu.py", line 187, in load_icon
    self.factory.add(name, g.IconSet(pixbuf=pb))
TypeError: pixbuf should be a GdkPixbuf

---

### Post by Mark76 on 2009-07-05
Can anyone help me with this?  I really miss my menu and I can't figure out why it's playing this game with me :(

---

