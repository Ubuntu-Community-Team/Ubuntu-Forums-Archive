---
title: "Wine cursor problem."
date: 2010-04-18
forum: General Help
---

### Post by NT2015 on 2010-04-18
I hope this is the right place for this, but I am having a bit of a issue with my cursor in wine. Its not all wine programs or games, just one game in particular. Now yesterday I had this game running perfect. But I ran into some problems with a different program and decided to uninstall and reinstall wine. I did so by opening synaptic and selecting "mark for complete removal" I also deleted the .wine folder in my home folder. Now, so far my other wine games, and programs seems to be running fine after i reinstalled wine. But whenever I go to play a game called "Battlezone II" I get an issue with my cursor. I suppose the best way to describe it would be that my systems cursor is moving faster than the games cursor. So lets say that both cursors are in the middle of the screen, if I were to move the mouse left, right, up or down. the systems cursor would reach the edge of my screen first, in-effect stopping the games cursor from moving any further than maybe a quarter of the way across the screen. Now the only cursor that is visible is the games cursor, until the system cursor reaches the edge of my screen, then there both visible.

I hope that I made this issue understandable. Its a little confusing for me too, its one of those things you'd really have to see. I really hope i can get some help with this issue as I know it can be fixed because the game worked fine until I reinstalled wine. But ive been at it for hours now, and I'm just at a complete loss. :confused:

System Info:
Ubuntu 9.10 64bit
Wine version: 1.2
Game version: 1.3 Public Beta 5.1 (this patch updates the games engine from directX6 to DirectX9)

---

### Post by jkxx on 2010-04-18
According to Wine's appdb, the game you mentioned works once you update it to version 1.2 (see [http://appdb.winehq.org/objectManager.php?sClass=application&iId=5633]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=5633") for the details).

I'd try that first before doing anything else. If that doesn't work, you could try getting winetricks and installing the directx files as those can help with some games. That's not a very good idea though so try updating the game first, hopefully that'll do it.

Good luck.

---

### Post by NT2015 on 2010-04-18
I currently have version 1.3 of the game which is supported with a silver rating 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10750](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10750)

I have tired using winetricks to install d3dx9.dll also dinput8.dll and vcrun2005, as they are required for the game to run. As I said, the game ran absolutely perfect until I uninstalled and reinstalled wine.

---

### Post by NT2015 on 2010-04-18
Ok so I fixed the cursor problem by going back to wine version 1.1 but now I have no sound in any wine apps which is the reason i reinstalled to begin with... so now im right back where I started

---

### Post by NT2015 on 2010-04-18
OK problem solved, but in a weird way. 

So I installed wine 1.1, and installed the game, and all necessary dependences. The game run just fine except there was no sound. 

I removed 1.1 and reinstalled wine 1.2, then installed the game again, and had sound but I then had the cursor problem again.

So what I did was reinstalled wine 1.1, installed and configured the game, I then upgraded from 1.1 to 1.2 using synaptic and now all is right with the world. :guitar:

See, one of the main reasons why even if the sound did work in 1.1 i would still have to of upgraded to 1.2 is because I actually managed to get Photoshop CS4 running perfectly in wine, but it only runs in 1.2 it will not run in any older versions. and I absolutely have to have Photoshop. And yes I know all about the GIMP, but frankly the ui for the GIMP is just horrible, something that takes me 10seconds in photoshop took me over an hour to figure out in GIMP and it still didn't look 100% right.

Thanks for all the help. I absolutely love this community, even though not all of my problems have been solved since I started using Ubuntu. every time I ask a question on these forums I at least get people doing the best they can to help, and that's all anyone can ever ask, and that's more than I ever got with windows.:P

---

### Post by bulldogue88 on 2011-08-23
hey as it stands right now alot of people are having trouble with cursor problems with wine 1.3...... especially with games through steam 1.2 is what im running and seems to be the most stable at the moment.

---

