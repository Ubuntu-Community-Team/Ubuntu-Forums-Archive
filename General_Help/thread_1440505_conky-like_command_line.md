---
title: "conky-like command line?"
date: 2010-03-27
forum: General Help
---

### Post by gfunkera on 2010-03-27
is it possible to have a command line prompt available on the desktop, operating sort of like conky?

---

### Post by darolu on 2010-03-27
You can use conky in xubuntu too.
```
sudo apt-get install conky
```
Just in case, read this thread:
[http://ubuntuforums.org/showthread.php?t=850669](http://ubuntuforums.org/showthread.php?t=850669)

---

### Post by gfunkera on 2010-03-27
> **darolu said:**
> You can use conky in xubuntu too.


[COLOR=Black]
[/COLOR] [COLOR=Black][B]i think you have misnderstood my question or i have not adequately explained it...

 i am not asking how to install conky or if its available in xubuntu... i already have done that..

i am asking if there is any way to get a terminal/console prompt ready for input and feedback on the desktop...

other ways of asking this question:
-can you have a terminal built into the desktop?
-is there anyway i can get conky to function as a command line?
-has anyone written a program that allows for a user to use the terminal/console/command line without opening a separate window but rather just having it ready at all times on the desktop, running as a program like conky does?
[/B][/COLOR]

---

### Post by nitstorm on 2010-03-27
[http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop](http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop)

maybe this link would be helpful, cheers :)

---

### Post by nothingspecial on 2010-03-27
You can achieve that alot easier if you are running compiz

Go to the window rules config and enter the title of the window into the "below" (which means that the terminal will always be below every other window, effectively making it your desktop while it is running), and "sticky" (which means it will be on all workspaces).

Because I sometimes like to run other terminals I run byobu in the "Desktop" terminal. Byobu is as conkyish as you can make your terminal in the sense that you can display system info with it  - fan speed, temperature, etc etc.

This means the windows title is nothingspecial@laptop - byobu rather than nothingspecial@laptop which would be any old terminal.

Byobu (a fancy gnu screen) has workspaces too. Press F2 to create a new one and use F3 and F4 to toggle between them. So your "terminal desktop" can run loads of different stuff at the same time.

---

### Post by nothingspecial on 2010-03-27
You need to know how to find a windows title.

Type

```
xprop WM_NAME | cut -d\" -f2
```

Your pointer will turn into a cross. Use it to click the terminal window and the title will be displayed.

Also you need to add the command to start your terminal to system > preferences > startup applications. Mine is

```
gnome-terminal --geometry=128x35+0+0 -x byobu
```

Your geometry will be different probably. The first number is the amount of characters your terminal will display horizontaly, the second is the vertical value.

---

