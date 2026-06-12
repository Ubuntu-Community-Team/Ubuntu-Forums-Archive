---
title: "Havibg trouble setting up 'timekpr'"
date: 2012-01-03
forum: General Help
---

### Post by OxentroT on 2012-01-03
Hello, I am having some issues setting up 'timekpr'. I have a very sneaky kid that I need to limit his access on the computer while I am at work. I have downloaded all the necessary files, however, ```
./configure
``` directive doesn't seem to work for some reason. Neither does ```
install
``` command I have also ran ```
sudo make install 
``` but all that did was make a duplicate file of the included install.sh file. Here is a list of files contained in the folder extracted from the tarball.

```
a0n@NoVuM:~/Desktop/timkp/stable$ ls
artwork           etc         old         timekpr-client    timekpr.pot
CONTRIBUTORS.txt  gui         README.txt  timekprcommon.py  timekpr.py
COPYRIGHT.txt     install     setup.py    timekpr-gui       TODO.txt
debian            install.sh  testing     timekpr-gui.py
doc               locale      timekpr     timekprpam.py

```

Am I missing anything?


also: file source: [https://launchpad.net/timekpr](https://launchpad.net/timekpr)

thank you for any pointers!

---

### Post by jim_deadlock on 2012-01-03
Make sure install.sh is executable then do

```
sudo ./install.sh
```

---

### Post by OxentroT on 2012-02-17
Thankyou!

---

