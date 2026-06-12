---
title: "Help with shell script"
date: 2010-11-02
forum: General Help
---

### Post by Rypervenche on 2010-11-02
Hi all. I am rather new to shell scripts, but I made a few of them to start a java game. I am having a little trouble though. Here is what I am using.

#! /bin/bash

killall ibus-daemon

java -Xmx1024M -Xms512M -cp /home/rypervenche/&#36938;&#25138;/Minecraft/Minecraft.jar net.minecraft.LauncherFrame

ibus-daemon --xim &

disown


The game does not work when ibus is active, so I have the script kill it then start the game. When I close the game I want the script to automatically restart ibus-daemon so this is what I was told to use. Here is my problem though...

It works fine when I run it in the terminal and when I double-click on it and choose "Run". Ibus is started at the end.

However, when I open it through a launcher or double-click on it and choose "Run in terminal", it does not open ibus-daemon once I close the game. Is this a problem on my end? How can I fix this so that I can start my game from a launcher and have ibus-daemon up and running once I close the java game?

Thank you in advance for all help.

---

### Post by janisozaur on 2010-12-17
try launching
```
XMODIFIERS= java -Xmx1024M -Xms512M -cp /home/rypervenche/&#36938;&#25138;/Minecraft/Minecraft.jar net.minecraft.LauncherFrame
```

---

