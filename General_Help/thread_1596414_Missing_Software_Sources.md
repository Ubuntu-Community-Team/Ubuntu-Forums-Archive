---
title: "Missing Software Sources"
date: 2010-10-14
forum: General Help
---

### Post by rowanrh on 2010-10-14
Just updated from **Lucid** to **Meerkat** and **System>Administration **no longer contains a tag for **Software Sources**. Has this been renamed, resited, made redundant or have I had a bad upgrade?

---

### Post by garvinrick4 on 2010-10-14
> **rowanrh said:**
> Just updated from **Lucid** to **Meerkat** and **System>Administration **no longer contains a tag for **Software Sources**. Has this been renamed, resited, made redundant or have I had a bad upgrade?Not there anymore go to Synaptics and its drop down menu  settings and choose repository. I must have installed in mine:
rick@rick-HP-G71-Notebook-PC:~$ aptitude show software-properties-gtk
Package: software-properties-gtk  
State: installed
Automatically installed: no
Version: 0.76.7
Priority: optional
Section: gnome
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Uncompressed Size: 459k
Depends: python (< 2.7), python (>= 2.6), python-central (>= 0.6.11), synaptic
         (>= 0.57.8), gksu, python-software-properties, python-gtk2
Conflicts: update-manager (< 0.55)
Replaces: update-manager (< 0.55)
Description: manage the repositories that you install software from
 This software provides an abstraction of the used apt repositories. It allows
 you to easily manage your distribution and independent software vendor software
 sources. 
 
 This package contains a GTK+ based graphical interface.
```
sudo apt-get install software-properties-gtk
```
Or it will be in Ubuntu software center or synaptics in GUI

---

### Post by lordberic on 2010-10-14
Software sources has been phased out (or is being)

You can still get to it via synaptic (might be wrong on that count)

Ubuntu with Maverick wants you to use the software center, the replacement for software sources is in there.

Don't worry you haven't made a bad upgrade, it's just changed :)

---

### Post by rowanrh on 2010-10-14
> **garvinrick4 said:**
> Not there anymore go to Synaptics and its drop down menu  settings and choose repository. I must have installed in mine:
rick@rick-HP-G71-Notebook-PC:~$ aptitude show software-properties-gtk
Package: software-properties-gtk  
State: installed
Automatically installed: no
Version: 0.76.7
Priority: optional
Section: gnome
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Uncompressed Size: 459k
Depends: python (< 2.7), python (>= 2.6), python-central (>= 0.6.11), synaptic
         (>= 0.57.8), gksu, python-software-properties, python-gtk2
Conflicts: update-manager (< 0.55)
Replaces: update-manager (< 0.55)
Description: manage the repositories that you install software from
 This software provides an abstraction of the used apt repositories. It allows
 you to easily manage your distribution and independent software vendor software
 sources. 
 
 This package contains a GTK+ based graphical interface.
```
sudo apt-get install software-properties-gtk
```
Or it will be in Ubuntu software center or synaptics in GUI
Many thanks, software-properties-gtk is now installed. Most impressed with speed of help from first post.

---

### Post by crichard on 2010-10-14
One more method is available too.  In Menu Bar, Right click & Pick  Edit Menus -> System -> Administartion Then, Check the Software Sources.  :)

---

