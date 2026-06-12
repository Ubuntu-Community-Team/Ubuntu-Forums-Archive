---
title: "Main Menu Panel"
date: 2010-01-27
forum: General Help
---

### Post by CortPryor on 2010-01-27
Hello All,  I am a new Ubuntu user and I am having a problem with the main menu panel. I am talking about the panel that loads to the top of the screen with the default setting.  It contains preferences tab, system tab, etc.  I changed the properties and set the position to bottom of screen, and autohide.  When I launch Ubuntu the panel shows up on the bottom but I can't use it or access the properties.  Can someone please help me get back to the default setup.  I am currently running Unbuntu 9.10 with the most recent updates.

Thanks, 
Cort

---

### Post by raktarok on 2010-01-27
Hi there,

Try this form a terminal - it resets the panel to its default settings:

```
gconftool --recursive-unset /apps/panel
```

Then logout and relogin.

The panel should work even if you keep it at the bottom and autohide it. I don't know what is wrong though, can you provide more details? you can't use the menus when you keep it at the bottom?

---

### Post by CortPryor on 2010-01-27
yes that is correct I can't use the menus and when I put the cursor over the bottom panel....it starts flickering and eventually the default bottom panel appears....the panel that contains the trash can and show desktop button.   I will try your command and see what happens
Thanks,

cort

---

### Post by raktarok on 2010-01-27
Did you delete the bottom panel before moving the top panel there? The flickering should stop after that...

---

