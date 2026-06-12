---
title: "Using the Openbox main menu instead of the LXDE default."
date: 2010-12-27
forum: General Help
---

### Post by gngf123 on 2010-12-27
I have tried a couple of things. But nothing really seems to work. I have got the menu showing on right click, but it only shows the defaults (terminal, pcmanFM, Browser). 

I have tried replacing the contents of menu.xml with the contents of lubuntu-rc.xml, didn't seem to make any impact. Has anyone successfully done this yet?

---

### Post by Brandon Williams on 2011-01-10
I just figured this out myself, so I hope this "better-late-than-never" response is still helpful ...

I installed the lxde meta-package, not lubuntu-desktop, but I expect that the general approach is the same in both cases, even if it's not exactly the same.

With lxde, the default openbox rc.xml and menu.xml are found in /usr/share/lxde/openbox/. When you run an lxde session for the first time, the startlxde script copies /usr/share/lxde/openbox/rc.xml to $HOME/.config/openbox/lxde-rc.xml. That file, the one under your $HOME/.config/openbox/ directory is now the operative one. I'm not sure exactly what the naming convention is when your session is started with startlubuntu instead of startlxde, but I expect that you will find the rc.xml file in that same directory, even if the name is slightly different. From your post, I'm guessing that your rc file is called lubuntu-rc.xml.

What I did with lxde was to copy /usr/share/lxde/openbox/menu.xml to $HOME/.config/openbox/lxde-menu.xml. Then, I opened $HOME/.config/openbox/lxde-rc.xml and changed this line ```
<file>/usr/share/lxde/openbox/menu.xml</file>
``` to this (replacing username with my username) ```
<file>/home/username/.config/openbox/lxde-menu.xml</file>
``` After this, I can edit the menu defined in $HOME/.config/openbox/lxde-menu.xml to make the openbox desktop menu look how I want it.

---

