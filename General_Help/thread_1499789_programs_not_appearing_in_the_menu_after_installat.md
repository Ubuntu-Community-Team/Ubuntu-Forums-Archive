---
title: "programs not appearing in the menu after installation"
date: 2010-06-02
forum: General Help
---

### Post by nearadyn on 2010-06-02
I have an unusual request for help. I asked this question on the Backtrack forums, but they were less than helpful.
I have a dualboot of Ubuntu 9.04 and Backtrack 4 on my laptop. Backtrack 4, for those that don't know, is a security penetration testing distro based on Ubuntu with a KDE environment. It basically IS ubuntu, but with some changes, so I figured I'd ask this here.

The menu in backtrack has been stripped of it's "Games" folder, as well as some other folders. so when I use "add/remove applications" to install a game it doesn't put a shortcut to it in a Games directory. I tried adding a Games directory to the menu bar myselff, but when I try to install a game, the installer still doesn't see it and put a shortcut there. How can I fix this so that it does?

---

### Post by ajgreeny on 2010-06-02
Install alacarte, the menu editor if it is not already installed and then you should be able to add the games section to those that show in the Applications part of the menu bar.

Just a thought, the _menu bar_ is normally associated with gnome, not kde.  Does backtrack use the gnome menu bar instead of the kde single "menu" button?  If not and it uses a kde style menu, there must be some way to edit it, I'm sure, as you can change just about everything, and a bit more, normally in kde.

---

### Post by nearadyn on 2010-06-02
I installed alacarte and no luck. It does allow me to edit the menu as you said. However, I can right click on the menu button ( and yes it's a menu button not menu bar) and then click "edit menu" and a menu editor pops up which is very similar to alacarte, which allows me to do the same thing. I did put a "Games" submenu in before my first post.
 The problem is that when I install a game, the package installer doesn't add shortcuts to the game in the "Games" menu that I created like it does in regular Ubuntu. I was wondering if there was a way to fix it so that when I install a Game, using the "add/remove programs" program, it creates the shortcuts in the menu automagically like ubuntu does. 
 If there isn't a way to do this, then I could add the shortcuts manually provided I knew where the games, or other programs, were installed on my HD. But I don't know where they are, even after doing searches for the files. The trouble is, after installing some things, I don't know what the filenames are because they aren't the same as the name of the program or anything like it. Where are games installed in Ubuntu? I never had a need to know these things until now. :?



*EDIT*  I found a solution. From what I now understand, it's not possible to easily do what I wanted. I did figure that the programs are being installed under /usr/bin so I can just manually edit the menus.

---

