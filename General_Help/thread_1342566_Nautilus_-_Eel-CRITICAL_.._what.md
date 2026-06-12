---
title: "Nautilus - Eel-CRITICAL .. what ?"
date: 2009-11-30
forum: General Help
---

### Post by Virtual Liberty on 2009-11-30
```
(nautilus:3912): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

```

How do I get rid of this ? I can't launch Nautilus ..

---

### Post by utnubuuser on 2009-12-01
Don't know,  but you might check gconf-editor's settings.
Alt+F2, then type: gconf-editor, then look for Apps>>Nautilus

---

### Post by Virtual Liberty on 2009-12-01
Still haven't fixed this. Even reinstalled Ubuntu ( Minimal CD + gnome-core ). Does anybody have ideas what could cause this ? Found a few bug reports but none of them seemed to be solved.

---

### Post by utnubuuser on 2009-12-02
try deleting all your configuration files with > cd /home/yourusernamethen> sudo rm -rf .gnome2 .gconf .gconfd .metacity
This should restore the system to a default desktop.  - From a recovery screen of course.
It will wipe out all configuration settings, including Evolution settings, so back those up before using the command.

You could also try totally removing Nautilus, then reinstalling Nautilus> sudo apt-get remove nautilus --purgerestart, then> sudo apt-get install nautilus

This might have something to do with the fact that you've got gnome-core installed instead of ubuntu-desktop.

---

### Post by afrodeity on 2010-02-01
I also have the problem, what was the solution?

---

### Post by 23dornot23d on 2010-03-03
Here is the bug ..... report ...

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/454234](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/454234)

 for Eel-CRITICAL and here is the patch .... supplied back then ....

[https://launchpad.net/~erez-volk/+archive/nautilus]("https://launchpad.net/%7Eerez-volk/+archive/nautilus")

There is a patch supplied ...... as shown below .... if you do not want to search through for it ,,,

**Adding this PPA to your system**

                  You can update your system with unsupported packages from           this untrusted PPA by adding           **ppa:erez-volk/nautilus**           to your system's Software Sources.           Not using Ubuntu 9.10 (karmic)?


___________________________________________



I added it and the problem went away .......

---

