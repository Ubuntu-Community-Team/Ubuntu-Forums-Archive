---
title: "Wine not creating menu items for installed programs"
date: 2010-11-16
forum: General Help
---

### Post by dcp0 on 2010-11-16
Hi, i am really new to ubuntu and linux in general and any help would be appreciated.

So i have installed Wine 1.2.1, running Ubuntu 10.10 and i can run .exe's with wine and install programs. My issue is that NONE of the programs i install are showing up in Applications>Wine>Programs .. the only thing in there is the Applications>Notepad that was default.

I have tried Streamtorrent and Foobar(foobar just to test) neither will add anything to the menu for running, ya i can edit the menu manually but could be a pain to do everytime and I would like to have the functionality of everyone else.

The programs are showing up in the WINE install/uninstal dialog
and i can run them both, just dont know why the menus are not being generated

I went into /home/<user name>/.config/menus/applications.menu
and only have this, no deleted items:
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
</Menu>

maybe that is the issue ??

I read these and some other Google'ness, but nada.
[http://ubuntuforums.org/showthread.php?t=1536265](http://ubuntuforums.org/showthread.php?t=1536265)
[http://ubuntuforums.org/showthread.php?t=650738](http://ubuntuforums.org/showthread.php?t=650738)

---

### Post by dcp0 on 2010-11-16
BUMP, please help

---

### Post by dcp0 on 2010-11-16
so nothing is even being added to the application.menu file, like i belive it should be by reading random things..

anyone know what would prevent WINE from being able to add things to that ?

---

