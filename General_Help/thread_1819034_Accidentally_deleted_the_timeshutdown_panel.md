---
title: "Accidentally deleted the time/shutdown panel"
date: 2011-08-05
forum: General Help
---

### Post by pannerrammer on 2011-08-05
The top right panel item contains the shutdown, time, network icons, etc. 

I don't use the messaging icon so right-clicked and chose 'remove from panel'. The whole lot disappeared!

How can I restore things to their original state?

---

### Post by syntr on 2011-08-05
You can try

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by Jouke S on 2011-08-05
> **syntr said:**
> You can try

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

This command restores the panels back to their default state. I wouldn't recommend it. Instead, right click the top panel - add to panel and add the indicator applet complete.

You can right click individual panels to lock them to the panel, and then proceed to delete unwanted ones, instead of keeping them all in a set.

---

### Post by pannerrammer on 2011-08-05
> **Jouke S said:**
> This command restores the panels back to their default state. I wouldn't recommend it. Instead, right click the top panel - add to panel and add the indicator applet complete.

You can right click individual panels to lock them to the panel, and then proceed to delete unwanted ones, instead of keeping them all in a set.


I didn't know that the thing on the right is called the "indicator applet complete". Thanks.

---

### Post by syntr on 2011-08-05
> **Jouke S said:**
> This command restores the panels back to their default state. I wouldn't recommend it. Instead, right click the top panel - add to panel and add the indicator applet complete.

You can right click individual panels to lock them to the panel, and then proceed to delete unwanted ones, instead of keeping them all in a set.

He asked "How can I restore things to their original state?", but I should have mentioned that that would restore the default panels. :)

Also, AFAIK it's impossible to remove the messaging icon without removing the other app indicators as well.

---

### Post by pannerrammer on 2011-08-05
> **syntr said:**
> He asked "How can I restore things to their original state?", but I should have mentioned that that would restore the default panels. :)

Also, AFAIK it's impossible to remove the messaging icon without removing the other app indicators as well.

"it's impossible to remove the messaging icon without removing the other app indicators as well". Yes, it's a pity they can't be split. I never use the sound, messaging or chat things (yes, I'm the grumpy old man to be spotted standing at the back at parties... yes, next to the beer!)

Thanks syntr. I've added both the  info about adding the "indicator applet complete" applet and the terminal command to my "how to..." file

---

