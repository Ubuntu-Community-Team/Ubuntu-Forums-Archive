---
title: "How to launch a program without an icon?"
date: 2010-08-21
forum: General Help
---

### Post by chucksters on 2010-08-21
how do you launch a program without an icon? I'm trying to open Transmission for torrents and I can't find it. How do I add it to my favorites on my desktop in Ubuntu netbook?

The icon is in user/bin but it doesn't run the program. Can I just double click on something to make it run or do I have to modify a whole bunch of stuff?

I don't like typing stuff to run a program, I just want everything on my favorites on desktop. Can somebody help? --thanks

---

### Post by Ginsu543 on 2010-08-22
Right click any place on your desktop and select "Create Launcher...". Type in the name of the program (in this case Transmission). Type in the command that will launch the program (in this case transmission %F). You can optionally type in a comment (which will show up if your linger your mouse over the icon). If you want to change the default icon, click on the icon image on the left. I suggest you set the directory path to the appropriate transmission.png in /usr/share/pixmaps.

---

### Post by sikander3786 on 2010-08-22
Alternatively, you can just drag and drop an icon to the desktop for later use.

---

### Post by Ginsu543 on 2010-08-22
That was my first idea, too, but the OP seemed to indicate that he can't find the Transmission icon in the menu to drag.

---

### Post by kerry_s on 2010-08-22
> **chucksters said:**
> how do you launch a program without an icon? I'm trying to open Transmission for torrents and I can't find it. How do I add it to my favorites on my desktop in Ubuntu netbook?

The icon is in user/bin but it doesn't run the program. Can I just double click on something to make it run or do I have to modify a whole bunch of stuff?

I don't like typing stuff to run a program, I just want everything on my favorites on desktop. Can somebody help? --thanks

transmission should be under internet, click the button on the top right of the icon to add to favorites.

---

### Post by chucksters on 2010-08-24
"Create Launcher" is not an option when I right click on my desktop. Only "Change Desktop Background" is available. 

Transmission is not in the "Internet" folder, only Firefox and Skype are there

---

### Post by ChaosChris2009 on 2010-08-24
Try this, open Terminal, type in the name of the application, in your case, Transmission

so open Terminal and type in "Transmission" without the quotes and hit ENTER

---

### Post by kerry_s on 2010-08-24
> **chucksters said:**
> "Create Launcher" is not an option when I right click on my desktop. Only "Change Desktop Background" is available. 

Transmission is not in the "Internet" folder, only Firefox and Skype are there

go to system-> main menu
click "internet" on the left
make sure transmission is checked.

---

### Post by chucksters on 2010-09-05
> **kerry_s said:**
> go to system-> main menu
click "internet" on the left
make sure transmission is checked.


That's what I was looking for. Thanks, hombre

---

