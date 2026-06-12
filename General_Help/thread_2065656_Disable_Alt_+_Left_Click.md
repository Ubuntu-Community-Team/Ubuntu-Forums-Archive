---
title: "Disable Alt + Left Click"
date: 2012-10-02
forum: General Help
---

### Post by scorpiosnake on 2012-10-02
I am using Ubuntu and Gnome Shell. I am trying to use Blender and as such I need to disable the option to move windows when you press Alt + Left Click. I have searched and tried several things but nothing changes the behavior.

I have tried changing settings in gconf-editor and Compiz Config Settings Manager per [here]("http://askubuntu.com/questions/67518/how-to-disable-window-move-with-alt-left-mouse-button"). But nothing changes it. It shows that the settings are changed but the behavior remains.

Any help please? 

Thank you.

---

### Post by scorpiosnake on 2012-10-02
I was finally able to find the solution [here]("http://blenderartists.org/forum/showthread.php?222109-How-to-disable-alt-right-click-in-gnome-3"). For Gnome Shell I had to use dconf-editor (not gconf-editor).

org &#8594; gnome &#8594; desktop &#8594; wm &#8594; preferences &#8594; mouse-button-modifier

and changed the value to <Super>

---

