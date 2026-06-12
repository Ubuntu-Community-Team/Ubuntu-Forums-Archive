---
title: "&quot;Unity Plugin&quot; missing from CCSM in 10.10"
date: 2011-11-27
forum: General Help
---

### Post by asuastrophysics on 2011-11-27
Hey everyone,

So I managed to get unity 3d up and running, but now I want to tweak it (use semi-transparent panels, resize the icons in the dock),

but the "unity plugin" is missing in compiz-config-settings-manager! How do I add this plugin? Is this plugin exclusive to the 11.04 version of CCSM? I tried reinstalling unity, but that didn't change anything.

Any thoughts?

---

### Post by Frogs Hair on 2011-11-27
11.04 is the first release to include the unity plug-in . 10.10 doesn't have Unity unless you install Unity 2D via the PPA .[http://www.webupd8.org/2011/01/unity-2d-qt-now-available-in-ppa-for.html](http://www.webupd8.org/2011/01/unity-2d-qt-now-available-in-ppa-for.html)

If you are using 11.10 you may need to install a proprietary driver from additional drivers to run Unity 3D . The Compiz version for 11.10 is  0.9.5.92 .

---

### Post by asuastrophysics on 2011-11-27
> **Frogs Hair said:**
> 11.04 is the first release to include the unity plug-in . 10.10 doesn't have Unity unless you install Unity 2D via the PPA .[http://www.webupd8.org/2011/01/unity-2d-qt-now-available-in-ppa-for.html](http://www.webupd8.org/2011/01/unity-2d-qt-now-available-in-ppa-for.html)

If you are using 11.10 you may need to install a proprietary driver from additional drivers to run Unity 3D . The Compiz version for 11.10 is  0.9.5.92 .

I've got unity 2d and 3d installed. Is the unity plug-in only included in the version of compiz that comes with 11.10? If so, is there a way to install the 11.10 version of compiz on my ubuntu 10.10 machine, or will I hit a brick wall with unmet dependencies?

---

### Post by Frogs Hair on 2011-11-27
> **asuastrophysics said:**
> I've got unity 2d and 3d installed. Is the unity plug-in only included in the version of compiz that comes with 11.10? If so, is there a way to install the 11.10 version of compiz on my ubuntu 10.10 machine, or will I hit a brick wall with unmet dependencies?

11.10 uses Gnome 3 and 10.10 uses Gnome 2 so that would be a brick wall . As I wrote 11.04 was the first desktop release to have Unity as the default environment . I don't remember what version of Compiz was used in 11.04.

If you want Unity 3d install 11.04 or 11.10 .

---

### Post by 3rdalbum on 2011-11-27
The version of Unity in 11.04 and later is implemented as a plugin in Compiz, so it should appear in CCSM.

If you're just installing the 10.10 version of Unity and that's what you're running, it won't have options in CCSM because it's not even running Compiz.

To confirm what version of Unity you are using, how about posting a screenshot of your desktop with the Dash open?

---

