---
title: "Clicking on &quot;Broadcast&quot; under mail applet in Lucid does nothing"
date: 2010-04-27
forum: General Help
---

### Post by CTenorman on 2010-04-27
Hello,

I had gwibber working great until earlier today. Now it won't load when I click on the mail applet at the top of the screen and click on Broadcast.

When I try to load gwibber manually I get the following error:

** (gwibber:10043): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:10043): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:10043): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Updating...
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 67, in <module>
    client.Client()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 447, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 41, in __init__
    if len(json.loads(self.service.GetAccounts())) == 0:
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Python.AttributeError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/dispatcher.py", line 491, in GetAccounts
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
----------------



Any ideas?

---

### Post by CTenorman on 2010-04-27
OK, after randomly force-killing a few processes that looked related gwibber, the thing magically works again! It hadn't before even after a reboot, so I've no idea what fixed it. But I'm back in business!

---

