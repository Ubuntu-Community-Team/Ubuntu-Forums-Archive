---
title: "How do I make a terminal command run by clicking an icon?"
date: 2010-08-22
forum: General Help
---

### Post by nigh3252 on 2010-08-22
Hi all!  I have my xbox 360 connected to my laptop running Ubuntu 10.04 using the Ushare program.  In order to reset Ushare and have it send any new files I have to the 360, I have to go into the terminal and enter 
sudo /etc/init.d/ushare stop
sudo /etc/init.d/ushare start
sudo /etc/init.d/ushare start

Is there a way I can have an icon in my panel/toolbar thing at the top of the screen that will run this command string automatically?  I'm getting tired of having to enter the whole thing by hand every time.  Thanks!

---

### Post by PaulReaver on 2010-08-22
in a terminal paste this

gedit ~/.360.sh

paste this into the gedit that opens

#! /bin/sh
sudo /etc/init.d/ushare stop
sudo /etc/init.d/ushare start
sudo /etc/init.d/ushare start
fi

then save it



paste this into a terminal

chmod +x ~/.360.sh

paste this into a terminal

gedit ~/Desktop/360.desktop

then paste this into the gedit that opens

#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=~/.360.sh
Name=ushare 360
Icon=notification-network-ethernet-connected

and save it

hope it helps

---

### Post by spcwingo on 2010-08-22
Just my $0.02, but instead of sudo I would use gksudo so you could enter your sudo password (note: if you're using the KDE environment it would be kdesudo instead).

---

### Post by nigh3252 on 2010-08-22
It worked!  Thanks to both of you!  To get it to work for myself, I changed the "sudo" commands to "gksudo" in the first .sh file.  I also had to change the ~/ to the full path to my login folder (/home/*my login name/) in the 360.desktop file, then finally I had to right click on the desktop icon, go to properties->permissions then click "allow executing file as program".  Once I did that, it worked like a charm!  (no sarcasm meant, i've spent a year goofing around trying to make this work before asking, and it's seemed impossible).  Thanks again!

---

### Post by PaulReaver on 2010-08-22
you figured out half of it yourself anyway but, no problem, any time.

---

### Post by spcwingo on 2010-08-22
I'm glad that you got it going, bro.  Happy Ubuntuing!  :)

---

