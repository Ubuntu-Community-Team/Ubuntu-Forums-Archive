---
title: "GNOME bar error"
date: 2011-03-09
forum: General Help
---

### Post by nkae100 on 2011-03-09
10.04 LTS:

I added a second bar and set it at the top (with my other one) and to auto-hide... now it has overlapped the original bar and left/right clicking in it does nothing.

How can I remove this bar? I guess this is a bug and I will have to delete it manually from like a configuration file?

---

### Post by Frogs Hair on 2011-03-09
Try to reset panels to default.```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by nkae100 on 2011-03-09
Thanks! But thats out of the question. :)

---

### Post by Verbeck on 2011-03-09
> **nkae100 said:**
> Thanks! But thats out of the question. :)
may i ask why?
that's the way to reset them to default

(another way is to remove the folder *~/.gconf/apps/panel/ *[I])
[/I]press alt+F2[I] (run dialogue) OR alt+ctrl+T (terminal) and

rm -rf ~/.gconf/apps/panel/
pkill gnome-panel [/I]

---

### Post by nkae100 on 2011-03-09
This problem has been solved by [[COLOR=#D40000]**howefield**[/COLOR]]("http://ubuntuforums.org/member.php?u=186490"):

Try pressing the Alt + F2 and in the run box type,

 	Code:
 	gconf-editor 
Navigate to apps > panel > toplevels > top_panel_screen0  and uncheck the box next to auto_hide.

Does that do it ?

You might have to look at some of the other options.

If this doesn't work, you can put the panels back to default by deleting  the configuration folder in /home. But doing that might be a bit of a  sledgehammer to crack a nut

---

