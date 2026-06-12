---
title: "part of my system thinks my screen is wider than it is"
date: 2010-06-30
forum: General Help
---

### Post by Daan on 2010-06-30
I have a problem with in the Gnome Desktop environment. Some parts of my system seem to think my screen is wider than it actually is.

To the right if my screen, there is a part of my workspace which I can't see. I can move the mouse pointer there (although I cannot see it then) and I can also drag windows onto this area. If I do that, the window disappears from sight, however, it is visible in the little workspaces of the workspace-switcher-applet in the lower right corner. This applet does display the entire width of the workspace (which is too wide for my screen). If I maximize a window, it does not go onto the invisible part of the workspace.

What can I do to fix this?

I'm using Ubuntu 10.04 Lucid Lynx on an HP 6930p notebook.

---

### Post by robsoles on 2010-06-30
Have you ever (1) plugged a second monitor into this laptop and (2) then set it display to 'twinview' or 'big desktop' or similar kind of thing?

Go into "System"->"Preferences" menu and see if you can find 'Monitors" in there, if so click it and either it will open or it will ask you if you want to open the "... vendor's tool instead" - open the vendor's tool if it is available.

Try to find if something in there is indicating 'twinview' or 'big desktop' or similar and if so then select 'mirrored' or something like that (at least different to what it says there) till you see what you want.

Successfully saving the settings from some of these configurators can be a tricky and even nasty task, if you can change the setting but can't make it permanent then post back to this thread with that problem and if I am still up I will probably beat anyone to walking you through getting that done.

I wish I was there to help you make a backup copy of your /etc/X11/xorg.conf file before you try changing settings and saving them but I spose we'll (you'll) have to bite that bullet when you get there!

(If you haven't access to another computer with which to get on forums just have your LiveCD handy when you try to save your new settings and reboot just in case it doesn't make it so easy back to a graphical desktop!)

Of course, just say so if nothing is as I suggest it might be in the settings program.

---

