---
title: "Software Sources not opening"
date: 2010-03-26
forum: General Help
---

### Post by JohnJD on 2010-03-26
I go to System-->Administration-->Software Sources and the app doesn't launch.  I try to launch from the terminal using its command, and here is what I get:

```

johnny@johnny-desktop:~$ gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
  File "/usr/bin/software-properties-gtk", line 110, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 87, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 536, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

```

From this, can anyone tell what is wrong?

---

