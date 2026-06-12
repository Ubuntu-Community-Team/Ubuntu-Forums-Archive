---
title: "How to make script run in terminal automatically without choice dialogue?"
date: 2011-01-09
forum: General Help
---

### Post by LewRockwellFAN on 2011-01-09
Is there any way to make a launcher pointing to a script (or the script itself) always run in a terminal when I double click on it without popping up the [run/run in terminal/display] choice? 

I can make it always display by unsetting the executable permission in properties. I can make it always run (without showing a terminal) by using a launcher. But I haven't figured out any way to make it always run in a visible terminal without going through that choice dialogue.

---

### Post by sjhaffner on 2011-08-09
I was wondering this same thing. If anyone could help that would be great!

---

### Post by angry_johnnie on 2011-08-09
create a script.desktop file in /usr/share/applications

an example of a .desktop file:

```
[Desktop Entry]
Encoding=UTF-8
Name=name of your script/program
Comment=a description of your script/program
Icon=/path/to/desired/icon
Exec=/path/to/your/script
Terminal=true
Type=Application
Categories=where in the menu you want it (Audio, Games, System, etc.)

```

make sure you can read and execute this file

```
sudo chmod a+rx /usr/share/applications/yourfile.desktop
```

then you can update your menu entries

```
sudo update-menus
```

you'll find a new entry, for your script or program.
since the .desktop file contains the line "Terminal=true" it will run in terminal, without asking.


another quick way to do it is to create a launcher for the terminal command itself.

if you press alt+f2 and then run

```
xterm -e /path/to/your/script
```

it will automatically execute your script in a xterm window.
you can also create a launcher with the xterm -e command.

i'm pretty sure there must be a similar option for gnome-terminal, although i don't know that by heart :p

---

### Post by Habitual on 2011-08-10
```
gnome-terminal -e "/home/jj/bin/weather.sh"
```

runs my weather.sh script w\out any prompting.
Quotes are part of the command-line but turns out to be unnecessary.
If your script filename has spaces, use quotes
else
no quotes
endif

---

