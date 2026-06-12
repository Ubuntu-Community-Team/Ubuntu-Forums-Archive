---
title: "Geany colour scheme"
date: 2012-06-01
forum: General Help
---

### Post by samwillc on 2012-06-01
Hi everyone,

Apologies for maybe being a bit dense here, but how exactly do I use this colour scheme?

[http://www.barryvan.com.au/2009/01/geany-ide-tango-dark-colour-scheme/](http://www.barryvan.com.au/2009/01/geany-ide-tango-dark-colour-scheme/)

Home/.config/geany/colourschemes does exist so stage one all good!

The folder I have downloaded is called 'barryvan-Geany-Tango-Dark-65cefc9'
Which contains another folder called 'filetypes'

So what do I put where?

Thanks if anyone can shed some light on this!

Sam.

---

### Post by samwillc on 2012-06-01
This is actually unsolved, as doing the following:

Geany readme says this:

[I]*IMPORTANT: UBUNTU/UNITY USERS*
-------------------------------
There is a conflict in Geany's code when you are using Unity's DBUS menu (that
global menu at the top of the screen). The fix for this will be available in
the 1.22 Geany release. To work around the problem, you can ensure that the
environment variable `UBUNTU_MENUPROXY` is set to `0` before running Geany.
This will disable Unity from stealing Geany's main menu and will leave it
within Geany's main window. You should be able to edit your launchers for
Geany to run like this `UBUNTU_MENUPROXY=0 geany`. You can even make a Bash
alias if you wish.[/I]

I ran *UBUNTU_MENUPROXY=0 geany *from terminal and geany opened, with app menu within the window as expected AND the theme switching worked perfectly!

This is not a solution though to do this every time I want to run the program. Any ideas how I can solve this? I want to try a few themes to see which one I am most comfortable with. Thanks.

Sam.

------------------------------------------------------------------------------------------------------------
Can I just add I get this in terminal if this helps

[I]sam@sam-pc:~$ geany -v
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkRange::trough-side-details' of type `gboolean' from rc file value "((GString*) 0x237cd40)" of type `GString'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkRange::trough-side-details' of type `gboolean' from rc file value "((GString*) 0x237cd40)" of type `GString'

(geany:2968): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed[/I]

---

