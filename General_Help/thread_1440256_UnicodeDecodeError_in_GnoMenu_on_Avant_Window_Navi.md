---
title: "UnicodeDecodeError in GnoMenu on Avant Window Navigator"
date: 2010-03-27
forum: General Help
---

### Post by Agent.Logic_ on 2010-03-27
Hi,

I decided to bite the bullet and install AWN 0.4 beta, because it supported GnoMenu. However, adding the GnoMenu applet to AWN triggers a **UnicodeDecodeError**, which looks something like this:

```
UnicodeDecodeError in GnoMenu: 'utf8' codec can't decode byte 0xb5 in position 1: unexpected code byte
```

The traceback is as follows:

```
Traceback (most recent call last):
  File "/var/lib/python-support/python2.6/awn/extras/awnlib.py", line 1462, in init_start
    applet_class(applet)
  File "/usr/share/avant-window-navigator/applets/GnoMenu/GnoMenu.py", line 46, in __init__
    self.hwg = Main_Menu(self.HideMenu)
  File "/usr/lib/gnomenu/Menu_Main.py", line 75, in __init__
    self.setup()
  File "/usr/lib/gnomenu/Menu_Main.py", line 299, in setup
    self.PGL = TreeProgramList()
  File "/usr/lib/gnomenu/Menu_Widgets.py", line 902, in __init__
    self.XDG = XDGMenu()
  File "/usr/lib/gnomenu/Menu_Items.py", line 79, in __init__
    self.CacheSettings = xdg.Menu.parse("settings.menu")
  File "/var/lib/python-support/python2.6/xdg/Menu.py", line 524, in parse
    __genmenuNotOnlyAllocated(tmp["Root"])
  File "/var/lib/python-support/python2.6/xdg/Menu.py", line 856, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/var/lib/python-support/python2.6/xdg/Menu.py", line 859, in __genmenuNotOnlyAllocated
    tmp["cache"].addMenuEntries(menu.AppDirs)
  File "/var/lib/python-support/python2.6/xdg/Menu.py", line 1022, in addMenuEntries
    self.__addFiles(dir, "", prefix, legacy)
  File "/var/lib/python-support/python2.6/xdg/Menu.py", line 1036, in __addFiles
    self.__addFiles(dir, os.path.join(subdir,item), prefix, legacy)
  File "/var/lib/python-support/python2.6/xdg/Menu.py", line 1028, in __addFiles
    menuentry = MenuEntry(os.path.join(subdir,item), dir, prefix)
  File "/usr/lib/python2.6/posixpath.py", line 70, in join
    path += '/' + b
UnicodeDecodeError: 'utf8' codec can't decode byte 0xb5 in position 1: unexpected code byte
```

Any ideas on what is happening?

---

### Post by Agent.Logic_ on 2010-03-27
After hours of breaking my head trying to figure out what was going on, I came across this thread: [http://forums.linuxmint.com/viewtopic.php?f=76&t=29522&p=230731](http://forums.linuxmint.com/viewtopic.php?f=76&t=29522&p=230731)

What I did was: backed up the ~/.config/menus folder (in case something went wrong), then deleted it. I tried adding the GnoMenu to AWN again after that, and presto! It worked. Just putting this out here in case anyone else might be having this problem.

Cheers.

---

