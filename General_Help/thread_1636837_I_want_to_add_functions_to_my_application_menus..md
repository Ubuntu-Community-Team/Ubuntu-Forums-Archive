---
title: "I want to add functions to my application menus."
date: 2010-12-03
forum: General Help
---

### Post by ivarn on 2010-12-03
Hey. I want to add a few functions to my menu.
You know how you can uninstall a program from the mint menu by right-clicking the program you want to remove? I want this function on my ubuntu menu since I don't really like the mint menu (too many things and it looks like a big messy box).
And I also want to add the "rename", "delete file" and "preferences" options.
I hope these things will be added to the menu in future versions.
But ok, if someone could give me a step by step guide and tell me how to do this, that would be very cool.
Thank a lot (in advance).

---

### Post by ngrieb on 2010-12-03
I think this would be great as well. I have been trying to develop things in Ubuntu too, and I would like a right-click open terminal here feature like in OpenSuse (might be a KDE thing...correct me if I am wrong). Do you have any experience with GTK development, such as widgets or Qt. I could certainly make a Bash or Python script to simply remove the program via a command line call to apt-get, but the GUI menu implementation is where I would get lost. If someone could tell us where the program code that creates the right click menus in Ubuntu resides, then it would be simple to alter the code and add a few menu option buttons, with some underlying shell script to preform the simple tasks that you want. 

You could try a google search for it, but I have been trying to complete a GTK applet (as an attempt to learn Python on my own and having no familiarity of widgets or Qt menus), which have little documentation, and sadly no one on the forums seems to care much about helping other people develop new software.

I will definitely help you if you can figure out what file to add to to get the desired effects. Good luck.

---

### Post by ddarsow on 2010-12-03
> **ngrieb said:**
> I think this would be great as well. I have been trying to develop things in Ubuntu too, and I would like a right-click open terminal here feature like in OpenSuse (might be a KDE thing...correct me if I am wrong). Do you have any experience with GTK development, such as widgets or Qt. I could certainly make a Bash or Python script to simply remove the program via a command line call to apt-get, but the GUI menu implementation is where I would get lost. If someone could tell us where the program code that creates the right click menus in Ubuntu resides, then it would be simple to alter the code and add a few menu option buttons, with some underlying shell script to preform the simple tasks that you want. 

You could try a google search for it, but I have been trying to complete a GTK applet (as an attempt to learn Python on my own and having no familiarity of widgets or Qt menus), which have little documentation, and sadly no one on the forums seems to care much about helping other people develop new software.

I will definitely help you if you can figure out what file to add to to get the desired effects. Good luck.

To get the "open terminal here" function is easy. Just:
```
sudo apt-get install nautilus-open-terminal
```
...you might have to reboot before it works.

the scripts for the context menu are found in the following directory if you want to write and add your own:
```
~/.gnome2/nautilus-scripts
```

also, if you have Ubuntu Tweak installed it has a feature to easilly add right click context scripts

---

### Post by ivarn on 2010-12-03
I know about the terminal on right-click, I use it a lot.
But now back to my thing here. How do I add these functions to the menu icons right-click menu? I have ubuntu-tweak but I can not see any option there that makes this possible.
The Nautilu script alternative would work just incase I can't solve this the way I want.
I don't want it to be like Right Click > scripts > uninstall. That looks just weird.

---

### Post by ivarn on 2010-12-05
Burp

---

### Post by ivarn on 2010-12-06
[SIZE=7][COLOR=Blue]_**Bump**_[/COLOR][/SIZE]

---

### Post by ivarn on 2010-12-07
Bump.
Does any of you pc experts know how I can add functions such as uninstall to the right click menu on the applications, places and system menus?

---

### Post by ivarn on 2010-12-11
Bump

---

### Post by argedion on 2010-12-11
> And I also want to add the "rename", "delete file" and "preferences" options.

to add delete menu option you can open nautilus click edit then preferences in the preferences dialog box click the behavior tab then under the Trash heading check the box "Include a delete command that bypasses trash. I can't help you with the others at the moment but hopefully that does help

alternatively you can always hold down the Shift key and press delete at the same time. It also bypasses the trash. This works also in Windows

---

### Post by ivarn on 2010-12-23
> **argedion said:**
> to add delete menu option you can open nautilus click edit then preferences in the preferences dialog box click the behavior tab then under the Trash heading check the box "Include a delete command that bypasses trash. I can't help you with the others at the moment but hopefully that does help

alternatively you can always hold down the Shift key and press delete at the same time. It also bypasses the trash. This works also in Windows
Thanks but this will only delete the file.
I want the uninstall function that you can see in the mint menu.
Also, deleting files using shift + del does not work in the menus to delete a  file.

---

