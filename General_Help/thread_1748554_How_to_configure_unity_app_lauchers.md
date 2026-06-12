---
title: "How to configure unity app lauchers"
date: 2011-05-03
forum: General Help
---

### Post by bkline on 2011-05-03
Anyone know how to configure the launcher for an app in unity?  In Gnome, you could just right-click the icon, select properties and go to town.  In Unity, all right-click gets you is (for example):
[LIST]
[*]Terminal
[*]Keep In Launcher
[*]Quit
[/LIST]

I'd like to change the geometry for new terminal windows.

---

### Post by chipper_farley on 2011-05-03
You need to alter the launcher parameters in /usr/share/applications.  For the terminal one, I believe it's the "gnome-terminal.desktop" file.  Edit that file and change the parameter "Exec=gnome-terminal" to add whatever parameters you want to add to the execution of the gnome-terminal command.  gnome-terminal accepts a "--geometry" parameter.  You can get more info on that by entering "man gnome-terminal".  Make the change to the file and save it and see if that doesn't get it for you.

I believe you can also put customized versions of the launchers in /home/YOURID/.local/share/applications/ in order to have your custom ones not affect all users of the computer.

Good luck!

---

### Post by bkline on 2011-05-03
Thanks, Chipper!

---

### Post by mc4man on 2011-05-03
An additional thing you can do, if useful, is to add quicklists entries to the launcher icon's r. click
Ex on terminal, (am keeping menus in the terminals w/ the env on the Exec= lines
(you can add as many as is reasonable to any app/added launcher icons

In this instance blue added to orig.
```
[Desktop Entry]
Name=Terminal
Comment=Use the command line
TryExec=gnome-terminal
Exec=env [COLOR="Blue"]UBUNTU_MENUPROXY=0[/COLOR] gnome-terminal
Icon=utilities-terminal
Type=Application
X-GNOME-DocPath=gnome-terminal/index.html
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-terminal
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=2.32.1
Categories=GNOME;GTK;Utility;TerminalEmulator;
StartupNotify=true
X-Ubuntu-Gettext-Domain=gnome-terminal
[COLOR="Blue"]X-Ayatana-Desktop-Shortcuts=NewTerminal;LargeTerminal;

[NewTerminal Shortcut Group]
Name=New Terminal
Exec=env UBUNTU_MENUPROXY=0 gnome-terminal
TargetEnvironment=Unity

[LargeTerminal Shortcut Group]
Name=Large Terminal
Exec=env UBUNTU_MENUPROXY=0 gnome-terminal --geometry=200x40
TargetEnvironment=Unity[/COLOR]
```

Edit: you don't have to confine a launchers quicklists to one paricular app, one can make menus that have a group of app types or however defined - small ex. here
[http://ubuntuforums.org/showthread.php?p=10741859#post10741859](http://ubuntuforums.org/showthread.php?p=10741859#post10741859)

---

### Post by bkline on 2011-05-03
> **mc4man said:**
> An additional thing you can do, if useful, is to add quicklists entries to the launcher icon's ....

Excellent, thanks!

---

### Post by mc4man on 2011-05-03
> Excellent
I see the launcher as an easy way to create menus - take a basic .desktop and add whatever one wants to the quicklists to create a <whatever>  menu (r click, l click, executed

( it would seem that a 'quicklist writer' wouldn't be to hard to build for someone who does such things, there only 4 inputs needed

---

### Post by BradleyAtkins on 2011-05-05
```
Shortcuts=NewTerminal;LargeTerminal;

[NewTerminal Shortcut Group]
Name=New Terminal
Exec=env UBUNTU_MENUPROXY=0 gnome-terminal
TargetEnvironment=Unity

[LargeTerminal Shortcut Group]
Name=Large Terminal
Exec=env UBUNTU_MENUPROXY=0 gnome-terminal --geometry=200x40
TargetEnvironment=Unity[/COLOR]
```

How can you use this to run something with elevated permissions? Like: -

```
Exec=sudo somejob
```

or whatever.

---

### Post by mc4man on 2011-05-05
> How can you use this to run something with elevated permissions?
Well have it open a root terminal, then manually input command or 
Exec=/path/to/script_that_does_what_you_want_to_do

---

### Post by BradleyAtkins on 2011-05-06
Yes I know how to run a job from the terminal using sudo but I can't do the same from a short cut. 

For example clamav needs to run as root if its going to check the whole computer. I can run sudo clamtk from the terminal but it would be nice to be able to just run it from the applications interface in unity and be prompted for my password.

Just seems a little inconsistent that we can run things with elevated permissions from the command line but not from the desktop.

---

### Post by mc4man on 2011-05-06
> **BradleyAtkins said:**
> Yes I know how to run a job from the terminal using sudo but I can't do the same from a short cut. 

For example clamav needs to run as root if its going to check the whole computer. I can run sudo clamtk from the terminal but it would be nice to be able to just run it from the applications interface in unity and be prompted for my password.

Just seems a little inconsistent that we can run things with elevated permissions from the command line but not from the desktop.
If you think that you need to open clamtk with a different launch command than the default then just change the Exec= line in clamtk.desktop to do so or add a quicklist entry for an add. open option (Exec=gksu clamtk

Nothing to do with a terminal and nothing inconsistent, the launcher opens applications, either using the default launch command or modified launch commands for that app or any valid launch command for any executable you have. (the same as Alt+F2

---

### Post by BradleyAtkins on 2011-05-06
That's great :) Thanks

Hadn't heard of gksu

---

### Post by dino99 on 2011-05-06
[http://theravingrick.blogspot.com/2011/04/my-effort-at-writing-help-for-unity.html](http://theravingrick.blogspot.com/2011/04/my-effort-at-writing-help-for-unity.html)

[http://ubuntuforums.org/showthread.php?t=1741293](http://ubuntuforums.org/showthread.php?t=1741293)

---

