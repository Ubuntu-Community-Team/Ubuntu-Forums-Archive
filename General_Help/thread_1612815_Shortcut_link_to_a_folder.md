---
title: "Shortcut link to a folder"
date: 2010-11-03
forum: General Help
---

### Post by Nuxala on 2010-11-03
How do I get a shortcut link to a folder on my desktop?  I tried to use 
  lxshortcut 
but it says application shortcut and not link.

I read this but I still don't understand how to make link:

> **Desktop Icons/links **

 Desktop links are not totally obvious. Here are some hints. 
 **[[edit]("http://wiki.lxde.org/en/index.php?title=PCManFM&action=edit&section=5")]  How to Make Them **

 Open the files with editor to see how they work: 
 
[LIST]
[*] Look at the examples here: */usr/share/applications*
[*] A typical file name is like this one: *leafpad.desktop* The *.desktop* file extension won't show up on pcmanfm.
[/LIST]
 **[[edit]("http://wiki.lxde.org/en/index.php?title=PCManFM&action=edit&section=6")]  Other Hints **

 
[LIST]
[*] Copy files from */usr/share/applications* to your ~/Desktop folder.
[*] Make your own desktop links by following the examples above and put them in your ~/Desktop folder.
[*] The same *.desktop* files are used for the buttons in the lxpanel (bottom task bar).
[/LIST]


---

### Post by cavalier911 on 2010-11-03
I followed this tutorial to make a shortcut/launcher to my home folder.
[http://peppermintos.net/viewtopic.php?f=40&t=236](http://peppermintos.net/viewtopic.php?f=40&t=236)
When you click it launches pcmanfm with the home folder open.
To open a different folder add your path after Exec=pcmanfm
Say you want to launch the Documents folder:
Exec=pcmanfm ~/Documents
Name=Documents
Icon=path to your icon
If you want drag and drop have to use a distro with gnome or kde.

---

### Post by rbc on 2010-11-03
The question you ask is how to make a desktop shortcut/link to a folder. The directions you are trying to follow explain how to make a desktop shortcut to an application/program. Which are you trying to accomplish?

---

### Post by Nuxala on 2010-11-03
> **rbc said:**
> The question you ask is how to make a desktop shortcut/link to a folder. The directions you are trying to follow explain how to make a desktop shortcut to an application/program. Which are you trying to accomplish?

how to make a desktop shortcut/link to a folder like pictures

---

### Post by Nuxala on 2010-11-04
> **cavalier911 said:**
> I followed this tutorial to make a shortcut/launcher to my home folder.
[http://peppermintos.net/viewtopic.php?f=40&t=236](http://peppermintos.net/viewtopic.php?f=40&t=236)
When you click it launches pcmanfm with the home folder open.
To open a different folder add your path after Exec=pcmanfm
Say you want to launch the Documents folder:
Exec=pcmanfm ~/Documents
Name=Documents
Icon=path to your icon
If you want drag and drop have to use a distro with gnome or kde.

 Thanks for the link. The one with the home folder works for me, but when I try to make one with Documents or Pictures it doesn't. This is what I did:

> #!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Name=Documents
Comment=Browser
Exec=pcmanfm ~/Documents
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=system-file-manager
Categories=Application;Desktop;Filemanager
StartupWMClass=Pcmanfm
StartupNotify=true

---

### Post by Nuxala on 2010-11-04
> **Nuxala said:**
> Thanks for the link. The one with the home folder works for me, but when I try to make one with Documents or Pictures it doesn't. This is what I did:

Solved instead of using:

 Exec=pcmanfm ~/Documents

I used

Exec=pcmanfm /home/username/Downloads

Thanks for the tip **cavalier911.**

---

