---
title: "nvdia drivers in ubuntu 9.10"
date: 2009-12-05
forum: General Help
---

### Post by Roone on 2009-12-05
OK, i am completely lost (and new at Linux)
i am trying to play games using wine, when they launch the graphics are messed up.  so i assume i need to upgrade my divers [i have an nvdia geforce 9600gt-oc wit 512Mb of gddr3 memory] but every time i try to install the drivers it tells me i need a kernel interface matching my kernel version [or something to that effect]

please help 

p.s. i´m running Ubuntu 9.10

edit:crap misspelled the title

---

### Post by wd5gnr on 2009-12-05
Try this thread: [http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+driver](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+driver)

You do need to completely get out of X before installing this. That thread explains it all.

---

### Post by Roone on 2009-12-05
i have gotten out of x, i still need some kernel interface thingy...

---

### Post by Roone on 2009-12-05
oh by the way the game im attemting to play-fornow-is perfect world international (a free MMO for those who havent heard of it)

---

### Post by RedSingularity on 2009-12-05
Look in system>admin>hardware drivers and make sure the driver is active.

---

### Post by fluffman86 on 2009-12-05
System > Administration > Hardware Drivers?
edit: bah, RedSingularity beat me by less than a minute. :P

---

### Post by Roone on 2009-12-05
so if that is on my NEW driver will install?

---

### Post by fluffman86 on 2009-12-05
no, if that is on, it *IS* your new driver.  You don't need to go and compile one from scratch after you install that one.

---

### Post by Roone on 2009-12-05
so then, why are the models in game messing up?

---

### Post by fluffman86 on 2009-12-05
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9923&iTestingId=46209](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9923&iTestingId=46209)

There are some issues with that game.  Wine isn't perfect.  Google for the name of the game + wine and you may come up with some workarounds.  I don't know about this game, but Amazon Kindle for PC works perfectly in wine, as long as you set wine to emulate Windows 98.  It won't work with anything else.  Maybe there's some configuration that you need to set with this game.

---

### Post by Roone on 2009-12-05
ok so it works now-for the most part
i have had my screen go completely black but the computer is still on...
can that be fixed through software or is it a hardware issue only?

---

### Post by RedSingularity on 2009-12-06
Some games dont work so well with wine.  You can check on [http://appdb.winehq.org/](http://appdb.winehq.org/) for your game.

---

### Post by Roone on 2009-12-06
wines is on that list, but the video is with ubuntu 8.04, i use ubuntu 9.10 i really dont understand why it wouldnt work

---

### Post by RedSingularity on 2009-12-06
Someone may have not updated the list with that game for Ubuntu 9.10 and thats why it wont give you the 9.10 stats for that game.

---

### Post by Roone on 2009-12-06
so does anyone happen to know proper settings for PWI in ubuntu 9.10?

---

### Post by jcm2302 on 2009-12-06
i have a similar problem i belive to be a graphics issue maby not i can change to motherboard graphics in bios and boot fine but when i try to download the drivers for my nvidia geforce 8400 gs my distro crashes ive come out of x ant loaded ive used both nvidia and provided drivers from ubuntu 9.10 i hava an asus p4p800mx mobo 2.5 g ram pent 4 ht 3.0 ghz cpu 500 gb wd sata drive ant two ide drives for backup one for music and pics and one for programs when i boot back in i get a flashing screen asking me to sign in and it wont let me after re install for the 10th time i am stuck using onboard graphics and a third monitor to use any linux distro same happens for mint8 7 or 6 ubuntu 9.1 or 9.04 ive tried all the usual post and i am lost ive tried all of the bios settings one at a time at no avail also if it helps when i try to boot a fresh distro from nvidia screens i get the attached screen

---

### Post by Roone on 2009-12-06
well crap, 
i did get the game running fine, but menus and icons are weird, the models are fine

could it be that i need direct x [from winetricks?] if so what version would be best [again im using ubuntu 9.10]

---

### Post by Roone on 2009-12-06
apparantly i need to turn off S3TC in wine how do i do that in wine version 1.0.1 ?

---

### Post by Roone on 2009-12-06
think i have it working...we will see, if it worls i will link to what helped

---

### Post by Roone on 2009-12-06
nope still cant manage the s3ct hack

---

### Post by Roone on 2009-12-06
i feel stupid i simply needed a wine update

for those who have the same problem

sudo apt-get update && sudo apt-get dist-upgrade

---

