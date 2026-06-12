---
title: "noob seeking help on software installation"
date: 2010-05-15
forum: General Help
---

### Post by trollger on 2010-05-15
I am switching from windows and am somewhat ignorant to Ubuntu

I am wondering were the folders are for the software that is installed from the software center. For example let's say I am running GIMP and I want to install a brush to the GIMP brush folder were would I find all the files for GIMP

also I would like to know where the files are for software that is installed from .deb packages. I install them and I cant find the files or where to run them. 

I am running Ubuntu 10.04 on virtual box (I don't know if it makes a difference:p)

---

### Post by parn on 2010-05-15
Unlike windows, applications are not installed in a specific folder like -> C:\Program Files\Application_Name. 

In general, you do not need to find those files. They are usually installed in /bin, /usr/bin, /usr/share. If you really want to find them, lets say gimp, you can type in a terminal: 
whereis gimp

After installing a program, you can usually find it in your Application menu.

In general, when you run an application, a folder will be created in your home folder and you can usually add to that folder. I do not use GIMP but when you run GIMP, a .gimp folder will be created in your home folder.

You need to type:
ls -a in a terminal to see that folder because it is hidden.

If you are using the GUI, simply hit CTRL+H to see the hidden folders.

Hope this helps.

---

### Post by trollger on 2010-05-15
very much so:mrgreen:

---

