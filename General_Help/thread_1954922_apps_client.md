---
title: "apps client"
date: 2012-04-09
forum: General Help
---

### Post by huynhhuuhieu on 2012-04-09
i have some wrongs with gwibber and rhymbox
they can't access to facebook, libre.fm. running them via terminal i get warms
```
huynhhuuhieu@huynhhuuhieu:~$ gwibber

(gwibber:4716): Gtk-CRITICAL **: gtk_radio_button_set_group: assertion `!g_slist_find (group, radio_button)' failed

(gwibber:4716): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
Loading plugin for identica
Loading plugin for facebook
Loading plugin for twitter
```
```
huynhhuuhieu@huynhhuuhieu:~$ rhythmbox
Sense key: 0x72 0x0b 0x47 0x00 0x00 0x00 0x00 0x0e 0x09 0x0c 0x00 0x00 0x00 0x02 0x00 0x00 0x00 0x00 0x00 

** (rhythmbox:4750): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 707, in get_info
    return self.service.folders.get_info(path)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 156, in inner
    result = f(*new_args, **new_kwargs)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/logger.py", line 269, in inner
    res = f(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 707, in get_info
    mdobj = self.fs_manager.get_by_path(path)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 780, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/huynhhuuhieu/.ubuntuone/Purchased from Ubuntu One'


** (rhythmbox:4750): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

(rhythmbox:4750): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```
could you help me.

---

### Post by dino99 on 2012-04-09
Please post the output of :    cat  /etc/apt/sources.list

---

### Post by huynhhuuhieu on 2012-04-10
there's no thing in there
             :p
for gwibber, i can't add account. it shows 
```
[COLOR=#000000][FONT=sans-serif]**Unable to load page**
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Problem occurred while loading the URL http://api.twitter.com/oauth/authorize?oauth_token=WgZWfrIJHdHDFzTGMPZOBcCGwK2UfGfLJrbk58sH9Y
Cannot resolve proxy hostname ()
[/FONT][/COLOR]

```
for rhythmbox: ```
connection error, please try logging again
```

---

