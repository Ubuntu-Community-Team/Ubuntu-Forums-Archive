---
title: "DockBar(x) broken user config"
date: 2011-03-16
forum: General Help
---

### Post by Crazedpsyc on 2011-03-16
I loved dockbarx, but when I tried to install dockbarx-awn (manually) DockBarX and DockBar stopped working. when run from the terminal, the gnome panel reports:
```
** (gnome-panel:7882): WARNING **: panel-applet-frame.c:1273: failed to load applet OAFIID:GNOME_DockBarXApplet:
System exception: IDL:Bonobo/GeneralError:1.0 : Child process did not give an error message, unknown failure occurred

```
and awn (I am actually running the DockBarX.py file in /usr/share/avant-window-navigator/plugins/DockBarX/) says:
```
** Message: pygobject_register_sinkfunc is deprecated (AwnOverlay)

** (DockBarX.py:15018): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (DockBarX.py:15018): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (DockBarX.py:15018): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
ERROR:dbus.proxies:Introspect error on :1.579:/org/gnome/zeitgeist/log/activity: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Traceback (most recent call last):
  File "DockBarX.py", line 21, in <module>
    import dockbarx.dockbar
  File "/usr/local/lib/python2.6/dist-packages/dockbarx/dockbar.py", line 37, in <module>
    from groupbutton import *
  File "/usr/local/lib/python2.6/dist-packages/dockbarx/groupbutton.py", line 41, in <module>
    import zg
  File "/usr/local/lib/python2.6/dist-packages/dockbarx/zg.py", line 34, in <module>
    iface = client.ZeitgeistDBusInterface()
  File "/usr/lib/pymodules/python2.6/zeitgeist/client.py", line 194, in __init__
    self.INTERFACE_NAME, self.OBJECT_PATH)
  File "/usr/lib/pymodules/python2.6/zeitgeist/client.py", line 123, in __init__
    self.__methods, self.__signals = self.get_members(proxy.Introspect())
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name :1.579 was not provided by any .service files
```

However, when I run the same file as root, or any other user, it runs nicely and gives the happy messages of success!

I think it would be very strange to run AWN as another user all the time, so if there is some config for dbx in my home folder that I can't find, I will delete or fix it.

---

### Post by M7S on 2011-03-17
Zeitgeist problems. Try remove your zeitgeist data for the user or upgrade or downgrade zeitgeist to get a version without the bug (by installing from ppa or removing ppa and installing from repository). Next version of DockbarX should not crash because of zeitgeist bugs.

---

### Post by Crazedpsyc on 2011-03-17
Thanks, How can I do that? I don't even use zeitgeist, so I just purged it and deleted its log. Maybe that'll help?
I'll edit this post once I reinstall zeitgeist and try dbx.

UPDATE: I got the same errors!
Is there a way that I can get an alpha or beta version of DBX? I have a ppa already, but is there a trunk ppa or something? I would rather use that any way, and if it would fix the problems...?

Details: I am on 64bit ubuntu 10.10 using dbx 0.43-1~webupd8~maverick1 (yes, the webupd8 ppa) and zeitgeist 0.7-0ubuntu1~0ppa1~maverick

---

### Post by Crazedpsyc on 2011-03-23
kerBump

---

### Post by M7S on 2011-03-23
Sorry, I missed your answer earlier. Did you try to run dockbarx while zeitgeist wasn't installed? DockbarX isn't depending on zeitgeist, it just enables recent and most used documents "jumplists". 

To install a newer version of zeitgeist (if you still want to do that):
```
sudo add-apt-repository ppa:zeitgeist/ppa
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Crazedpsyc on 2011-03-28
I'm updating the repos right now...
It takes a long time with all my ppas...

I'll edit with an update when I upgrade

UPDATE: I finished updating and upgrading zeitgeist, then I even rebooted, and DBX still has the same error message!
btw: I said a alpha/beta dbx, not zeitgeist, but that's ok.
I would be interested in testing anything, and if you don't already have a pre-release version publicly available I recommend doing so, even an automatic nightly build.

now I am removing zeitgeist entirely to try again.

YES! it works great w/out

except running "dbx_preference" returns:
```
Traceback (most recent call last):
  File "/usr/bin/dbx_preference", line 1452, in <module>
    PrefDialog()
  File "/usr/bin/dbx_preference", line 834, in __init__
    self.__update()
  File "/usr/bin/dbx_preference", line 993, in __update
    self.globals.settings["media_buttons"])
KeyError: 'media_buttons'

```

No functionality at all in the gnome panel either

---

### Post by Crazedpsyc on 2011-03-29
Every time I run dockbarx_factory (no .py anymore right?) it gives:
```
Traceback (most recent call last):
  File "/usr/bin/dockbarx_factory", line 20, in <module>
    from dockbarx.log import *
ImportError: No module named log
```
Do I just need to cd to wherever the log module is?
BTW: there is no log folder or file in ~/.dockbarx/, there is only a "launchers" folder with the .desktops for my two launchers.

EDIT: no, I see there are three log.py files for dockbarx:
> 
/usr/lib/pymodules/python2.6/dockbarx/log.py
/usr/lib/pymodules/python2.6/dockbarx/log.pyc
/usr/share/pyshared/dockbarx/log.py

and when I import dockbarx from a normal python shell, it creates the following module object (i'm posting so you can see the path)
```
>>> import dockbarx
>>> dockbarx
<module 'dockbarx' from '/usr/local/lib/python2.6/dist-packages/dockbarx/__init__.pyc'>
```
But "from dockbarx import log" or "from dockbarx.log import *" imply that the log module is nonexistant.

The contents of that folder are:
```

cairowidgets.py   dockbar.pyc      iconfactory.py   theme.pyc
cairowidgets.pyc  groupbutton.py   iconfactory.pyc  windowbutton.py
common.py         groupbutton.pyc  __init__.py      windowbutton.pyc
common.pyc        i18n.py          __init__.pyc     zg.py
dockbar.py        i18n.pyc         theme.py         zg.pyc

```
No log.py

So I cped one of the other log.py files to that folder and "dockbarx_factory run-in-window" works now.
Unfortunately, "dbx_preference" still does not.

The next thing I will try will be reinstalling dockmanager. Aren't the new media buttons related somehow to dockmanager helpers?

Unless I can find, or you can direct me to the file in which configuration is stored, so I can manually disable media buttons, or at least tweak a few things like enabling previews and the helpers I actually use.

---

### Post by M7S on 2011-03-29
I'm afraid you have multiple versions of DockbarX installed in different locations and python is choosing the older one. You should probably remove /usr/local/lib/python2.6/dist-packages/dockbarx/ folder and the dockbarx.egg (or similar) from /usr/local/lib/python2.6/dist-packages/.

---

### Post by Crazedpsyc on 2011-03-29
Yup, that did it! Thanks!
the egg was "Dockbarx-0.3.1.egg-info"

---

