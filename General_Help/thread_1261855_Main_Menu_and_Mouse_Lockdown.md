---
title: "Main Menu and Mouse Lockdown"
date: 2009-09-09
forum: General Help
---

### Post by Frihet on 2009-09-09
I want to remove the main menu from the menubar and disable the trackpad right button to prevent the user from putting it back. I have tried btnx, but it does not seem to work -- at least on my trackpad.

There may also be a chicken and egg problem here. I need the right button to remove the main menu, but I may need the main menu to disable the right button. Hmmm.

I could remove the mainmenu and drop to the CL to edit a mouse config file, if I knew where to look.

Ideas?

Thank you!!

---

### Post by Frihet on 2009-09-09
I think the answer lies in Gnome configuration. That should take care of the right button as well. I am doing research.

Ideas appreciated!

---

### Post by Frihet on 2009-09-09
gconf took care of the menubar nicely: 

start gconf-editor, navigate to /apps/panel/global/locked_down, and set it to true.

but it will not help with right-click.

I am still looking, but ideas will be appreciated.

---

### Post by Frihet on 2009-09-09
OK, I got it. Right click can be disabled in this way:

Create a .Xmodmap file in /userhome. The file contains one line:

pointer = 1 31 32 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 2 3

Ubuntu is configured for 32 buttons on the pointer device. (???) We exchange 2 and 3 for buttons we don't have, thus disabling right click. If I don't put all 32 buttons in, I get an error. I can't use 1 for all buttons.

I'm good to go.

---

