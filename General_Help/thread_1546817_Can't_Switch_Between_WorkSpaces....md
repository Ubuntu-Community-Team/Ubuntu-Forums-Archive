---
title: "Can't Switch Between WorkSpaces..."
date: 2010-08-05
forum: General Help
---

### Post by DTHCND on 2010-08-05
I can't switch between them at all... I tried clicking and Ctrl + Alt + Left/Right, etc... Can't figure out what's wrong... Hmm... 10.04 is getting a bit irritating... (Already had to reformat 3 time...) Any help???

---

### Post by ubunterooster on 2010-08-05
add to panel "workspace switcher" click on which workspace you want to go to

---

### Post by DTHCND on 2010-08-06
I already tried that... Clicking on one of the other workspaces doesn't do anything... It used to work fine, but i recently reformatted my HDD (like I said before) and I didn't check to see if it was working, so idk if it was always like this or if it was something I installed afterwards... Thinking I should reformat... < Fastest fix... Not to many things I got to reinstall...

---

### Post by DTHCND on 2010-08-06
Ok I just backed up all my photos and stuff... Goin to reformat now... I'll tell you guys how it goes...

---

### Post by WorMzy on 2010-08-06
If the workspace switcher isn't working, then I think that indicates that your window manager (metacity/compiz) has crashed. Opening a terminal and running ```
metacity --replace
```
should fix it.

There's really no need reinstall your entire OS every time something goes wrong, this isn't Windows. o.O

---

### Post by DTHCND on 2010-08-06
Ya lol, good thing I didn't yet... For some reason in Compiz settings, Desktop Cube was enabled but Rotate Desktop was disabled... Idk how that happened, but ya... Fixed now... :D

---

### Post by xieon on 2010-10-03
> **WorMzy said:**
> If the workspace switcher isn't working, then I think that indicates that your window manager (metacity/compiz) has crashed. Opening a terminal and running ```
metacity --replace
```should fix it.

There's really no need reinstall your entire OS every time something goes wrong, this isn't Windows. o.O


I had this prolem, and that indeed did fix it. Thanks

**[COLOR=Red]Edit[/COLOR]**: Actually it doesn't work, it screws my screen up and put black boxs where my docks are and i need to restart. 
Then when I restart, and the docks load this brings back the problem, so I believe that the docks I'm using Cairo Dock (sp) is not allowing the switch.

---

