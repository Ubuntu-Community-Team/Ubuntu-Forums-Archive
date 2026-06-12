---
title: "Help me Please"
date: 2010-09-20
forum: General Help
---

### Post by robinpaschal on 2010-09-20
Hello to all Mates,

I am newbie in Ubuntu...Now i got one more problem.
When i am starting my pc it never shows the icons at Panel(Both).


How can i solve it?

---

### Post by sikander3786 on 2010-09-20
Please provide some more details.

Which version of Ubuntu are you running? Can you see the panel itself? And what about desktop icons? Was it working anytime before or it is a fresh install?

---

### Post by robinpaschal on 2010-09-20
This is Ubuntu 9.1.
I am using from last 4 months so it is not fresh copy.
I can see desktop icons.
I can see the Panel...But Panel icons(Application, Places, System) are not appear.
Also when i clicking it's not get any effect.

---

### Post by xdweaver on 2010-09-20
you can try sudo gnome -panel restart

---

### Post by utnubuuser on 2010-09-20
Can you get your icons etc with > sudo gnome-panel restartfrom a terminal?

---

### Post by k33bz on 2010-09-20
This may be a dumb question, but by any chance can you right click on the panel and choose "Add to panel"?

---

### Post by robinpaschal on 2010-09-20
> **k33bz said:**
> This may be a dumb question, but by any chance can you right click on the panel and choose "Add to panel"?


Ya The question is Dumb...But perhaps you don't know I am still facing the Dumb error with Panel. When I click the right then not a single Option appearing.

That's why i ask for help.

---

### Post by Ahava591 on 2010-09-20
> **robinpaschal said:**
> Ya The question is Dumb...But perhaps you don't know I am still facing the Dumb error with Panel. When I click the right then not a single Option appearing.

That's why i ask for help.

They weren't saying your question is dumb; they were saying their question might be dumb to you.
Hope your problem is solved soon.

---

### Post by k33bz on 2010-09-20
> **robinpaschal said:**
> Ya The question is Dumb...But perhaps you don't know I am still facing the Dumb error with Panel. When I click the right then not a single Option appearing.

That's why i ask for help.

The reason I asked that way, because my question may of been dumb to you, however sometimes people over look the small details, I was just looking to see if maybe they were deleted from panel and all you had to do was add them back in.

Since that does not seem to be the case, reloading the panels, as stated above, should work.

---

### Post by robinpaschal on 2010-09-20
> **k33bz said:**
> The reason I asked that way, because my question may of been dumb to you, however sometimes people over look the small details, I was just looking to see if maybe they were deleted from panel and all you had to do was add them back in.

Since that does not seem to be the case, reloading the panels, as stated above, should work.


Thanks for the suggestion. I am always trying my best to solve problem with own capability. But As you know i am totally newbie in Ubuntu. 

But that forum members helps me lot to operate this one. Thanks for the admin and all member. Perhaps you don't know how much problem i had with Ubuntu. You can check i have 17 post and all threads started by me to solve something.

Anyway thanks to all.....

---

### Post by robinpaschal on 2010-09-21
How can i type this command?

> sudo gnome -panel restart

I can't see anything at panel. So how can i go to Terminal:confused:

---

### Post by bigsmitty64 on 2010-09-21
right click on the desktop, choose "create launcher"

In the window that pops up:
Leave the **Type**: application

Make,
**Name:**         Terminal
**Command**:   gnome-terminal

press "**ok**"  that will give you a terminal on the desktop.

**Then you can run**: sudo gnome -panel restart

I hope this helps you!

---

### Post by robinpaschal on 2010-09-21
Great to see this. I will try this and tell you after 30 Minutes.

---

### Post by utnubuuser on 2010-09-22
Alt+F2 opens a RUN dialog... you can launch darn near anything from that.  Alt+F2 is the way to run gconf-editor too....

---

