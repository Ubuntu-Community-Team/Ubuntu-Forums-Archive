---
title: "add places to app menu"
date: 2010-02-27
forum: General Help
---

### Post by rock4christ on 2010-02-27
is there a way to add places to the application menu(to get something closer to gnome "main menu" that has applications, system and places in one drop down)

---

### Post by DeadSuperHero on 2010-02-27
There's a GNOME applet that comes bundled with ubuntu.

Right click and remove your Menu Bar on the panel. Then, right click again and Add to Panel.

The applet is called Main Menu. It functions more like a Windows XP main menu.

However, if you would like to take it a step further, there's a GNOME panel applet called GnoMenu that you can customize to your own tastes:

The repository is here:
[https://launchpad.net/~gnomenu-team/+archive/ppa]("https://launchpad.net/%7Egnomenu-team/+archive/ppa")

EDIT: Whoops, I hadn't realized this was for Xubuntu. =/

This thread might be of use: [http://wwww.ubuntuforums.org/showthread.php?t=726660](http://wwww.ubuntuforums.org/showthread.php?t=726660)

---

### Post by Oatworm on 2010-03-01
There is, but there doesn't appear to be an easy or simple way to do it.

**Background**
Xfce uses a mixture of XML and plain-text files to store menu configurations.  The menu framework itself is stored in .menu files, which are XML files; if you want to see an example of one, you can view the one that your system is probably using in */etc/xdg/xubuntu/menus*.  The only one in there, at least on my system, is *xfce-applications.menu* - if you plan on editing it, you'll need root permissions.  This .menu file, meanwhile, calls a couple other file types, namely:

*.desktop* - These files are the shortcut files in the menu.  They'll include information on what icon you want to show and what program you wish to launch.  This is a plain-text file.
*.directory* - These create and define your sub-menus.  This, amusingly, is also a plain-text file.

Any edit to the main file will incorporate all three of these sets of files.  There's a little more information on them here:

[http://wiki.xfce.org/howto/customize-menu]("http://wiki.xfce.org/howto/customize-menu")

Unfortunately, it looks like the lack of a GUI tool to properly manage this was a big "whoops" for this Xfce release cycle, which probably ties into why it's such a pain in the rear to manually do this - nobody was ever really supposed to do this by hand.

Good luck!

---

### Post by Cool Javelin on 2010-05-29
I am using Xubuntu Hardy 8.04

Has there been any GUI created in the newer versions to handle this menu editing?

There are a few shortcomings when I install new programs (Using either apt-get, or Synaptics,) many times the new programs do not show up in the menu, Has there been any improvement in that area as well?

Mark.

---

### Post by Cool Javelin on 2010-05-29
OK, I see Oatworm replied only a few days ago, so never mind.

---

