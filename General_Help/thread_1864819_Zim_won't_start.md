---
title: "Zim won't start"
date: 2011-10-19
forum: General Help
---

### Post by CarlosFerreira on 2011-10-19
Sorry for bringing this thread back from the dead.

Mine has simply stopped working. Won't open at all in my netbook (running 10.04 LTS), despite working as well as ever on 11.10. Tried uninstalling and reinstalling via Software Centre, no luck. Does not give any warning or error, simply won't start.

Has anyone had a comparable problem?

---

### Post by bash on 2011-10-19
> **CarlosFerreira said:**
> Sorry for bringing this thread back from the dead.

Mine has simply stopped working. Won't open at all in my netbook (running 10.04 LTS), despite working as well as ever on 11.10. Tried uninstalling and reinstalling via Software Centre, no luck. Does not give any warning or error, simply won't start.

Has anyone had a comparable problem?

Have tried launching it from the terminal with *zim --debug*. Maybe that gives you some idea what might be wrong.

---

### Post by cariboo on 2011-10-19
@CarlosFerreira, I created a new thread for you, as the Cafe is not the palce to ask support questions.

---

### Post by CarlosFerreira on 2011-10-23
> **cariboo907 said:**
> @CarlosFerreira, I created a new thread for you, as the Cafe is not the palce to ask support questions.

Thank you for that.

Here's the result of the debug:

> INFO: This is zim 0.43
DEBUG: Python version is (2, 6, 5, 'final', 0)
DEBUG: Zim revision is:
    branch: pyzim-trunk
    revision: 191 [email]pardus@cpan.org[/email]-20100118004246-c2i3mku13s44bxsk
    date: 2010-01-18 01:42:46 +0100

DEBUG: Not running from a source dir
DEBUG: Set XDG_DATA_HOME to /home/carlosferreira/.local/share
DEBUG: Set XDG_DATA_DIRS to [<Dir: /usr/share/gnome>, <Dir: /usr/local/share>, <Dir: /usr/share>]
DEBUG: Set XDG_CONFIG_HOME to /home/carlosferreira/.config
DEBUG: Set XDG_CONFIG_DIRS to [<Dir: /etc/xdg/xdg-une>, <Dir: /etc/xdg>]
DEBUG: Set XDG_CACHE_HOME to /home/carlosferreira/.cache
DEBUG: Running command: gui
DEBUG: Cache dir: /home/carlosferreira/Documents/Scrapbook/.zim
DEBUG: Index database file: /home/carlosferreira/Documents/Scrapbook/.zim/index.db
INFO: Flushing index
INFO: Opening default notebook
INFO: Starting UnixSocketDaemon
DEBUG: Socket address: /tmp/zim-carlosferreira/daemon-socket
DEBUG: Wrote /tmp/zim-carlosferreira/daemon.pid
DEBUG: Sending to daemon: ["ping",[],{}]

DEBUG: Daemon replied: "Ack"
DEBUG: Sending to daemon: ["vivicate",["zim.gui.GtkInterface","file:///home/carlosferreira/Documents/Scrapbook"],{"usedaemon":true,"notebook":"file:///home/carlosferreira/Documents/Scrapbook"}]

DEBUG: Child spawned 5237 (u'zim.gui.GtkInterface', u'file:///home/carlosferreira/Documents/Scrapbook')
DEBUG: Daemon replied: true
DEBUG: Sending to daemon: ["relay",[["zim.gui.GtkInterface","file:///home/carlosferreira/Documents/Scrapbook"],"present",null],{"geometry":null,"fullscreen":null}]

DEBUG: Sending to child 5237: ["present",[null],{"geometry":null,"fullscreen":null}]

DEBUG: Daemon replied: true
carlosferreira@carlos-NC10:~$ DEBUG: Gtk version is (2, 20, 1)
DEBUG: Pygtk version is (2, 17, 0)
DEBUG: Loaded plugin calendar (<CalendarPlugin object at 0xa05ca04 (zim+plugins+PluginClass at 0xa0de990)>)
DEBUG: Loaded plugin printtobrowser (<PrintToBrowserPlugin object at 0xa05b7d4 (zim+plugins+PluginClass at 0xa0dead0)>)
DEBUG: Loaded plugin versioncontrol (<VersionControlPlugin object at 0xa05b8c4 (zim+plugins+PluginClass at 0xa0d8b80)>)
DEBUG: Accelmap: /home/carlosferreira/.config/zim/accelmap
DEBUG: Opening notebook: file:///home/carlosferreira/Documents/Scrapbook
DEBUG: Cache dir: /home/carlosferreira/Documents/Scrapbook/.zim
DEBUG: Index database file: /home/carlosferreira/Documents/Scrapbook/.zim/index.db
INFO: Starting background index update
DEBUG: Action: set_pathbar_none
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/zim/gui/__init__.py", line 1455, in do_set_pathbar
    self.pathbar.set_history(self.ui.history)
  File "/usr/lib/pymodules/python2.6/zim/gui/pathbar.py", line 371, in set_history
    self._select(history.get_current())
  File "/usr/lib/pymodules/python2.6/zim/history.py", line 129, in get_current
    return HistoryRecord(self, self.current)
  File "/usr/lib/pymodules/python2.6/zim/history.py", line 34, in __init__
    Path.__init__(self, history.history[i])
IndexError: list index out of range
INFO: No VCS detected
ERROR: Error in child main:
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/zim/daemon.py", line 462, in spawn
    self._main()
  File "/usr/lib/pymodules/python2.6/zim/daemon.py", line 504, in _main
    obj.main()
  File "/usr/lib/pymodules/python2.6/zim/gui/__init__.py", line 357, in main
    path = self.history.get_current()
  File "/usr/lib/pymodules/python2.6/zim/history.py", line 129, in get_current
    return HistoryRecord(self, self.current)
  File "/usr/lib/pymodules/python2.6/zim/history.py", line 34, in __init__
    Path.__init__(self, history.history[i])
IndexError: list index out of range
DEBUG: Child exited 5237 (u'zim.gui.GtkInterface', u'file:///home/carlosferreira/Documents/Scrapbook')
INFO: Last instance quit - exiting daemon
INFO: Stopped UnixSocketDaemon


Something wrong with python, perhaps?

One thing I have been thinking is I synchronise my Zim folders over Ubuntu One, and it's not been working very well - sync issues. Could that be causing it?

---

### Post by mar.esther23 on 2012-02-07
I'm having the same problem. 

> 
$ zim --debug
INFO: This is zim 0.43
DEBUG: Python version is (2, 6, 5, 'final', 0)
DEBUG: Zim revision is:
	branch: pyzim-trunk
	revision: 191 [email]pardus@cpan.org[/email]-20100118004246-c2i3mku13s44bxsk
	date: 2010-01-18 01:42:46 +0100

DEBUG: Not running from a source dir
DEBUG: Set XDG_DATA_HOME to /home/mariana/.local/share
DEBUG: Set XDG_DATA_DIRS to [<Dir: /usr/share/gnome>, <Dir: /usr/local/share>, <Dir: /usr/share>]
DEBUG: Set XDG_CONFIG_HOME to /home/mariana/.config
DEBUG: Set XDG_CONFIG_DIRS to [<Dir: /etc/xdg/xdg-gnome>, <Dir: /etc/xdg>]
DEBUG: Set XDG_CACHE_HOME to /home/mariana/.cache
DEBUG: Running command: gui
DEBUG: Cache dir: /home/mariana/Dropbox/Notebooks/Clases/.zim
DEBUG: Index database file: /home/mariana/Dropbox/Notebooks/Clases/.zim/index.db
INFO: Opening default notebook
INFO: Starting UnixSocketDaemon
DEBUG: Socket address: /tmp/zim-mariana/daemon-socket
DEBUG: Wrote /tmp/zim-mariana/daemon.pid
DEBUG: Sending to daemon: ["ping",[],{}]

DEBUG: Daemon replied: "Ack"
DEBUG: Sending to daemon: ["vivicate",["zim.gui.GtkInterface","file:///home/mariana/Dropbox/Notebooks/Clases"],{"usedaemon":true,"notebook":"file:///home/mariana/Dropbox/Notebooks/Clases"}]

DEBUG: Child spawned 3743 (u'zim.gui.GtkInterface', u'file:///home/mariana/Dropbox/Notebooks/Clases')
DEBUG: Daemon replied: true
DEBUG: Sending to daemon: ["relay",[["zim.gui.GtkInterface","file:///home/mariana/Dropbox/Notebooks/Clases"],"present",null],{"geometry":null,"fullscreen":null}]

DEBUG: Sending to child 3743: ["present",[null],{"geometry":null,"fullscreen":null}]

DEBUG: Daemon replied: true
mariana@C3:~$ DEBUG: Gtk version is (2, 20, 1)
DEBUG: Pygtk version is (2, 17, 0)
DEBUG: Loaded plugin calendar (<CalendarPlugin object at 0x9c18e14 (zim+plugins+PluginClass at 0x9c90020)>)
DEBUG: Loaded plugin printtobrowser (<PrintToBrowserPlugin object at 0x9c25c5c (zim+plugins+PluginClass at 0x9c8a180)>)
DEBUG: Loaded plugin versioncontrol (<VersionControlPlugin object at 0x9c25d4c (zim+plugins+PluginClass at 0x9c8a010)>)
DEBUG: Accelmap: /home/mariana/.config/zim/accelmap
DEBUG: Opening notebook: file:///home/mariana/Dropbox/Notebooks/Clases
DEBUG: Cache dir: /home/mariana/Dropbox/Notebooks/Clases/.zim
DEBUG: Index database file: /home/mariana/Dropbox/Notebooks/Clases/.zim/index.db
INFO: Starting background index update
DEBUG: Action: set_pathbar_none
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/zim/gui/__init__.py", line 1455, in do_set_pathbar
    self.pathbar.set_history(self.ui.history)
  File "/usr/lib/pymodules/python2.6/zim/gui/pathbar.py", line 371, in set_history
    self._select(history.get_current())
  File "/usr/lib/pymodules/python2.6/zim/history.py", line 129, in get_current
    return HistoryRecord(self, self.current)
  File "/usr/lib/pymodules/python2.6/zim/history.py", line 34, in __init__
    Path.__init__(self, history.history[i])
IndexError: list index out of range
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/zim/gui/__init__.py", line 1551, in do_open_notebook
    self.set_toolbar_style(self.uistate['toolbar_style'])
  File "/usr/lib/pymodules/python2.6/zim/gui/__init__.py", line 1468, in set_toolbar_style
    assert style in ('icons_and_text', 'icons_only', 'text_only'), style
AssertionError
INFO: No VCS detected
ERROR: Error in child main:
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/zim/daemon.py", line 462, in spawn
    self._main()
  File "/usr/lib/pymodules/python2.6/zim/daemon.py", line 504, in _main
    obj.main()
  File "/usr/lib/pymodules/python2.6/zim/gui/__init__.py", line 357, in main
    path = self.history.get_current()
  File "/usr/lib/pymodules/python2.6/zim/history.py", line 129, in get_current
    return HistoryRecord(self, self.current)
  File "/usr/lib/pymodules/python2.6/zim/history.py", line 34, in __init__
    Path.__init__(self, history.history[i])
IndexError: list index out of range
DEBUG: Child exited 3743 (u'zim.gui.GtkInterface', u'file:///home/mariana/Dropbox/Notebooks/Clases')
INFO: Last instance quit - exiting daemon
INFO: Stopped UnixSocketDaemon


I also tried > zim --no-daemon and it still failed.

---

### Post by mar.esther23 on 2012-02-08
Managed to solve it. The trick is deleting ".zim" folder from the notebook folder.

---

### Post by tedynaidenov on 2012-05-03
> **mar.esther23 said:**
> Managed to solve it. The trick is deleting ".zim" folder from the notebook folder.

I had the same problem. This "fix" works for me too. Thanks!

---

