---
title: "Loss of Placeces Menu"
date: 2011-02-19
forum: General Help
---

### Post by waltwin on 2011-02-19
[SIZE=2]I had to reformat my hard drive because I was trying to run windows 7 and ubuntu 10.10 on the same drive which caused many problems. After re-installing ubuntu 10.10 alone I noticed that I no longer had access to any of the "Places" sub menus, Home folder through Ubuntu one. 

Can anyone help me get access those sub menus?

Thank you in advance.

waltwin[/SIZE]

---

### Post by gerowen on 2011-02-19
Can you take a screenshot of what you're seeing?  You could try re-adding the menu to the panel, and if that doesn't work you could try just resetting Gnome to its default configuration.  To do this you just delete the hidden folders in your home folder and then reboot.  This command will make it quick and easy for ya:
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```
Just run that as yourself, not root, and then restart your computer.  When you log in Gnome should be reset to its default state.

---

### Post by waltwin on 2011-02-20
I really don't have a screen shot to take. When I select any sub folders I get the circle that is searching thing then it just stops. I entered the info you suggested into terminal but no joy!

---

