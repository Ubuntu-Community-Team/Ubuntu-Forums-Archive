---
title: "Can't open terminal"
date: 2010-06-09
forum: General Help
---

### Post by mkoijn9 on 2010-06-09
Hi, I'm new to Ubuntu 10.04, I just installed it yesterday on my r50e ibm laptop I used the 32bit version.

When I try to open a terminal from the menus on the top left hand side of the desktop, I get the spinning cursor and then nothing happens, the cursor reverts to the default cursor and the terminal doesn't open.

Any ideas?

Best regards

Albert

---

### Post by jwbrase on 2010-06-09
Well, you can try this:

Hit CTRL-ALT-F1:

You'll get a text display with a login prompt. Type your username, enter, then your password, and enter. (Note, when you type your password, you won't see anything happening. Unlike the graphical login, it doesn't even show stars where your password would be).

Once successfully logged in, type:

```
xterm -display :0
```

If it shows any errors, tell us what it says.

Otherwise, hit ALT-F7 to get back to the GUI. You should have a white space in the upper left corner (actually, I don't think that's what's supposed to happen, but it's what happens on my machine), and an item on the window list on the bottom panel that says "xterm". Click where it says "xterm" twice and you should have a terminal window where the white space was. Type in that terminal window:

```
gnome-terminal
```

which is the program that the "Terminal" item in the menus opens. At this point, you should get an error message describing what's wrong.

---

