---
title: "Removing unused stuff in maverick meerkat"
date: 2011-02-20
forum: General Help
---

### Post by Ykcir on 2011-02-20
I really don't know where to post this but my computer runs a lot slower  now (amd64,athlon 11x2 235e, nvidia GeForce 6150SE nForce 430, maverick meerkat) so I have been trying to remove stuff like printers, evolution, things I have no use for but the package manager only lets me remove bits and pieces of apps...why if you remove those items will the gnome desktop have to be uninstalled too? What does the desktop have to do with emails or printing? I am from the old school...if you don't need it remove it. Some stuff I have removed is Openoffice (that really cleared some space!) and replaced it with Abiword, also got rid of Shotwell photo manager, Empathy, Bittorrent, Gwibber, Telepathy, and parts of evolution...any way to completely remove Evolution?  Any other programs I can get rid of without uninstalling my desktop? And what about all those useless printer files? I ran virus scanner and computer janitor also.

---

### Post by oldos2er on 2011-02-20
It is safe to remove the package ubuntu-desktop; the only time you would need it is if you want to upgrade to a newer version of Ubuntu in the future.

If I remember correctly, you can remove every evolution package except evolution-data-server or evolution-data-server-common (can't remember which).

Removing these packages will free up some disk space, but it won't speed up your machine. If possible you might want to try a desktop environment that's lighter than Gnome, like Xubuntu (not that much lighter) or Lubuntu (much lighter). 

[http://www.xubuntu.org/](http://www.xubuntu.org/)

[http://lubuntu.net/](http://lubuntu.net/)

Or do a minimal install and only install packages you want. 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

