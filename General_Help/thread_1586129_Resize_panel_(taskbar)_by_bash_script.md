---
title: "Resize panel (taskbar) by bash script"
date: 2010-10-01
forum: General Help
---

### Post by WG- on 2010-10-01
Hello people,

This is my first post as user on this forum. I recently installed ubuntu besides Windows 7. And I'm planning to use ubuntu more for development and writing notes during college with xournal (far better then windows journal :))

So I'm a tablet user. I've already created a bash script to rotate my screen and change the orientation of my tablet pen. 

Because I also like to operate my tablet with my fingers I want to create a bash script which does the following thing automatic... 

When you go to your panal (taskbar on the top) you can do right click -> prefences in the form that pops-up you can change the size of the panel... I want to change this size by a script so I can add it to my bash script which is executed when I go into tablet mode...

Anyone knows how to do this???

ps. if anyone knows some cool software applications for tablets in ubuntu I would like to know about it.

Thanks already for your help and regards!

---

### Post by WG- on 2010-10-01
With some help I figured it out...

```
gconftool-2 --set /apps/panel/toplevels/bottom_panel_screen0/size --type integer <number>
gconftool-2 --set /apps/panel/toplevels/top_panel_screen0/size --type integer <number>
```

---

### Post by Favux on 2010-10-02
Hi WG-,

Welcome to Ubuntu forums!

What kind of tablet pc do you have?

You should check out at least CellWriter and EasyStroke.

---

### Post by WG- on 2010-10-03
> **Favux said:**
> Hi WG-,

Welcome to Ubuntu forums!

What kind of tablet pc do you have?

You should check out at least CellWriter and EasyStroke.

Hello Favux :)

I've a toshiba portégé m750. CellWriter I already found :) easystroke not so thank you for the tip!

Maybe you can help me with another problem I've: [http://ubuntuforums.org/showthread.php?t=1587413](http://ubuntuforums.org/showthread.php?t=1587413)

---

### Post by Favux on 2010-10-03
Already posted.  Are the gconftool-2 commands yours?  You said you had help.

---

