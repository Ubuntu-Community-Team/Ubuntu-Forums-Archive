---
title: "Building a frontend in BASH?"
date: 2010-06-08
forum: General Help
---

### Post by Darkness Des on 2010-06-08
I want to be able to create a Dialog (similar to the one for Winetricks, run it without parameters to see it) with a checklist that tells my script to go out and download whatever scripts of mine I've selected. I also wish to make a GUI for some of my more complex scripts, such as my Backup script so I can have a nice looking menu instead of a text based one.

Does anybody know a good place to learn how to do this, with lots of explanations and breakdowns of each part of the script?

---

### Post by Serpher on 2010-06-08
I kinda forget how to bash script but you're going to have to learn the more programming like side of it such as if statements and variables. Now bash is a shell, and not capable of a GUI, however programming languages like C and python (I think) allow you to program a line like the following (The system line would be something you would see in Python):

```
if chkwine=true then
   system("sudo apt-get install wine")
end if
```

You would also learn how to program with a GUI. All things GNOME usually use GTK while KDE uses K. IMO more trouble than it's worth if you're just doing it for this one script.

---

### Post by TheForumTroll on 2010-06-08
I love Python but if you want to build GUIs I wold use something else. Myself I use Free pascal and Lazarus for GUIs.



For what you talk about have a look at dialog/[kdialog]("http://techbase.kde.org/Development/Tutorials/Shell_Scripting_with_KDE_Dialogs") or [zenity]("http://freshmeat.net/projects/zenity"). 

I think Zenity is what is used in Ubuntu so it might already be installed on your machine! :)

---

### Post by patchwork on 2010-06-08
> For what you talk about have a look at dialog/[kdialog]("http://techbase.kde.org/Development/Tutorials/Shell_Scripting_with_KDE_Dialogs") or [zenity]("http://freshmeat.net/projects/zenity").

+1

Zenity is easy to use and produces good-looking interfaces, though it is limited to the set functions.  The zenity man pages include all the information you need with examples.

```
man zenity
```

---

### Post by Darkness Des on 2010-06-08
It is fully possible to launch a dialog from within a BASH script. I did find a tutorial on that, but it was rather complex. It can be a dialog like Aptitude or Lokkit have, or it can be an Xdialog. That kind of thing. The Winetricks GUI was also fully built in BASH. I plan to use this in more than one script.

EDIT:
I was responding to Serpher, sorry for the late post. I'll look into that. I personally have GNOME, KDE, and XFCE all installed, but I plan to distribute this so I'll find a way. Thanks!

---

