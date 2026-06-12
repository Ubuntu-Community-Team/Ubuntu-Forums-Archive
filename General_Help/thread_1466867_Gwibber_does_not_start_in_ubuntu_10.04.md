---
title: "Gwibber does not start in ubuntu 10.04"
date: 2010-04-30
forum: General Help
---

### Post by saini7002 on 2010-04-30
I installed ubuntu 10.04 today..but when i clicked on "broadcast accounts" of nothing happened at all..I tried to run gwibber manually but again nothing happed at all...the "chat accounts" are working fine..the problem is only with gwibber..I searched different forums and found that some users are experiencing this problem and others are not...I want to know whether it is a bug...how can i fix it..plz help..

---

### Post by ssdt on 2010-05-07
Facing the same problem. Anyone please help as soon as possible. Please notice this because even a bug report cannot be made as nothing opens up.

---

### Post by Sslaxx on 2010-05-08
To bump this up and give a little more background as to the problem some of us seem to be running into.

Running Gwibber from the command-line causes this to happen:

[QUOTE="stuart@sslaxxworks:~$ gwibber"]** (gwibber:4582): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:4582): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:4582): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
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
AttributeError: 'NoneType' object has no attribute 'makefile'[/QUOTE]

---

### Post by philinux on 2010-05-08
Moved to General Help.

---

### Post by warjowuch on 2010-05-08
This problem has a lot of bug reports in Launchpad!
look [here]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=WARNING+**%3A+Trying+to+register+gtype+%27WnckWindowActions%27+as+enum+when+in+fact+it+is+of+type+%27GFlags%27&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=") for a lot of bug reports and subscribe ourselves!

---

