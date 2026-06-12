---
title: "i need some help on Linux  and Unix"
date: 2006-04-14
forum: General Help
---

### Post by animae on 2006-04-14
hello guys! i m new here and so i am in using linux OS. :D 
so i have some difficulties in getting used to it. first of all, i don't now how to use commands and ofcourse the correct structure of a command. so, do you know where to find any good .pdf books about linux in general and about learning how to use the unix commands? 

the other problem that i have is: linux doesn't recognise my wifi. i have a pci wifi card : LevelOne WNC-0301 11g. do you know if there are any drivers for this one?

i have searched for both things that i asked, but i didn't find something that could help me. 

i hope i m on the right section.if not, sorry:rolleyes: 

thanx in advance!

---

### Post by ubernoob on 2006-04-14
The one page linux manual is a good start: [http://homepage.powerup.com.au/~squadron/linux_manual.pdf](http://homepage.powerup.com.au/~squadron/linux_manual.pdf)

---

### Post by truNWA on 2006-04-14
well the easy way to install wifi (and the way i did it) is install automatrix and let it do that for you. You will need the windows drivers though.


Search this site for automatrix

---

### Post by taurus on 2006-04-14
[QUOTE=truNWA]
Search this site for automatrix[/QUOTE]
Automatix is right here, [http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295)...  ;)

---

### Post by animae on 2006-04-14
[QUOTE=truNWA]well the easy way to install wifi (and the way i did it) is install automatrix and let it do that for you. You will need the windows drivers though.


Search this site for automatrix[/QUOTE]

hope this one works! on the other hand if this installation requires the use of command line, then i guess that i cannot do it because i don't know how to use them (the commands-which command should i use and how do i write it).

thanx everyone!

---

### Post by Monster_user on 2006-04-14
[quote=NDISWRAPPER - Wiki]ard: LevelOne WNC-0301

    * pciid: 11ab:1fa6 subsys: 16ab:1fa6
    * Chipset: Marvell Libertas
    * Driver: from CD that comes with the card, version 2.3.0.3
    * Other:#*Driver for use with ndiswrapper is prepackaged in Ark Linux -- Ark Linux users simply "apt-get install driver-marvell". [/quote]

It is on the compatibility list for NdisWrapper. It a small program that uses Windows' WiFi drivers, for Linux. It says just use the ones on the CD.

---

### Post by Zimmer on 2006-04-14
[http://tille.xalasys.com/training/tldp/ch02s02.html](http://tille.xalasys.com/training/tldp/ch02s02.html)
Good start for the basics...
..and the tuxfiles link in my signature is good, too.

---

### Post by animae on 2006-04-14
[QUOTE=Monster_user] It a small program that uses Windows' WiFi drivers, for Linux. It says just use the ones on the CD.[/QUOTE]


i ve searched the drivers' cd of levelone, but it only has win drivers.

ps: i m trying to find a link to dl Automatix in here [http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405) , but i can't find one...

---

### Post by Monster_user on 2006-04-14
Use the WIN drivers with ndiswrapper, to get your wireless card to work

NdisGTK should help you get it to work.
[http://users.on.net/~spohlenz/ubuntu/ndisgtk_0.4-1_all.deb](http://users.on.net/~spohlenz/ubuntu/ndisgtk_0.4-1_all.deb)
[http://ubuntuforums.org/showthread.php?t=50607](http://ubuntuforums.org/showthread.php?t=50607)

> PLEASE DO NOT INSTALL (24) IF YOU ARE IN THE UNITED STATES OF AMERICA. IT IS ILLEGAL TO DO SO.

Installation Instructions:

To install Automatix in Ubuntu do the following from terminal(one line at a time, pressing enter after each step):
Code:

wget [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb) 

sudo dpkg -i automatix_5.7-3_i386.deb

There are the instructions for installing Automatix.

1. Open a Terminal. Click on the Applications Menu, and then Accessories. Select "Terminal.

2. Use wget to download the Deb file

3. use sudo dpkg to install the Deb file. Alternatively, browse to your home folder, and double-click the Automatix DEB file.

---

### Post by animae on 2006-04-14
thank you monster_user! i ll try it sometime tomorrow and i ll tell if i can handle it!

thank you all for your help!

---

### Post by Anilkumar on 2006-04-15
u just need to edit u r repositries . you will find repostries in synoptic package manger.this is to update the packages in ubuntu.Now just go there from system->adminstration->synaptic pakage manager>then u go to settings, repostries .Then u will find a window with all repostries.This will show the important updates.

This is some part of information>i will continue on reply..

make free open source more free .

anil

---

### Post by haffy on 2007-01-31
> **Anilkumar said:**
> u just need to edit u r repositries . you will find repostries in synoptic package manger.this is to update the packages in ubuntu.Now just go there from system->adminstration->synaptic pakage manager>then u go to settings, repostries .Then u will find a window with all repostries.This will show the important updates.

This is some part of information>i will continue on reply..

make free open source more free .

anil


PLS! Explain to me.
I am using Ubuntu Server, if there is a problem I can change to desktop. 
But is there a way to fix my WNC-0301 card? I need wlan at my server.

---

### Post by Monster_user on 2007-03-18
Did you ever get it to work?

I don't know much about Ubuntu Server, but try a few commands from a console, to see what will work.

synaptic

That will load the Ubuntu package manager, if it is installed. 

ndiswrapper -l (" L" lower case)

That will check to see if there are any NDISwrapper drivers loaded. Then you just have to download the drivers, and use "ndiswrapper -i *driverfile.inf*" to load the Windows NDIS drivers.

---

