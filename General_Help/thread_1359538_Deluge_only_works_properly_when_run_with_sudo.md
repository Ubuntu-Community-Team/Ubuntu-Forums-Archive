---
title: "Deluge only works properly when run with sudo"
date: 2009-12-19
forum: General Help
---

### Post by dai_vernon on 2009-12-19
My laptop was running deluge and shutdown abruptly due to low battery.  Now, when I click the icon, the "Starting Deluge..." entry appears in the taskbar, but goes away and nothing happens. When run from the terminal, it outputs the version number and dumps me back to the prompt, which implies that it crashes, I guess.  When run with sudo, I get this, and the window comes up as normal and the program works fine.

```
1.1.9
/usr/lib/pymodules/python2.6/deluge/ui/gtkui/statusbar.py:109: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips = gtk.Tooltips()
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
    self.run()
  File "/usr/lib/pymodules/python2.6/deluge/core/preferencesmanager.py", line 451, in run
    + "&plugins=" + quote_plus(self.config["enabled_plugins"])
  File "/usr/lib/python2.6/urllib.py", line 1231, in quote_plus
    return quote(s, safe)
  File "/usr/lib/python2.6/urllib.py", line 1223, in quote
    res = map(safe_map.__getitem__, s)
KeyError: 'Blocklist'

/usr/lib/pymodules/python2.6/deluge/ui/gtkui/statusbar.py:229: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips.set_tip(item.get_eventbox(), tooltip)
/usr/lib/pymodules/python2.6/deluge/ui/gtkui/statusbar.py:175: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips.set_tip(self.dht_item.get_eventbox(), "DHT Nodes")
```

Any idea what is going on?  I'm running karmic on an X200s

---

### Post by wojox on 2009-12-19
Run 

```
top
```

in the terminal and see if it's running in the background. It may still be downloading something.

---

### Post by dai_vernon on 2009-12-19
I think there was just an initialization problem.  After running it with sudo and then quitting normally, the program works properly now.  Never mind.

---

### Post by lovinglinux on 2009-12-19
> **dai_vernon said:**
> I think there was just an initialization problem.  After running it with sudo and then quitting normally, the program works properly now.  Never mind.

Never run such graphical applications with sudo. If you need to run them with administrative rights, which is really a bad idea, then use gksudo. I don't know about deluge, but running firefox with sudo changes the ownership of FF profiles and then you can't save bookmarks and other stuff. Firefox basically fails after that. You should check the ownership of your downloaded files to make sure they do not belong to root.

---

