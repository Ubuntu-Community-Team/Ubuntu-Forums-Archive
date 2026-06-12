---
title: "Grub ubuntu 9.04 installation through windows"
date: 2009-07-30
forum: General Help
---

### Post by smvenkat on 2009-07-30
firstly i hav xp in primary drive then i installed ubuntu 8.10 from windows through live cd. i hav upgraded ubuntu 8.10 to 9.04 and used for abt a month. all went cool. Recently i got a problem with windows and formatted it. now i cant get the ubuntu(no grub), i know that the grub will not be there. i hav tried by live cd but can get the solution. Can any one help me out. I have saved many of my important files in the ubuntu, can any one plz help me out

---

### Post by philcamlin on 2009-07-30
if you want the liuve cd this is what you want to do 

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

 	Code:
 	sudo grub 
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

 	Code:
 	find /boot/grub/stage1 
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

 	Code:
 	root (hd?,?) 
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

 	Code:
 	setup (hd0) 
Finally exit the grub shell
 	Code:
 	quit 
That is it. Grub will be installed to the mbr.

---

### Post by michy99 on 2009-07-30
> **philcamlin said:**
> if you want the liuve cd this is what you want to do 

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

 	Code:
 	sudo grub 
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

 	Code:
 	find /boot/grub/stage1 
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

 	Code:
 	root (hd?,?) 
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

 	Code:
 	setup (hd0) 
Finally exit the grub shell
 	Code:
 	quit 
That is it. Grub will be installed to the mbr.

But will this work for a Wubi installation? I believe that is what the OP has.

---

### Post by smvenkat on 2009-07-31
its showing that file not found.... i hav tried this in listing but cant find the solution...

---

### Post by louieb on 2009-07-31
> **smvenkat said:**
> ..i installed ubuntu 8.10 from windows through live cd... 

Sound like a WUBI install. Since that is an inside windows install - when you formated windows you may have wiped Ubuntu out too. See if this helps.
[WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide")

---

