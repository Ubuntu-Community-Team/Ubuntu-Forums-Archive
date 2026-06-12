---
title: "Ubuntu 9.10 64 bit Lightscribe Installation"
date: 2009-12-09
forum: General Help
---

### Post by Serdar on 2009-12-09
go to [www.lightscribe.com](www.lightscribe.com) and download or click links below 

save them to your home folder!!!

[LIGHTSCRIBE SYSTEM SOFTWARE]("http://download.lightscribe.com/ls/lightscribe-1.18.10.2-linux-2.6-intel.deb")
[LIGHTSCRIBE SIMPLE LABELER]("http://download.lightscribe.com/ls/lightscribeApplications-1.18.6.1-linux-2.6-intel.deb")

---------------------------------------------------------------------------
---------------------------------
first add the 32 bit libraries
sudo apt-get install ia32-libs
--------------------------------

then to install

open terminal (version numbers might be different)

sudo dpkg -i --force architecture lightscribe-1.18.10.2-linux-2.6-intel.deb       

sudo dpkg -i --force architecture lightscribeApplications-1.18.6.1-linux-2.6-intel.deb

sudo ln -s /usr/lib/liblightscribe.so.1 /usr/lib32/

sudo ln -s /usr/lib/liblightscribe.so /usr/lib32/

sudo ldconfig

-----------------------------------------------------------
option to print darker labels
sudo /usr/lib/lightscribe/elcu.sh
-----------------------------------------------------------
Creating a shortcut

sudo nautilus

copy lightscribe.png to 

/usr/share/icons/hicolor/scalable/apps

then go to 

System > Preferences > Main Menu
(New Item)

Type
Application

Icon
/usr/share/icons/hicolor/scalable/apps/lightscribe.png

Name
Lightscribe Simple Labeler

Command
'/opt/lightscribeApplications/SimpleLabeler/SimpleLabeler' 
Using /etc/lightscribe.rc

Worked for me, any ideas would be nice to make this process shorter.

---

### Post by spiranha on 2010-01-15
Great.

I've Lightscribe installed and it works like this way... 
 Many thanks to Serdar. I've made a copy of the Lightscribe-icon in the terminal.
It's another way, but did the same like nautilus....

Info for all...
When there is an German Installationguide needed, please contact me...
There are sometimes user who needs a handout in German language. Let me know...

;) greetz spiranha

---

### Post by 00czar00 on 2010-12-11
Do you still have to install it on ubuntustudio??? cuz some packages come on studio like encrypted dvd... can't find if it does come on it...

---

### Post by oregonbob on 2011-05-26
Your recipe worked great for me on Natty 11.04. Thanks!

---

### Post by Nightcrawlers on 2011-09-06
I just installed Natty 64 bit and I am still a noob with Ubuntu...BUT....I managed to follow your instructions and it works perfectly!  Thanks!  :guitar:

> **Serdar said:**
> go to [www.lightscribe.com](www.lightscribe.com) and download or click links below 

save them to your home folder!!!

[LIGHTSCRIBE SYSTEM SOFTWARE]("http://download.lightscribe.com/ls/lightscribe-1.18.10.2-linux-2.6-intel.deb")
[LIGHTSCRIBE SIMPLE LABELER]("http://download.lightscribe.com/ls/lightscribeApplications-1.18.6.1-linux-2.6-intel.deb")

---------------------------------------------------------------------------
---------------------------------
first add the 32 bit libraries
sudo apt-get install ia32-libs
--------------------------------

then to install

open terminal (version numbers might be different)

sudo dpkg -i --force architecture lightscribe-1.18.10.2-linux-2.6-intel.deb       

sudo dpkg -i --force architecture lightscribeApplications-1.18.6.1-linux-2.6-intel.deb

sudo ln -s /usr/lib/liblightscribe.so.1 /usr/lib32/

sudo ln -s /usr/lib/liblightscribe.so /usr/lib32/

sudo ldconfig

-----------------------------------------------------------
option to print darker labels
sudo /usr/lib/lightscribe/elcu.sh
-----------------------------------------------------------
Creating a shortcut

sudo nautilus

copy lightscribe.png to 

/usr/share/icons/hicolor/scalable/apps

then go to 

System > Preferences > Main Menu
(New Item)

Type
Application

Icon
/usr/share/icons/hicolor/scalable/apps/lightscribe.png

Name
Lightscribe Simple Labeler

Command
'/opt/lightscribeApplications/SimpleLabeler/SimpleLabeler' 
Using /etc/lightscribe.rc

Worked for me, any ideas would be nice to make this process shorter.

---

