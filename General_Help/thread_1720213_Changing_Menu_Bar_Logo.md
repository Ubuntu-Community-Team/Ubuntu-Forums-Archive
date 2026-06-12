---
title: "Changing Menu Bar Logo"
date: 2011-04-03
forum: General Help
---

### Post by OSAppleX on 2011-04-03
I recently applied a nice, early Mac OSX theme and it's complete except for the menu bar logo.

I tried these steps but they didn't work.  Ubuntu 10.10

> 
Once you've selected the icon you want, get into the configuration  editor -- System Tools|Configuration Editor, or aptitude install  gconf-editor if necessary. From there -- apps|panel|objects. 

You will see a series of folders named object_0, object_1, etc. The  trick now is to discover which of those objects is your menu  application. Believe me, it could be any of them. Each folder contains a  similar collection of information. The solution for me was to click  thru all the objects watching the "position" key. Since my menu is at  the left side of the panel, it was the one with the lowest number in  that key. That turned out to be object_3.

From there on, it's a piece of cake. Click the checkbox for  "use_custom_icon", then right-click on "custom_icon", select "Edit  key..." and enter the full path to your chosen icon. (For me: /usr/share/pixmaps/menu32.png) 			 		

---

