---
title: "Workspace settings 12.04"
date: 2012-05-01
forum: General Help
---

### Post by megabuffen on 2012-05-01
I'm using classic Gnome in 12.04. How do I disable the workspaces completely? If i right-click on the workspace switcher on the bottom panel I can change the settings. I can change the number of workspaces, but if I set the value to 1, I get 4 of them. Any other number works, such as 2 workspaces, but setting it to 1 will always result in 4.

---

### Post by BoppaGene on 2012-05-01
I have a similar problem with 12.04 workspace switching. I am also using Gnome Classic but tried ubuntu default dash and had the same problem. When I start the switcher the icon at the right of the windows switch bar at the bottom of my screen shows 4 workspaces in a 2x2 grid. This icon is half hight on the bar. I had 6 workspaces on 11.10 in a 2x3 grid. I select preferences from the icon and see a 2 row 1 column setting indicated. I change this to a 2 row 3 column set up. I get a 2x3 full hight switcher icon on the window bar. BUT! All of the workspaces are empty. None of the applications can be reached. None of the normal buttons and menus work. Using hot keys I can move between workspaces in the 2x3 set up but can not get to anything in the 2x2 set up. The only way I can get out of the condition is to use a hardware interrupt to shut the machine down. When I restart I am again in the 2x2 set up.

---

### Post by megabuffen on 2012-05-01
The problem seems to have been solved now. I set the number of workspaces to 1. After rebooting my computer, it started working. Now I can remove the workspace switcher.

I don't find the workspace feature very useful at all since I usually have three monitors.

---

### Post by ryanyeah on 2012-05-04
> **megabuffen said:**
> The problem seems to have been solved now. I set the number of workspaces to 1. After rebooting my computer, it started working. Now I can remove the workspace switcher.

I don't find the workspace feature very useful at all since I usually have three monitors.

How do you remove the workspace switcher? I also want to remove all workspaces, and it works if i set workspaces to "1" and then reboot. But after I press ctrl + alt + arrow key it will bring back 4 workspaces.

---

### Post by ryanyeah on 2012-05-05
Ok quickfix for now is to just disable the shortcuts for accessing any other workspace.

---

### Post by megabuffen on 2012-05-08
The workspace switcher can be removed by holding Alt+Super and right clicking on it.

However, I keep getting 4 workspaces even though i've selected 1 in "Preferences".

---

### Post by AlbertJB on 2012-05-08
Me too, It's quite annoying not being able to delete the extra workspaces. On top of that, it's annoying when right-clicking on a minimized window at some panel (inferior panel in my case) and having to select between a lot of options (move to workspace x, etc.....)

---

### Post by mc4man on 2012-05-08
If using Classic then you're using compiz so the number of WS's should be adjusted there.
You could use ccsm & change in General options > Desktop size or run 2 commands
```
gconftool --type Integer --set /apps/compiz-1/general/screen0/options/vsize 1

```
```
gconftool --type Integer --set /apps/compiz-1/general/screen0/options/hsize 1
```

(- on Classic (no effects) if any issue it's set in metacity - 
```
gconftool --type Integer --set /apps/metacity/general/num_workspaces 1
```

---

### Post by AlbertJB on 2012-05-09
Thanks a lot mc4man, I owe you BIG time! :)

Although I would like to disable the ALT key for moving/deleting items on the panels (like in gnome 2.x).

I've tried gconftool-2 --set --type string /apps/metacity/general/mouse_button_modifier 'disabled' on Gnome-classic without effects but it seems Gnome Team really want the users to use the Alt+RightClick method in Gnome Classic.. :(

---

### Post by megabuffen on 2012-05-13
I found the solution some days ago. CompizConfig was the solution.

---

### Post by cch63 on 2012-06-14
Personaly, I use to work with gnome-classic, and with 4 workspaces. after migrating to 12.04, I always get nothing on workspaces 2-4.

To solve it, I have activated DesktopWall option in CCSM, and now my workspaces are working correctly.

Hope it will help those who want multiple workspaces on 12.04 and gnome-classic.

---

