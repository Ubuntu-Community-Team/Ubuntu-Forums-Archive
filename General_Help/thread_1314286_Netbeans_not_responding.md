---
title: "Netbeans not responding"
date: 2009-11-04
forum: General Help
---

### Post by shaon3343 on 2009-11-04
[LEFT][B][SIZE=2] hi there, 
[/SIZE][SIZE=2]I've installed netbeans for C/C++ programming from this file: netbeans-6.5-ml-cpp-linux.sh.
[/SIZE][SIZE=2]It worked well several times. But After about 15 days I tried to lunch it but it shows the "starting NetBeans" and then disappear, nothing happens !! I just cant lunch and use it for my programming! Please help me to solve this problem.
[/SIZE][/B][/LEFT]

---

### Post by kellemes on 2009-11-04
Start Netbeans from a terminal-window and watch the output for hints..

---

### Post by shaon3343 on 2009-11-04
I entered netbeans and it says :

shaon@shaon-desktop:~$ netbeans
The program 'netbeans' is currently not installed.  You can install it by typing:
sudo apt-get install netbeans
bash: netbeans: command not found
shaon@shaon-desktop:~$

---

### Post by kellemes on 2009-11-04
> **shaon3343 said:**
> I entered netbeans and it says :

shaon@shaon-desktop:~$ netbeans
The program 'netbeans' is currently not installed.  You can install it by typing:
sudo apt-get install netbeans
bash: netbeans: command not found
shaon@shaon-desktop:~$

Did you have a specific reason to install using the netbeans installscript?
Since you installed using this script the netbeans-executable probably is somewhere outside the system searchpath.

You can install netbeans like so..
```
sudo apt-get install netbeans
```

---

### Post by shaon3343 on 2009-11-04
ya,
 I do  have a huge reason to install this from netbeans installscript, that is , here my download speed is terrible ( maximum download speed is 12 KBPS)!!  So i collected this from my friend and installed this . I use this netbeans several times to do some programming and it worked well. But suddenly it is not lunching! plese help me.

---

### Post by digiPixel on 2009-11-04
Often I have to use the version of NetBeans supplied on the official NetBeans website since the version in the Ubuntu repository is often out of date (currently supplies version 6.0.1). Using NetBeans 6.7.1 as an example you can find out how NetBeans is being started by going to Preferences -> Main Menu, and opening the properties for the Applications menu entry.

You should see something similar to this:

[INDENT]/bin/sh "/usr/local/netbeans-6.7.1/bin/netbeans"[/INDENT]


I always find that Ubuntu has application names hardwired which is totally wrong, even when the application's executable is in the PATH environment variable it is completely ignored. In that situation you change the working directory to the same directory that the executable is located in, and run it like this:

[INDENT]./netbeans[/INDENT]


One possibility that you should rule out first (create a backup beforehand) is to remove your NetBeans user settings directory, and startup NetBeans (through the Applications menu). For example with the joe user and NetBeans 6.7.1 the settings directory is located in /home/joe/.netbeans/6.7.

---

### Post by digiPixel on 2009-11-04
I forgot to mention that sometimes your NetBeans setting directory can become corrupted which could prevent NetBeans from starting up, or it messes up the NetBeans user interface.

---

