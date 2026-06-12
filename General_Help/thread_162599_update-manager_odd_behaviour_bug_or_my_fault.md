---
title: "update-manager odd behaviour: bug or my fault?"
date: 2006-04-19
forum: General Help
---

### Post by red_Marvin on 2006-04-19
Sometimes when I run update-manager it behaves oddly, sometimes #1 sometimes #2:

1) When I press install the downloading window flashes for <1s and nothing gets downloaded or installed.
I have to press reload to make it work, sometimes restart the app.

2) When I preess install or reload there is an error on the console:
[I]Traceback (most recent call last):
  File "/usr/bin/update-manager", line 369, in run_synaptic
    apt_pkg.PkgSystemUnLock()
SystemError: E:Not locked[/I]
and have to restart the application.

---

