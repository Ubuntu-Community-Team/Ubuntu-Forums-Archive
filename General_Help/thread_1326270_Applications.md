---
title: "Applications"
date: 2009-11-14
forum: General Help
---

### Post by jeskin76 on 2009-11-14
My applications drop down menu is empty, can switch user and it works? 
How do I get it back ? Please be gentle new to linux in general

---

### Post by Brandon Williams on 2009-11-14
Right click on the 'Applications' button and select properties. In the section labeled 'Menu File', what is selected? 

If it's 'Use custom menu file', then verify that the specified menu file exists. If the file exists, you might want to post the contents of the file so we can see what might be wrong with it. In the mean time, try switching to 'Use default desktop menu file'.

If the current setting is 'Use default desktop menu file', it should be working. I can't think of what to check to figure out why it isn't. However, you could switch to 'Use custom menu file' and explicitly specify /etc/xdg/menus/xfce-applications.menu.

---

### Post by jeskin76 on 2009-11-14
Right clicked all it says is help, edit menus, remove, lock to panel

---

### Post by Brandon Williams on 2009-11-14
Ah ... that sounds like gnome-panel. You marked the thread as xubuntu, so I assumed that you're running an xfce desktop.

What does the menu look like in the editor when you click on 'edit menus'? Does it show all the expected content? Also, take a look in your ~/.config/menus directory. Does it contain an applications.menu file?

---

### Post by Filkfive on 2009-11-24
I've got the same problem so it sounds like I must be using gnome-panel as well.  (Whatever that means)  When I click on "Edit Menus", nothing at all happens.

Right now all I can access through the applications button is Places, System, and Quit.

I don't know if I have access to more options as a different user as the original poster did though.  I only have one user set up.

---

