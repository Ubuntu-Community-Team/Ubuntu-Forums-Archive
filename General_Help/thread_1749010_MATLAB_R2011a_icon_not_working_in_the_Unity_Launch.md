---
title: "MATLAB R2011a icon not working in the Unity Launcher [11.04 64bit]"
date: 2011-05-04
forum: General Help
---

### Post by Blitz Tungsten on 2011-05-04
I've just installed MATLAB R2011a (64bit version) in the latest Ubuntu 11.04 (obviously 64bit as well).

I've followed this [http://thameera.wordpress.com/2010/10/21/installing-matlab-2008a-on-ubuntu-10-10/]("guide") for the installation part.

Then after running Matlab for the first time with the command:

```
sh /usr/local/matlab/bin/matlab
```

I right-clicked on the Unity Launcher to add Matlab, but after logging off it disappeared from there.

Then from Ubuntu help I've tried:

1. Get an icon:

```
sudo wget http://upload.wikimedia.org/wikipedia/commons/2/21/Matlab_Logo.png -O /usr/share/icons/matlab.png
```

2. Get the launcher file:

```
sudo wget 'https://help.ubuntu.com/community/MATLAB?action=AttachFile&do=get&target=matlab-r2011a.desktop' -O /usr/share/applications/matlab.desktop
```

The icon remains there after closing Matlab, but I've yet to log-off or restart.

The problem is that when I click on it, it does nothing!

So to open Matlab I've always to type in terminal:

```
sh /usr/local/matlab/bin/matlab
```

Did any of you succeed in putting a working icon of Matlab in the brand new Unity Launcher?

Thanks in advance!

---

### Post by F.V. on 2011-06-15
There is a workaround, but it's not perfect: right-click on the desktop, create a launcher for matlab and then drag it from the desktop to the unity launcher.

You have now an icon that launches Matlab. However, when you do it, you will have two matlab icons on the launcher: one that brings matlab windows to the front, and another that launches another matlab process.

---

### Post by josian_220 on 2011-07-22
I think this is a issue with most java apps. Like minecraft for instance. This also happens with Gnome3 launcher, it would be interesting to know if it also happens with the launcher in windows 7 and mac os x, I don't really know about those ones.

---

