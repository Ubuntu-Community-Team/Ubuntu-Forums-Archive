---
title: "Edit Applications Menu from terminal"
date: 2010-02-24
forum: General Help
---

### Post by txwooley on 2010-02-24
I wrote a simple little poker game in python.  Now I want to write an 'installer' that will check for dependencies and place it into the Applications menu under 'Games'.  How would I place a homemade program into the apps-menu via command-line?  I know how to 'chmod a + x my_app', and then to run it would be './my_app'.  I even know how to manually place it in the menu.  How would I do it through the command-line though?

---

### Post by warp99 on 2010-02-24
> **txwooley said:**
> I wrote a simple little poker game in python.  Now I want to write an 'installer' that will check for dependencies and place it into the Applications menu under 'Games'.  How would I place a homemade program into the apps-menu via command-line?  I know how to 'chmod a + x my_app', and then to run it would be './my_app'.  I even know how to manually place it in the menu.  How would I do it through the command-line though?

If you want this system-wide then place a *.desktop file into your /usr/share/applications folder with the command. Best thing is to make a *.deb package to install everything. Since you don't need to build from source it's pretty simple:

[http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/How-to-make-deb-packages/](http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/How-to-make-deb-packages/)

---

### Post by txwooley on 2010-02-24
I'm not sure a .deb is really the solution I'm looking for.  I want to give this program out to a few close friends, that's why I wanted to make an 'installer', but I didn't really want to INSTALL it.  My 'installer' will just check for dependencies and then place an executable in the Applications>Games menu.  To 'uninstall', simply delete the my_app.py file in their home folder.

---

### Post by warp99 on 2010-02-24
If you want an item to run you can just include a *.desktop file and drop it into ~/Desktop. Then the user can run it from the desktop and delete the icon with a right mouse click when finished. If you put the *.desktop file into the local menu, ~/.local/share/applications, the user also has to manually remove the icon from the menu unless you write a script to remove it. Why don't you just write a script with a case function so the user only needs to run the script?

```
#! /bin/bash

echo -n "My Poker Program

(a) Install
(b) Remove
(q) Quit (Leave this menu)

Please type a letter from the above choices and press 'Enter': "

read answer
case "$answer" in

[Aa]*)
echo "Installing ..."

$do_something

;;

[Bb]*)
clear
echo "Removing ..."

$do_something

;;

[Qq]*)

exit 0 ;;
*) ;;

esac
done

```

---

### Post by txwooley on 2010-02-24
I probably should just let them leave it on the desktop as an executable.  I just thought it would be cool if I could put it in the drop-down menu next to Blackjack and AisleRiot Solitaire.  Guess they'll just have to do that themselves.  Thanks for the input.

---

