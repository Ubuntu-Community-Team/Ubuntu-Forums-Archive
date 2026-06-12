---
title: "Minecraft and java"
date: 2011-07-22
forum: General Help
---

### Post by Hermies on 2011-07-22
So, im trying to download and play minecraft and i cant for the life of me get java so is there and apt-get's i can use to find java?

---

### Post by roololing on 2011-07-22
If I remember correctly, ```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by Hermies on 2011-07-22
> **roololing said:**
> If I remember correctly, ```
sudo apt-get install sun-java6-jre sun-java6-plugin
```


turn up as 
nicks@CapPlanet:~$ sudo apt-get install sun-java6-jre sun-java6-plugin
[sudo] password for nicks: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jre' has no installation candidate
E: Package 'sun-java6-plugin' has no installation candidate

---

### Post by Hermies on 2011-07-22
well as it says this is my first cup of Ubuntu and could it be that i have no E;/? or what-haves i only have one hdd

---

### Post by roololing on 2011-07-22
Try ```
sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```
And when the window pops up, tab to "OK" and press enter, and in the next one tab to "Yes" and press enter. I got it from [here]("http://www.multimediaboom.com/how-to-install-java-in-ubuntu-11-04-natty-narwhal-ppa/").

EDIT: "First Cup of Ubuntu" is just a sort of forum title that gives users an idea of how new you are on the forum.

---

### Post by robbiemacg on 2011-07-22
That being said, if memory serves, you should be able to play Minecraft with the open java stuff that's built into your stock install. 
Download the minecraft.jar file from [http://www.minecraft.net/](http://www.minecraft.net/) and just run the following command in a terminal:

```
java -Xmx1024M -Xms512M -cp **PATH/TO/YOUR/**Minecraft.jar net.minecraft.LauncherFrame
```After that, just decided where you want to keep your minecraft.jar file... (I like to toss mine inside the .minecraft directory that pops up in an ~/ after the first run, then build a launcher that points there. Though perhaps not the most professional move, it's clean and recursive. B-))

---

