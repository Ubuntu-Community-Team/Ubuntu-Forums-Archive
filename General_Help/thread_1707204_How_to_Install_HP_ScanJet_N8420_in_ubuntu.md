---
title: "How to Install HP ScanJet N8420 in ubuntu"
date: 2011-03-15
forum: General Help
---

### Post by imtiaz.ahmad on 2011-03-15
Hi,
i m relative new for ubuntu as a technical user, and i m facing problem in installing HP Scanjet N8420, i searched many forums but i m unable to get success on it,
is there any one who can help me on this, i already tried the given code below it works for Canon scanner lide 110, but doesn't works for HP ScanJet N8420.

$ sudo add-apt-repository ppa:plaxx/random-fixes
$ sudo apt-get update
$ sudo apt-get install libsane sane-utils

Thanks in advance.

---

### Post by nickleboyblue on 2011-03-15
I don't see anything on that printer, which either means very few people have it, or very few people have problems with it.  So, what exactly is the problem?  Is it printing but not scanning?

In order to install a new printer, you should first click on system->administration->printing (the menus hierarchy) and click the add button in the window that pops up.  If the printer is connected to the computer by USB cable, it should be easy to find it in that dialog.

If the printer is a network printer, first make sure it's connected to your router (wirelessly or otherwise).  Once you know it's connected, again, open the same printing dialog and add a new printer.  In the add dialog, there is a tree to the left.  Click on network printers, and wait for maybe a minute.  If your printer doesn't show up in a selectable list automagically, you should search for it's ip address.

---

### Post by imtiaz.ahmad on 2011-03-15
Its a scanner not printer...
i have link for it you can visit it ... it may clear it you in helping me...
 
[http://www.youtube.com/watch?v=XHlcDshTpw4](http://www.youtube.com/watch?v=XHlcDshTpw4)

thanks for your response.

---

### Post by limitcrosser on 2011-03-18
I think it can be done by installing its windows software/driver through wine...I'll experiment it with you at office...

---

