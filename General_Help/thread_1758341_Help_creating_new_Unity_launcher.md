---
title: "Help creating new Unity launcher"
date: 2011-05-14
forum: General Help
---

### Post by javaman67 on 2011-05-14
I would like to create a custom Unity laucher for Expo Shift+Alt+Up to show Expo mode in all windows in the current workspace.

Any idea's ?


Thanks in advance,

Brian

---

### Post by wgarcia on 2011-05-14
I think you need the Dbus plugin activated. Check the following post:

[http://ubuntuforums.org/archive/index.php/t-744668.html](http://ubuntuforums.org/archive/index.php/t-744668.html)

But if you use Unity careful, it sometimes complains when you change things in the Compiz settings.

---

### Post by fishbulb1022 on 2011-07-24
I think you are actually talking about the Scale plugin, not the expo plugin. In any case, you can use xte from the xautomation package. Here are the steps:

1) Install xautomation

2) Right-click on your desktop and click Create Launcher

3) In the command field type: xte 'keydown Shift_L' 'keydown Alt_L' 'key Up' 'keyup Shift_L' 'keyup Alt_L'

4) Fill in the other fields however you wish, and set an icon by clicking on the icon in the upper left corner of the window

5) As root, open /usr/share/applications

6) Copy the launcher you created to /usr/share/applications

7) Drag and drop the launcher from /usr/share/applications to the unity launcher

8 ) If you don't want the launcher on your desktop, you can now delete it

---

