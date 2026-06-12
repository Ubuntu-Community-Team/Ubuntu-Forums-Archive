---
title: "help understanding wine"
date: 2010-06-23
forum: General Help
---

### Post by blackhawx on 2010-06-23
I'm trying to wrap my finger around the use of wine.  I have star wars republic commando and star wars Jedi  academy cd's. So if i install wine from inside of ubuntu, then do i simply run the window video game cd's right from my desktop too?  Or do I have to log out, log into windows, install the game and then log back into ubuntu to play them???

Thanks for helping understand the best way to load window games into ubuntu

---

### Post by ronnielsen1 on 2010-06-23
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=4479](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4479)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2315](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2315)

Winehq is a great place to see of others have been successful at running windows software in wine and what tweaks (if any) they have had to do. You right click the file > Open with wine or wine /media/cdrom0/windowssoftware.exe on a terminal

[http://frankscorner.org/index.php?p=quickstart](http://frankscorner.org/index.php?p=quickstart)

---

### Post by blackhawx on 2010-06-23
I installed wine and ran setup.exe with wine.  It appeared to install correctly. But when i try to run the program I get a blank white screen pop-up window instead of the game window.  I didn't install direct x or anything like that - just the game.  any ideas?

---

### Post by blackhawx on 2010-06-23
> **ronnielsen1 said:**
> [http://appdb.winehq.org/objectManager.php?sClass=application&iId=4479](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4479)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2315](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2315)

Winehq is a great place to see of others have been successful at running windows software in wine and what tweaks (if any) they have had to do. You right click the file > Open with wine or wine /media/cdrom0/windowssoftware.exe on a terminal

[http://frankscorner.org/index.php?p=quickstart](http://frankscorner.org/index.php?p=quickstart)
[ronnielsen1]("http://ubuntuforums.org/member.php?u=61926") I am new to understanding the first game link you sent me.  All I see if a wine page that talks about the game.  what do I do once I get there?  Is there a patch on that page I am suppose to apply?  I have no idea - please help! (trying to get republic commandos up and running)

---

### Post by ronnielsen1 on 2010-06-24
>  I get a blank white screen pop-up window instead of the game window.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7255](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7255)

I couldn't find anything about the white screen. The posts I saw said it was supposed to work. You might try to edit your system.ini for the game
> Make sure to set NoDistort=True in the System.ini if the whole screen is rendered distorted.

to see if that helps. 
Another thing is in winecfg or Wine > Configure wine you might try different windows versions. Some software might work in XP but not in Vista. Also in the drives tab click on Autodetect > Apply, Try to install again and post errors. I'd try to install but I don't own the game

---

