---
title: "Desktop launcher will not launch"
date: 2012-02-13
forum: General Help
---

### Post by Ansha on 2012-02-13
So I'm trying to create a desktop shortcut to a game I downloaded called Lambda Rogue.
I've put in the full path to the bin in the command box, but when I double click the launcher, nothing happens.
If I set the the launcher to run from the terminal, the terminal flashes open and closes in a brief instant.

The game works fine when running the actual executable; it's just the launcher that will not work.

Help with resolving this issue is appreciated.

---

### Post by HiImTye on 2012-02-13
you should make a script to launch it and make sure that you change to the games' directory

note: to call it in the same directory you need to add ./ to the filename, i.e.:
```
cd /path/to/game
./gamefile
```

---

### Post by efflandt on 2012-02-13
I made a desktop launcher that creates a desktop launcher, it runs:

```
sh -c 'gnome-desktop-item-edit --create-new ~/Desktop'
```Without the **sh -c** and single quotes it would not interpret the parameters correctly.

But if you create ~/bin and log out and back in, that bin will automatically end up in your $PATH and you can put any scripts there to do whatever you need to do to run the game. Then the desktop launcher can simply run your script by its name (assuming you set execute permission on the script).  Example of script run by desktop launcher in a terminal for minecraft:
```
#!/bin/sh
# Change cd line to your path to orig minecraft.jar, NOT ~/.minecraft/bin
cd ~/MC-client
java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
```

---

