---
title: "Adeskbar Edit Menu"
date: 2010-10-06
forum: General Help
---

### Post by mooreted on 2010-10-06
Using Adeskbar and Openbox. Love Adeskbar, but how do you edit the Application Menu?

---

### Post by demosthenese on 2010-10-06
I think adeskbar just uses the existing desktop environment menu. You might be able to edit this with alacarte, though this is aimed at gnome it should work with any opendesktop compliant desktop - not sure if this applies to openbox though.

I prefer to leave the existing menus alone, and have a separate drawer plugin labelled favourites to launch frequently used applications.

---

### Post by mooreted on 2010-10-07
The thing I want to change is there are two entries for Synaptic; one that asks for a password and one that doesn't. I'm selling this machine to a regular computer user type person and I'm trying to cut out as much possible confusion as I can. Since it's a Pentium III 1.1 Ghz system with 256 MB of RAM, I have to go lite.

---

### Post by demosthenese on 2010-10-07
If you go to /usr/share/applications you will see a list of desktop files that are used to build menus. There should be at least one file for each application. Some may have two, if for example one is set to appear only in KDE and another is set to appear in anything but KDE.

You can edit these with a text editor such as gedit or mousepad. [You will need to be root]. If you want to hide an application's menu entries, then add the following line to the end of the file:

```
NoDisplay=true
```

You may find the following article useful.
[http://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/]("http://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/")

---

### Post by mooreted on 2010-10-07
That makes sense, I'll see what desktop files I have for Synaptic. There must be two.

Thanks for the help.

---

### Post by twodogs on 2010-12-16
or, you can edit the menu.xml file under main menu>openbox config :)

---

