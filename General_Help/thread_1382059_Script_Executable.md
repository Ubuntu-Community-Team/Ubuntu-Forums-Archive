---
title: "Script Executable?"
date: 2010-01-15
forum: General Help
---

### Post by Tourdog on 2010-01-15
How do you make a script written in a text editor (gedit) executable for use in the sequenced, "Startup Applications" ???    

 ie What goes in "Terminal" and what goes in the "gedit" ???

TIA !  :)

---

### Post by d3v1150m471c on 2010-01-15
to make it executable, the best way is to save it in your home folder, then inside the terminal type:

chmod +x filename

You can also rightclick the file and in properties > permissions, select all the stuff you want it to do. then you can run the file in the terminal by typing ./filename or opening it and it will prompt you with various commands. I know a bit about bash scripts. I'm no expert but chances are i can probably give you some good pointers if you tell me what it is you are trying to get the script to do.

Also, to add it to startup, go to your "startup applications" in your preferences and add a new app. add ./filename to the startup applications as the command.

Feel free to send me a private message. Or...
<--- click that yahoo icon right there. I'm almost always around my computer.

---

### Post by nothingspecial on 2010-01-15
If you make a directory /home/username/bin and put it in there, you don`t need to navigate to where it is and ./ it. You can just type the file name.

If you put it in /usr/bin then every user will be able to use it in this way

---

### Post by Portmanteaufu on 2010-01-15
> **d3v1150m471c said:**
> to make it executable, the best way is to save it in your home folder, then inside the terminal type:

chmod +x filename

You can also rightclick the file and in properties > permissions, select all the stuff you want it to do. then you can run the file in the terminal by typing ./filename or opening it and it will prompt you with various commands. I know a bit about bash scripts. I'm no expert but chances are i can probably give you some good pointers if you tell me what it is you are trying to get the script to do.

Also, to add it to startup, go to your "startup applications" in your preferences and add a new app. add ./filename to the startup applications as the command.

Feel free to send me a private message. Or...
<--- click that yahoo icon right there. I'm almost always around my computer.

Everything he said, except you'll probably have to put the absolute path (the complete path, starting from "/") to the script in your startup applications rather than "./filename".

---

### Post by Tourdog on 2010-01-15
d31150m471c
nothingspecial
Portmanteaufu,

You guys are fantastic!  I'm working on that info right now.  :)

Thank you again!

script solves it !  Done.

---

