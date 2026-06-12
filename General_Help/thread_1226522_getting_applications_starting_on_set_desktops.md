---
title: "getting applications starting on set desktops"
date: 2009-07-29
forum: General Help
---

### Post by diggedy on 2009-07-29
Does anyone know how to do this when not using compiz? I can do it using the place windows function in compiz but Ive found compiz is giving me some stability issues so im trying to get away from it

---

### Post by Zorael on 2009-07-29
Hmm.

[list][*]System Settings -> Window Behavior -> Window-specific -> New.
[*]Detect Window Properties, point at your application/specific window of the application, choose class/window matching as you see fit.
**- edit:** A shortcut is to click the icon of a window (generally to the left of the window title, topleft corner of a window), then Advanced -> Special Window/Application Settings.
[*]Geometry tab, Desktop -> Apply Initially -> pick desktop number.[/list]
That *should* technically work. Toy around with class/window matching to get the results you want. If you pick Force instead of Apply Initially, I imagine the window gets locked to that desktop. And I guess Remember makes it open in the desktop you closed it in last.

If you create other rules, don't forget that most require you to check that checkbox next to the do not affect/force/apply initially/etc dropdown menu.

I have a few rules for apps that lodge themselves in the system tray (kopete, amarok, konversation, etc). Since they're already there and they have tray icon effects for when they want attention, it seems like a waste of screen budget to also have them create taskbar entries on my already cramped netbook screen. Preferences tab, Skip taskbar -> check the box. Using "specific window" as the class/window match method, kopete chat windows properly get a taskbar entry, but the main window doesn't.

---

### Post by diggedy on 2009-07-30
your a star! Works better than place windows with compiz too.

---

