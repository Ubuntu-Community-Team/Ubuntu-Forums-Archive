---
title: "Trouble with a crontab"
date: 2011-03-30
forum: General Help
---

### Post by Rikeshar on 2011-03-30
Hello everyone, I'm hoping you can give me some help figuring out what might be going wrong here. 

I'm running Ubuntu, and have created a script which will automatically  fetch a file from the server I'm running Minecraft from. There is then a  java program called Tectonicus which uses the data in the world folder  to generate a Google-maps style map of the world. The script I've  written is:

```

/usr/bin/scp -r USERNAME@SERVER:/home/zach0242/minecraft/world /home/thornbury/Desktop 

java -jar /usr/games/Tectonicus_v1.30.jar  worldDir=/home/thornbury/Desktop/world  outputDir=/home/thornbury/Desktop/TectonicusTest cameraAngle=225  imageFormat=jpg  minecraftjar=/home/thornbury/.minecraft/bin/minecraft.jar  playersInitiallyVisible=false signs=all signsInitiallyVisible=false  useBiomeColours=true 

rm -rf /home/thornbury/Desktop/world

```...where "USERNAME" and "SERVER" have their appropriate values. 

I have this script, titled tectonicus, on my desktop. If I run the script from the command line:

```

/home/thornbury/Desktop/tectonicus

```... it runs perfectly. The trouble I"m having is that I"m trying  to create a crontab to run it remotely. The crontab looks like:

```

30 12 * * * /home/thornbury/Desktop/tectonicus

```... and I've been changing the timing to test.

What's going on is that the script will execute, the world file is  downloaded and Tectonicus starts... but it doesn't finish. It creates  the TectonicusTest file on my desktop, creates the Cache folder with the  skineCache, tileCache, and tileLists folders, which are empty. After  this it deletes the world folder from my desktop and that's it. I tried  removing the line that deletes the world folder from the script, and the  only difference it made was that the folder wasn't deleted; Tectonicus  still didn't finish running after only making those files.

I tried running the crontab with crontab -e and sudo crontab -e, thinking there might be a permissions conflict, to no avail. 

Any ideas?

---

### Post by Dave_L on 2011-03-30
The last line in the script is the line that deletes the world folder. What do you expect to happen after that?

---

### Post by Rikeshar on 2011-03-30
After that, the script should end itself. That's the last thing that should happen.

I'm wondering, since the second part of the script, the java program, takes some time (up to an hour and a half if there's no cache yet) does the script wait until that java program is finished before deleting the world file? It might be that the script downloads the file, starts the java program, and then after it starts, it moves on to the next line and deletes the world, which would cause the java program to not be able to finish running. Is there a way I can delay this besides maybe moving the remove line to a different crontab which runs a few hours later?

---

### Post by DaithiF on 2011-03-30
capture stdout and stderr output from the job to see if any errors are being reported:

```
30 12 * * * /home/thornbury/Desktop/tectonicus > /path/to/some/logfile 2>&1
```

also make sure that the same version of java is being called as when you execute it manually ... you don't have java aliased in your profile to another java jdk location for example?

---

### Post by Rikeshar on 2011-03-30
Ah, looks like adding DISPLAY=:0 to the crontab fixed the issue. Could someone maybe explain to me why that would do? I thought that was used for gui scripts?

---

### Post by DaithiF on 2011-03-31
scp and rm won't care about DISPLAY, but i guess the tectonicus java program does

---

