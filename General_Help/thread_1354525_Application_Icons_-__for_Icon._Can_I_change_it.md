---
title: "Application Icons - ? for Icon. Can I change it?"
date: 2009-12-14
forum: General Help
---

### Post by Roasted on 2009-12-14
Several applications I use have a question mark as an icon, and I'm not sure why. Is there a way I can change it?

[http://img297.imageshack.us/img297/386/snapshot5v.png](http://img297.imageshack.us/img297/386/snapshot5v.png)

---

### Post by tom.swartz07 on 2009-12-14
> **Roasted said:**
> Several applications I use have a question mark as an icon, and I'm not sure why. Is there a way I can change it?

[http://img297.imageshack.us/img297/386/snapshot5v.png](http://img297.imageshack.us/img297/386/snapshot5v.png)

There is a way, but its not easy...

You would have to add them yourself to the icon folder.
The images should be around 50-60 pixels square, and in .png format.

when you get them, the hard part is to figure out what the name of the icon would be, perhaps a google search would help; typically theyre the names that you would use in the terminal to start the program, for example the USB startup creator is usb-creator-gtk

the icons go in the folder
/usr/share/icons/*
where * stands for the theme and any icon type after that- applications, animations, devices, etc.

Good Luck!


ps- ive found that sometimes its best to look into another icon theme set and snip icons from there. try to mirror the locations as best you can.

---

### Post by Roasted on 2009-12-14
Why don't they come down automatically? :(

---

### Post by Vaphell on 2009-12-14
They usually do
It's the package/installer provider's fault. Looks like someone forgot to include icon or properly assign it to menu item.

---

### Post by Roasted on 2009-12-14
> **Vaphell said:**
> They usually do
It's the package/installer provider's fault. Looks like someone forgot to include icon or properly assign it to menu item.

Understandable. I'm at work now on an XP box so I can't look at my rig and tell, but is there a way I can just DL a virtualbox icon and link it over to the missing app icon? I tried to right click the app but I didn't get any viable menus that would indicate I could link over a different picture icon. Unless it was because I was doing it under my favorites menu? Perhaps I need to try it where the application lives under applications/internet/whatever?

---

### Post by running_rabbit07 on 2009-12-14
You may also change the icon by right-clicking and going to properties, then click on the icon and that will bring up a menu to select an icon or picture.

---

