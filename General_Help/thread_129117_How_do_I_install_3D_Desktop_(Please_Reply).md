---
title: "How do I install 3D Desktop (Please Reply) ?"
date: 2006-02-13
forum: General Help
---

### Post by Zach1188 on 2006-02-13
I want to download 3D Desktop, but all of them are .RPM and source files. I do not have any clue as what to do, can somone help?

Links:
[http://desk3d.sourceforge.net/]("http://desk3d.sourceforge.net/")
[http://sourceforge.net/project/showfiles.php?group_id=59688]("http://sourceforge.net/project/showfiles.php?group_id=59688")

Or, if anyone knows if better add-ons like this, I would be GLAD to hear about it.

---

### Post by Jucato on 2006-02-13
3D Destkop is available in the repositories. you can install it from your favorite Package Manager (Adept, Syanptic, whatever). I think it's in the Universe Repository.

---

### Post by Zach1188 on 2006-02-13
I installed it, but I cant use it. Do I right click the taskbar, and click "Add Aplet to Panel"? If so, it is not there.

---

### Post by Jucato on 2006-02-13
There are instructions on the website. But here's a rundown.

To get the snapshots of your desktops, you need to enter the command "3ddesk --acquire". You can do it either from the terminal or from a Run Command dialog box (Alt+F2). This will also activate the 3ddeskd daemon.

To run 3D Desktop, you can type 3ddesk (terminal or run command) or make a keyboard shortcut for it. It will run the program. Left or right cursor rotates the desktops, Enter chooses the desktop, Esc exits. You can also use the mouse: Left mouse button to go left, right to go right, and middle to choose the desktop.

Note that you can run 3ddesk without doing the 3ddesk --acquire, but your other desktops will display only grayed views, which will change once you choose that desktop.

Hope it helps

---

### Post by Jaygo333 on 2006-02-13
I know how it works, but my question is,
How do I make a keyboard shortcut for it.?

:h34r: Jaygo333 :h34r:

---

### Post by Jucato on 2006-02-13
I think there must be another way, but, lazy that I am, did it the hard way. I made a menu entry in K Menu, associated a shortcut combination/key with it. and presto! The only thing I haven't successfully done yet is making KDE run "3ddesk --acquire" during login.

NOTE: remember to turn off launch feedback for the 3d desktop menu item.

---

### Post by procras on 2006-02-13
Following is only relevant to GNOME
~~~~~~~~~~~~~~~~~~~~~

Applications->System Tools->Configuration editor
Go to apps->metacity->global_keybindings

Right click a blank run_command eg. run_command_1 and select edit and enter your key binding eg. <Alt>F1

Then enter the command for that key in apps->metacity->keybinding->commands
Right click command_1 (or whatever you chose above) and enter /usr/bin/3ddesk

I noted a system hog with 3ddesk every few seconds due to the daemon screening all my desktops and cacheing them. I turned this off by editing /etc/3ddesktop/3ddesktop.conf and setting 
autoaquire 0 
At about line 37.

---

### Post by Sokraates on 2006-02-13
A HOW-TO can be found here:

[http://www.ubuntuforums.org/showthread.php?t=100167](http://www.ubuntuforums.org/showthread.php?t=100167)

---

### Post by Jucato on 2006-02-13
[QUOTE=procras]Following is only relevant to GNOME
~~~~~~~~~~~~~~~~~~~~~

Applications->System Tools->Configuration editor
Go to apps->metacity->global_keybindings

Right click a blank run_command eg. run_command_1 and select edit and enter your key binding eg. <Alt>F1

Then enter the command for that key in apps->metacity->keybinding->commands
Right click command_1 (or whatever you chose above) and enter /usr/bin/3ddesk

I noted a system hog with 3ddesk every few seconds due to the daemon screening all my desktops and cacheing them. I turned this off by editing /etc/3ddesktop/3ddesktop.conf and setting 
autoaquire 0 
At about line 37.[/QUOTE]

I wonder how this can be done in KDE...

EDIT: I so hate it when I find solutions to my own problems half an hour later, when I couldn't find them half a week before...

A very short tutorial on keyboard shortcuts WITHOUT having to put them in K Menu (works only in KDE of course).

[http://www.ubuntuforums.org/showthread.php?t=87737&highlight=kde+keyboard+shortcut]("http://www.ubuntuforums.org/showthread.php?t=87737&highlight=kde+keyboard+shortcut")

---

