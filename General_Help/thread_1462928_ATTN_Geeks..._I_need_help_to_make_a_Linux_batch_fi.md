---
title: "ATTN: Geeks... I need help to make a Linux batch file.."
date: 2010-04-26
forum: General Help
---

### Post by schwabdale on 2010-04-26
How do I make a file that contains some commands like sudo apt-get ....
I want to make this an executable file like a windows batch file.

Please help. I just want to be able to double click it to do an install.

---

### Post by davrosuk on 2010-04-26
Any text file you create can be a 'batch' file. In this case you would be making a bash script.

To make the file executable use chmod 770 <filename>

to execute you can double click on it and run or ./<filename>

---

### Post by conradin on 2010-04-26
Well, you write a script. The danger of writing this type of script is what to do with the admin password. Do you include it in a variable in the script where any joe can find it? or Type it in while runing the script. 

Heres a nice scripting how to for BASH
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html#toc3](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html#toc3)

I think there is a way to do it with a launcher too right click the panel and select add to panel --> Custom application launcher.
name it, give the command, if its a terminal app select that from the drop down, change its icon if you want, write back if you need more help.
maybe 
```

sudo apt-get upgrade

```

---

### Post by overlordchin on 2010-04-26
alternatively you could make an alias if you want an easy way to install apps. Edit your bashrc file which can be found under /home/youruser/.bashrc

add a line that looks like:

alias inst="sudo apt-get install"


than you can type "inst firefox"
and it will search the repo for firefox

---

### Post by schwabdale on 2010-04-27
Thanks for the replies.

So, lets say I want to download GoogleEarth.bin from Google. 
I download it to the desktop. Now I have a .bin file sitting on the desktop.

Next, I right click the desktop and create a Launcher that runs in the terminal. 
I want this launch to switch to the desktop and install the binary file... But I can't get it to work. 
Here is the command I am putting in...

  	 	 	 	 	 	  [COLOR=#000000]**cd Desktop chmod +x GoogleEarthLinux.bin && ./GoogleEarthLinux.bin**[/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]What am I doing wrong?[/COLOR]

---

### Post by rnerwein on 2010-04-27
hi
if you already have installed it then you have to look for the executable with the name: googleearth-bin
in a terminal run: ~/find . -iname "googleeearth-bin"
this should be the executeable ( i guess it's in ~/google-earth/[COLOR=Red]googleearth-bin[/COLOR]
thats the place where it was stored in my configuration ( i ain't know why it was there because i normaly store my downloads by default on another place )
hope this will help you.
ciao

---

### Post by schwabdale on 2010-04-27
I did already install it. This is just an example. I want to do this automatically with a executable file instead of 
a command line you always have to put in. 
The file is located on the desktop. Does anyone know what command I would put in?

---

### Post by overlordchin on 2010-04-28
So if I am reading this correctly you just want to be able to right click on a file make it executable and then run it or install it if need be?

If that is the case you could make a nautilus script to accomplish this. Also this assumes the file in question does not need to be interpreted or run through another application like wine in order to execute.

something like:

```

#!/bin/bash
chmod +x $@;
./$@;

```


then copy the script to /home/youruser/.gnome2/nautilus-scripts/

It should appear on your context menu when you right click on a file on your desktop under "scripts".
If I am misunderstanding could you elaborate a little more on what you need?

If on the other hand you are just asking how to run a bin file in ubuntu check this thread out:

[http://ubuntuforums.org/showthread.php?t=452512]("http://ubuntuforums.org/showthread.php?t=452512")

---

