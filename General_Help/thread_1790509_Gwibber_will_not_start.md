---
title: "Gwibber will not start"
date: 2011-06-25
forum: General Help
---

### Post by DogMatix on 2011-06-25
Gwibber won't start in Ubuntu Natty. It has previously been running fine but yesterday it failed to start. Starting it from a Terminal gives:

```
  File "/usr/bin/gwibber", line 87, in <module>
    client.Client()
  File "/usr/lib/python2.7/dist-packages/gwibber/client.py", line 623, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.7/dist-packages/gwibber/client.py", line 71, in __init__
    self.setup_ui()
  File "/usr/lib/python2.7/dist-packages/gwibber/client.py", line 254, in setup_ui
    if stream["stream"]:
KeyError: 'stream'

```

I have tried reinstalling it but the problem persists.

---

### Post by Toz on 2011-06-25
Have a look at: [//bugs.launchpad.net/ubuntu/+source/gwibber/+bug/778889]("//bugs.launchpad.net/ubuntu/+source/gwibber/+bug/778889"). Solution in post #2.

---

### Post by DogMatix on 2011-06-25
```
gconftool-2 --recursive-unset /apps/gwibber
```

Yep! that worked.

Thank you Toz

---

