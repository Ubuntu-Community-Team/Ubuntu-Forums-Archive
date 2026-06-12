---
title: "Installing Opera"
date: 2006-04-26
forum: General Help
---

### Post by SolidSnake2 on 2006-04-26
I download the .tar version of Opera 8.5, and I cant figure out how to install it with my Linux noob skillz. Can anyone walk me through it?

---

### Post by aysiu on 2006-04-26
[https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)

---

### Post by CybaCowboy on 2006-05-10
I've followed the instructions at the link above, but I have troubles when I get up to the step that says:
[i]Open a terminal. Type:  
  sudo dpkg -i opera<Tab key>.deb
 **Note:** Tab completion can be a major help with long, complex filenames. Provided you're in the correct directory, just typing "opera" and then hitting the Tab key where it says <Tab key> in the above command should get Ubuntu to finish the filename for you. 
  Opera will take a minute to install.[/i]

 


 Here is *exactly* what I typed in Terminal (the -8.54-20060330.6-shared-qt.i386-en.tar.gz part was added automatically when I pressed Tab):
 *sudo dpkg -i opera-8.54-20060330.6-shared-qt.i386-en.tar.gz.deb*

 
And here's the *exact* error message I get:
[i]dpkg: error processing opera-8.54-20060330.6-shared-qt.i386-en.tar.gz.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 opera-8.54-20060330.6-shared-qt.i386-en.tar.gz.deb[/i]

 

 
I saved the file "/home/cowboy/opera-8.54-20060330.6-shared-qt.i386-en.tar.gz" to the "Home" folder...

---

### Post by barbarian on 2006-05-10
> Here is exactly what I typed in Terminal (the -8.54-20060330.6-shared-qt.i386-en.tar.gz part was added automatically when I pressed Tab):
sudo dpkg -i opera-8.54-20060330.6-shared-qt.i386-en.tar.gz.deb


Hei, you should better pick Ubuntu .deb package from official Opera website instead of .tar.gz i guess..

---

### Post by CybaCowboy on 2006-05-10
Never mind - I was installing the wrong file!

I was saving the file in "TAR.GZ" format instead of "Ubuntu 5.10 Breezy Badger"...


Anyway, I managed to get Opera installed, working and even assign a sexy icon! :KS

---

### Post by jonnymccullagh on 2006-05-10
I love Opera myself but I just installed using Automatix (it has Opera in its sources.list)
For information,
jonny

---

### Post by bigtwin on 2006-05-10
i am getting very frustrated trying to install this program (OPERA). i have tried using the method in the wiki linked above & get this error:

cookie@spare:~$ sudo dpkg -i opera-static_8.54-20060330.1-qt_en_i386.deb
Password:
dpkg: error processing opera-static_8.54-20060330.1-qt_en_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 opera-static_8.54-20060330.1-qt_en_i386.deb
cookie@spare:~$

the file is on the desktop.

i have searched this forum & google & tried other ideas i have found & all have failed.
what is automatix? sounds like it might do the job, but how do i get it/use it?

i also followed some instructions for apt-get. meaningless to a noob as most walkthroughs assume some knowledge of linux terminology. didn't work anyhow.

please could someone point me at a simple method that will work?

---

### Post by bigtwin on 2006-05-10
OK seems to have installed ok with automatix which i have found a guide for on these forums.

sorry for being a noob. would be nice to know why the terminal would not install the downloaded file on my desktop though.

---

### Post by gingermark on 2006-05-10
You have to navigate to where the file you want to install is. So, if your file was on the Desktop, you'd type "cd Desktop/" first.

(the error message does say "No such file or directory")

---

### Post by bigtwin on 2006-05-12
thanks. i thought it would be something simple :)

---

