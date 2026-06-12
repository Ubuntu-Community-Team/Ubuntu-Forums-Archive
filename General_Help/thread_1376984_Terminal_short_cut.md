---
title: "Terminal short cut"
date: 2010-01-09
forum: General Help
---

### Post by lsearcey on 2010-01-09
I have the below program that requires to use the terminal. Is their a way to shorten this up so I can just double click an icon or something like that?  I am using Ubuntu 9.10/   Thanks for your help in advance


From the terminal 
Code:
 cd ./Desktop/HeroScribe_1.0pre1

Code:
 java -jar HeroScribe.jar

---

### Post by kman269 on 2010-01-10
I'm not sure what the best way is since I am just a beginner but would a bash script work?

I would try opening a terminal and enter
cd /Desktop
gedit heroScribe

enter the following:

#!/bin/bash
java -jar /Desktop/HeroScribe_.0pre1/HeroScribe.jar

exiting out of that file and back in the terminal, enter

chmod +x heroScribe

you should then be able to start it by double clicking on that file. If you want to make it look a bit better, you can hide that file somewhere, create a launcher that starts it and you can use any picture as the icon.

---

### Post by Amagineer on 2010-01-10
You should be able to create a launcher in one of your gnome panels without making a bash script.

Right-click one of your panels (Personally I prefer the top one for my launchers) and select the "Add to Panel..." option. A new window should pop up. Double click the "Custom Application Launcher" item and yet another window should pop up. Set the "Title", the "Comment" and the Icon to whatever you'd like and the "Command" to ```
java -jar ~/Desktop/HeroScribe_1.0pre1/HeroScribe.jar
```

---

