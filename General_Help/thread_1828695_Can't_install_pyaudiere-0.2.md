---
title: "Can't install pyaudiere-0.2"
date: 2011-08-19
forum: General Help
---

### Post by thelugnut on 2011-08-19
I am trying to install pyaudiere-0.2.tar.gz
1. I open a terminal
2. I cd to Desktop
3. Then I type in:
```
tar xvzf program.tar.gz
```
4. The folder appears on my desktop with the files shown in the attachment.
I don't know where to go from here. 
Can someone please set me straight?:confused:

---

### Post by dino99 on 2011-08-19
i'm seeing a doc folder, maybe something interesting in it !!!

or look at its forum on sourceforge

---

### Post by vrhahaha on 2011-08-19
There is a deb file for pyaudiere-0.2 which you can try first. You have to meet the dependency which is python2.5 (>=2.5.2) 
Look at this thread to install it since it is not included in the repository 
[http://ubuntuforums.org/showthread.php?t=1468661]("http://ubuntuforums.org/showthread.php?t=1468661")

If it doesn't work, I would resort to set setup.py to executable and run it from terminal.
1. open up terminal and change to the folder where you extracted the pyaudiere
2. chmod +x setup.py
3. ./setup.py

---

### Post by thelugnut on 2011-08-19
dino 99 - WTF?

vrhahaha
Couldn't get by step 3. "No file or directory..."
I appreciate your response.

---

### Post by vrhahaha on 2011-08-20
Have you tried the first method i mentioned which is trying to install the deb file?

---

