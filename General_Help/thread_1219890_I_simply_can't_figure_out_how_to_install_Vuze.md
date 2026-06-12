---
title: "I simply can't figure out how to install Vuze"
date: 2009-07-22
forum: General Help
---

### Post by atreidex on 2009-07-22
Ok, i'm a Level 0 newbie, but i've read a lot of threads here on the forum and i simply can't figure out how to install Vuze. I've downloaded the .tar.bz2 archive from the vuze.com website. I've extracted its contents but now what...

The Readme states that the operation is pretty simple: 

"RUNNING:
1. Extract the contents of this .tar.bz2 file.
2. Change to the 'azureus' directory where the files were extracted.
3. Start Azureus by running the script named 'azureus'; ex. "./azureus"

NOTE:
If you have the Java JRE installed somewhere unusual (or not in your PATH),
use the JAVA_PROGRAM_DIR option in the script."

BUT if i try to run the script named "azureus" :) nothing happens. 

I changed the JAVA_PROGRAM_DIR to what i think that my java dir is "/usr/lib/jvm/java-6-openjdk/jre/bin" but again, nothing happens.

Anyone out there that can help me?

---

### Post by Psycho.mario on 2009-07-22
Why don't you just open a terminal and type:
```
sudo apt-get install vuze
```
This will install vuze and all the dependencies.

---

### Post by Cheesemill on 2009-07-22
Downloading software directly from a website should be your last resort with Ubuntu, the package manager provides a much more secure and easier method for installing programs.

Go to Applications > Add/Remove, type vuze into the search box then place a tick in the box next to Vuze then click on Apply Changes.

You can also do this from the command line by typing:
```
sudo apt-get install vuze
```

Check out the following link for more information on installing software on Ubuntu.
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by atreidex on 2009-07-22
Yes i did that but the latest version of Vuze in the app manager is 3.3
If i install it, vuze will require to update to the latest version (4.2), i off course agree, the app restarts, then again wants to upgrade, then again wants to restart and so on... something is wrong and i can't figure out why so i just wanted to get the latest version from the official website so i can stop this vicious cicle :(

---

### Post by The-ITu on 2009-07-22
look it up on synaptic,
else, just use apt-get like every one else suggested.
if you insist on installing it from the tar.bz2 file please tell me if there is one file (and if what extention does it have) or if there are manny file and folders.

---

### Post by atreidex on 2009-07-22
> **The-ITu said:**
> look it up on synaptic,
else, just use apt-get like every one else suggested.
if you insist on installing it from the tar.bz2 file please tell me if there is one file (and if what extention does it have) or if there are manny file and folders.

i used the apt-get but as i stated in my previous post something strange occurred with the updating of vuze, it kept updating the software and restarting the application over and over and over again, that's why i wanted the latest version.

in the Vuze folder i do have the following files&folders:
[folder] plugins
azureus
azureus2.jar
ChangeLog.txt
GPL.txt
installer.log
README.txt
swt.jar
TOS.txt
updateAzureus
vuze
vuze.png

I guess it's something related to the java settings but i can't figure out what.

---

### Post by Cheesemill on 2009-07-22
[http://ubuntuforums.org/showthread.php?t=995327](http://ubuntuforums.org/showthread.php?t=995327)

---

### Post by philinux on 2009-07-22
Open vuze. Cancel any update screens.

Tools>options>Interface>Start.

Untick Auto update assistant, and any other you dont like.

I'm using deluge instead. Much nicer feel.

---

### Post by atreidex on 2009-07-22
> **Cheesemill said:**
> [http://ubuntuforums.org/showthread.php?t=995327](http://ubuntuforums.org/showthread.php?t=995327)

oh yeah, this is what i needed!

thanks a lot !

---

### Post by Cheesemill on 2009-07-22
+1 for Deluge.
Vuze is far to bloated IMHO

---

