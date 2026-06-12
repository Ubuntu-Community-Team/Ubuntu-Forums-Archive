---
title: "Startup script on Ubuntu Server"
date: 2012-01-24
forum: General Help
---

### Post by Pazau on 2012-01-24
Hello all.

I have an Ubuntu server running a Minecraft server.

At every startup, I should start Screen, change directory, and run my script that starts the Minecraft server.

I've read a little bit about scripts, but I'm still unsure of some things - mostly about user rights. I am the only user on the server (besides root of course).


I want the script to start the screen, change directories and start either my script to the server file, or start the Minecraft serverfile with a Java command on my user - and log me out, if necessary.

The commands to use are:

"screen"
"cd /home/nicolas/STUMCS"
"./startmcserver.sh"


Someone who will help me with this? :D

---

### Post by Paqman on 2012-01-24
Just change the line in your Minecraft server start script so that it invokes screen:
```
screen -dmS minecraft java -Xms1024M -Xmx1024M -jar /path/to/minecraft_server.jar nogui
```

Then when you run your script, everything happens.

---

### Post by Pazau on 2012-01-24
Can I get it to run automatically at startup? :)

---

