---
title: "APT add repository problem"
date: 2011-09-20
forum: General Help
---

### Post by sptutusukanta on 2011-09-20
I'm trying to run this command:
```
sudo add-apt-repository ppa:gdm2setup/gdm2setup
```
It gives me an error:
```
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 55, in <module>
    sp = SoftwareProperties()	
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 538, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

```

What can I do now??

---

### Post by gmargo on 2011-09-20
Not enough information provided: You don't say what version of Ubuntu you are running.

That particular PPA, [https://launchpad.net/~gdm2setup/+archive/gdm2setup]("https://launchpad.net/%7Egdm2setup/+archive/gdm2setup") is only available for Lucid and Karmic.  Are you running one of those?

---

