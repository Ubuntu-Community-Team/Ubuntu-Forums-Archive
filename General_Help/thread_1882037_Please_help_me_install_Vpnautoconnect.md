---
title: "Please help me install Vpnautoconnect"
date: 2011-11-16
forum: General Help
---

### Post by joalin on 2011-11-16
Hi, i hope someone can help me with this, hopefully easy problem. I've  been using Ubuntu for quite a while now, but I never really understood  how to install programs without having an instruction, or by automatic,  like synaptics.

I'm trying to install vpnautoconnect, but can't fine any instruction. I  have downloaded the compressed file, and extracted it, an I now have a  vpnautoconnect folder in my home folder, but in there it's just a bunch  of files, including an install script, but i have no clue how to run it.  I tried some commands in the terminal, like getting in the right  directory and make install and such but i just get errors. Hope someone  knows how to guide me,

If you know how to install, please guide me with a step by step guide. I really googled alot, and tried to solve it myself but without luck.  

An administrator might delete my other post in the install category since those issues seemd to be just handling Ubuntu installs.

---

### Post by gandaran on 2011-11-16
does the package have a readme file with instructions?
also post the errors you get trying to install.

---

### Post by joalin on 2011-11-17
yes, the readme file  says this, which I dont understand at all:

HOW TO BUILD AN EXECUTABLE FOR YOUR SYSTEM
Install the libdbus-glib-1-dev package
#aptitude install libdbus-glib-1-dev libgtk2.0-dev libnotify-dev
The command 
    make 
Make the executable.
To make the configuration
    make config
Select your vpn configuration and your connection support (the connection used to connect the vpn)
And install it with
    sudo make install


I managed to install the libdbus package I think, since it had the exact command, but I dont get what to do with "make", since it's not a full command...

---

### Post by autonym on 2011-11-17
Hi joalin!

vpnautoconnect have just come out with a .deb package for Oneiric (happy times), so you are in luck. Just go to this website to download ("save file") the package;

[http://sourceforge.net/projects/vpnautoconnect/files/vpnautoconnect_1.2.1-ubuntu1_i386%28Ubuntu_11.10_Only%29.deb/download](http://sourceforge.net/projects/vpnautoconnect/files/vpnautoconnect_1.2.1-ubuntu1_i386%28Ubuntu_11.10_Only%29.deb/download)

Then you open the package with Ubuntu software center and voila!

You can follow the process of vpnautoconnect through this website;

[http://twitter.com/#!/vpnautoconnect](http://twitter.com/#!/vpnautoconnect)

---

### Post by joalin on 2011-11-18
Thanks Autonym! I managed to do it with the deb, so easy then :-)

---

### Post by joalin on 2011-11-22
Still some issues:

 seem to have Vpnautoconnect installed, but it doesnt seem to run.

I can find it under installed programs, but when i run it nothing happens, and I get no icon in the activity field.

I cant find it in the active processes either. What can I do to get further?

---

