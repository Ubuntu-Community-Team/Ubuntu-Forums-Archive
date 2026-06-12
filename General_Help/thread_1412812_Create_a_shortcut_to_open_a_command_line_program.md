---
title: "Create a shortcut to open a command line program"
date: 2010-02-21
forum: General Help
---

### Post by benerivo on 2010-02-21
I use a few command line programs quite often such as nano and mpc. I'd like to create a shortcut icon to open them rather than opening a terminal and then typing in the program name to open it. For example, how could i open konsole with nano opened in one step?

---

### Post by J V on 2010-02-21
on gnome theres an option to "run in terminal", also in gnome-terminal you can pass a flag to run a command when it starts...

try man konsole and see what it gives you...

---

### Post by Darkish Dave on 2010-02-21
> **benerivo said:**
> I use a few command line programs quite often such as nano and mpc. I'd like to create a shortcut icon to open them rather than opening a terminal and then typing in the program name to open it. For example, how could i open konsole with nano opened in one step?

Where do you want the shortcut?

If it is the Desktop, Left Click the desktop wallpaper (Or if it is the Panel Right Click the Panel you want the shourtcut to appear)  and Select "Create Launcher" . From The "Type" Dropdown menu Select "Application in Terminal". And type the program you want to open beside "Command:" And Don't forget to name the shourtcut.

---

### Post by benerivo on 2010-02-21
Thanks,  but I think i should have posted this in Desktop Environments, as it may be kde specific. I can create a launcher on the desktop (or any folder) for xterm, which will open with nano (the command line is just 'xterm nano'), but it doesn't work with konsole. In kde there is no 'run in terminal' or 'application in terminal' option i can see.

---

### Post by Darkish Dave on 2010-02-22
> **benerivo said:**
> Thanks,  but I think i should have posted this in Desktop Environments, as it may be kde specific. I can create a launcher on the desktop (or any folder) for xterm, which will open with nano (the command line is just 'xterm nano'), but it doesn't work with konsole. In kde there is no 'run in terminal' or 'application in terminal' option i can see.

Oh KDE sorry. I'll go though 

For a desktop shourtcut:

(If you haven't done so already)
Right Click the Desktop.
Select "Desktop Settings"
Under "Desktop Activity" header You will see a dropdown box called "Type:" by default it should be "Desktop". But you should change it to "Folder View.
Hit OK.


Then right click the desktop go to "Create New" -> "Link To Application" 
Select the "Application" Tab.
Fill in the Shourtcut name beside well..eh.. "Name:"
Fill in the command that would open the program beside "Command:"
[B]Then Click the "Advanced Options"
Check the "Run in terminal" box.[/B]
Click OK and then OK again to save the settings.

---

### Post by benerivo on 2010-02-22
Thanks Dave, the icon now occupies pride of place on my panel.

---

