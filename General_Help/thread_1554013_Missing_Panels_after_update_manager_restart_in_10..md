---
title: "Missing Panels after update manager restart in 10.04"
date: 2010-08-16
forum: General Help
---

### Post by UbuNewbie123 on 2010-08-16
I was working fine on my ubuntu 10.04 but decided to update all the packages as suggested by the update manager.

After I restarted my laptop, the panels all disappeared. I can only right click on the desktop and click on my desktop icons to launch programs.

I know I need to launch the terminal window but without the start menu, i cannot access it. Alt + f2 is not working for me. i have no way of getting to the terminal to reset the panel.

Any idea what i can now? I am now logged into my Windows 7 again. I won't be using Ubuntu often because i keep getting strange errors like this that waste a lot of my time to fix.

---

### Post by wojox on 2010-08-16
What about Ctrl+Alt+F1

Login

Run these three commands:

```

gconftool --recursive-unset /apps/panel 
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by PGScooter on 2010-08-16
UbuNewbie123,

Sorry to hear you're having troubles. You could try this to get access to a terminal:
1. right-click on your desktop or in a folder and create a new file (or do this with an existing file);
2. Right-click on the file and then go to "open with" and then "other application"
3. click on "use a custom command"
4. in the command box enter "gnome-terminal"

Does that work?

Once you get the terminal, I'm guessing you know to type "gnome-panel"

---

### Post by UbuNewbie123 on 2010-08-17
> **wojox said:**
> What about Ctrl+Alt+F1

Login

Run these three commands:

```

gconftool --recursive-unset /apps/panel 
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

I created a launcher on my desktop to launch the terminal. All the different keyboard shortcuts did not nothing for me.

I spent hours scouring the internet for solutions and it seems to be a bug in the latest 10.04 update. I have not been able to find a solution so I have resigned to enter:

[PHP]sudo gnome-panel[/PHP]

This launches my panels after I login....

Some of the solutions I have tried:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343)
[http://netgator.blogspot.com/2010/06/taskbar-missing-in-ubuntu-1004.html](http://netgator.blogspot.com/2010/06/taskbar-missing-in-ubuntu-1004.html)
[http://ubuntuforums.org/showthread.php?t=1503448&page=2](http://ubuntuforums.org/showthread.php?t=1503448&page=2)

After restarting my panels disappear once again.

---

### Post by PGScooter on 2010-08-18
how about having a script that runs on startup (after your login) that does that automatically for you? You could always put a sleep 5s command in or something if it runs before you need it to. There are many ways to have such scripts run.

Try going to system>preferences>startup applications>click on the add buton, and enter your command.

---

### Post by UbuNewbie123 on 2010-08-18
I would prefer a permanent fix for this issue. I have updated all my packages and nothing seems to fix this.

I hope the next update fixes this bug. I think annoyances like this will prevent a lot of Windows users from switching over to Ubuntu.

---

### Post by PGScooter on 2010-08-20
> **UbuNewbie123 said:**
> I would prefer a permanent fix for this issue. I have updated all my packages and nothing seems to fix this.

I hope the next update fixes this bug. I think annoyances like this will prevent a lot of Windows users from switching over to Ubuntu.

I agree. I saw that you looked at a couple of bug reports. If you haven't done so yet, you can help by contributing to those bug reports or opening a new bug report if it's not the same issue.

---

