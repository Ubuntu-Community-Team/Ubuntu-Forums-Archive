---
title: "Problems installing crebs"
date: 2011-12-27
forum: General Help
---

### Post by rmcellig on 2011-12-27
This is what I am typing into the terminal but am unsuccessful installing it. What am I doing wrong?


sudo add-apt-repository ppa:crebs/ppa
sudo apt-get update
sudo apt-get install crebs

sudo add-apt-repository ppa:crebs/ppa
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 60, in <module>
    sp = SoftwareProperties()	
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 538, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.7/dist-packages/aptsources/distro.py", line 91, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
randy@randyultimate ~ $

---

### Post by jerrrys on 2011-12-29
I am not finding a ppa for 11.10

[http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/](http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/)

---

