---
title: "Moving Java icon onto Unity launcher"
date: 2012-05-11
forum: General Help
---

### Post by RogerD on 2012-05-11
Hi

I've got a Java application, it's a JNLP file, that I start by clicking an icon on my 12.04 desktop. Is there any way I can move the icon to the Unity launcher? When I try to drag it onto the launcher, it just pops back onto the desktop.

Roger D

---

### Post by efflandt on 2012-05-11
In order for .desktop launchers to stick to the unity bar, they have to be in the proper location with proper ownership.  But when I was trying to do that, I did not even know what a .desktop file was supposed to contain.

Install **alacarte** (or shown as Main Menu in software center).  Then in Dash search for Main Menu and use that to make a launcher.  Then you should be able to find the launcher in Dash, and after using your launcher from there, you can make the icon in the Unity bar stick.

I set up a launcher like that for a java game (minecraft).  It runs a script in a terminal to cd to proper directory, then runs java to launch the game.  I extracted the favicon out of the minecraft.jar to use as icon for the launcher.

---

### Post by RogerD on 2012-05-11
Thanks.

Having problems creating a new item in Main Menu.

Is it Application in the Type box? Also, how do I know what to put in the Command box?

---

### Post by jonnyboysmithy on 2012-05-11
Yup, placing it under the "Application" menu should be just fine.
Open the 'Main menu' program. Click 'New Item' give it a name. Click browse and find the file you want to open. 

So in my case that is /home/.minecraft/minecraft.jar because thats where the file I want to run is located. Make sense?


If you want to get really fancy you can give it an icon. When you opened the "New item" windows click on the funny picture on the left, and you can select your own.

---

### Post by RogerD on 2012-05-11
Hmm...still having problems finding the file I want to open.

When I examine the properties of the desktop icon that currently launches the application I get: JNLP file (application/x-java-jnlp-file)

When I examine the same icon via Dash I get: 

#!/usr/bin/env xdg-open

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Link
Icon[en_GB]=gnome-panel-launcher
Name[en_GB]=apogee
URL=http://apogee.theiet.org:8080/media/ApogeeMedia.jnlp
Name=apogee
Icon=gnome-panel-launcher

Does any of this tell me what to do?

---

### Post by jonnyboysmithy on 2012-05-11
Looks like you opened the laucher with a text editor.
So now that you have this launcher try dragging it onto the unity sidebar. Since it is a launcher it should go on there no probs.

---

### Post by jonnyboysmithy on 2012-05-11
I have attached a recording of how I make a launcher for minecraft and add it to the unity launcher.

---

