---
title: "Pidgin to 'tray'"
date: 2010-04-01
forum: General Help
---

### Post by WASasquatch on 2010-04-01
Hey everyone, back with more help needed. ;)

Is there anyway I can make Pidgin attach itself to my tray like it's window addon? 

I am a PHP programer, and find myself with a lot of tabs open. While the second workspace is much appreciated by most, it's under appreciated by me as it adds a extra step between clients and work.

---

### Post by Vaphell on 2010-04-01
could you elaborate? i don't exactly understand what 'pidgin attach itself to tray like it's window addon' is supposed to mean/look like.
you want to have a permanent pidgin icon in system tray next to the clock?

---

### Post by WASasquatch on 2010-04-01
Yes, exactly that. Sorry I didn't explain that right. :P

---

### Post by gradinaruvasile on 2010-04-01
> **WASasquatch said:**
> Hey everyone, back with more help needed. ;)

Is there anyway I can make Pidgin attach itself to my tray like it's window addon? 

I am a PHP programer, and find myself with a lot of tabs open. While the second workspace is much appreciated by most, it's under appreciated by me as it adds a extra step between clients and work.

Tools -> Preferences -> Interface -> Show system tray icon: Always
?

---

### Post by colorlessprism on 2010-04-01
for my install, i use ubuntu, pidgin automatically hits the task bar when i start the program. check your options to see if it needs to be enabled. you may also need to add a "Notification Area" to your taksbar if there isn't one already. (you should be able to right click your task bar and click "add to panel"). for any program that does not minimize to the task bar(thunderbird and evolution come to mind) there is kdocker (my preference) and alltray. both of these should be in the repository (from the terminal type "sudo apt-get install kdocker")

---

### Post by Vaphell on 2010-04-01
just like gradinaruvasile said, goto preferences and set show system tray icon to 'always'

---

### Post by ajgreeny on 2010-04-01
I recall in a previous version of ubuntu using gnome, I had a need to add a sleep option to the pidgin command in the startup applications, or pidgin would start in its own window, in spite of the preferences being set for "start minimised".

The command I used in startup applications was ```
sh -c "sleep 10; pidgin"
```and then pidgin would start minimised as it was supposed to.  Is that your problem, that the application always starts in its window and not minimised?  If so, try the trick shown.

---

