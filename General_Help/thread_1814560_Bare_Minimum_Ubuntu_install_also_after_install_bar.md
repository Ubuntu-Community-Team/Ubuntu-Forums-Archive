---
title: "Bare Minimum Ubuntu install? also after install bare minimum KDE"
date: 2011-07-29
forum: General Help
---

### Post by xekon on 2011-07-29
Is there a way to install the absolute bare minimum Ubuntu. Currently I am using 11.04 with KDE 4.6.5

Ubuntu with gnome ide, with the gnome panels, package manager, drivers.
  but with every possible removeable application removed, gwibber, shotwell, games, tomboy, extra languages, etc, etc. If its removeable Ide rather it not install in the first place.
(
Then after installing I generally install kde-standard... but I find if you install that package then you cannot remove most of the applications that come bundled with kde... so is there a way to install just the kde desktop environment without all the extra applications?

---

### Post by Theredbaron1834 on 2011-07-29
Well, the only way I know to do that is to install the ubuntu server, and from there install kde. You have to be able to use the command line, cause the server is just that, a command line.

---

### Post by xekon on 2011-07-29
I just found: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

and: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

so after installing:

sudo apt-get update
sudo apt-get install xorg xterm gdm icewm menu firefox gksu synaptic --no-install-recommends
sudo service gdm start

would I change "icewm menu"
to something else if I dont want to use the ice window manager and just want what gnome uses for a window manager. (not sure what that package is called though?)

---

### Post by CatKiller on 2011-07-29
The default window manager is Compiz. Gnome's native window manager is Metacity.

---

### Post by Theredbaron1834 on 2011-07-29
Ubuntu uses compiz.
The thing is that if you want to use compiz, you also need a panel, cause icewm is a desktop enviro, where as compiz is just a window's manager. So if you want a lightweight one, you could go with lxpanel, or if you like gnome's it is gnome-panel.

You should also do something like
```
echo "exec gnome-session" > ~/.xinitrc
```To start gdm when you run "startx"

---

### Post by xekon on 2011-07-30
I got everything sorted out, followed this guide: [http://ubuntuforums.org/showthread.php?t=1759018](http://ubuntuforums.org/showthread.php?t=1759018)

Thanks everyone! and big thanks to -unseen-

---

