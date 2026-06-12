---
title: "system-config-kickstart does not work?"
date: 2006-06-26
forum: General Help
---

### Post by johann_p on 2006-06-26
I have installed this from a repository with the ubuntu logo beside it: package system-config-kickstart

When I run "system-config-kickstart --generate x"
I get the following error:

Traceback (most recent call last):
  File "/usr/share/system-config-kickstart/system-config-kickstart.py", line 58, in ?
    useCliMode(value)
  File "/usr/share/system-config-kickstart/system-config-kickstart.py", line 41, in useCliMode
    import profileSystem
  File "/usr/share/system-config-kickstart/profileSystem.py", line 23, in ?
    import language_backend
ImportError: No module named language_backend

Any workarounds or experiences with this?

---

### Post by johann_p on 2007-09-07
After two years, this bug is still there :(

no love for [https://bugs.launchpad.net/ubuntu/+source/system-config-kickstart/+bug/15156](https://bugs.launchpad.net/ubuntu/+source/system-config-kickstart/+bug/15156)

---

