---
title: "Panel not respond"
date: 2009-11-04
forum: General Help
---

### Post by ckinsung on 2009-11-04
What I did to the panel was only choose to auto hide it , but after restarting my computer, the panel freeze and I cannot see it on the desktop. I can't access all the applications . etc.. How can I restore my panel setting? 
[IMG]http://i6.photobucket.com/albums/y246/ckinsung/Screenshot1.png[/IMG]
[IMG]http://i6.photobucket.com/albums/y246/ckinsung/Screenshot2.png[/IMG]
As you can see from the second picture, when I tried to restart my computer, a screen saying that my panel is not working. I usually put my panel at the bottom rather at at the top(default), but you see that the default panel disappears at the bottom.

---

### Post by kelvin.illa on 2009-11-05
I think this (auto-hide feature) is still glitched; the panel fails to detect cursor contact. Since you can't click on the panel to change its properties, you have to change the settings somewhere else. Fire up 'gconf-editor' via terminal (though there are other ways to to this, this is the most direct for instructional purposes)  by typing "gconf-editor." In 'gconf-editor,' go to //apps/panel/toplevels*/top_panel_screen0*, there will be a list on the right; uncheck "auto_hide".

* (this is my settings) depends on your panel settings, may vary.

---

### Post by ckinsung on 2009-11-05
> **kelvin.illa said:**
> I think this (auto-hide feature) is still glitched; the panel fails to detect cursor contact. Since you can't click on the panel to change its properties, you have to change the settings somewhere else. Fire up 'gconf-editor' via terminal (though there are other ways to to this, this is the most direct for instructional purposes)  by typing "gconf-editor." In 'gconf-editor,' go to //apps/panel/toplevels*/top_panel_screen0*, there will be a list on the right; uncheck "auto_hide".

* (this is my settings) depends on your panel settings, may vary.


About 9 hours before, I managed to get some helps and it worked perfectly. 

gconftool-2 --shutdown && rm -rf ~/.gconf/apps/panel && pkill gnome-panel

Thank you for your helps also.

---

