---
title: "Problem with a Custom Application Launcher using terminal commands"
date: 2009-09-19
forum: General Help
---

### Post by cptfx on 2009-09-19
I'm running 9.04 and I have a set of commands that rotates my screen and wacom tablet by 90degrees.  These commands work fine when entered into the terminal but fail when I try to create a custom application launcher in terminal. The text that I'm entering into the launcher is :

xsetwacom set 'Wacom Graphire4 4x5 cursor' Rotate CW ; xrandr -o right ;

The error screen pops up really fast but it looks like it throws the error b/c of 'right'.  Originally it would complain about the 'CW' until I put the space between CW and ;  

I can copy that exact command and run it in terminal just fine.  So what is the difference between the application launcher and the terminal?

---

### Post by Brandon Williams on 2009-09-19
You might want to post the content of the .desktop file to get better advice.

I don't tend to define even moderately complex shell commands as the Exec commands for launchers. If I need more than one simple command line, then I create a shell script to run the command, put the script in my user ~/bin/ directory, and run the script from the launcher. That's not to say that it can't be done the way you're trying to do it, but I find testing/fixing such launchers more trouble than it's worth.

---

### Post by cptfx on 2009-09-19
Thanks.  I made a bash script and now it works.  For the sake of my own knowledge, where is the .desktop file and what information does it contain?

---

### Post by mc4man on 2009-09-19
> where is the .desktop file 
If you created a desktop launcher then the .desktop is the launcher. To read the .desktop (vs. a r. click -> properties -> ....,) you'd just open it in a text editor based on displayed name.desktop

Ex.
Have a launcher named avidemux2 on the desktop
```

gedit ~/Desktop/avidemux2.desktop
```

What can be a bit more difficult is opening .desktops created from using a custom command.

In those cases the the .desktop is located in ~/.local/share/applications, but the display name is not the .desktop name

The actual name is userapp-<1st name in command>-XXXXXX.desktop
To open those in a text editor requires finding the actual name.

That can gleaned from finding it's entry(s) in ~/.local/share/applications/mimeapps.list or by having a nautilus action - 'open in text editor', then it can be opened directly from the r. click

Ex.
A . desktop with display name of mplay (created from custom command

this would open it in a text editor
```
gedit ~/.local/share/applications/userapp-mplay-ZMORVU.desktop


```

---

