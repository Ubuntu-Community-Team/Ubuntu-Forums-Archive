---
title: "Software centre has stopped working"
date: 2011-10-11
forum: General Help
---

### Post by jonathanpeter on 2011-10-11
My software centre has stopped working.  When I load, it tries forever to load the categories.  

When run from the command line, I get the following message.  Any ideas please?

/usr/share/software-center/softwarecenter/app.py:1191: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.window_main.show_all()
2011-10-11 13:52:16,178 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.7/zeitgeist/client.py', 367, 'reconnect_monitors')'
2011-10-11 13:52:16,178 - zeitgeist.client - INFO - Reconnected to Zeitgeist engine...
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/app.py", line 508, in on_view_switcher_changed
    self.view_manager.set_active_view(view_id)
  File "/usr/share/software-center/softwarecenter/view/viewmanager.py", line 39, in set_active_view
    active_view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/view/availablepane.py", line 126, in init_view
    SoftwarePane.init_view(self)
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 276, in init_view
    if self.db:
  File "/usr/share/software-center/softwarecenter/db/database.py", line 445, in __len__
    return self.xapiandb.get_doccount()
AttributeError: 'StoreDatabase' object has no attribute 'xapiandb'
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/utils.py", line 87, in <lambda>
    glib.timeout_add(500, lambda: wrapper(*args, **kwargs))
  File "/usr/share/software-center/softwarecenter/utils.py", line 92, in wrapper
    f(*args, **kwargs)
  File "/usr/share/software-center/softwarecenter/models/viewswitcherlist.py", line 166, in _update_channel_list
    self._update_channel_list_available_view()
  File "/usr/share/software-center/softwarecenter/models/viewswitcherlist.py", line 188, in _update_channel_list_available_view
    for channel in self.channel_manager.channels:
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 65, in channels
    return self._get_channels()
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 191, in _get_channels
    for channel_iter in self.db.xapiandb.allterms("XOL"):
AttributeError: 'StoreDatabase' object has no attribute 'xapiandb'
2011-10-11 13:52:17,235 - softwarecenter.app - INFO - software-center-agent finished with status 1
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 153, in _check_for_channel_updates_timer
    if self._check_for_channel_updates():
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 171, in _check_for_channel_updates
    for channel in self.channels:
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 65, in channels
    return self._get_channels()
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 191, in _get_channels
    for channel_iter in self.db.xapiandb.allterms("XOL"):
AttributeError: 'StoreDatabase' object has no attribute 'xapiandb'

---

