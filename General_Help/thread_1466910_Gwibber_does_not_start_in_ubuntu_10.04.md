---
title: "Gwibber does not start in ubuntu 10.04"
date: 2010-04-30
forum: General Help
---

### Post by saini7002 on 2010-04-30
I installed ubuntu 10.04 today..but when i clicked on "broadcast  accounts"  nothing happened at all..I tried to run gwibber manually  but again nothing happened at all...the "chat accounts" are working  fine..the problem is only with gwibber..I searched different forums and  found that some users are experiencing this problem and others are  not...I want to know whether it is a bug...how can i fix it..plz help..

---

### Post by xtremesupremacy3 on 2010-04-30
Hello there,

I have been testing Ubuntu 10.04 from Beta 2 until now and unfortunately it is very unstable from my experience, I suggest daily updates, this you will need to do manually from either System, Administration and the Update Manager...or terminal using 'sudo apt-get update' and 'sudo apt-get upgrade'...In my experience Gwibber performs perfectly one day and is dead the next. Let's just hope the issue is sorted soon

---

### Post by sototallycarl on 2010-05-01
I have the same issue, however, i was able to get it running after a fresh boot, launched from terminal. Worked in every beta, even upgraded all the way to to release from a beta. Then I decided to do a nice clear fresh install and it doesn't work...

Might be some prefs I copied over or something as I never had issues with gwibber (beyond the keyring 100% processor bug that was fixed)

---

### Post by guitarMan666 on 2010-05-03
I am having the same issue with Gwibber. I have always had this problem with it, but I never bothered with it. However with a new release I wanted to take advantage of the new integration. On my very first reboot after the upgrade, Gwibber worked perfectly fine (didn't try to send anything out though I had nothing to say). It properly loaded my Twitter and Facebook feeds. On closing the window I was unable to get Gwibber to start again even after rebooting.

On a fresh boot, attempting to start Gwibber (either with the Menu, Gnome Do or the Indicator Applet) will crank the processor for a little while (visible on the monitor I have on the bottom panel) then nothing. Subsequent attempts produce only a short spike in processor use.

Attempting to start from the command line yields this:
```
$ gwibber

** (gwibber:16788): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:16788): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:16788): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
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
```

Hope this adds something meaningful. Any thoughts?

---

### Post by Sylvestra on 2010-05-04
I have the same problem and I just found a bug on launchpad for it:
[https://bugs.launchpad.net/gwibber/+bug/573522](https://bugs.launchpad.net/gwibber/+bug/573522)

hope that issue is resolved fast, i really liked the facebook support

---

### Post by Sylvestra on 2010-05-04
and here seems to be an older bug saying the same
[https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/530195](https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/530195)

... and still an older one:
[https://bugs.edge.launchpad.net/gwibber/+bug/523964](https://bugs.edge.launchpad.net/gwibber/+bug/523964)

i guess if you count all the duplicates, there might be quite a few people affected by this

---

### Post by xtremesupremacy3 on 2010-05-05
After having tried many ideas from launchpad, I am still just as confused as ever and doesn't do anything for me.

There is still no clearcut solved issue for this problem and I am monitoring the bug rapports, I will add to this post if a fully working workaround or fix has been found. I am just surprised to see that it has left out of the door without it working on an LTS to be honest

---

### Post by fragos on 2010-05-05
On my 10.04 Gwibber comes up very slowly and did fail to come up the first few times I tried it. I upgraded from 9.10 but Don't know if upgrade vs clean install had an effect.

---

### Post by bootbat on 2010-05-06
Facing the same issue. Gwibber does not launch on clicking "Set up Broadcast Accounts". An attempt to launch it from Terminal returns the following:

```
:~$ gwibber

** (gwibber:4492): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:4492): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:4492): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 50, in <module>
    from gwibber import client
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 3, in <module>
    import gtk, gobject, gwui, util, resources, actions, json, gconf
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 2, in <module>
    import os, json, urlparse, resources, util
  File "/usr/lib/python2.6/dist-packages/gwibber/util.py", line 2, in <module>
    from microblog.util.couch import RecordMonitor
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/util/couch.py", line 10, in <module>
    OAUTH_DATA = desktopcouch.local_files.get_oauth_tokens()
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 323, in get_oauth_tokens
    oauth_token_secrets = cf.items_in_section("oauth_token_secrets")[0]
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 189, in items_in_section
    raise ValueError("Section %r not present." % (section_name,))
ValueError: Section 'oauth_token_secrets' not present.
```

Is this bug resolved yet?

---

### Post by halfsane on 2010-05-08
I just wanted to chime in to say that I have the same problem.

---

### Post by fretinator on 2010-05-15
I have the same problem in a fresh install of the 10.04 release. I did not have this problem with then alpha or beta. The python error, as noted above, end with this line:

ValueError: Section 'oauth_token_secrets' not present.

I have tried everything, but this is a bummer. It prevents the use of gwibber as well as the configuration dialog of UbuntuOne. The actual UbuntuOne service works (files are copied up and down), I just can't open the configuration dialog due to the above error.

I have tried the command-line options that cause the web configuration to open (where you sign in with Launchpad user name and password), but the authentication never seems to "stick". 

As a possible clue, I did choose the automatically login option when I installed 10.04. I wonder if that causes an issue with the keyring, or something else related to authentication token.

At this point, I'm not sure even a fresh install (since that is what I started with) would work. I just don't think I will be able to use Gwibber or customize UbuntuOne.

---

### Post by Vince N on 2010-05-15
Just wanted to +1 on this.   I have noticed that if I go into System Monitor I can see Gwibber Service as sleeping.  If I kill this process and then attempt to load gwibber it seems to work normally for a while.

This is really annoying as I think this is one of the neater features of Lucid.  It would be nice if it were working properly.

---

### Post by guitarMan666 on 2010-05-16
Sounds like a condescending thing to say but make sure your systems are up to date with all the updates. I haven't had the problem nearly as often since a recent update, although it did occur once but a reboot fixed it.

---

### Post by Vince N on 2010-05-16
Just finished my daily updates if you must know.

---

### Post by ssdt on 2010-05-16
Still this problem persists in the system.

---

### Post by fretinator on 2010-05-16
Been updating every day to see if this issue would resolve. Nothing yet.

---

### Post by Coolpuppy on 2010-05-18
I shut is down the process and restarted and it seems to work... So far So good!!

---

### Post by mark_melvin on 2010-06-12
Same here.  Gwibber was working fine a day ago.  It just died today.

---

### Post by mark_melvin on 2010-06-12
Actually, rebooting solved my issue.  I think it may be related to suspending or hibernating.  I was experimenting with hibernation as my sound dies when resuming, then coincidentally Gwibber failed to start as well.

---

### Post by tidmarsh on 2010-08-05
+1
Gwibber worked day before yesterday. Yesterday it quit. Gwibber and Gwibber service show up in system monitor, but there's no program window. I've kept up with regular updates, and updated after it quit working and even uninstalled and reinstalled Gwibber. Still, I get nada.

---

