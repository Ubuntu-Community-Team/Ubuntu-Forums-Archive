---
title: "HELP! My Ubuntu is broken!"
date: 2009-07-25
forum: General Help
---

### Post by Stugol on 2009-07-25
Yesterday I followed the instructions given at [http://brainstorm.ubuntu.com/idea/14381/](http://brainstorm.ubuntu.com/idea/14381/) - specifically, these instructions:

> sudo aptitude install apt-build 
sudo apt-build source gnome-panel 
cd /var/cache/apt-build/build/gnome-panel* 
sudo gedit gnome-panel/panel-menu-items.c 

then change macros, save file and execute: 
sudo apt-build install -f gnome-panelThis apparently did nothing, informing me that no files were built because I already had the latest version. I tried MAKE, but it said I didn't have a makefile. So I gave up.

This morning, I powered the machine on again. Now, when I insert a removeable drive, the Gnome panel freezes up. When this happens, I am unable to shut down or restart because the Gnome panel refuses to close. Also, I can't access the drive I have inserted.

I have used Synaptic to remove apt-build and reinstall Gnome-Panel. I don't see what else I can do to fix this.

Can anyone help, please, before I tear all of my hair out in frustration?

---

### Post by blueridgedog on 2009-07-25
Have you tried:

```
apt-get install --reinstall gnome-panel
```

---

### Post by Stugol on 2009-07-25
> **blueridgedog said:**
> Have you tried:

```
apt-get install --reinstall gnome-panel
```

No, but I reinstalled it through Synaptic like I already explained :confused:

Since posting this question, I told Synaptic to reinstall EVERYTHING that was currently installed and had "Gnome" in its name or description.

This took about 15 minutes, and seems to have solved the problem :D

---

### Post by Stugol on 2009-07-25
Or perhaps it didn't... ... the system's still crashing for no apparent reason at random intervals. I'm not even sure that the problem was anything to do with Gnome-panel now.

Help?

---

