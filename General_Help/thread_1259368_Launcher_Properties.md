---
title: "Launcher Properties"
date: 2009-09-06
forum: General Help
---

### Post by hariks0 on 2009-09-06
I was wondering how to create a launcher for an application when i do not know the application name. In other words i would like to know the terminal equivalent for an icon in the desktop or panel. It is possible to see the properties of the main menu items in 'Edit Main Menu' dialog. But what about ones like "Control Center" or "Force quit an Application" or other applets for the panels etc.

[http://ubuntuforums.org/showthread.php?p=7947781#post7947781](http://ubuntuforums.org/showthread.php?p=7947781#post7947781)

System--> Preferences--> CompizConfig Settings--> General--> General Options--> Key Bindings--> Show Desktop [with a monitor icon]. Click on it and select the edge or corner of the screen to activate show desktop.

THEN

Use value of command 1 "nautilus ~" [without quotes] to open your home folder with Super+e or "nautilus /" [without quotes] to open your root folder.

The other settings i use in compiz are

"gnome-terminal" with super+r
"gnome-session-save --logout-dialog" with super+l
"xkill" with super+delete


And that is not all. I use

xvkbd -text "\[Alt_L]\[F1]"

for starting the main menu without using even a single key press of keyboard keys.

To do so goto System--> Preferences--> CompizConfig Settings--> General--> Commands--> Commands--> Command 4 and set the value of Edge binding to

Left.

Do the same for invoking the Run Application dialog with

xvkbd -text "\[Alt_L]\[F2]" and set the value of Edge binding to

Right.

Note : Use xvkbd -text "\[Alt_L]\[F1]" [with quotes and the command starts from xvkbd] You will have to install pckage xvkbd. Code = [sudo apt-get install xvkbd]. The command for Run Application dialog seems to invoke the main menu also. May get corrected after a loggof and logon.

---

### Post by kerry_s on 2009-09-06
there is no terminal equivalent to "applets" that are run in the panel.

---

### Post by Bodsda on 2009-09-06
> **hariks0 said:**
> I was wondering how to create a launcher for an application when i do not know the application name. In other words i would like to know the terminal equivalent for an icon in the desktop or panel. It is possible to see the properties of the main menu items in 'Edit Main Menu' dialog. But what about ones like "Control Center" or "Force quit an Application" or other applets for the panels etc.

Some of these are a bit more difficult, some of them have a right click properties menu I think, but apart from that I wouldn't know. If you are really struggling to find the names, either try googling them, searching for the author or post a thread asking for help. Alternatively, try searching logically for the package. For example, I just found the package for the control center by doing
```
apt-cache search control | grep -i center
```
which returned the following
```

gnome-control-center - utilities to configure the GNOME desktop
gnome-control-center-dev - utilities to configure the GNOME desktop
fglrx-amdcccle - Catalyst Control Center for the ATI graphics accelerators

```
I know it is not #3, and I know that any package with -dev on the end are packages intended for developers/compilers so that leaves us with #1.

The applets are going to be trickier though. Hope this helps, and good luck.

Kind regards,
Bodsda

> **kerry_s said:**
> there is no terminal equivalent to "applets" that are run in the panel.

Yes there is, it all depends on the applet. For example, wicd can be started from the terminal which adds its icon to the panel. Some applets do, some applets don't.

---

### Post by Eldera on 2009-09-06
A launcher for "force quit" is available from the "add to panel" list.

Right click panel. Click "add to panel" select laucher from list, click add.

Have a good day, Eldera

---

