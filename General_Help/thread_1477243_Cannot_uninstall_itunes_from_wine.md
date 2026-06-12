---
title: "Cannot uninstall itunes from wine"
date: 2010-05-08
forum: General Help
---

### Post by albanee on 2010-05-08
hi i am using linux ubuntu 9.10 i installed wine and installed linux using these steps 
[http://www.ehow.com/how_5197743_download-itunes-linux-ubuntu.html](http://www.ehow.com/how_5197743_download-itunes-linux-ubuntu.html)
however in step 8 i clicked on yes instead of no. not the itunes dont work neither will it go out of wine when i click or uninstall it stops at a certain places and stops responding.
someone please help me i need to sync my iphone

---

### Post by albanee on 2010-05-15
Seriously it has been one week, no one really knows ????

---

### Post by emarkay on 2010-05-15
Curious too - oh no I don't use that rubbish, but my GF does...  :)  
Got to get her "Away from the Window!"

---

### Post by polarops on 2010-07-16
I've been around unix a little, but this is first time using wine. Possibly it's a bug. I used the wine application itself to try to uninstall itunes, which launches the itunes installer/uninstaller. This goes through the process, looking like it is uninstalling, but ultimately does not. Is this the same problem you are having?
So looks like we might actually have to uninstall wine in order to uninstall iTunes, unless somebody else has another idea.
Also, I noticed that the files are stored in ~/.wine ....

---

### Post by Mark Phelps on 2010-07-17
If you'd bothereed to check the WineHQ site (linked below) or do a forum search on iTunes, you would have found out that it basically does not work in Wine:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347")

Garbage rating means it won't work, not matter what you do; Bronze means it barely works and is nearly useless.

---

### Post by inameiname on 2010-07-17
It's happen to me as well. Basically just delete the itunes folder(s) under your /home/me/.wine/drive_c folder and delete whatever was left in the tmp folder and that's about all I can see you can do. You may have to edit the program menu and remove the folder there to if the uninstall under Wine doesn't do it. In the end, it'll remain supposedly installed, but it's not. Unless someone else has figured it out. I've redone my computer many times since so my woes are long gone, but I do know Itunes just doesn't work under Wine.

---

