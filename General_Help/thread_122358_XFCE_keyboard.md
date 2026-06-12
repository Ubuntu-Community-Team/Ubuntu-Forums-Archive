---
title: "XFCE keyboard"
date: 2006-01-27
forum: General Help
---

### Post by MiguelC on 2006-01-27
Hi to all !!

i'm using Ubuntu 5.10 and tried the 2 main graphical shells. Now i'm trying XFCE and it's really fast. Question is: does anyone know how to change the keyboard layout under Xfce? Thanks in advance;)

---

### Post by kairu0 on 2006-02-06
There is a plugin available in the respositories for that. It's called xfce4-xkb-plugin. Install the package and add it to your panel.

One trick: you have to list the keyboards that you want to use in your xorg.conf file, under the keyboard section, with comments between them. The plugin reads that file to determine what you can type.

---

### Post by MiguelC on 2006-02-06
I'm new to Linux. How can I do that?

Thanks again !! :D

---

### Post by kairu0 on 2006-02-14
1. Add keyboard layouts:

```
sudo kate /etc/X11/xorg.conf
```

Go to the keyboard section that probably only has "us" in it. Add other layouts separated by commas. Example: "us,fr,jp" (USA, France, Japan)

2. Add the xkb keyboard plugin

```
sudo apt-get install xfce4-xkb-plugin
```

3. Add the plugin (right-click on the XFCE panel, "Add," choose the plugin from the list.

---

### Post by MiguelC on 2006-02-14
That did the trick. Thanks! :D

---

