---
title: "Kompozer is installed, but will NOT run!"
date: 2011-01-01
forum: General Help
---

### Post by makoshark55 on 2011-01-01
I have installed  Kompozer from the ubuntu software menu, synaptic and from the terminal  and I not only don't have icons or menu item, but I cannot load it from  terminal either. I have tried complete removal with synaptic but it  changes nothing. I wondering if something is hanging around from the old  one, but I would not know were to look? I installed kompozer on another machine and that one works?

                                                                                               [URL="http://blog.nilandsplace.com/linuxblog/"]
[/URL]

---

### Post by Foxheadz on 2011-01-01
Try running ```
sudo apt-get purge kompozer
``` and then reinstall

---

### Post by makoshark55 on 2011-01-01
Well It did not work. in comparison with my other machine it is not installing the US folder.

---

### Post by dcstar on 2011-01-02
> **makoshark55 said:**
> I have installed  Kompozer from the ubuntu software menu, synaptic and from the terminal  and I not only don't have icons or menu item, but I cannot load it from  terminal either. I have tried complete removal with synaptic but it  changes nothing. **I wondering if something is hanging around from the old  one**, but I would not know were to look? 


Rename any (hidden) **~.nvu**, **~.kompozer** & **~.kompozer.net** folders.

---

### Post by makoshark55 on 2011-01-02
this is what I got for the purge
> james@james-desktop:~$ sudo apt-get purge kompozer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kompozer-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  kompozer*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 17.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 274447 files and directories currently installed.)
Removing kompozer ...
Purging configuration files for kompozer ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for python-support ...
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

james@james-desktop:~$ 


---

