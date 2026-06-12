---
title: "How to find the shortcut's target in Ubuntu ?"
date: 2011-11-29
forum: General Help
---

### Post by andrey_ on 2011-11-29
Hi
You can start gedit in Ubuntu (11.04) by typing "gedit" in the Terminal or by clicking its shortcut from the GUI, my question is: how to find the corresponding command in general for an application or utility?
for example: Time&date, Disk Utility or any newly installed application...
( In Windows you'll be able to allocate the path to the target (exe file) by a right-click)

---

### Post by Bobhuber on 2011-11-29
> **andrey_ said:**
> Hi
You can start gedit in Ubuntu (11.04) by typing "gedit" in the Terminal or by clicking its shortcut from the GUI, my question is: how to find the corresponding command in general for an application or utility?
for example: Time&date, Disk Utility or any newly installed application...
( In Windows you'll be able to allocate the path to the target (exe file) by a right-click)
Go into synaptic package manager and look up the app you are interested in (IE gedit). Highlight it and on the middle bar you will be able to display the installed files and there locations along with dependencies etc..

---

### Post by andrey_ on 2011-11-29
> **Bobhuber said:**
> Go into synaptic package manager and look up the app you are interested in (IE gedit). Highlight it and on the middle bar you will be able to display the installed files and there locations along with dependencies etc..

Thank you Bob!

---

### Post by mcduck on 2011-11-29
You can also use the "Main Menu"-tool to browse through the program launchers and check the commands used, or drag&drop a launcher into desktop, right-click and then view the properties.

..and also the "*which*" command in terminal will tell you the name and location of a program's executable file, for example "*which firefox*" returns "*/usr/bin/firefox*". (pretty much with every user-level application the executable is simply a file with the program's name, located in /usr/bin)

...and one more way is to look at the .desktop files located in /usr/share/applications.

In case you aren't exactly sure about the real name of a program (for example if you wouldn't knwo that the application called "Text Editor" is actually called "Gedit", you can use the "*apropos*" command in terminal. It will search for programs that fit a given description, for example "*apropos text editor*" to find out programs that can be used to edit text.

---

### Post by andrey_ on 2011-11-30
> **mcduck said:**
> You can also use the "Main Menu"-tool to browse through the program launchers and check the commands used, or drag&drop a launcher into desktop, right-click and then view the properties.

..and also the "*which*" command in terminal will tell you the name and location of a program's executable file, for example "*which firefox*" returns "*/usr/bin/firefox*". (pretty much with every user-level application the executable is simply a file with the program's name, located in /usr/bin)

...and one more way is to look at the .desktop files located in /usr/share/applications.

In case you aren't exactly sure about the real name of a program (for example if you wouldn't knwo that the application called "Text Editor" is actually called "Gedit", you can use the "*apropos*" command in terminal. It will search for programs that fit a given description, for example "*apropos text editor*" to find out programs that can be used to edit text.
Thanks, great information!

---

