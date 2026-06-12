---
title: "73 Workspaces? How to remove?"
date: 2009-11-24
forum: General Help
---

### Post by Uss_Defiant on 2009-11-24
Hey guys, I've got a ridiculous number of workspaces on my computer... I dont know how they all appeared. How would I limit this number? I've tried going into the "preferences" option in the workspace switcher applet on the gnome toolbar, but it does not give me any option to reduce this number

Any help would be appreciated, thanks!

---

### Post by hwttdz on 2009-11-24
You can't click the down arrow in workspace preferences? or just type in something reasonable (2-4)?

If using metacity you can try 
gconf-editor
and change 
/apps/metacity/general/num_workspaces
to the desired value

you could also try setting 
/desktop/gnome/applications/window_manager/number_of_workspaces

or if using compiz set the desktop size under general options in ccsm.

---

### Post by Uss_Defiant on 2009-11-24
Sweet, thanks a bunch... for some reason I could not click the down arrow in workspace preferences...

I did manage to modify it by using compiz, so that it now has 3 desktops.

Thanks again

---

