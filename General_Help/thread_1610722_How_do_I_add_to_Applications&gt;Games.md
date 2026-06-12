---
title: "How do I add to Applications&gt;Games?"
date: 2010-11-01
forum: General Help
---

### Post by helios16v on 2010-11-01
I've just made a shortcut to a web page which opens a game I play online, I would like to find out where the default location is for all of the games so I can put my web page shortcut in there so it's out of the way, however I want the icon to my shortcut in the Applications menu under the Game section.

-Ben

---

### Post by HiImTye on 2010-11-01
right click your menu button (on the taskbar) and choose 'edit menus'
navigate to games
choose 'new' or something to that extent
copy your command, description, etc in the appropriate boxes

---

### Post by helios16v on 2010-11-01
When I did this the icon didn't show up in the games menu as well as it not working. When I tried to open it a window popped up and said permission denied.. hmm..

---

### Post by Miyavix3 on 2010-11-01
The program to edit gnome menus is called alacarte.

Run it through the terminal for any error messages that may not show up otherwise. 

If you need root, use sudo.

---

### Post by Eddison on 2010-11-01
Thanks HiImTye,

This worked a treat for me, except the game wasn't listed in 'games' menu, it was listed in the main applications' menu.

Eddison

---

### Post by yetiman64 on 2010-11-02
> **Eddison said:**
> Thanks HiImTye,

This worked a treat for me, except the game wasn't listed in 'games' menu, it was listed in the main applications' menu.

Eddison

**@ Eddison,**

Look in your home folder, in ~/.local/share/applications (~ is a system  variable for your home folder). CTRL + H in your home folder will expose the .local folder. The launcher for your game is in there (in applications), though the name displayed may differ from its .desktop fileneme.

So in terminal use
```
ls -l ~/.local/share/applications
```to get the .desktop filename for your game.

When you determine the .desktop name for the game use,
```
gedit ~/.local/share/applications/<name>.desktop
```Replace <name> with the name you have just found.

Locate the line which has
> Categories=change
> Utilityto
> GameNote do not alter any semi-colons before or after this entry.

**If** the "Categories=" doesn't exist add the line
> Categories=Game;to the end of the file. (**Do not repeat this entry if already there**)

On saving the file (and if alterations are done correctly) the game will now be in the games menu.

**@ OP**,please note to use gksudo or gksu with alacarte if root privileges are required as it is a graphical application. Terminal only commands are fine with normal sudo though.

---

### Post by Eddison on 2010-11-02
Ok here is what happened.. You see the game flightgear has a default setting of a cessna 172. But I wish to run the R22 chopper. so i would type in the code:
fgfs --aircraft=R22
Into the terminal window. But as written above I put it into the application menu to save typing. I used your suggestion, and it worked fine, except when i typed Categories=Game; the Game showed up in red type, so I changed it to Games. 
But It is not showing up in application>> games so far ??  probably because it's a terminal launch?
Here is what came up in gedit..

#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Icon[en_IE]=gnome-panel-launcher
Name[en_IE]=R22
Exec=fgfs --aircraft=R22
Name=R22
Icon=gnome-panel-launcher
Categories=Games;


eddison

---

### Post by yetiman64 on 2010-11-02
>  Game showed up in red type, That is normal, a red block with black text.
Change it back to > Categories=Game;

**Edit: @ Eddison, post #9**, You're Welcome :-)

---

### Post by Eddison on 2010-11-02
Magic !!! It worked !!
Thanks very much =D>

Is very satisfying to be able to do things like this.

Eddison

---

