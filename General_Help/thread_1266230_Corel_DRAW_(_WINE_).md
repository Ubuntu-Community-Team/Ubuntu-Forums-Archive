---
title: "Corel DRAW ( WINE )"
date: 2009-09-14
forum: General Help
---

### Post by C_Bomb on 2009-09-14
[B]Hey Guys,

I'm a graphic designer and I use Corel Draw13 a lot...

So I downloaded the latest version of WINE to install windows software.
Corel Draw 13 installs perfectly, but when I run the application (corel draw)

It gives me a lot of registry error messages and then it closes....

How can I fix this?

Thanks..
[/B]
*Ps...it amazes me how you guys know so much about Linux...*

---

### Post by NoaHall on 2009-09-14
What kind of messages? Have you used wine tricks to install extra things?

Accourding to this page -> [http://appdb.winehq.org/objectManager.php?sClass=version&iId=1840&iTestingId=39782](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1840&iTestingId=39782) 
It should run fine on the latest wine build and on 9.04. However, there are problems on the older versions of Ubuntu which match your description.


Try this ->

Before installing copy MCSetup.dll and SWCustEN.dll to your system32 folder and start setup. After it installs create profiles for CorelDrw.exe, CorelPP.exe, Rave.exe and do liboverride:

[AppDefaults\\\\.exe\\\\DllOverrides] 
\"wintab32\" = \"native\"

---

### Post by P4man on 2009-09-14
Have you tried Inkscape?
If you're used to coreldraw (like me ages ago, until version 8 or so lol), you'll feel at home quite quickly. Its in the add/remove programs applet, and its quite good imho.

---

### Post by C_Bomb on 2009-09-15
[B]Hey guys,

Yeah I installed the newest version of Wine..

I'll try and give the correct errors, I'm at work now, So i'll try to remember..

...something IU Language errors....and ends with Runtime error C++...

Maybe if I install the older version of Wine?[/B]

Thanks for the comments.

---

### Post by NoaHall on 2009-09-15
Then use a script called wine tricks to download and install c++ runtime. It's probably 2005 you want, but it could be the 2008 version.

---

### Post by C_Bomb on 2009-09-28
why when I try to copy the DLL files into the system32, it tells me that I don't have permission to do that.

how can I gain permission?

---

### Post by C_Bomb on 2009-10-11
> **NoaHall said:**
> What kind of messages? Have you used wine tricks to install extra things?

Accourding to this page -> [http://appdb.winehq.org/objectManager.php?sClass=version&iId=1840&iTestingId=39782](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1840&iTestingId=39782) 
It should run fine on the latest wine build and on 9.04. However, there are problems on the older versions of Ubuntu which match your description.


Try this ->

Before installing copy MCSetup.dll and SWCustEN.dll to your system32 folder and start setup. After it installs create profiles for CorelDrw.exe, CorelPP.exe, Rave.exe and do liboverride:

[AppDefaults\\\\.exe\\\\DllOverrides] 
\"wintab32\" = \"native\"


How do I create profiles?

---

