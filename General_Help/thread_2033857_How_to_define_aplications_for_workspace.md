---
title: "How to define aplications for workspace"
date: 2012-07-27
forum: General Help
---

### Post by miguelpires on 2012-07-27
Hello,
How can I define the aplications that start in a defined workspace:

Example:
Workspace 1 - firefox
Workspace 2 - Games
Workspace 3 - Thunderbird
Workspace 4 - Virtualbox

Anyone know how can this be setuo?
Regard's
Miguel Pires

---

### Post by dcstar on 2012-07-27
> **miguelpires said:**
> Hello,
How can I define the aplications that start in a defined workspace:

Example:
Workspace 1 - firefox
Workspace 2 - Games
Workspace 3 - Thunderbird
Workspace 4 - Virtualbox

Anyone know how can this be setuo?
Regard's
Miguel Pires
This is how I start Firefox in #2:
```
#!/bin/bash

sleep 3 && wmctrl -s1 && firefox & wmctrl -s0 &

exit 0
```
Might still work in 12.04 - give it a try.

---

