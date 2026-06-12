---
title: "Creating a Custom Launcher"
date: 2010-09-23
forum: General Help
---

### Post by kadafy on 2010-09-23
Hey, first off I'd like to say thanks for any support that's given. :)

Okay, so my issue is I'm trying to create a launcher that's doing two separate commands. Here's currently what I have.
```
rm ~/Games/Nintendo\ DS/NO\$Zoomer.ini; wine ~/Games/Nintendo\ DS/NO\$Zoomer.exe
```Now, the reason I have to delete the .ini file, is for some reason the file gets corrupted every time (it's a well known problem, from what I've read.) and I can't start up the program until it's removed. Now, it works fine in Terminal, but when I run it through my Launcher icon, it does nothing.

Thanks again.

---

### Post by MooPi on 2010-09-23
Create a script including your commands and chmod +x the file. Change the executable to the script in the launcher instead of your command. Another thought and I can't test this for you, is you may need terminal emulation to get the wine app running. For this you should add ```
gnome-terminal -e wine ~/Games/Nintendo\ DS/NO\$Zoomer.exe
```

---

### Post by kadafy on 2010-09-24
I'm trying to make sure I understand everything correctly. If I type those commands directly into terminal, everything works. I'm not sure if I made my script correctly. I'm trying to read up on it, but it could be my lack of sleep that makes it difficult. I just went into gedit, and put that exact string I posted in the forums and just named it "test.sh". I tried running it directly off the Desktop, nothing. I tried doing run as terminal, nothing. I went into terminal, went to the Desktop, and ran "./test.sh" and nothing came up either. There HAS to be something I'm doing wrong.

Oh, I also tried the command you gave me. It didn't run the program. :(

---

### Post by MooPi on 2010-09-24
To run a script in terminal use ```
sh shellname.sh
```
I can't help with the coding but if it works in terminal it should work as a script. I have written scripts and moved them to /usr/lib. I then create a keyboard shortcut for my Openbox desktop. That is the equivalent to having a launcher in Gnome. I would suggest breaking down the command and to see where it is failing.

---

### Post by kadafy on 2010-09-24
Works perfectly now. Thank you so much! <3

Now I learned something new. :)

---

