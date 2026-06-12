---
title: "nautilus-open-terminal command"
date: 2011-02-28
forum: General Help
---

### Post by AndrewSimoes on 2011-02-28
I have installed nautilus open terminal so that while navigating through nautilus I can right click and open terminal and I'll be in that directory.
Is there a way to enable a command line version of that ? As in I want to create and application that launches a script within a terminal . I would normally use 
gnome-terminal -x .....
However that would always get me into the home directory. I need to launch this application from within the folder I'm in at that time. 
So something like 
nautilus-terminal -x ...
What's the command?

---

### Post by Vaphell on 2011-02-28
[http://stackoverflow.com/questions/844677/gnome-terminal-how-to-start-in-a-different-directory](http://stackoverflow.com/questions/844677/gnome-terminal-how-to-start-in-a-different-directory)

either way try nautilus-actions, it allows to create custom context menu entries that perform some defined action on selected stuff which can be anything: files and/or folders, names matching patterns, mimetypes. It's a quite flexible tool
You would be able to create a script accepting directory as a parameter (my_script %f, where %f substitutes selection), wrapping up your desired action.
cd $1;
actual_stuff

or going directly with gnome-terminal --working-directory=%f <stuff that matters>

configuration panel is in menu or you can invoke it with nautilus-actions-config-tool. I think playing with actions requires nautilus restart, if newly created action is valid then it should appear in context menu

---

### Post by AndrewSimoes on 2011-03-01
> **Vaphell said:**
> [http://stackoverflow.com/questions/844677/gnome-terminal-how-to-start-in-a-different-directory](http://stackoverflow.com/questions/844677/gnome-terminal-how-to-start-in-a-different-directory)

either way try nautilus-actions, it allows to create custom context menu entries that perform some defined action on selected stuff which can be anything: files and/or folders, names matching patterns, mimetypes. It's a quite flexible tool
You would be able to create a script accepting directory as a parameter (my_script %f, where %f substitutes selection), wrapping up your desired action.
cd $1;
actual_stuff

or going directly with gnome-terminal --working-directory=%f <stuff that matters>

configuration panel is in menu or you can invoke it with nautilus-actions-config-tool. I think playing with actions requires nautilus restart, if newly created action is valid then it should appear in context menu

Thanks for the reply. 
I however want to be able to graphically navigate through nautilus and right click a file and run it with a script that I have created. In that case I either need to invoke a nautilus-terminal from where the script command is to be executed or else I have to find a means of passing the absolute path of the file to the script from where the first command will be cd *absolute path*

---

### Post by AndrewSimoes on 2011-03-01
Hey thanks. Nautilus-actions did the trick. Damn useful

---

