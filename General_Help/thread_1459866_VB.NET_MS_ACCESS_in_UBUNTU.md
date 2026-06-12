---
title: "VB.NET MS ACCESS in UBUNTU"
date: 2010-04-22
forum: General Help
---

### Post by rameses19 on 2010-04-22
Good day all

i am currently using ubuntu 9.10 - the Karmic Koala

i have a .net application written in VB which uses a shared backend MS ACCESS database saved in an NT machine

im done with installing mdac
wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
sh winetricks fakeie6 mdac28

and also done with installing jet 4.0
wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
sh winetricks fakeie6 jet40

my problem is when I start the application using wine, it throws an exception that the .mdb path is not valid

this is the datasource of my oleddb connection

data source = "\\server\database\MAIN.mdb"

this .net application successfully works in an XP, Vista or W7 machine.

I am having a hard time to figure out this problem

---

### Post by clhsharky on 2010-04-22
HI 

Not meaning to be mean but

Windows apps in windows

Linux apps in linux

Wine would be who I ask, there the ones your using to mis match,
apps & OS.

Sharky

---

