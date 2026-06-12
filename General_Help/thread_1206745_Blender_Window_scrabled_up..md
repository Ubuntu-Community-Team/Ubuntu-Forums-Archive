---
title: "Blender Window scrabled up."
date: 2009-07-07
forum: General Help
---

### Post by MDSmith2 on 2009-07-07
Hello, I have been having a lot of trouble with blender recently.
I run blender and the window is scrambled up like crazy (screenshot below)!

Here is the log: ```
michael@mdsmiths:~$ blender
Compiled with Python version 2.6.2.
Checking for installed Python... got it!
Failed to initialize GEM.  Falling back to classic.

```I have direct rendering working and I have an Intel video card. I have also downgraded my Intel driver to 2.4

---

### Post by ju2wheels on 2009-07-07
Have you tried disabling compiz effects if you have them enabled?

---

### Post by MDSmith2 on 2009-07-07
> **ju2wheels said:**
> Have you tried disabling compiz effects if you have them enabled?
Nope, not got them enabled.

---

### Post by Jebtrix on 2009-07-07
Do you get any problems with other opengl apps like glxgears?

---

### Post by Jebtrix on 2009-07-07
If its just Blender, try the latest 2.49a Ubuntu package release directly from blender.org.

---

### Post by MDSmith2 on 2009-07-07
> **Jebtrix said:**
> Do you get any problems with other opengl apps like glxgears?
I get that GEL message or whatever with most 3D apps but it doesn't seem to have any effect on anything but blende.
> **Jebtrix said:**
> If its just Blender, try the latest 2.49a Ubuntu package release directly from blender.org.
Ok, will try and I will edit back when it is installed.

---

### Post by MDSmith2 on 2009-07-07
Hmm, same thing with the new blender.

---

### Post by ju2wheels on 2009-07-07
Click System->Preferences->Appearance and select the "Visual Effects" tab. Which option is selected (if any)..?

Also, im almost inclined to say you are having a graphics driver issue especially since you are using Hardy and they have made some serious headway since then in fixing Intel related issues if I recall correctly (not sure what those issues were off the top of my head though).

---

### Post by MDSmith2 on 2009-07-07
> **ju2wheels said:**
> Click System->Preferences->Appearance and select the "Visual Effects" tab. Which option is selected (if any)..?

Also, im almost inclined to say you are having a graphics driver issue especially since you are using Hardy and they have made some serious headway since then in fixing Intel related issues if I recall correctly (not sure what those issues were off the top of my head though).
I am using Jaunty with the Intel 2.4 driver and I can't use that menu because I am using XFCE (sorry, should of mentioned that before).

---

### Post by Jebtrix on 2009-07-07
[http://blenderartists.org/forum/showthread.php?t=153233&page=4](http://blenderartists.org/forum/showthread.php?t=153233&page=4)

Add:

```
Option "dri" "off"
```

To the device section of your /etc/X11/ xorg.conf file. 

Basically its because intel graphics drivers are in transition. I would try the xorg.conf but that will disable 3D acceleration and off the load on your CPU (which u may or may not be able to live with). Or you can install latest 2.6.3x kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc2](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc2)... Or you can run the Ubuntu 9.10 Alpha 2.... Or mess around with different intel graphic drivers (not fun)...

---

### Post by MDSmith2 on 2009-07-07
> **Jebtrix said:**
> [http://blenderartists.org/forum/showthread.php?t=153233&page=4](http://blenderartists.org/forum/showthread.php?t=153233&page=4)

Add:

```
Option "dri" "off"
```To the device section of your /etc/X11/ xorg.conf file. 

Basically its because intel graphics drivers are in transition. I would try the xorg.conf but that will disable 3D acceleration and off the load on your CPU (which u may or may not be able to live with). Or you can install latest 2.6.3x kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc2]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.31-rc2")... Or you can run the Ubuntu 9.10 Alpha 2.... Or mess around with different intel graphic drivers (not fun)...
I would rather not turn DRI off because my other 3D apps would be useless (I experimented with DRI once before trying to get Google Sketchup to run under wine) and Blender might not work, either. 
That link doesn't have a kernel image for IX86.
how stable is Alpha 2 now? I use my computer for other things that need more stability then Window$ ;)
I wouldn't play with driver unless it was an absolute necessity.

Thanks!

---

### Post by Jebtrix on 2009-07-07
I'm be dang it seems so doesnt it, try:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/)

As for Alpha 2 it really does work pretty good. The only problem adding repositories and such because most dont have a karmic branch yet. So if you stick with mainly Canonical repositories your fine, otherwise you might have to force some installs.

---

### Post by Jebtrix on 2009-07-07
You could always use Remastersys to backup your current installation completely. Then if you got any problems just use your custom remastersys installer disc to reinstall it back with all your settings intact.

---

### Post by MDSmith2 on 2009-07-08
> **Jebtrix said:**
> I'm be dang it seems so doesnt it, try:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/")

As for Alpha 2 it really does work pretty good. The only problem adding repositories and such because most dont have a karmic branch yet. So if you stick with mainly Canonical repositories your fine, otherwise you might have to force some installs.
Hmm, that is the current kernel I am using and it doesn't make a difference :(

---

