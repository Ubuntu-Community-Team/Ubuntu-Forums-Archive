---
title: "Trying to get minecraft to work?"
date: 2011-05-29
forum: General Help
---

### Post by Charlene Shave on 2011-05-29
I am trying to get minecraft to work in ubuntu 11.04 I have got java installed but its just goes to grey screen and says on there would like a bit off help please thanks

---

### Post by linuxinstalledfromhdd on 2011-05-29
Hi there.. First make sure you have installed everything on your system you will need to get it to run correctly:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

Secondly, here is a newer script to install minecraft:

[http://cinderbox.net/2011/04/19/games-minecraft-for-ubuntu-installation-script/](http://cinderbox.net/2011/04/19/games-minecraft-for-ubuntu-installation-script/)

Hopefully this works for you..

Cheer. :)

---

### Post by Charlene Shave on 2011-05-29
Thank your for your help :)

---

### Post by Charlene Shave on 2011-05-29
Sorry for the bump, I got my boyfriend to help me, he's used Ubuntu for alot long then i have

---

### Post by linuxinstalledfromhdd on 2011-05-29
Hopefully that works for you..  :P

---

### Post by linuxinstalledfromhdd on 2011-05-29
If that doesn't work you can try this as well. Uninstall it with the script file first.  Then delete
the hidden .minecraft directory in your home directory.  Then reinstall it again:

```
wget http://cinderbox.net/wp-content/uploads/2011/04/Minecraft_Installer_18.sh.tar.gz

tar zxvf Minecraft_Installer_18.sh.tar.gz Minecraft_Installer_18.sh

sudo chmod +x ./Minecraft_Installer_18.sh

./Minecraft_Installer_18.sh
```

---

### Post by Charlene Shave on 2011-05-29
Its ok now got it working thanks for the help :) My boyfriend did it as i am not good at stuff like did play minecraft on vista but it was really laggy so i thought i tried out ubuntu and its looks good now go lag :)

---

### Post by linuxinstalledfromhdd on 2011-05-29
Find some diamonds :)

---

### Post by Mr_VeRiTy on 2011-05-29
If it still stays on a grey or black screen, you might need replace the bundled lwjgl files, to do this (but first[COLOR=Red] back up your /.minecraft folder[/COLOR][COLOR=Black]):
[/COLOR]
1) click [HERE]("http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.7.1/lwjgl-2.7.1.zip/download") to download the latest lwjgl.
2) extract the zip file it downloads (right click, click extract here.)
3)open the lwjgl folder go to native and then linux and copy all of the files in there to your /.minecraft/bin/natives  folder (it's a hidden folder in you home directory,) and replace the files already there.
4) Go back the the lwgjl folder and go to the jar folder, and copy the following files to your /.minecraft/bin folder:
jinput.jar
lwjgl.jar
lwjgl_util.jar
lwjgl_util_applet.jar
replace the files already there
5)Start minecraft and enjoy!


Edit: Oops too late :S lol

---

### Post by Charlene Shave on 2011-05-29
linuxinstalledfromhdd: How come you wanted me to find some diamond?



Mr_VeRiTy: Its ok dont worry about it thanks for the help anyway :)

---

### Post by linuxinstalledfromhdd on 2011-05-29
They are virtually impossible to find. :)

---

### Post by Charlene Shave on 2011-05-29
Oh right i found some before when i looking in caves, all you got do is keeping down not hard havent you found when you been playing??

---

