---
title: "Missing SYSTRAY and Taskbar"
date: 2011-12-10
forum: General Help
---

### Post by ibrrfarr on 2011-12-10
Running Ubuntu 11.10 with Compiz no other programs and fresh install on a Compaq CQ57.  

So, when I logged on today I noticed that the normal system tray on the upper right hand corner is gone as is the taskbar (I guess that's the name --- it has the dash deal to look up whatever and all the icons are square boxes) on the left is gone as well.  They are all replaced by the old school left upper listing of File, etc.  The only other novelty I have installed is Cairo OpenGL.  Also, when I log in I enter under Ubuntu and Ubuntu 2D as this is the only way I can run the cube.

Any help appreciated.

---

### Post by BC59 on 2011-12-10
If you still can open a terminal CTRL+ALT+T you could uninstall Cairo:

```
sudo apt-get remove cairo-dock cairo-dock-plug-ins
```

---

### Post by Frogs Hair on 2011-12-10
Cairo dock with open GL requires a 3D driver .

---

### Post by ibrrfarr on 2011-12-10
> **BC59 said:**
> If you still can open a terminal CTRL+ALT+T you could uninstall Cairo:

```
sudo apt-get remove cairo-dock cairo-dock-plug-ins
```

So, then am I to understand that by running Cairo I give up the system tray which is normally on the top right had corner?  The deal with the wireless signal, the system tab, the username, time, etc?

---

### Post by ibrrfarr on 2011-12-10
> **Frogs Hair said:**
> Cairo dock with open GL requires a 3D driver .

Not sure how that deals with no systray, but for the record I am running Cairo OpenGL with the crome buttons which spin and all and simply login with Ubuntu and not Ubuntu 2D checked.  Now, I have no idea what drivers are spun up.  Cairo, though, isn't the issue.  I am talking about the system tray on the upper top right hand corner with the username, wireless signal, etc. and the task bar on the left hand side with the dash menu.

---

### Post by BC59 on 2011-12-10
Why don't you try reinstall Unity?

```
sudo apt-get install --reinstall unity
```

---

### Post by ibrrfarr on 2011-12-10
> **BC59 said:**
> Why don't you try reinstall Unity?

```
sudo apt-get install --reinstall unity
```

Let me ask a couple questions first.  Are the missing systray and sidebar due to the fact that Unity is uninstalled?  I ask as I enabled the rotate cube and am very happy with it and I just want to make sure that if I do reinstall Unity (or is there a way to see if it is uninstalled) it will not impact the cube nor the dock.  I finally got them all the way I like after the fourth reinstall of Ubuntu.  :)

---

### Post by ibrrfarr on 2011-12-10
Ah, all I had to do was reinstall the Ubuntu Unity Plugin in the CCSM.  Thanks for your replies as it triggered my memory!

---

