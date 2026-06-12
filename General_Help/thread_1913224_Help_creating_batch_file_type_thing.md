---
title: "Help creating batch file type thing"
date: 2012-01-22
forum: General Help
---

### Post by stifmyster1 on 2012-01-22
wasn't sure what to call it in the title sorry.

I'm brand new to ubuntu. But I'm liking it so far. I'm currently using it to run a minecraft server for a me and my mate. Unfortunately every time it turns on i have to open then terminal and type out this code:

home:-/cd survival-server
home/survival-server:-/ java -Xmx1024M -Xms1024M -jar minecraft-server.jar nogui

home:-/cd creation-server
home/creation-server:-/ java -Xmx1024M -Xms1024M -jar minecraft-server.jar nogui

what i want to be able to do. Is type a simple command that will execute a files which will then run the above command line. Similar to the .bat file on windows.

I've browsed several forums and haven't been able to find anything. I've found plenty that describe auto running from start-up but i run 2 different servers from the one computer and need to be able to change easily.

Anyone know of how to create a executable .txt file or ubuntu's version of that and then how to execute that file from terminal?

---

### Post by davethewave83 on 2012-01-22
> **stifmyster1 said:**
> wasn't sure what to call it in the title sorry.

I'm brand new to ubuntu. But I'm liking it so far. I'm currently using it to run a minecraft server for a me and my mate. Unfortunately every time it turns on i have to open then terminal and type out this code:

home:-/cd survival-server
home/survival-server:-/ java -Xmx1024M -Xms1024M -jar minecraft-server.jar nogui

home:-/cd creation-server
home/creation-server:-/ java -Xmx1024M -Xms1024M -jar minecraft-server.jar nogui

what i want to be able to do. Is type a simple command that will execute a files which will then run the above command line. Similar to the .bat file on windows.

I've browsed several forums and haven't been able to find anything. I've found plenty that describe auto running from start-up but i run 2 different servers from the one computer and need to be able to change easily.

Anyone know of how to create a executable .txt file or ubuntu's version of that and then how to execute that file from terminal?

You don't need to cd if you use the full path from root (i.e /home/survival-server/java -Xmx1024M -Xms1024M -jar minecraft-server.jar nogui)

does it work to create a new file called minecraft (right click desktop-> create document -> empty file) 

add: 

/home/survival-server/java -Xmx1024M -Xms1024M -jar minecraft-server.jar nogui
/home/creation-server/java -Xmx1024M -Xms1024M -jar minecraft-server.jar nogui

to it, save the file (use your own full path if these are not correct)

rightclick the file "minecraft" click properties -> permissions and allow executing file as a program

to test it so you can see it working, open a terminal window and run the file from the terminal using the ./ prefix "./minecraft" 

so if you created the file on the desktop, open a terminal and run ./home/yourusername/Desktop/minecraft from root 

or cd to /home/yourusername/Desktop/ and run ./minecraft

it should tell you if the script is working or not.

if it is working you can just double click the file minecraft and click run in terminal

if not, what are the errors?

---

### Post by stifmyster1 on 2012-01-22
It appears as if it tries to run if i double click it. But then its as if terminal crashes. It open terminal. half a second later terminal crashes. And if I try cd to the home folder the type: run ./minecraft it says that the command run does not exist.

---

### Post by NightFoxyarrith on 2012-01-22
That won't work because java is not in your home dir. Try putting this in the minecraft file instead:
```

#!/bin/bash
java -Xmx1024M -Xms1024M -jar /home/survival-server/minecraft-server.jar nogui
java -Xmx1024M -Xms1024M -jar /home/creation-server/minecraft-server.jar nogui

```
And be sure to make it executable (either using the graphical way explained by davethewave83, or the command chmod +x minecraft).
That should do it.

---

### Post by davethewave83 on 2012-01-22
> **NightFoxyarrith said:**
> That won't work because java is not in your home dir. Try putting this in the minecraft file instead:
```

#!/bin/bash
java -Xmx1024M -Xms1024M -jar /home/survival-server/minecraft-server.jar nogui
java -Xmx1024M -Xms1024M -jar /home/creation-server/minecraft-server.jar nogui

```
And be sure to make it executable (either using the graphical way explained by davethewave83, or the command chmod +x minecraft).
That should do it.

4am is too early for me. :P

---

### Post by stifmyster1 on 2012-01-22
Ok. Im still getting the "run is not a recognized command"

---

### Post by NightFoxyarrith on 2012-01-22
There's no run command, just type ./minecraft

---

### Post by conradin on 2012-01-22
Im not clear if you got the script working. 
Do you want this script to run automatically (without so much as logging in), or run when you login?

---

