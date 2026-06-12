---
title: "Repo Adding Error"
date: 2009-11-22
forum: General Help
---

### Post by Prominence on 2009-11-22
I was trying to add a PPA and I had an error, please tell me how you fix it

grayson@Providence:~$ sudo add-apt-repository ppa:docky-core/ppa
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 28, in <module>
    sp = SoftwareProperties(options)	
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 536, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
grayson@Providence:~$

---

### Post by Prominence on 2009-11-22
> **Prominence said:**
> I was trying to add a PPA and I had an error, please tell me how you fix it

grayson@Providence:~$ sudo add-apt-repository ppa:docky-core/ppa
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 28, in <module>
    sp = SoftwareProperties(options)	
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 536, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
grayson@Providence:~$

Anyone?

---

