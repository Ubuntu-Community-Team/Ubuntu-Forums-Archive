---
title: "Question about developing software with GTK+"
date: 2010-12-26
forum: General Help
---

### Post by darkligh on 2010-12-26
Hello my friends! I'm new member of this forum...
First of all I want give thanks to all of you especially to Ubuntu!

I'm web developer and I'm searching for replacement of Windows.

Recently I got fresh install of 10.10 maverick with all updates, installed AWN with Cairo Menu, removed gnome-panel... and so on...

Before removing gnome-panel I had common key bindings like "<Alt>F1", "<Alt>F2", "<Control><Alt>T"

I am using terminal very often and I was able to set to launch it in compizconfig-manager.

But the problem is that I'm not able to set "<Alt>F1" to launch main menu under mouse pointer! I really need it...

Recently I decided to download source codes of awn-applets and add keybinding support into Cairo Menu, I installed all packages needed to compile applets. Then I got source code of keybinding support from awnterm applet, put it into cairo-menu, added it to Makefile, wrote a test code for keybindings, even compiled and ran that applet without any error!
But after that it did not work :( I did big work doing that, 'cause I'm really newbie...

I need help adding GLOBAL keybindings (maybe some tutorials).

And also, is there an alternative way to bring up main menu with keyboard and without gnome panel?



Guys, please tell me where should I put such kind of posts, 'cause I feel that I posted in wrong forum :)))



Best regards from Armenia! :)))

---

### Post by WorMzy on 2010-12-26
Unfortunately Alt+F1 and Alt+F2 are keybindings created by gnome-panel, I don't know if there is an equivalent for awn. I don't think that the terminal shortcut is a product of gnome-panel though, that should keep working.. However, you can create a new shortcut for that in Compiz.


You can have both AWN and gnome-panel running at the same time, so perhaps this would be a suitable solution for you? The alternative (unless someone else can suggest something else) would be to abandon the keyboard shortcuts and only use your mouse to open the menu.

---

### Post by darkligh on 2010-12-27
:(

First of all thank you for you fast reply!


The problem is that there is no any shell program that can trigger main menu. In that case I could simply bind a shortcut to that program from Compiz.

The gnome-panel is not usable for me and so I don't need it anymore and it takes extra space. I tried to auto-hide it, but in that case some times I put cursor on the top of the screen and it appears, it makes me a bit nervous.


Anyone else, please help me! Thanks! :)

---

