---
title: "Problem running a program from shortcut icon"
date: 2010-08-20
forum: General Help
---

### Post by redvenomweb on 2010-08-20
I have a game that I'd like to make available to all users.  The game has some subdirectories with supporting data files, so I created a folder in /usr/games and copied the exectuable and all of the data files there.  The folder and all of the contents have been chowned to root and chmoded to 755.

When I browse to the folder in Nautilus (as myself, not sudoed) and double-click the executable, the game runs without a problem.  However, when I create a launcher in the Applications->Games menu and try to run it from there, I get a black screen and I have to switch to another console and reboot.  I've also tried copying that launcher to my desktop and running it with gksudo, with the same result.

What can I try to troubleshoot this issue?

---

### Post by Morrad on 2010-08-20
> **redvenomweb said:**
> I have a game that I'd like to make available to all users.  The game has some subdirectories with supporting data files, so I created a folder in /usr/games and copied the exectuable and all of the data files there.  The folder and all of the contents have been chowned to root and chmoded to 755.

When I browse to the folder in Nautilus (as myself, not sudoed) and double-click the executable, the game runs without a problem.  However, when I create a launcher in the Applications->Games menu and try to run it from there, I get a black screen and I have to switch to another console and reboot.  I've also tried copying that launcher to my desktop and running it with gksudo, with the same result.

What can I try to troubleshoot this issue?

In the gnome panel, go to System -> Preferences -> Main Menu, find the entry for your game, and make sure that the command is correct.  Try running that same command in a terminal and see what output it produces.

---

### Post by redvenomweb on 2010-08-20
The command is what it should be.  However, I think I've figured out what the problem is:

- If I open a terminal and issue the command, I get the same black screen
- If I open a terminal **and cd to the program's folder**, then issue the command, the game runs fine

It seems that I need to do the equivalent of setting the "working directory" when this launcher is executed.  How can I do that?

---

### Post by fragos on 2010-08-20
create a short bash file with:

#!/bin/bash
cd /usr/games/{folder with your game in it}
{command to execute game}

---

### Post by redvenomweb on 2010-08-20
Thanks.  I also found this as a solution (change launcher application properties to the following):

*gnome-terminal --working-directory /path/to/working/dir/ -e /path/to/executable*

Kind of kludgy, but it gets the job done.

---

