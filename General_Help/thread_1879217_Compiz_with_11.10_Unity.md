---
title: "Compiz with 11.10 Unity"
date: 2011-11-11
forum: General Help
---

### Post by Raweed on 2011-11-11
Hi I am a new linux user and have just installed the latest ubuntu release 11.10.
I have installed compiz with the following command 
```
sudo apt-get install compizconfig-settings-manager
```

I have enabled the unity plug in and have tried changing backend to and from 'Flat-file' and 'GConf' but no changes from ccsm are effecting my desktop e.g. wobbly windows, annotate etc.

when i type compiz into the software centre the following are installed
-OpenFL windows and compositing manager
-Compiz
-CompizConfig Settings Manger


not installed
-Compiz Fusion Icon
-Screenlets
-SimDock


And I am running ubuntu of a Ext USB hard drive, does that make it a problem?
Any help would be appreciated. :)

---

### Post by sikander3786 on 2011-11-11
First of all, make sure you are running Unity (3D) that runs on Compiz and not Unity 2D -which almost resembles Unity in its looks and looks can be deceiving - which runs on Metacity.

So, search the Dash (by pressing <Super> key) for Terminal and post the output of this command please:

```
/usr/lib/nux/unity_support_test -p
```

---

### Post by Raweed on 2011-11-11
Hi when I try to enter the code into Terminal I get the following output

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault

```

Before I log in I can change the shell to which I log in
the following options are availible
Gnome
Gnome Classic
Gnome Classic(no effects)
Ubuntu
Ubuntu 2D

I always use Ubuntu, 

When I click on System Information it only says Ubuntu 11.10 but nor if its 3D or 2D

UPDATE : when I run the code unity --reset whilst logged in to either Ubuntu or Ubuntu 2D i get the code


```
(metacity:7749): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
(metacity:7749): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
(metacity:7749): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
(metacity:7749): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

```

I think because it says metacity it could mean I am still running 2D, if so could anyone also pleases direct me how to run 3D. I have a HP Pavillion dv6 with a Intel® Core&#8482;2 Duo CPU T6600 @ 2.20GHz × 2  processor, 3GB RAM and am booting off a 500GB ext hdd through USB.

---

