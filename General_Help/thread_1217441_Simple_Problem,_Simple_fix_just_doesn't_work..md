---
title: "Simple Problem, Simple fix just doesn't work."
date: 2009-07-19
forum: General Help
---

### Post by onexmadxdisaster on 2009-07-19
Okay, so ever since i got my dell mini with ubuntu, I set it all up so it looked and functioned the way I want. Except for the clock. No matter how many times I right click, go to preferences, and select 12 hour format and change it, it doesnt actually change. I have rummaged through all the settings and options, changed it and restarted, etc, and nothing will actually change it from 24 hour. I know how to read military time, I just really don't like it. Any Ideas?

---

### Post by ybmatters on 2009-07-19
Just a thought, but have you set your location?

---

### Post by TeoBigusGeekus on 2009-07-19
Have you tried removing it and then adding it again to the panel?

---

### Post by michy99 on 2009-07-19
Not sure why that isn't working, but you can try changing it in the configuration editor. If it is not in the Applications menu under System Tools, you can start it from the terminal by entering```
gconf-editor
```Look under /apps/panel/applets/clock_screen0/prefs and set 'format' to '12-hour'.

---

### Post by onexmadxdisaster on 2009-07-19
Yep. Tried both. and if i manually edit the time, it just changes itself or continues to be 24 hour format for the wrong time later. Idk what to do.

---

### Post by onexmadxdisaster on 2009-07-19
When i go to terminal, launch the gconf-editor, click apps, panel, applets, ... there is no clock_screen0
I cant find anything like it in there...
When i took it off the panel, i went to put it back on, but now it isnt over by the other icons like I wanted it...

---

### Post by TeoBigusGeekus on 2009-07-19
> **onexmadxdisaster said:**
> When i go to terminal, launch the gconf-editor, click apps, panel, applets, ... there is no clock_screen0
I cant find anything like it in there...
When i took it off the panel, i went to put it back on, but now it isnt over by the other icons like I wanted it...

What do you mean? Does it show the correct time now?

---

### Post by michy99 on 2009-07-19
You should be able to right-click in it and choose 'Move' (you may have to un-check 'Lock To Panel' first)

---

### Post by onexmadxdisaster on 2009-07-19
Sorry, I am not the best at important details yet...
When I took it off and put it back on the panel, it showed 24 format. when I change it to 12 hour it stays in 24 hour. when I manually change the time, it changes to 12 hour, but by the time it gets to the 12 hour mark again it still goes to 13 and not 1.
Also, when i right click and select move, it wont move past a little divider that separates the icons from the menus. and when I remove the divider, it gets rid of my battery and wireless icons and i still cant move the time past my username up top. 
idk if this makes any sense...

---

### Post by michy99 on 2009-07-19
Yes, you are making sense, but I don't know how to fix it. When you add it to the panel, it should add it at the spot you click on.

---

### Post by onexmadxdisaster on 2009-07-19
But I can't right click the panel in the spot between the sound icon and the icon that lets me choose to restart or hibernate or whatever. because if I right click its one of the existing icons. there is no inbetween. which is where I want it. and now my that my freaking wireless and battery icons are gone, i can add new ones in a different place, but they aren't even the same icons. they are uglier. I have messed with this too much to fix...

---

### Post by onexmadxdisaster on 2009-07-19
Okay, I managed to get the clock past my username by moving my username and other things... some progress. But I still havent permanently fixed the time problem, and I dont want the ugly wireless and battery icons.....

---

### Post by onexmadxdisaster on 2009-07-19
More progress, when i select add to panel, there is an option for custom program launcher or something, and I wanted under administration there is a power management icon. But i still cant find my wireless icon that i like. it doesnt have the two monitors like everything else...
wondering if this is an icon specific for the wireless itself? maybe if i reboot it will appear on its own...... *sigh*
And forget the clock... i am tired of trying to fix such an insignificant problem that nobody else has. 
Frustration gets me nowhere....

---

