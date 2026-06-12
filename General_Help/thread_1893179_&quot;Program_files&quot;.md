---
title: "&quot;Program files&quot;"
date: 2011-12-09
forum: General Help
---

### Post by R15KY on 2011-12-09
Hi guys. Where is something like "Program files" on linux. I am using newest version of Ubuntu (11.10 i think), and because of some error in one game i must to "crack it" (patch it). I must to find folder where is that game installed. Can you help me how to do that...Please

---

### Post by lisati on 2011-12-09
Where the game gets stored can vary according to which game it is.

Is this a **_legal_** copy of the game that you need to patch? If not, we might not be able to help.

---

### Post by seawolf167 on 2011-12-09
[LIST=1]
[*]Is it a game you legally own? If not, sorry, we can't help you there
[*]What is the name of the game in question?
[*]What is the exact error message you are receiving?
[/LIST]

---

### Post by R15KY on 2011-12-09
Yea it's legal copy... and there is no message... Just some "loading" after double click, and than nothing... i was looking on the net for some tutorials, and there i saw that i must to "crack it" with some othher gta_sa_exe file... Now i don't know how to find directory ... It's about GTA San Andreas game, and i want to play it on multyplayer, but i can't because of that. On windows was working perfectly but now i dont know what to do...

---

### Post by seawolf167 on 2011-12-09
You'll have to use Wine to play the game

[WineHQ]("http://www.winehq.org/")
[Wine @ Ubuntu]("https://help.ubuntu.com/community/Wine")

```
sudo apt-get install wine
```

[Here ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3780")is the WineHQ page for that particular game, you can read through the test results and see what works and what doesn't.

It looks as if you need to use [this site ]("http://www.sa-mp.com/")to play online.

---

### Post by R15KY on 2011-12-09
Is there any way to get into the program files/rockstar games, because i don't understand ubuntu...
I am using wine, but i said, i cant start game with it (some loading and stop)...

---

### Post by |{urse on 2011-12-09
open the Terminal appication.

cd ~/.wine/drive_c/Program\ Files/

Thats where it is, to get there from a file-browser you  will need to enable the showing of hidden files.

---

