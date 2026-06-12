---
title: "Panel unresponsive"
date: 2010-08-19
forum: General Help
---

### Post by demontranoth on 2010-08-19
I was experimenting with the look of my desktop and I made a third panel which I placed at the right of my screen, I made it so that it could autohide. For some reason, it got stuck while being hidden and now I cant get rid of it!!! this is anoying because now I have a red line at the right of my screen. How can I delete this third panel?

---

### Post by plucky on 2010-08-19
> **demontranoth said:**
> I was experimenting with the look of my desktop and I made a third panel which I placed at the right of my screen, I made it so that it could autohide. For some reason, it got stuck while being hidden and now I cant get rid of it!!! this is anoying because now I have a red line at the right of my screen. How can I delete this third panel?

Right click on another panel and select **Properties**.

When the window opens, under **Orientation** select **Right** and un-tick **Autohide**.

The panel should then appear.You can then click on it and delete it.

Good Luck

---

### Post by M4he on 2010-08-19
It got stuck while hiding? Do you mean it's unresponsive?
If so you can try opening a terminal and type:
```
killall gnome-panel
```(that will restart the panels, so it might react to your mouse again)


If that doesn't help you can just reset your panels by typing
                           ```
gconftool-2 --recursive-unset /apps/panel 
        
pkill gnome-panel
   
  
```Warning: that will reset all gnome-panels to the default!

---

### Post by gadolinio on 2010-08-19
> **M4he said:**
> It got stuck while hiding? Do you mean it's unresponsive?
If so you can try opening a terminal and type:
killall gnome-panel

+1.
If that doesn't work, try opening gconf-editor (press Alt+F2, then type "gconf-editor").
Go to apps/panel/toplevels and see it you can find simething useful there. (just be careful not to ruin the panels you want to keep :P  )

---

### Post by pjizz on 2010-10-11
i have this same error, and resetting the panels fixes it, except when i try to make the new panels autohide the error keeps reproducing.  in fact, any panel i create and then tell to autohide becomes stuck the first time it hides

anyone else experiencing this issue?  i just upgraded to 10.10

---

### Post by mcco2242 on 2011-03-06
Yeah i got the same problem, i had to reste my panels twice before. I don't know why that's happening... I know the applets still work (if you hit Alt+F1, the main menu opens) so it may be a problem with the detection of the mouse over the panel.
Anyway if someone find's out anything, it would be great to share.:)

---

