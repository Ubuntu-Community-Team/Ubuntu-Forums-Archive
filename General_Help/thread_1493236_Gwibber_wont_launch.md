---
title: "Gwibber wont launch"
date: 2010-05-25
forum: General Help
---

### Post by Arcath on 2010-05-25
I updated my machine from 9.10 to 10.04 and gwibber hasnt worked at all.

When i try to run it i get this the error message:
```
[21:02:20][arcath@Highgate ~]$ gwibber

** (gwibber:8182): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:8182): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:8182): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
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

---

### Post by meonkeys on 2010-05-27
See [https://bugs.launchpad.net/gwibber/+bug/544753](https://bugs.launchpad.net/gwibber/+bug/544753)

---

