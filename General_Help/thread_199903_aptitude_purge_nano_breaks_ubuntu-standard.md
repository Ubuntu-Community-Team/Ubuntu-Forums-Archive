---
title: "aptitude purge nano breaks ubuntu-standard?"
date: 2006-06-19
forum: General Help
---

### Post by ewaguespack on 2006-06-19
I would like to remove nano, for no other reason than I just dont want it, but it breaks the virtual package ubuntu-standard... if I allow it to do so, what are the ramifications?

root@iceman:/home# aptitude purge nano
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  ubuntu-standard
The following packages have been kept back:
  capplets-data desktop-file-utils eog gdm gnome-about gnome-accessibility-themes gnome-applets gnome-applets-data gnome-control-center
  gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-media gnome-panel gnome-panel-data gnome-screensaver gnome-session gnome-terminal
  gnome-terminal-data gnome-themes gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtkhtml3.8
  language-pack-en language-pack-gnome-en libgd2-xpm libglibmm-2.4-1c2a libgnome-desktop-2 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomevfs2-0
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml3.8-15 libgtkmm-2.4-1c2a libmetacity0
  libmysqlclient15off libnautilus-burn3 libpanel-applet2-0 libpango1.0-0 libpango1.0-common libqt3-mt libsoup2.2-8 libvte-common libvte4 libwnck-common
  libwnck18 linux-386 linux-image-386 linux-restricted-modules-386 linux-restricted-modules-common metacity mysql-client mysql-client-5.0 mysql-common
  mysql-server mysql-server-5.0 nautilus-cd-burner pcmcia-cs python-pyorbit python-vte python2.4-pyorbit sound-juicer wpasupplicant yelp
The following packages will be REMOVED:
  nano{p}
0 packages upgraded, 0 newly installed, 1 to remove and 78 not upgraded.
Need to get 0B of archives. After unpacking 1450kB will be freed.
The following packages have unmet dependencies:
  ubuntu-standard: Depends: nano but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-base
ubuntu-standard

Score is -654

Accept this solution? [Y/n/q/?]

---

### Post by 5-HT on 2006-06-19
ubuntu-standard is simply a metapackage that makes upgrading/installing a base Ubuntu system easier.

The package itself doesn't do anything except for depending all the packages -  nano being one - Ubuntu devs felt make a comfortable text-only environment.

You can safely remove the package and, in fact, will need to if you want to uninstall nano.
However, it is recommended to reistall the metapackage prior to upgrading to a new Ubuntu release.

Hope that helps.

---

