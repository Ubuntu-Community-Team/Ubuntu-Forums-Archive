---
title: "Help compiling myunity w/ gambas??"
date: 2012-03-11
forum: General Help
---

### Post by miasmablk on 2012-03-11
OK so im stuck i don't see a configure file, (tried it anyways though)

```
richard@richard-Inspiron-1545:~/myunity-3.1.0$ ls
authors-11.04.txt  img               MQuicklist.module
authors-11.10.txt  INSTALL.rst       MThemes.module
authors-12.04.txt  Main.module       myunity
CHANGELOG          Makefile          myunity.1
COPYING            MDash.module      myunity.desktop
FMain.class        MDesktop.module   myunity.png
FMain.form         MFont.module      RestoreDefault.module
FMessage.class     MLauncher.module
FMessage.form      MPanel.module
richard@richard-Inspiron-1545:~/myunity-3.1.0$ 
```then move on to the "make" command and it keeps giving me this

```
sudo make
gbc2 -a -t -p .
/home/richard/myunity-3.1.0/FMain.class:1485: Unknown identifier: PictureBox
make: *** [build] Error 1

```also tried 

```
sudo gbc2 -a make
``` 

```
sudo gbc2 -a make
/home/richard/myunity-3.1.0/FMain.class:1485: Unknown identifier: PictureBox
```
and got this

what am i doing wrong?

---

### Post by miasmablk on 2012-03-11
bump

---

### Post by miasmablk on 2012-03-12
bump..?

---

### Post by Pixel_it on 2012-03-13
if you see into the INSTALL.rst:

COMPILATION
-----------
Simply type:
``make``
to compile MyUnity. Configuration step is not needed before compiling.


INSTALLATION
------------
After compilation, you can run the command:
``myunity``
to start the program.
If you wish to install the program in a system-wide directory, run:

``make install``

This will install in /usr/local by default. You can override the installation directory setting the $PREFIX variabile before launching make install.

Regards

---

### Post by miasmablk on 2012-03-13
how do i see into the INSTALL.rst file?

please forgive me as i am at school at the moment.

can i use nano or gedit for this? or do i just cd to it?

---

### Post by Pixel_it on 2012-03-14
gedit, nano what you want :)
the file contains installation instructions.

---

### Post by miasmablk on 2012-03-15
```
sudo nano INSTALL.rst
``` 

revealed that a PPA was available.

thanks for the help man :)

marking as solved

---

