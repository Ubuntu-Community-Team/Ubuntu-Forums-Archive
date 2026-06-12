---
title: "Can't start Software Center"
date: 2011-11-27
forum: General Help
---

### Post by Aleksey O. on 2011-11-27
Console output:
```
$ software-center
2011-11-27 11:18:10,608 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2011-11-27 11:18:13,570 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for ambiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
Traceback (most recent call last):
  File "/usr/share/software-center/update-software-center-agent", line 39, in <module>
    from softwarecenter.db.update import update_from_software_center_agent
  File "/usr/share/software-center/softwarecenter/db/update.py", line 91, in <module>
    cataloged_times = pickle.load(open(CF))
cPickle.UnpicklingError: unpickling stack underflow
2011-11-27 11:18:15,943 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 1
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1193, in show_lobby
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 125, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 109, in init_view
    SoftwarePane.init_view(self)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/softwarepane.py", line 261, in init_view
    self.icons, self.show_ratings)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/appview.py", line 76, in __init__
    self.helper = AppPropertiesHelper(db, cache, icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/models/appstore2.py", line 228, in __init__
    softwarecenter.paths.APP_INSTALL_PATH)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 111, in parse_applications_menu
    category = self._parse_menu_tag(child)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 267, in _parse_menu_tag
    l = self._parse_directory_tag(element)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 142, in _parse_directory_tag
    from softwarecenter.db.update import DesktopConfigParser
  File "/usr/share/software-center/softwarecenter/db/update.py", line 91, in <module>
    cataloged_times = pickle.load(open(CF))
cPickle.UnpicklingError: unpickling stack underflow
```I have see just Software Center window with toolbar (All apps, History, Installed) and that all, it's shows loading progress with no effect:(

---

### Post by Aleksey O. on 2011-11-28
Worked for me
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/891499](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/891499)

---

