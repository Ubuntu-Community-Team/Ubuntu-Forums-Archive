---
title: "DockbarX problem"
date: 2010-01-24
forum: General Help
---

### Post by grantoos on 2010-01-24
Hi,

I'm new to Ubuntu and I've installed Dockbarx and all went well.  Then for some reason now when I click on the Properties option, all I get is a tiny minimized window and it's empty!  I'm thinking it's something to do with the way dockbarx is starting up, so I re-installed it, restarted/logout, etc and the same thing keeps happening.

Any suggestions on how to fix this?

Thanks.

---

### Post by grantoos on 2010-01-24
Here's some code, maybe this will help.  Thanks.

```
** (dockbarx.py:4838): WARNING **: Trying to register gtype 'WnckWindowState' as flags when in fact it is of type 'GEnum'

** (dockbarx.py:4838): WARNING **: Trying to register gtype 'WnckWindowActions' as flags when in fact it is of type 'GEnum'

** (dockbarx.py:4838): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as flags when in fact it is of type 'GEnum'
dockbar init
Traceback (most recent call last):
  File "/usr/bin/dockbarx.py", line 4430, in <module>
    dockbarwin = DockBarWindow()
  File "/usr/bin/dockbarx.py", line 4398, in __init__
    self.dockbar = DockBar(None)
  File "/usr/bin/dockbarx.py", line 3770, in __init__
    self.reload()
  File "/usr/bin/dockbarx.py", line 3810, in reload
    self.themes = self.find_themes()
  File "/usr/bin/dockbarx.py", line 3881, in find_themes
    for f in os.listdir(dir):
OSError: [Errno 20] Not a directory: '/home/grantoos/.dockbarx/themes'
```

---

### Post by M7S on 2010-01-25
You can fix that problem easy by making a folder .dockbarx in your home folder and a folder named themes in .dockbarx. I'll look into this and fix this bug to the next version. You use version 0.24.0 right?

M7S,
DockbarX developer

---

### Post by grantoos on 2010-01-25
Thanks for the reply, that fixed it!  Yes, I'm using 0.24.0.

---

