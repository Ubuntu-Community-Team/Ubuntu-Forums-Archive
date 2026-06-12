---
title: "How do I use emerald theme?"
date: 2010-05-26
forum: General Help
---

### Post by ALF102 on 2010-05-26
Ok, I use Ubuntu 10.04 and I have compiz installed and also emerad. Currently I have the theme Ambiance and I want to change it to another theme that use emralld, but the problem is nothing change.

---

### Post by WorMzy on 2010-05-26
I'm guess you figured out how to change it? Pressing Alt+F2 and running

```
emerald --replace
```

sometimes works, but the best way (I've found) is to enable the window decorator plugin in compiz, and set that to use emerald. Then do

```
compiz --replace
```

You might need to run gconf-editor and modify /desktop/gnome/applications/window_manager/default to "/usr/bin/compiz", and /desktop/gnome/session/required_components/windowmanager to "gnome-wm".

If you found another way, please post it here so others can benefit from it.

---

### Post by ALF102 on 2010-05-27
Ok thanks for the help but I do found another way.

Install Emerald theme manager from the Software center. Then Install Compiz Fusion Icon from the Software center. Run Compiz Fusion Icon, after that you'll see the Compiz Fusion icon in your notification area. Right click the icon in the notification area and select "Emerald Theme Manager". The theme manager will appear and then you just import the .emerald theme there. 
    
   But before that, make sure you do this first before importing any .emerald theme.
Right click on the Compiz Fusion icon on the notification area again and go to "Select Window Manager" and select Compiz.
 Right click on the Compiz Fusion icon on the notification area again  and go to "Select Window Decorator" and select Emerald. Done.

---

