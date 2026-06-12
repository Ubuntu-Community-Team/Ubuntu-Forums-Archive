---
title: "can't use software sources, add-apt etc"
date: 2009-12-04
forum: General Help
---

### Post by joey-elijah on 2009-12-04
NO idea how this broke, but i can't open software properties or use add-apt in a terminal.

I get the following: -

raceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 28, in <module>
    sp = SoftwareProperties(options)    
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 536, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

Is there an easy way to fix this? Should i roll back to a previous version of something?

---

### Post by The Zezima of &#370;buntu on 2009-12-04
What's add-apt? The only command I've used that's close to that is apt-get. But then I've only been using Ubuntu for about 6 months now.

---

### Post by joey-elijah on 2009-12-04
> **The Zezima of &#370 said:**
> What's add-apt? The only command I've used that's close to that is apt-get. But then I've only been using Ubuntu for about 6 months now.

sudo add-apt-repository ppa:blahblah/whatever

I've tried the fix mentioned @ [https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/364092](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/364092) but still no hable.

Edit: I've since tried a ton of stuff from other bug reports. I don't know what to do... I really don't want to have reinstall my entire operating system in order to be able to manage software sources...

---

