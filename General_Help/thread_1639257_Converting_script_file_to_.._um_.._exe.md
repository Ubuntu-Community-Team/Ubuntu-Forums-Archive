---
title: "Converting script file to .. um .. exe?"
date: 2010-12-06
forum: General Help
---

### Post by xavier666 on 2010-12-06
Wait! Don't trash this thread yet!
I know that there is no such thing as exe in Linux but some of the applications have caught my eye. For example take mahjongg
All I have to do is click on the icon and it starts. For someone who recently transferred to Linux, it's as good as an exe. So, I go to /usr/games, I can see that it's some sort of executable.

So all I'm asking, can I convert my shell script to Linux executables along with custom icons?

Thanks...

---

### Post by oldos2er on 2010-12-06
chmod +x foo.sh

---

### Post by buddyd16 on 2010-12-06
1. Write your shell script in gedit/text editor of your choice and save it with a .sh extension. 
2. Right click the .sh file and verify that it is executable 
3. Create a launcher and point it at the .sh file you created. when you create the launcher you can specify an icon to be used.

---

### Post by lcdrovers on 2010-12-06
You'll need to make a .desktop file if you want to make a clickable sort of thing with an icon. An example is the built-in calculator's .desktop file.

```
#!/usr/bin/env xdg-open

[Desktop Entry]
Name=Calculator
Comment=Perform arithmetic, scientific, or financial calculations
Exec=gcalctool
Icon=accessories-calculator
NotShowIn=KDE;
Terminal=false
Type=Application
StartupNotify=true
Categories=GNOME;GTK;Utility;Calculator
X-GNOME-DocPath=gcalctool/gcalctool.xml
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gcalctool
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-OtherBinaries=gnome-calculator
X-Ubuntu-Gettext-Domain=gcalctool
```

I really don't know what most of the options do, but the Name, Comment, Exec, Icon, and Categories should be all that you need to make a useful .desktop file. After making the .desktop file, you can name it whatever you want and, if you want, put it in the "Applications" menu by moving the .desktop to /usr/share/applications, although you need sudo access to do this.

The Exec field points to the actual file it's going to execute; in your case, it would be the path to your shell script. Icon points to the icon; just put in the path to the picture that you'd like to use for the icon. I don't know what file formats it supports, but .png works, so you can probably just convert to that for such a small picture. The Categories field puts the desktop into the appropriate category; obviously, there are several, but the important ones (meaning the ones that put it into separate categories in the Applications menu) are Utility (goes into the "Accessories" category), Game, Graphics, Network, Office, Video, Education, System (which put the launcher in the system dropdown menu), and Development (which is for programming tools). Remember, in the categories field, all of the categories given must end with a semicolon, except the last one.

I'm new to Ubuntu, but I know a bit about this after noodling with it myself. I hope this helps!




EDIT: I realized after typing up this post that you were probably just looking for how to simply make a shell script executable, but if you ever want to make a .desktop file, it's there now. :D

---

### Post by xavier666 on 2010-12-07
> You'll need to make a .desktop file if you want to make a clickable sort of thing with an icon. An example is the built-in calculator's .desktop file.
As far as I know, if I make a launcher a desktop file, it can no longer be executed :(

> chmod +x foo.sh
My script file is working perfectly :D

This is my shell script. Executing this script directly connects me to the net. The location of this script is in a folder named "Scripts" inside my Home Folder. The net client program (crclient) is in the folder Software/crclient in the Home Folder 

```

cd ..                        //  To go 1 lvl up from "Scripts"
cd Softwares/crclient        //  To go to the net client program
./crclient -u abcd           //  Executing the client using Username
                             //  Password is stored beforehand

```

This script is working fine (If i click on the script, it offers me two choices, to run in terminal or to just run. Though for reasons I can't understand, it just refuses to run in terminal but runs fine otherwise)

Now I did the following
[LIST]
[*]Right click on desktop
[*]Select "Create Launcher"
[*]Select Type as "Application/Application In Terminal" (Any one)
[*]In Command, i'm just giving the script location
[*]Clicking OK
[/LIST]
The created Launcher refuses to work?

Any explanations?

Thanks...

---

### Post by efflandt on 2010-12-07
If you **mkdir ~/bin** and put your script in that path, the next time you login, that will automatically be included in your PATH.  Then right click on the desktop or a panel and create a launcher that will launch your script.  If it needs a terminal you should select "Application in Terminal" at the top instead of just Application.

As long as it is in your ~/bin you do not need a path, but if it is not somewhere in your PATH, you may need the "full" path to it as a Command in the launcher (shortcuts like ~/ or $HOME/ might not work).

---

### Post by WorMzy on 2010-12-07
> cd ..

Use absolute paths instead of relative paths if you want the script to be called from any location. e.g.
```
cd /home/username
```

---

### Post by buddyd16 on 2010-12-07
Type will be "Application in Terminal"

Command will need to be:
```
sh -c "cd /home/your username/Scripts && ./scriptname"
```

---

### Post by xavier666 on 2010-12-08
> Use absolute paths instead of relative paths if you want the script to be called from any location. e.g.
Thanks wormzy! Not that it solved the problem (it was something different) but it helped me to write better scripts.

I don't know why but making the launcher an "*Application*" instead of an "*Application in Terminal*" solved the problem

However the thing is, only half the time the launcher works. I just can't explain it

Thanks for all the posts! =D>

---

