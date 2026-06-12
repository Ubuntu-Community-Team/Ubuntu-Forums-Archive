---
title: "Caught inside the Desktop Cube"
date: 2009-10-06
forum: General Help
---

### Post by sopadeajo on 2009-10-06
This just happened to me.

Learning to use Desktop Cube and Rotate Cube i configured by mistake Rotate Right With Window (using the mouse) to Button 1 (i had configured it first to Ctrl +Shift+Button1 and then unchecked Ctrl and Shift not realising that Button1 remained (i said yes to a warning message without reading it because there are tons of messages in these settings). I had not seen the sweep icon served to disable.

By chance Terminal was started in one of the 4 Desktops of the virtual but real  cube inside of which i only could rotate.

I managed to write ccsm in it and open Compiz Config Setting Manager which had closed and then uncheck Rotate Cube check mark by using Win+ Alt+Button1 (a chance this combination worked for unchecking).

If Terminal had not been opened in Desktop I would have had to reinstall Ubuntu.

Anybody with ideas of what to do in such a situation?

Other ways to solve this situation???

---

### Post by scouser73 on 2009-10-06
You wouldn't have needed to reinstall Ubuntu, rather just do a hard shutdown.

---

### Post by yeeeev on 2009-10-06
In any case, you can always do <ctrl+alt+f1> which will get you to a terminal, and then 
```
metacity --replace
```

---

### Post by sopadeajo on 2009-10-06
> **scouser73 said:**
> You wouldn't have needed to reinstall Ubuntu, rather just do a hard shutdown.

I did 2 hard shutdowns and i got exactly to the same situation each time inside the same deskstop with my left click serving only to rotate around the 4 desktops.

---

### Post by sanguinoso on 2009-10-06
You can hit ALT-F2 to pull up the terminal to be able to type ccsm

---

### Post by Portable_Jim on 2009-10-06
> **sopadeajo said:**
> This just happened to me.

Learning to use Desktop Cube and Rotate Cube i configured by mistake Rotate Right With Window (using the mouse) to Button 1 (i had configured it first to Ctrl +Shift+Button1 and then unchecked Ctrl and Shift not realising that Button1 remained (i said yes to a warning message without reading it because there are tons of messages in these settings). I had not seen the sweep icon served to disable.

By chance Terminal was started in one of the 4 Desktops of the virtual but real  cube inside of which i only could rotate.

I managed to write ccsm in it and open Compiz Config Setting Manager which had closed and then uncheck Rotate Cube check mark by using Win+ Alt+Button1 (a chance this combination worked for unchecking).

If Terminal had not been opened in Desktop I would have had to reinstall Ubuntu.

Anybody with ideas of what to do in such a situation?

Other ways to solve this situation???
Use keyboard shortcuts.

The following steps are a small tour, now the problem has been fixed

[LIST=1]
[*]Close all windows
[*]Place (physical) mouse in weird position so you know when you touch it. (i.e. you will not need to)
[*]Press Alt + F2 and type ```
gnome-terminal
```
[*]Type in ```
ccsm
``` into the terminal
[*]Use the tab key to select the option you would normally click on.
[*]Press the space bar to go into the option
[*]Use the spacebar to toggle options
[*]Use the arrow keys to change numerical options
[/LIST]

---

### Post by sopadeajo on 2009-10-06
Simpler way to do it:

Alt+F2-->
type ccsm-->
Down Arrow Key until you get to Desktop-->
Space bar to go to Desktop option--->
Right Arrow to be situated in trhe column where Rotate Cube option is-->
UP Arrow until you reach Rotate Cube-->
Space Bar to unmark Rotate cube checkmark.

---

