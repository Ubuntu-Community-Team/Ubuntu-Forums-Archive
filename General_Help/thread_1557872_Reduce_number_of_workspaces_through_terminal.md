---
title: "Reduce number of workspaces through terminal"
date: 2010-08-21
forum: General Help
---

### Post by jakupl on 2010-08-21
I tried to check how many workspaces my desktop could have at once, and it got stuck at 36. Now i can't reduce the number. When I click the workspace switcher, and press "preferences", the preferences screen flickers like crazy, and I can't change it.
The window title bars and borders are altso gone, but gnome is running.
I don't have compiz running.

Is there any way of reducing the amount of workspaces, through gconf, or terminal?
Any help is appreciated.

---

### Post by sikander3786 on 2010-08-21
Have you looked for this key in gconf?

/schemas/apps/metacity/general/num_workspaces

---

### Post by ajgreeny on 2010-08-21
In gconf-editor go to apps-metacity-general ->num_workspaces and change the 36, which is what I assume it will say at the moment, back to 4, or whatever you prefer.

If you need to do it in the terminal you need to edit /home/*username*/.gconf/apps/metacity/general/%gconf.xml using gedit, or other text editor.

---

### Post by stinkeye on 2010-08-21
In the terminal
For compiz
```
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
```


For Metacity
```
gconftool-2 --type int --set /apps/metacity/general/num_workspaces 4
```

---

### Post by jakupl on 2010-08-21
> **sikander3786 said:**
> Have you looked for this key in gconf?

/schemas/apps/metacity/general/num_workspaces
yes. When I try to change it, I get:
Currently pairs and schemas can't be edited. This will be changed in a later version.

---

### Post by jakupl on 2010-08-21
> **ajgreeny said:**
> 
If you need to do it in the terminal you need to edit /home/*username*/.gconf/apps/metacity/general/%gconf.xml using gedit, or other text editor.

Worked perfectly, thaaanks.

---

