---
title: "Evolution : Task List in Calendar View"
date: 2009-09-15
forum: General Help
---

### Post by twjolson on 2009-09-15
I'm about ready to chuck Evolution and go for KOrganizer.

When I click the Calendar button, there is the calendar in the center and the task list to the right.  However, the calendar takes up like 200-250 pixels, and the task list takes up the majority of the remaining space.  It's annoying.  I see no reason for this, since none of the tasks are nearly that long, text-wise.

Is there a remove the task list from the calendar page, or keep it as small as possible and have that setting remembered?

---

### Post by jmatties on 2009-09-16
I have the exact same problem. I've tried some configuration editor stuff, but nothing seems to work.

---

### Post by twjolson on 2009-09-16
Glad to know I'm not alone.

Anyone have a solution?

That or anyone know a better PIM, KOrganizer seem 'ok', but doesn't seem anything more wonderful than evolution.

---

### Post by twjolson on 2009-09-17
I take that as a No?

---

### Post by jmatties on 2009-09-17
> **twjolson said:**
> I take that as a No?
I've tried to add an to the configuration editor but I really have no idea what I am doing. I found this site:
[http://www.gnome.org/~bmsmith/gconf-docs/C/evolution-calendar.html]("http://www.gnome.org/~bmsmith/gconf-docs/C/evolution-calendar.html")

I thought this &#8595; seemed like the right sort of setting, but I have no idea where to go from here.
/schemas/apps/evolution/calendar/display/task_vpane_position

---

### Post by twjolson on 2009-09-17
Yea, I thought you were on the right track, but I don't think so now.

I opened up gconf-editor, found the key you listed.  You can't edit it, something about schemas, So, I deleted that key and recreated it with a value of 5.  That didn't work, it still taking up all the real estate.

This is what I hate about linux, configuration is extensive, but difficult at best.

---

### Post by jmatties on 2009-09-17
Linux is awesome! Configuration is only possible because its linux. Good luck changing an inner code on outlook or ical.

Under views > current views > define view, I was hoping to be able to set it like that... but nothing.

---

### Post by Altsi on 2009-10-31
Well hello,

I had the same exact awfully annoying problem for a while. I was fiddling with gconf-editor and schemas and applications and ended up having an error every time when opening the calendar.

Finally I noticed that in side bar there are couple of different calendars - "personal" and "birthdays and anniversaries" (in month view choose view->layout->Show side bar). After choosing/activating "personal" calendar you are finally able to change the layout and the changes are saved next time you use the app.


Cheers,

Allu

---

### Post by Altsi on 2009-11-01
No, sorry, that didn't help. This is pretty annoying. If someone knows solution, would be great to hear about it. Meantime I think I go for Sunbird.

---

### Post by jmatties on 2009-11-05
I just looked at the hotkeys for Evolution mail, and ctrl+3 will show the month-view. When I do this, the tasks do not show up. I need a script that will run evolution and then enter ctrl+3.

---

### Post by dcstar on 2009-11-05
> **twjolson said:**
> I'm about ready to chuck Evolution and go for KOrganizer.

When I click the Calendar button, there is the calendar in the center and the task list to the right.  However, the calendar takes up like 200-250 pixels, and the task list takes up the majority of the remaining space.  It's annoying.  I see no reason for this, since none of the tasks are nearly that long, text-wise.

Is there a remove the task list from the calendar page, or keep it as small as possible and have that setting remembered?

If I simply drag the LHS of the Tasks column (where the mouse cursor changes) I can shrink it virtually off the entire screen, and it saves that setting after an Evolution restart.

That seem to do exactly what you want.

---

