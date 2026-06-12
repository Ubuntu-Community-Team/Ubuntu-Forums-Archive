---
title: "Gwibber Fail of epic propotions"
date: 2010-05-01
forum: General Help
---

### Post by Elie-M on 2010-05-01
This is the error generated:

```

elie-m@elie-m-laptop:~$ gwibber

** (gwibber:7207): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:7207): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:7207): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 67, in <module>
    client.Client()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 447, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 29, in __init__
    self.model = gwui.Model()
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 42, in __init__
    self.settings = util.SettingsMonitor()
  File "/usr/lib/python2.6/dist-packages/gwibber/util.py", line 91, in __init__
    DEFAULT_SETTINGS)
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/util/couch.py", line 66, in __init__
    self.database = CouchDatabase(dbname, create=True)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server.py", line 57, in __init__
    server_class=server_class, oauth_tokens=oauth_tokens, ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 152, in __init__
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

```


any idea?

---

### Post by Elie-M on 2010-05-01
bump

---

### Post by cygnis1 on 2010-05-02
I have installed Gwibber(2.0.0) on my Karmic machine and it is not connecting to my Facebook account.  I have authorized Gwibber on my account settings (notifications).  My account shows up in Gwibber, but I can't authorize the account.  I get a notification of success from Gwibber, but there is nothing there, other than my account name.  This is the error message from Gwibber:
receive failed with error on facebook 18 hours ago
            Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/__init__.py", line 130, in run
    messages = self.perform_operation(opdata)
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/__init__.py", line 107, in perform_operation
    for message in output:
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/facebook.py", line 161, in receive
    stream = self.get_messages()
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/facebook.py", line 158, in get_messages
    return self.facebook.stream.get(self.facebook.uid, limit=80)
  File "", line 10, in get
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/support/facelib.py", line 433, in __call__
    return self._client('%s.%s' % (self._name, method), args)
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/support/facelib.py", line 845, in __call__
    c.perform()
error: (28, 'SSL connection timeout')

---

### Post by cygnis1 on 2010-05-02
I opened Gwibber with the terminal and got this error message:

john@john-laptop:~$ Gwibber
No command 'Gwibber' found, did you mean:
 Command 'gwibber' from package 'gwibber' (universe)
Gwibber: command not found
john@john-laptop:~$ gwibber
WARNING:root:desktopcouch is not available. .  falling back to gconf

** (gwibber:6168): WARNING **: Trying to register gtype 'WnckWindowState' as flags when in fact it is of type 'GEnum'

** (gwibber:6168): WARNING **: Trying to register gtype 'WnckWindowActions' as flags when in fact it is of type 'GEnum'

** (gwibber:6168): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as flags when in fact it is of type 'GEnum'

---

### Post by williamson389 on 2010-05-02
Umm yeah im getting the same error message.  gwibber wont open for me from the menu.  I just updated to 10.4 and was trying to utilize the broadcast accounts thing but ran into trouble there.  It too has no response.

pretty much <bump>

---

### Post by madmaxo on 2010-05-03
I'm having the same problem! Any ideas?

---

### Post by Elie-M on 2010-05-04
okay guyz I'm the thread maker. For those who have MY ERROR, please go to:

[http://code.google.com/p/httplib2/issues/detail?id=62](http://code.google.com/p/httplib2/issues/detail?id=62)

and find the Fail_to_connect_crashes.diff and use the command patch to patch the diff file to make the desired changes.

HOWEVER, some other error happened to me after applying the patch successfully as noted in my post in:

[https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/534941](https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/534941)

read my post and see my error if that happens to u or not and go file a report after my post in:

[https://bugs.launchpad.net/ubuntu/+source/desktopcouch/+bug/522538](https://bugs.launchpad.net/ubuntu/+source/desktopcouch/+bug/522538)

because as they say it must be fixed in the latest patch of gwibber but it's not.

---

### Post by vivek40 on 2010-05-04
Hi i was able to resolve this by following this link  [https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/533017/comments/25](https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/533017/comments/25) .. it does look like a workaround as of now.. but can be tried

---

### Post by toiletgoose on 2010-05-04
Getting a different error, one that I haven't seen around the web yet, and this is on a new x64 install of Lucid:

** (gwibber:6208): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:6208): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:6208): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 67, in <module>
    client.Client()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 447, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 29, in __init__
    self.model = gwui.Model()
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 42, in __init__
    self.settings = util.SettingsMonitor()
  File "/usr/lib/python2.6/dist-packages/gwibber/util.py", line 91, in __init__
    DEFAULT_SETTINGS)
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/util/couch.py", line 66, in __init__
    self.database = CouchDatabase(dbname, create=True)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server.py", line 57, in __init__
    server_class=server_class, oauth_tokens=oauth_tokens, ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 152, in __init__
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
  File "/usr/lib/pymodules/python2.6/httplib2/__init__.py", line 865, in _conn_request
    raise ServerNotFoundError("Unable to find the server at %s" % conn.host)
httplib2.ServerNotFoundError: Unable to find the server at localhost

Used to love Gwibber... going to have to install choqok again until they sort the issues they are having with gwibber out.

---

### Post by ru_wing on 2010-05-04
Here is what I'm getting. Although my error is different too:
 $ gwibber

** (gwibber:9047): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:9047): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:9047): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 67, in <module>
    client.Client()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 447, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 29, in __init__
    self.model = gwui.Model()
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 42, in __init__
    self.settings = util.SettingsMonitor()
  File "/usr/lib/python2.6/dist-packages/gwibber/util.py", line 91, in __init__
    DEFAULT_SETTINGS)
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/util/couch.py", line 66, in __init__
    self.database = CouchDatabase(dbname, create=True)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server.py", line 57, in __init__
    server_class=server_class, oauth_tokens=oauth_tokens, ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 152, in __init__
    self._reconnect()
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 176, in _reconnect
    if self._database_name not in self._server:
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 124, in __contains__
    self.resource.head(validate_dbname(name))
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 981, in head
    return self._request('HEAD', path, headers=headers, **params)
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 1035, in _request
    raise ServerError((status_code, error))
couchdb.client.ServerError: (400, '')

---

### Post by StickGrinder on 2010-05-06
The same for me: brand new installation of Lucid, first run worked well, then, after some upgrades and package installations, here is my error:

paolo@loki:~$ gwibber

** (gwibber:7379): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:7379): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:7379): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 67, in <module>
    client.Client()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 447, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 29, in __init__
    self.model = gwui.Model()
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 42, in __init__
    self.settings = util.SettingsMonitor()
  File "/usr/lib/python2.6/dist-packages/gwibber/util.py", line 91, in __init__
    DEFAULT_SETTINGS)
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/util/couch.py", line 66, in __init__
    self.database = CouchDatabase(dbname, create=True)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server.py", line 57, in __init__
    server_class=server_class, oauth_tokens=oauth_tokens, ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 152, in __init__
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

---

### Post by Elie-M on 2010-05-07
apparently StickGrinder u don't read the topic posts.

---

### Post by Perturbed Penguin on 2010-05-09
Yep I get the same errors.

For me I connected to facebook fine the first time and then I decided to remove my fb account from gwibber b/c I decided I no use for gwibber. I later decided that being able to update my fb status from the memenu was worth using gwibber so I tried to re-add my fb account to gwibber and now after the authorization process it says I'm authorized but when I click 'add' it doesn't do anything and I can't re-add my account.

---

### Post by gnuts on 2010-05-14
I was having the same error, after the most recent update 5/13/10. then magically this morning it is working again. It still gives the following errors when started though:

** (gwibber:3171): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:3171): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:3171): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Updating...
Updating...
/usr/bin/gwibber:68: GtkWarning: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
  gtk.main()

I hope that helps someone.

---

### Post by Kenda on 2010-05-14
Mee Too with this one. I'm afraid. :(

---

### Post by Elie-M on 2010-05-14
this is THE buggiest application *just to be polite and not saying another word* I've ever seen in my life. it's worst than windows vista.

---

### Post by mordoc on 2010-05-15
For the time being I gave up and am using Pino for Twittering:

[http://pino-app.appspot.com/](http://pino-app.appspot.com/)

---

### Post by Elie-M on 2010-05-16
wulda solved that issue long ago if it was only a twitter concern.. I want to use facebook much more than my twitter.....  there's plenty of apps for twitter but not much for fbook other than gwibber...

---

### Post by toiletgoose on 2010-06-15
Another good twitter app that is in the repository I think is: QWIT. So when I am using Gnome I fire this one up, in KDE I fire up Choqok... but the nagging about account credentials is starting to get to me.

I would love it if they could sort out the bugs in Gwibber so that I could enjoy the unified messaging system everyone else seems to have. I haven't seen too many other people with the httplib2.ServerNotFoundError problem. I have done a complete re-install and haven't had any better luck.

---

### Post by toiletgoose on 2010-08-06
Regarding my:

** (gwibber:620: WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:620: WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:620: WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
File "/usr/bin/gwibber", line 67, in <module>
client.Client()
File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 447, in __init__
self.w = GwibberClient()
File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 29, in __init__
self.model = gwui.Model()
File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 42, in __init__
self.settings = util.SettingsMonitor()
File "/usr/lib/python2.6/dist-packages/gwibber/util.py", line 91, in __init__
DEFAULT_SETTINGS)
File "/usr/lib/python2.6/dist-packages/gwibber/microblog/util/couch.py", line 66, in __init__
self.database = CouchDatabase(dbname, create=True)
File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server.py", line 57, in __init__
server_class=server_class, oauth_tokens=oauth_tokens, ctx=ctx)
File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 152, in __init__
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
File "/usr/lib/pymodules/python2.6/httplib2/__init__.py", line 865, in _conn_request
raise ServerNotFoundError("Unable to find the server at %s" % conn.host)
httplib2.ServerNotFoundError: Unable to find the server at localhost

Found out on a fresh install that before installing the fglrx drivers it worked fine... once the ATI stuff was installed these errors started happening.

Gwibber (at least on my computer) doesn't seem to want to play nice with the fglrx driver.

---

### Post by Baldemar on 2010-08-08
This is what I get, I have FB on my Gwibber but my stream is 2 days old.


** (gwibber:3539): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:3539): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:3539): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Updating...
Updating...
/usr/bin/gwibber:68: GtkWarning: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
  gtk.main()

---

### Post by awi on 2010-08-09
I have the exact same problem as **Baldemar**, on Lucid fully updated. :(

---

