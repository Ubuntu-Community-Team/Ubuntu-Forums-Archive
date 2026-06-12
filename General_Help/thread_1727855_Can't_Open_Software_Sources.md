---
title: "Can't Open Software Sources"
date: 2011-04-13
forum: General Help
---

### Post by klausner on 2011-04-13
On a new (re-)install of 10.04LTS, can't get *System->Administration->Software Sources* to open. In Synaptic I can't get the *Settings->Repositories* to open either.

Trying from the command line, I get:> $ sudo  /usr/bin/software-properties-gtk
[sudo] password for ********: 
[INDENT]Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 113, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 87, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 536, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template[/INDENT]

Adding repositories was almost the first thing I tried after the new install. So why can't I get it to work?

---

### Post by austinium on 2011-04-13
Have a look here, it might be of help.
[http://getsatisfaction.com/jolicloud/topics/software_properties_gtk_could_not_find_a_distribution_template_error]("http://getsatisfaction.com/jolicloud/topics/software_properties_gtk_could_not_find_a_distribution_template_error")

Google comes up with a lot of responses if you search for the last line of the error output.

---

### Post by klausner on 2011-04-13
Found the answer in Launchpad bugs. Turns out I had a bad version of */usr/share/python-apt/templates/Ubuntu.info*. I copied one from another Lucid system, and that fixed things.

---

