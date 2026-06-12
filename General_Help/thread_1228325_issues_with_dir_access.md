---
title: "issues with dir access"
date: 2009-07-31
forum: General Help
---

### Post by stlsaint on 2009-07-31
everytime i make a dir thru terminal i get error saying cant access or dont have permissions whenever i try and run something from within that terminal...maybe im using a wrong command or something?!!

---

### Post by TeoBigusGeekus on 2009-07-31
Depends on where you want to make that directory. 
In Ubuntu you can only access freely your /home partition. To perform any changes anywhere else, you have to have root (administrator) privileges.
If you know what you're doing, precede your command with sudo (super user do), give your password and you're done.

---

### Post by credobyte on 2009-07-31
Everything outside your home directory is owned by root - use *sudo* !

---

### Post by MaxIBoy on 2009-07-31
...and if you encounter something for which you need root access, *make sure you know what it is and what it's for* before you mess with it!

---

### Post by stlsaint on 2009-07-31
thank you all for your replys but still a problem...of course i make all dir in home folder but i still get error when trying to access them...for example...i donwload software from net then mkdir "software" and then i put the software inside the "software" dir and then cd "software" then sudo make install!!! all from inside the terminal and i get cannot access software!

---

### Post by credobyte on 2009-07-31
> **stlsaint said:**
> thank you all for your replys but still a problem...of course i make all dir in home folder but i still get error when trying to access them...for example...i donwload software from net then mkdir "software" and then i put the software inside the "software" dir and then cd "software" then sudo make install!!! all from inside the terminal and i get cannot access software!

```
mkdir software && cd software
```
It simply can't fail. If you can create a directory, you can cd to it ( even delete it ). Can you do all the process again and show us the copy of your terminal window ( what you typed, what you got, etc. ) ?

---

### Post by TeoBigusGeekus on 2009-07-31
Could you post us your exact steps and commands?

---

### Post by stlsaint on 2009-07-31
> **TeoBigusGeekus said:**
> Could you post us your exact steps and commands?


here is what i do...

stlsaint@stlsaint-laptop:~$ ls
amsn_received         Desktop    download  Music     pidgin.gpg  Templates
CS_MinInstaller_5_13  Documents  Gnomenu   Pictures  Public      Videos
stlsaint@stlsaint-laptop:~$ cd CS_MinInstaller_5_13
stlsaint@stlsaint-laptop:~/CS_MinInstaller_5_13$ sudo java -jar ChurchSoftware_Installer_v4_5.jar
[sudo] password for stlsaint: 
Unable to access jarfile ChurchSoftware_Installer_v4_5.jar
stlsaint@stlsaint-laptop:~/CS_MinInstaller_5_13$

---

### Post by credobyte on 2009-07-31
```
cd $HOME/CS_MinInstaller_5_13 && ls -l

```

Show us what you got there.

---

### Post by stlsaint on 2009-07-31
> **credobyte said:**
> ```
cd $HOME/CS_MinInstaller_5_13 && ls -l

```

Show us what you got there.


heres what i get...


stlsaint@stlsaint-laptop:~/CS_MinInstaller_5_13$ cd $HOME/CS_MinInstaller_5_13 && ls -l
total 134860
-rw-r--r-- 1 stlsaint stlsaint 137956231 2009-07-30 22:53 CS_MinInstaller_5_13.jar
stlsaint@stlsaint-laptop:~/CS_MinInstaller_5_13$

---

### Post by stlsaint on 2009-07-31
any assistance please!!

---

### Post by TeoBigusGeekus on 2009-08-01
> **stlsaint said:**
> here is what i do...

stlsaint@stlsaint-laptop:~$ ls
amsn_received         Desktop    download  Music     pidgin.gpg  Templates
CS_MinInstaller_5_13  Documents  Gnomenu   Pictures  Public      Videos
stlsaint@stlsaint-laptop:~$ cd CS_MinInstaller_5_13
stlsaint@stlsaint-laptop:~/CS_MinInstaller_5_13$ sudo java -jar ChurchSoftware_Installer_v4_5.jar
[sudo] password for stlsaint: 
Unable to access jarfile ChurchSoftware_Installer_v4_5.jar
stlsaint@stlsaint-laptop:~/CS_MinInstaller_5_13$
Thats because you don't have a file named ChurchSoftware_Installer_v4_5.jar in the directory.
The only file that exists there is the CS_MinInstaller_5_13.jar file as the ls command shows you. 
Try
```
sudo java -jar CS_MinInstaller_5_13.jar
```

---

### Post by stlsaint on 2009-08-01
heres what i get from above said code...


stlsaint@stlsaint-laptop:~$ sudo java -jar CS_MinInstaller_5_13.jar
[sudo] password for stlsaint: 
Unable to access jarfile CS_MinInstaller_5_13.jar
stlsaint@stlsaint-laptop:~$

---

### Post by credobyte on 2009-08-01
Can't you just right click on *Open With* and select Java ? :confused:

---

### Post by stlsaint on 2009-08-01
:P...i have a whole other thread just on dealing with opening this jar with java...its insane what im going thru...the program is trying to open a file and install it without even having it!! yea its crazy right now!!

---

### Post by TeoBigusGeekus on 2009-08-01
Of course you can't open it - you're not in it's directory.
```
cd CS_MinInstaller_5_13
```
and then
```
sudo java -jar CS_MinInstaller_5_13.jar
```

---

