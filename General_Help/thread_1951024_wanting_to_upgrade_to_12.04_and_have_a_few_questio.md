---
title: "wanting to upgrade to 12.04 and have a few questions"
date: 2012-04-01
forum: General Help
---

### Post by rollinsmoke on 2012-04-01
hi i have ubuntu 11.10 installed currently and was wanting to give 12.04 a shot but what i was wanting to know is actualy a wine question i guess but i have a few games such as diablo2 spore and obvilion installed if i take and copy the c: drive folders for those games to another harddrive then just replace them with my fresh install would that cause any problems would that work 

thanks for looking 
-chris

---

### Post by oldos2er on 2012-04-01
I don't know if that would work or not, I think you'd need to install any games or programs you want through Wine. But before you do, check the app database to see if there's any hope of getting them to run. [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by rollinsmoke on 2012-04-01
yea they all work now all i was mainly wondering is if i can backup my saved games mostly i can reinstall the game itself i just dont want to lose where im at in the game

---

### Post by grahammechanical on 2012-04-01
I am not on either my 11.10 or my 12,04 with wine at the moment so I am guessing.

There is a hidden file .wine notice the dot ( . ) in front of the name. If you set file manager to view hidden files you will see it in your home folder. That is the one you need to save.

I have not done what you want to do with wine programs but I have done it with Linux programs. After a re-install and downloading the programs I replaced the newly created dot folders with the older ones that I copied to a safe place. Then when I launched the program it picked up all my user settings and recently open documents and that kind of stuff. So, this may work with you.

You may have to replace the folders for each specific program in that wine folder. Or maybe simply replace the new dot wine folder with the earlier dot wine folder that you have a copy of.

Regards

---

### Post by 3Miro on 2012-04-01
I use wine quite a bit. I have a separate wine folder for each game that I am playing and I have all the games installed on a separate HDD. I used to distro-hop quite a lot and it was very easy to just mount the extra HDD and then play the game. The entire game installation is entirely contained within the folder, so you can copy/paste the folder to another location and it will work just fine. All you have to do is find the right folder, the default is .wine in your home directory, but it may another manually specified folder.

The only potential issue comes with the different versions of wine. If you move from an older to a newer version, then there is no issue. Most of the time, when you move from a newer version to an older version is no issue either. However, wine assumes that you are going up in version, so things may not work if you try to go back (hasn't happen to me, but it is possible).

---

### Post by rollinsmoke on 2012-04-01
awesome thanks i think im going to install a test copy and try it before i go through with the upgrade thanks for the help guys

---

