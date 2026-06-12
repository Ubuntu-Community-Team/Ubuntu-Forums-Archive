---
title: "Hide a specific instance of a window"
date: 2010-07-21
forum: General Help
---

### Post by zbrown0529 on 2010-07-21
Hi guys, I have a terminal that opens when the system starts and I was wondering if there is any way to keep it specifically, not other terminal windows, from appearing in the window switcher in compiz?

Thanks!

---

### Post by stinkeye on 2010-07-22
This is an example using htop as the command to execute in terminal.
Change to whatever your using.

Open the terminal and create a new profile called **myhtop**
In the **Title and Command **tab change the initail title to **myhtop**
and set to **keep initial title**

Then in ccsm > window management > window rules
add **title=myhtop** to the skip taskbar box so it looks similar to the attached pic.
There is a bug in ccsm  where it doesn't copy the grabbed window, so just put it in manually.


Then as your startup command for the terminal use
```
gnome-terminal --window-with-profile=myhtop -x [COLOR="Magenta"]htop[/COLOR]
```
[COLOR="#ff00ff"]Change for whatever your using.[/COLOR]

---

### Post by zbrown0529 on 2010-07-22
wow, that worked perfectly.

Thanks :D

---

