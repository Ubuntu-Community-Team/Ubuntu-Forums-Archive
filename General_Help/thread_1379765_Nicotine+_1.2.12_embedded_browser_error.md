---
title: "Nicotine+ 1.2.12 embedded browser error"
date: 2010-01-12
forum: General Help
---

### Post by QuaxEros on 2010-01-12
(ubuntu 9.10 on Dell XPS m1530)
Hi All,

Yesterday i shut down my (working) nicotine+ 1.2.12 and today it came up with a gray screen.
When running it from the command prompt it gives following output.

```
/usr/lib/pymodules/python2.6/pynicotine/gtkgui/frame.py:346: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips = gtk.Tooltips()
/usr/lib/pymodules/python2.6/pynicotine/gtkgui/frame.py:347: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips.enable()
/usr/lib/pymodules/python2.6/pynicotine/gtkgui/frame.py:2432: DeprecationWarning: Use the new widget gtk.Tooltip
  tips.enable()
Embedded Mozilla webrowser failed to load: 'NoneType' object has no attribute 'set_profile_path'
Traceback (most recent call last):
  File "/usr/bin/nicotine", line 267, in <module>
    run()
  File "/usr/bin/nicotine", line 253, in run
    app = frame.MainApp(config, plugins, trayicon, tryrgba, hidden, webbrowser)
  File "/usr/lib/pymodules/python2.6/pynicotine/gtkgui/frame.py", line 3629, in __init__
    self.frame = NicotineFrame(config, plugindir, trayicon, rgbamode, start_hidden, WebBrowser)
  File "/usr/lib/pymodules/python2.6/pynicotine/gtkgui/frame.py", line 755, in __init__
    self.browser = BrowserWindow(self, "http://nicotine-plus.org")
  File "/usr/lib/pymodules/python2.6/pynicotine/gtkgui/frame.py", line 204, in __init__
    self.pack_start(self.view, True, True)
AttributeError: 'BrowserWindow' object has no attribute 'view'

```

Is there a way to manually set variables (like set_profile_path) or is this not the way to go about this problem?
I don't know why the problem came up after running the app succesfully.
Anyone with a suggestion for a solution?

Any comments on the "DepreciationWarning"s (or is that not important?)

---

### Post by QuaxEros on 2010-01-13
OKay...

Went to the file ~/.nicotine/config and changed this line:

mozembed = True
into
mozembed = False

Now nicotine starts fine.
And when searching in the settings GUI when hovering over the option for the embedded browser a WARNING shows up, stating that you need to configure this option well to prevent instable behavior....

Voila!!
My mistake clearly....
I'll read about the "mozembed" package and configuring it before checking the option next time...

_____________________________________________________________
If all other options fail...Read the f*cking manual!!!

---

