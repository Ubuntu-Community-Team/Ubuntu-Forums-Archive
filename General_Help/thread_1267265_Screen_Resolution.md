---
title: "Screen Resolution"
date: 2009-09-15
forum: General Help
---

### Post by bigboy7foru on 2009-09-15
**I found this but i cant seem to find _Configuration Editor_** in my system tools or in the synaptic thing
 
help please??
 
 
**Re: Why must I set the correct screen resolution on every startup?** 
do the following:

Click the applications menu, select Configuration Editor from the System Tools menu.

Now go to the following key (location):

/desktop/gnome/screen/default/0/

In the right pane you should see a key called 'resolution', double click this and enter your preferred resolution in the value box.

restart

You should find that everytime u login your preferred resolution is in use.

Have a nice day!

---

### Post by hwttdz on 2009-09-15
That probably refers to gconf-editor, so you can go to terminal and type in gconf-editor, if you get a not found you need to 
sudo apt-get install gconf-editor (or install through synaptic)
If the default is not to have it added to a menu you can right click the menu, and hit edit menus, and add it where you will. 

In sum:
editor is gconf-editor
you might need to install it
you might need to add it to the menu

---

### Post by bigboy7foru on 2009-09-15
is there an easier way to get it working??
 
I have a ATI 3D card and then i go to Preferences>Display it says monitor not found?
 
i wanna have at least 1280x800 resolution

---

### Post by atmiller65 on 2009-09-15
/desktop/gnome/screen/default/0/
 
I cannot find /screen/ after gnome...

---

