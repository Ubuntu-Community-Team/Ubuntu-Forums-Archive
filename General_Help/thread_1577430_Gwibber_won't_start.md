---
title: "Gwibber won't start"
date: 2010-09-18
forum: General Help
---

### Post by EienTatsu on 2010-09-18
Gwibber won't run and when i try from command line i get this


```
** (gwibber:24804): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:24804): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:24804): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Updating...
Updating...
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 67, in <module>
    client.Client()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 448, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 59, in __init__
    self.setup_ui()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 145, in setup_ui
    self.stream_view.set_state(self.model.settings["streams"] or DEFAULT_SETTINGS["streams"])
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 492, in set_state
    for item in state: self.new_stream(item)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 486, in new_stream
    if state: item.set_state(state)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 626, in set_state
    self.update()
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 619, in update
    self.message_view.render([self.selected_stream["view"]])
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 737, in render
    accounts=accounts)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 279, in render
    content = template.render(theme=util.get_theme_colors(), resources=resources, _=_, **kwargs)
  File "/usr/lib/pymodules/python2.6/mako/template.py", line 133, in render
    return runtime._render(self, self.callable_, args, data)
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 364, in _render
    _render_context(template, callable_, context, *args, **_kwargs_for_callable(callable_, data))
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 381, in _render_context
    _exec_template(inherit, lclcontext, args=args, kwargs=kwargs)
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 414, in _exec_template
    callable_(context, *args, **kwargs)
  File "memory:0x2d94090", line 207, in render_body
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 255, in <lambda>
    return lambda *args, **kwargs:callable_(self.context, *args, **kwargs)
  File "base_mako", line 805, in render_messages
  File "memory:0x2d94090", line 84, in message
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 255, in <lambda>
    return lambda *args, **kwargs:callable_(self.context, *args, **kwargs)
  File "base_mako", line 317, in render_sidebar
KeyError: 'sender'
```

---

### Post by fragos on 2010-09-18
Make sure you're running Gwibber 2.30.2. Twitter made some changes in authorization API that were fixed in 2.30.2

---

### Post by roignac on 2010-09-20
Please, specify which Gwibber version are you using and which protocols have you added (if you did)

---

### Post by EienTatsu on 2010-09-21
version 2.30.2

I'm using facebook and twitter

---

### Post by juuri on 2010-10-04
I'm having the same problem here.

Tried removing and re-installing it, but it didn't help.

> 
** (gwibber:22941): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:22941): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:22941): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Updating...
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 67, in <module>
    client.Client()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 448, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 42, in __init__
    if len(json.loads(self.service.GetAccounts())) == 0:
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Python.AttributeError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/dispatcher.py", line 493, in GetAccounts
    for account in self.accounts.get_records(COUCH_TYPE_ACCOUNT, True):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 482, in get_records
    exists = self.view_exists(view_name, design_doc)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 429, in view_exists
    self.with_reconnects(self.db.__getitem__, doc_id)["views"]
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 168, in with_reconnects
    self._reconnect()
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 176, in _reconnect
    if self._database_name not in self._server:
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 124, in __contains__
    self.resource.head(validate_dbname(name))
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 981, in head
    return self._request('HEAD', path, headers=headers, **params)
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 1014, in _request
    resp, data = _make_request()
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 1009, in _make_request
    body=body, headers=headers)
  File "/usr/lib/pymodules/python2.6/httplib2/__init__.py", line 1129, in request
    (response, content) = self._request(conn, authority, uri, request_uri, method, body, headers, redirections, cachekey)
  File "/usr/lib/pymodules/python2.6/httplib2/__init__.py", line 901, in _request
    (response, content) = self._conn_request(conn, request_uri, method, body, headers)
  File "/usr/lib/pymodules/python2.6/httplib2/__init__.py", line 871, in _conn_request
    response = conn.getresponse()
  File "/usr/lib/python2.6/httplib.py", line 984, in getresponse
    method=self._method)
  File "/usr/lib/python2.6/httplib.py", line 330, in __init__
    self.fp = sock.makefile('rb', 0)
AttributeError: 'NoneType' object has no attribute 'makefile'


current version: 2.30.2-0ubuntu2

---

### Post by EienTatsu on 2010-10-04
Mine still doesn't work

---

### Post by CTJ73 on 2010-10-11
Updated to 10.10 and gwibber won't start now

laptop:~$ gwibber

** (gwibber:17989): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:17989): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:17989): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 72, in <module>
    client.Client()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 540, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 61, in __init__
    self.setup_ui()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 211, in setup_ui
    self.stream_view.set_state(streams)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 406, in set_state
    self.update()
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 393, in update
    self.messages.update(self.navigation.selected_stream)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 724, in update
    self.messages = self.message_view.render([selected_stream], count)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 782, in render
    accounts=accounts)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 256, in render
    content = template.render(theme=util.get_theme_colors(), resources=resources, _=_, **kwargs)
  File "/usr/lib/pymodules/python2.6/mako/template.py", line 189, in render
    return runtime._render(self, self.callable_, args, data)
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 403, in _render
    _render_context(template, callable_, context, *args, **_kwargs_for_callable(callable_, data))
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 434, in _render_context
    _exec_template(inherit, lclcontext, args=args, kwargs=kwargs)
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 457, in _exec_template
    callable_(context, *args, **kwargs)
  File "memory:0xab6ec8c", line 170, in render_body
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 278, in <lambda>
    return lambda *args, **kwargs:callable_(self.context, *args, **kwargs)
  File "base_mako", line 192, in render_messages
  File "memory:0xab6ec8c", line 133, in message
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 278, in <lambda>
    return lambda *args, **kwargs:callable_(self.context, *args, **kwargs)
  File "base_mako", line 269, in render_fold
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 278, in <lambda>
    return lambda *args, **kwargs:callable_(self.context, *args, **kwargs)
  File "base_mako", line 705, in render_location
KeyError: 'lon'

---

### Post by fragos on 2010-10-11
For what it's worth I have two Twitter accounts and Gwibber works well. I tried starting it from the command line and got these three warnings but none of your other messages.

fragos@Geo:~$ gwibber
** (gwibber:18897): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:18897): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:18897): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
/usr/bin/gwibber:73: GtkWarning: IA__gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
  gtk.main()
fragos@Geo:~$

---

### Post by EienTatsu on 2010-10-11
It works now that I upgraded to 10.10

---

### Post by CTJ73 on 2010-10-11
> **EienTatsu said:**
> It works now that I upgraded to 10.10

huh, mine worked in 10.04 and broke when I went to 10.10

---

### Post by hencethus on 2010-11-18
Just in case anyone is still having this problem (and I'll bet there are plenty that are), I was finally able to fix this by deleting all the Gwibber CouchDB databases, then uninstalling and reinstalling Gwibber.

Use
```
xdg-open ~/.local/share/desktop-couch/couchdb.html
```
to access the databases. Delete all the ones that start with Gwibber.

Then kill the gwibber and gwibber-service processes before running
```
sudo aptitude purge gwibber gwibber-service
sudo aptitude install gwibber gwibber-service
```

Then hope it doesn't happen again :-/

---

### Post by peperomia on 2010-12-21
> **hencethus said:**
> Just in case anyone is still having this problem (and I'll bet there are plenty that are), I was finally able to fix this by deleting all the Gwibber CouchDB databases, then uninstalling and reinstalling Gwibber.

Use
```
xdg-open ~/.local/share/desktop-couch/couchdb.html
```to access the databases. Delete all the ones that start with Gwibber.

Then kill the gwibber and gwibber-service processes before running
```
sudo aptitude purge gwibber gwibber-service
sudo aptitude install gwibber gwibber-service
```Then hope it doesn't happen again :-/

Thanks! This solved the problem for me!

UPDATE: Unfortunately, it wasn't a permanent solution. The next time I closed gwibber, I had to delete the gwibber CouchDB databases again to relaunch it...

---

