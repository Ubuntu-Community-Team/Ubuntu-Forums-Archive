---
title: "apt-broken?"
date: 2010-11-10
forum: General Help
---

### Post by Verbeck on 2010-11-10
just now when i tried to add the chromium ppa this showed up
```
me@my-laptop ~ $ sudo apt-add-repository ppa:chromium-daily/ppa
Traceback (most recent call last):
  File "/usr/bin/apt-add-repository", line 40, in <module>
    sp = SoftwareProperties(options)    
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 538, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

```
how could this be fixed?

---

### Post by Ancanus on 2010-11-10
This seems relevant:
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/364092](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/364092)

There is a solution in comment 7. Be sure to use your current distribution version.

---

### Post by Verbeck on 2010-11-10
Thanx.seems to have fixed it ;)

---

