---
title: "Is there a function similar to CTRL ALT DEL?"
date: 2009-08-22
forum: General Help
---

### Post by COOLDUDEGAMER on 2009-08-22
I have tried to find way to get a task list to close down a few running programs. I have tried to CTRL ALT DEL, but it does not work. I was wondering if there is a way to a similar key combination to get a task list to close down those programs to change settings in them without having to reboot.

Any help will be appreciated.

---

### Post by jheaton5 on 2009-08-22
in terminal type ```
htop <enter>
```

see ```
man htop
``` for usage information

---

### Post by earthpigg on 2009-08-22
right click on an empty spot on the top panel -> add to panel -> system monitor.

click when you need it.

it is a resource hog, so i do not recommend you leave it open and running all the time... let it hang out in your task bar and click when you need it.


there are superior command-line methods, of course, if you want to go over those?

---

### Post by earthpigg on 2009-08-22
> **jheaton5 said:**
> in terminal type htop <enter>

you forgot to tell him how to install htop, as it does not come installed by default :D

```
sudo apt-get install htop
```

---

### Post by COOLDUDEGAMER on 2009-08-22
Thank you both for your replies. I will have to try this when I get back from vacation in about a week.

---

### Post by jheaton5 on 2009-08-22
Do you remember the old DOS system where <ctrl><alt><del> rebooted the system?  It was the answer for everything. :)

---

### Post by BackwardsDown on 2009-08-22
System-monitor (System->Administration->System-monitor) is like the ctrl-alt-del dialog of windows XP. If you want you can set in System->Preferences->Keyboard-shortcuts that it will launch if you press ctrl-alt-del.

---

### Post by apparle on 2009-08-22
In kubuntu(KDE) its Ctrl+Esc
but I don't know on ubuntu
Maybe its same

---

### Post by ceramicm on 2009-08-22
gnome-system-monitor is an application (similar to Task Manager in Windows) that will display a task list and allow you to close an application. It is installed by default.

If you would like gnome-system-monitor to appear when you type control-alt-delete, open the terminal (Applications->Accessories->Terminal), paste the following, and press <Enter>:

```
gconftool-2 -s --type string /apps/metacity/global_keybindings/run_command_10 "<Control><Alt>Delete"
gconftool-2 -s --type string /apps/metacity/keybinding_commands/command_10 "gnome-system-monitor"
gconftool-2 -s --type string /apps/gnome_settings_daemon/keybindings/power ""
```

Now gnome-system-monitor should open when you press control-alt-delete. To close a program using gnome-system-monitor, click the Processes tab, select the program you wish to close, right click, and click "End Process". Attached is a screen shot of gnome-system-monitor.

---

### Post by scouser73 on 2009-08-22
Use **ALTGR, PRTSCR, K** to restart X

That&#8217;s alt-gr (the right hand alt key), Print screen and the key &#8220;k&#8221;

---

### Post by COOLDUDEGAMER on 2009-08-22
I will have to try all these key combinations and menu features and terminal typings after I get back from vacation in about a week. Thanks everyone for replying. I really appreciate all the help.

Oh and to the question about the CTRL ALT DEL command in DOS, I cannot really remember it as I am kinda too young to remember it (I will be 20 on the 14th of OCT) but, I know that you can do the same from a DOS style boot disk when upgrading a BIOS chip. :P

---

### Post by ajgreeny on 2009-08-22
While we're at it with all these utilities to stop things that are running, type xkill in terminal, place the cross cursor that then appears, over a faulty or frozen application, left click and it will be killed.  This can be very useful, but only of course, for GUI applications.

---

### Post by COOLDUDEGAMER on 2009-08-29
Thanks for the advice. I will have to keep that in my mind in the future. The only thing with that one command is that I am running Folding at Home, which does not have a gui linux version yet. That and even when exiting the console, the service will still run, but, in the future when the gui version comes out, it may be helpful if the program locks up. 

Thanks everyone for the help and support, I am going back home sometime early tomorrow (Sunday here in the USA) and I will be able to try all these different ideas/ features.

---

