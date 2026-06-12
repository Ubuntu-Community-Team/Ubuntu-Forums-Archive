---
title: "adeskbar doesn't load plugins"
date: 2011-11-22
forum: General Help
---

### Post by david sousa on 2011-11-22
Hello!

I'm using lubuntu and i installed the last adeskbar version 4.3

I can easly add apps without any problem, but when I try to load the menu plugin and window list they dont appear in the dock.

Also, I went at ~/.config/adeskbar/ and I found this output.log file:


> Traceback (most recent call last):
  File "/usr/share/adeskbar/adesk/bar.py", line 989, in load_plugin
    exec("import plugins.%s as plugin" % p)
  File "<string>", line 1, in <module>
  File "/usr/share/adeskbar/plugins/menuframe.py", line 22, in <module>
    class EventHandler(pyinotify.ProcessEvent):
NameError: name 'pyinotify' is not defined
Mixer plugin ERR: global name 'alsa' is not defined
Mixer plugin ERR: global name 'alsa' is not defined

---

### Post by Rodney9 on 2011-11-22
Quote from - [http://www.omgubuntu.co.uk/2010/11/adeskbar-dock-panel-replacement-for-ubuntu/](http://www.omgubuntu.co.uk/2010/11/adeskbar-dock-panel-replacement-for-ubuntu/)

> Oh yes, and for those of you who are saying the notification area will not display, you must install python-xlib, it's also worth installing python-alsaaudio if you have not done so already so that the volume control plugin can function. If your notification area still does not work after installing python-xlib and restarting adeskba

---

### Post by david sousa on 2011-11-22
Thank you for your reply. I did it, and it still doesn't work.. now i get this:

> Traceback (most recent call last):
  File "/usr/share/adeskbar/adesk/bar.py", line 989, in load_plugin
    exec("import plugins.%s as plugin" % p)
  File "<string>", line 1, in <module>
  File "/usr/share/adeskbar/plugins/menuframe.py", line 22, in <module>
    class EventHandler(pyinotify.ProcessEvent):
NameError: name 'pyinotify' is not defined
Traceback (most recent call last):
  File "/usr/share/adeskbar/adesk/barconf.py", line 1516, in row_deleted
    self.conf.plg_mgr.box.reorder_child(self.conf.plg_mgr.plugins[index], ind)
KeyError: '1322000359'
Traceback (most recent call last):
  File "/usr/share/adeskbar/adesk/bar.py", line 989, in load_plugin
    exec("import plugins.%s as plugin" % p)
  File "<string>", line 1, in <module>
  File "/usr/share/adeskbar/plugins/windowlist.py", line 4, in <module>
    import wnck
ImportError: No module named wnck
Traceback (most recent call last):
  File "/usr/share/adeskbar/adesk/barconf.py", line 1516, in row_deleted
    self.conf.plg_mgr.box.reorder_child(self.conf.plg_mgr.plugins[index], ind)
KeyError: '1322000359'
Fatal Python error: PyEval_RestoreThread: NULL tstate
resize and update icon for all plugins
Aborted

---

### Post by maxter on 2011-12-05
i resolved installing python-pyinotify.
the problem raise installing the deb with dpkg and then fixing the dependencies with 'apt-get -f install'
this will not install the reccomended packages :)

---

### Post by david sousa on 2011-12-05
I installed python-pyinotify and still I cannot load plugins...

---

### Post by Pierrot86 on 2011-12-15
Hi,

I'm on Lubuntu 11.10 and I use Adeskbar. The plugin menu doesn't work for me. It is impossible to add Lubuntu menu on the dock. Someone would have a solution ?

---

