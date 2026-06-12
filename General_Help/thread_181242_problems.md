---
title: "problems"
date: 2006-05-23
forum: General Help
---

### Post by LORD_PoLvO on 2006-05-23
whislt installing nvidia drivers i have come across a problem and was wondering if ne1 can please help me with the problem plz.

```
Reading package lists... Done
Building dependency tree... Done
Package nvidia-glx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx has no installation candidate
```


i threw causion to the wind and i continued to the next part

```
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
```


and then entered 

```
[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;
```


i tested to see if it worked so i opened terminal and went glxgears and it ran for about 2-3 seconds and then froze ne insight?

---

### Post by nalmeth on 2006-05-23
you have to have that nvidia-glx package installed.
Perhaps you need to have universe/multiverse enabled in your sources.list.

sudo nano /etc/apt/sources.list

uncomment (delete the ##) before the multiverse and universe repositories

try to install nvidia-glx again

---

