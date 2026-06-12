---
title: "Quodlibet - Will not start"
date: 2011-04-28
forum: General Help
---

### Post by Saiko Berry on 2011-04-28
I have an issue. When I launch Quodlibet, it gives me an error and will not open. It did not do this until I upgraded to Lucid.

What I get is the following;

```
Initializing audio backend (gstbe)
Initializing main library (~/.quodlibet/songs)
Supported formats: mod, mp3, mp4, mpc, spc, trueaudio, wav, wavpack, wma, xiph
/usr/lib/pymodules/python2.6/quodlibet/__init__.py:125: DeprecationWarning: enabling legacy plugin API
  "enabling legacy plugin API", DeprecationWarning)
/usr/lib/pymodules/python2.6/quodlibet/qltk/x.py:115: DeprecationWarning: Use the new widget gtk.Tooltip
  tips = gtk.Tooltips()
/usr/lib/pymodules/python2.6/quodlibet/qltk/x.py:118: DeprecationWarning: Use the new widget gtk.Tooltip
  tips.enable()
/usr/lib/pymodules/python2.6/quodlibet/qltk/quodlibetwindow.py:513: DeprecationWarning: Use the new widget gtk.Tooltip
  _("Check for changes in your library"))
/usr/lib/pymodules/python2.6/quodlibet/qltk/quodlibetwindow.py:516: DeprecationWarning: Use the new widget gtk.Tooltip
  _("Reload all songs in your library (this can take a long time)"))
/usr/lib/pymodules/python2.6/quodlibet/qltk/quodlibetwindow.py:519: DeprecationWarning: Use the new widget gtk.Tooltip
  _("The 40 songs you've played most (more than 40 may "
/usr/lib/pymodules/python2.6/quodlibet/qltk/quodlibetwindow.py:523: DeprecationWarning: Use the new widget gtk.Tooltip
  _("The 40 songs you've played least (more than 40 may "
/usr/lib/pymodules/python2.6/quodlibet/qltk/queue.py:82: DeprecationWarning: Use the new widget gtk.Tooltip
  tips.set_tip(b, _("Remove all songs from the queue"))
/usr/lib/pymodules/python2.6/quodlibet/qltk/quodlibetwindow.py:219: DeprecationWarning: Use the new widget gtk.Tooltip
  tips.set_tip(repeat, _("Restart the playlist when finished"))
Error grabbing key 173, 0x8ded000
Error grabbing key 171, 0x8ded000
Error grabbing key 172, 0x8ded000
Error grabbing key 209, 0x8ded000
Error grabbing key 174, 0x8ded000
/usr/lib/pymodules/python2.6/quodlibet/qltk/x.py:126: DeprecationWarning: Use the new widget gtk.Tooltip
  tips.enable()
/usr/lib/pymodules/python2.6/quodlibet/qltk/x.py:127: DeprecationWarning: Use the new widget gtk.Tooltip
  tips.set_tip(clear, _("Clear search"))
Traceback (most recent call last):
  File "/usr/bin/quodlibet", line 285, in <module>
    main()
  File "/usr/bin/quodlibet", line 59, in main
    window = widgets.init(player, library)
  File "/usr/lib/pymodules/python2.6/quodlibet/widgets.py", line 96, in init
    events.rescan()
  File "/usr/lib/pymodules/python2.6/quodlibet/plugins/__init__.py", line 165, in rescan
    self._load(name, mod)
  File "/usr/lib/pymodules/python2.6/quodlibet/plugins/events.py", line 106, in _load
    self._plugins[obj.PLUGIN_ID].destroy()
  File "/usr/lib/pymodules/python2.6/quodlibet/plugins/events/trayicon.py", line 515, in destroy
    self.disabled()
  File "/usr/lib/pymodules/python2.6/quodlibet/plugins/events/trayicon.py", line 251, in disabled
    if window.handler_is_connected(self.__w_sig_map):
TypeError: GObject.handler_is_connected() argument 1 must be integer<k>, not None

```

Though I am sure that the only necessary thing is the error at the bottom, so I will highlight that.

```
[b]    if window.handler_is_connected(self.__w_sig_map):
TypeError: GObject.handler_is_connected() argument 1 must be integer<k>, not None[/b]
```

Any insight?

---

### Post by Saiko Berry on 2011-04-28
Solved by upgrading to 2.3 which is not on Synaptic for some reason.

---

