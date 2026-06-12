---
title: "Application menu wont drop down 10.04"
date: 2011-07-09
forum: General Help
---

### Post by mattv111 on 2011-07-09
Hey so last night I received my invite for google music then I quickly realized the Music Manger isn't for Linux yet. So after searching around a bit I found this script that was suppose to make it run under wine which it did, but also after running that script my applications menu no longer drops down :( any help would be greatly appreciated I'm on Ubuntu 10.04

Here's the script
#!/bin/bash

echo " "
echo "Google Music Manager install for Ubuntu"
echo "   by bluescreenkid (june 2011)"
echo " "

# check if WINE is installed

if dpkg -s "wine" 2>/dev/null 1>/dev/null; then
   export user=$(whoami)	# current logged in username

   # copy windoze files
   echo " "
   echo "Installing Google Music Manager"
   cp -R Programs/ ~/.wine/drive_c/users/$user/Local\ Settings/Application\ Data/

   # create .desktop file
   echo " "
   echo "Creating Menu Entry"
   echo "[Desktop Entry]" > ~/.local/share/applications/musicmanager.desktop
   echo "Type=Application" >> ~/.local/share/applications/musicmanager.desktop
   echo "Terminal=False" >> ~/.local/share/applications/musicmanager.desktop
   echo "Icon=/home/"$user"/.wine/drive_c/users/"$user"/Local Settings/Application Data/Programs/Google/MusicManager/gmm.png" >> ~/.local/share/applications/musicmanager.desktop
   echo "Name=Google Music Manager" >> ~/.local/share/applications/musicmanager.desktop
   echo 'Exec=env WINEPREFIX="/home/'$user'/.wine" wine "/home/'$user'/.wine/drive_c/users/'$user'/Local Settings/Application Data/Programs/Google/MusicManager/MusicManager.exe"' >> ~/.local/share/applications/musicmanager.desktop

   # add into applications.menui
   echo " "
   echo "Adding Menu Entry"
   echo "   A backup copy is located at ~/.config/menus/applications.menu.bak"
   cp ~/.config/menus/applications.menu ~/.config/menus/applications.menu.bak
   sed '$d' < ~/.config/menus/applications.menu > tempmenu
   cat applications.menu.add >> tempmenu
   mv tempmenu ~/.config/menus/applications.menu
   echo " "
   echo "Completed Install"
   echo "   Google Music Manager can now be found in :"
   echo "   Applications > Internet > Google Music Manager"
   echo " "
else 
   echo " "
   echo "WINE is not installed." 
   echo " "
   echo "To install WINE please use ether of the below methods"
   echo " "
   echo "1 : sudo apt-get install wine"
   echo "or"
   echo "2 : sudo add-apt-repository ppa:ubuntu-wine/ppa"
   echo "    sudo apt-get update"
   echo "    sudo add-apt install wine"
   echo " "
fi

---

### Post by pqwoerituytrueiwoq on 2011-07-09
what does this give you
```
cat ~/.config/menus/applications.menu
```
```
cat ~/.config/menus/applications.menu.bak
```
post content using code tags

---

### Post by mc4man on 2011-07-09
That whole deal with the cp menu, ect. doesn't seem right.
Either delete  ~/.config/menus/applications.menu or copy/move the .bak back

```
cp ~/.config/menus/applications.menu.bak ~/.config/menus/applications.menu
```

If a menu item is desired create one yourself in alacarte if the .desktop previously created doesn'y show up

---

### Post by mattv111 on 2011-07-09
I figured it out in terminal I typed...

$ rm /home/<username>/.config/menus/applications.menu

it works normal now after that

---

### Post by mattv111 on 2011-07-09
I didn't see the replies before last post. Thanks guys!

---

