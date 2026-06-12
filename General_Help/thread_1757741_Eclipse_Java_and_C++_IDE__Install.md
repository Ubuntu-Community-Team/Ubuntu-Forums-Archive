---
title: "Eclipse Java and C++ IDE  Install?"
date: 2011-05-13
forum: General Help
---

### Post by Gr72 on 2011-05-13
ok, so I need help installing eclipse for Java and C++ IDE. I'm a partial newb coming from Windows and in windows I used JCreator but I now JCreator doesn't have a linux install. So I was going to use Eclipse but I don't know to actually install it. I've already downloaded the tar.bz for the java IDE. Can anyone help in installation? please. I will also need to know the installation for the C++ Ide because I want to start programming with c++. Thank you all!!!!

---

### Post by GregBrannon on 2011-05-13
Uncompress the file you've downloaded to a folder over which you have complete control and access, usually a folder under root/home/username/.  In the root folder of your destination will be an executable file called 'eclipse', or 'Eclipse", create a shortcut to that file, place the shortcut on your desktop or add it to your start menu, and you're done.  Have you installed the JDK and the build-essential packages?  For the build-essential, type the following at a command line:

```
sudo apt-get install build-essential
```

Generally, installing software in Ubuntu is done from the Ubuntu Software Center.  Look there for the JDK to determine if it has already been installed.  Install it if it hasn't already been installed.

---

### Post by oklokl on 2011-05-13
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)
```
sudo apt-get -y install build-essential git-core checkinstall automake yasm codeblocks wx-common libwxgtk2.8-dev codeblocks-contrib gdb
```/usr/bin/update-manager -> Canonical 
```
sudo apt-get install sun-java6-jdk[COLOR=#0900FF][FONT=Gulim]

[/FONT][/COLOR]
```

---

