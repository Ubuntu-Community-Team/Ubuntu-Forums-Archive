---
title: "Can't open Software Sources"
date: 2009-11-22
forum: General Help
---

### Post by Prominence on 2009-11-22
Whenever I attempt to open my Software Sources, it won't open, under Terminal, this is what it said, is there any possible solution? 

grayson@Providence:~$ gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
/home/grayson/.themes/Wasp-Alt/gtk-2.0/panels/panel.rc:7: Unable to locate image file in pixmap_path: "/panels/panel-bg-dark.png"
/home/grayson/.themes/Wasp-Alt/gtk-2.0/panels/panel.rc:12: Unable to locate image file in pixmap_path: "/panels/panel-bg-dark.png"
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
grayson@Providence:~$

---

### Post by Darin on 2009-11-22
I'm having the same problem. Have you installed any Mint-related packages recently? After looking around, it seems that's what's causing the problem for me... but I can't find any way to fix it. Apparently some Mint package modifies some system files, which disables Software Sources. My gnome-system-monitor also let's me know I'm running LinuxMint, even though I'm running Karmic.

Uninstalling software-properties-gtk allows you to use the Synaptic repository manager... but this makes you uninstall apturl, and ubuntu-desktop, which could cause upgrade problems later. I think it's also not as easy to add PPAs.

Hopefully someone will have some solution, but I've uninstalled, reinstalled, and changed a bunch of stuff with no luck.

- Darin

---

### Post by Prominence on 2009-11-22
Yes exactly, the Mint packages, there needs to be a way to correct this, if someone in the community could perhaps make a solution

---

